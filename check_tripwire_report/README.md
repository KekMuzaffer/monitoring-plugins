# check_tripwire_report

Verifies that Tripwire IDS reports are being generated on schedule. Designed for use as a Nagios/Icinga check plugin.

## Usage

```bash
./check_tripwire_report.sh
```

## Requirements

- Bash
- Tripwire installed and configured to write reports to `/var/lib/tripwire/report/`

## Exit codes

| Code | Meaning  |
|------|----------|
| 0    | OK — reports are current |
| 2    | CRITICAL — no recent report found |

## Configuration

Edit these variables at the top of the script if your setup differs:

- `TRIPWIRE_REPORT_PATH` — path to the Tripwire report directory
- `CRITICAL_TIME` — threshold (in `YYYYMMDDHHMMSS`-difference units) before a report is considered stale
