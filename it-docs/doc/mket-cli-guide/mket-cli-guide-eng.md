---
icon: calendar-lines-pen
---

# mket cli Guide (ENG)

| Item             | Detail      |
| ---------------- | ----------- |
| Document version | 1.0         |
| Issue date       | 14 May 2026 |

`mket-cli` is a command-line tool that generates the `MKET_PF_SUMMARY_T1_YYYYMMDD.txt` report file according to the customer's spec and places it into the customer's output directory (for example, the network share `\\mbketh\Reportmail\PF`).

{% hint style="info" %}
**Why it runs on the customer's machine** The tool is designed to run **one-shot** (run and exit — no daemon loop) via Task Scheduler on Windows or cron on Linux on the customer's machine. This is because the Level11 server container cannot write files to the customer's network share directly.
{% endhint %}

## How It Works

Each time `mket-cli` runs, it performs the following steps:

{% stepper %}
{% step %}
### Calculate the trigger date

End of the previous month + `run_days_after_eom` business days (skipping weekends and holidays from the specified calendar).
{% endstep %}

{% step %}
### Check whether today matches the trigger date

* If it **matches** trigger → log in → fetch the file via the API `/api/public/v1/report.nav.exportMket` → write it to `output_dir`.
* If it **does not match** trigger→ exit silently (unless `catchup: true` is enabled and the file for that value date does not yet exist).
{% endstep %}
{% endstepper %}

## Prerequisites

Make sure the following are ready before installation:

* Installation file — `mket-cli.exe` (Windows) or `mket-cli` (Linux)
* Sample config file — `config.example.yaml`
* A Level11 user account with the `report.*` and `masterfile.other.*` permissions
* Write access to the destination output directory / network share

***

## 1. Install on the Customer's Machine

{% tabs %}
{% tab title="Windows" %}
1. Create a folder, e.g. `C:\mket-cli\`
2. Copy `dist/mket-cli.exe` into the folder
3. Copy `cmd/mket-cli/config.example.yaml` into the same folder and rename it to `config.yaml`
4. Edit the values in `config.yaml` as needed (see [2. Configuration](mket-cli-guide-eng.md#2-configuration))
{% endtab %}

{% tab title="Linux" %}
```bash
sudo mkdir -p /opt/mket-cli
sudo cp dist/mket-cli /opt/mket-cli/
sudo cp cmd/mket-cli/config.example.yaml /opt/mket-cli/config.yaml
sudo chmod +x /opt/mket-cli/mket-cli
```

Then edit the values in `/opt/mket-cli/config.yaml` as needed (see [2. Configuration](mket-cli-guide-eng.md#2-configuration))
{% endtab %}
{% endtabs %}

***

## 2. Configuration

The full set of default values is available in `config.example.yaml`. The key fields are:

<table><thead><tr><th>Field</th><th width="115" align="center">Required</th><th width="393">Description</th></tr></thead><tbody><tr><td><code>api_base_url</code></td><td align="center">✅</td><td>URL of the Level11 server (do not include a trailing <code>/</code>)</td></tr><tr><td><code>auth_type</code></td><td align="center">—</td><td><code>"password"</code> (default) or <code>"token"</code> (not yet supported on the server side)</td></tr><tr><td><code>username</code> / <code>password</code></td><td align="center">✅</td><td>Must be a user with the <code>report.*</code> + <code>masterfile.other.*</code> permissions — supports <code>${ENV_VAR}</code> references</td></tr><tr><td><code>calendar_codes</code></td><td align="center">✅</td><td>e.g. <code>["TH"]</code> — holidays are merged as a distinct set across all listed codes</td></tr><tr><td><code>run_days_after_eom</code></td><td align="center">✅</td><td>Number of business days after end-of-month to trigger (<code>1</code> = first business day of the next month)</td></tr><tr><td><code>output_dir</code></td><td align="center">✅</td><td>Destination for the output file — see <a href="mket-cli-guide-eng.md#output-path">Output path</a></td></tr><tr><td><code>filename_pattern</code></td><td align="center">—</td><td>Defaults to <code>MKET_PF_SUMMARY_T1_${DATE}.txt</code>; supports <code>${DATE}</code> and <code>${DATE:&#x3C;go-layout>}</code></td></tr><tr><td><code>timezone</code></td><td align="center">—</td><td>IANA timezone, e.g. <code>Asia/Bangkok</code> (default)</td></tr><tr><td><code>catchup</code></td><td align="center">—</td><td><code>true</code> = if today is past the trigger date and the file for that value date does not yet exist, generate it retroactively</td></tr><tr><td><code>log_file</code></td><td align="center">—</td><td>Path to the log file (relative to the working directory)</td></tr><tr><td><code>timeout_seconds</code></td><td align="center">—</td><td>HTTP timeout in seconds (default <code>60</code>)</td></tr></tbody></table>

{% hint style="warning" %}
**Always set `timezone` explicitly** Do not rely on the machine's locale. If `timezone` is not set, or the machine is set to UTC, the trigger date may be off by one day.
{% endhint %}

### Output path

On **Windows**, three formats are accepted:

```yaml
output_dir: "\\\\mbketh\\Reportmail\\PF"   # UNC + escaped backslash
output_dir: '\\mbketh\Reportmail\PF'       # UNC + single quote
output_dir: "C:/mket-out"                  # drive + forward slash
```

On **Linux**, use a normal absolute path, e.g. `/mnt/mket-out`

### Credentials

{% hint style="danger" %}
**Never put the password as plain text in the YAML file** Use `${ENV_VAR}` in the config file, and set the environment variable in Task Scheduler / systemd / cron instead.
{% endhint %}

{% tabs %}
{% tab title="Windows" %}
Set the environment variable at the Machine level via PowerShell:

```powershell
[Environment]::SetEnvironmentVariable("MKET_CLI_PASSWORD", "xxxx", "Machine")
```
{% endtab %}

{% tab title="Linux" %}
Set the value in a systemd unit via `Environment=`, or use a wrapper script (see the cron example).
{% endtab %}
{% endtabs %}

***

## 3. CLI Flags

```bash
mket-cli [-config PATH] [-date YYYY-MM-DD] [-dry-run] [-verbose]
```

Running `mket-cli -help` produces:

```
Usage of mket-cli:
  -config string
        Path to YAML config file (default "config.yaml")
  -date string
        Override value date (YYYY-MM-DD). If set, skip the trigger-day check
  -dry-run
        Do everything except the final API call and file write
  -verbose
        Verbose logging
```

| Flag       | Default       | Use when                                                                               |
| ---------- | ------------- | -------------------------------------------------------------------------------------- |
| `-config`  | `config.yaml` | Specifying the path to the config file                                                 |
| `-date`    | —             | Forcing a value date (skips the trigger-day check) — for retroactive reruns or testing |
| `-dry-run` | `false`       | Doing every step except the actual export API call and file write                      |
| `-verbose` | `false`       | Producing detailed logs                                                                |

{% hint style="info" %}
**Exit codes** `0` = normal operation (including when it is not a trigger day) — `1` = an error occurred
{% endhint %}

***

## 4. Smoke Test Before Scheduling

Before setting up the real schedule, test with `-dry-run` first:

{% tabs %}
{% tab title="Windows" %}
```bash
C:\mket-cli\mket-cli.exe -config C:\mket-cli\config.yaml -verbose -dry-run
```
{% endtab %}

{% tab title="Linux" %}
```bash
/opt/mket-cli/mket-cli -config /opt/mket-cli/config.yaml -verbose -dry-run
```
{% endtab %}
{% endtabs %}

Check the log to confirm that:

* Login succeeds
* Holiday data is fetched successfully
* The trigger date is calculated correctly

Then test a real run by forcing a value date:

```bash
mket-cli -config config.yaml -date 2026-01-31 -verbose
```

Open the file at `output_dir` to confirm it was written successfully.

***

## 5. Troubleshooting

| Symptom                                     | Common cause and fix                                                                                                                                 |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Exit 0 but no file**                      | Not a trigger day — check with `-verbose -date YYYY-MM-DD`                                                                                           |
| **`auth failed`**                           | Wrong username/password, or the environment variable was not expanded (on Windows it must be set at the Machine level, not the current User session) |
| **`permission denied` when writing to UNC** | The task is running under an account without share access — change "Run as" in Task Scheduler                                                        |
| **Trigger date off by one day**             | `timezone` is not set, or the machine is on UTC — set `timezone: "Asia/Bangkok"` explicitly                                                          |
| **Missed run (machine was down)**           | Enable `catchup: true` together with the "Run as soon as possible after missed start" option in Task Scheduler                                       |
| **`holidays empty`**                        | `calendar_codes` is incorrect, or the user lacks the `masterfile.other.*` permission                                                                 |

{% hint style="success" %}
If the issue persists after checking the table above, please contact the Level11 team and attach the log file (run with `-verbose`) so we can investigate more quickly.
{% endhint %}
