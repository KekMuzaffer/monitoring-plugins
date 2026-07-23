# monitoring-plugins

A collection of custom monitoring plugins for Nagios and Icinga, written primarily in Bash. Each plugin lives in its own folder with its own usage instructions and follows standard Nagios exit-code conventions.

## Exit code convention

| Code | Meaning   |
|------|-----------|
| 0    | OK        |
| 1    | WARNING   |
| 2    | CRITICAL  |
| 3    | UNKNOWN   |

## Plugins

| Plugin | Description | Exit codes used |
|---|---|---|
| [check_tripwire_report](./check_tripwire_report) | Verifies that Tripwire IDS reports are being generated on schedule | 0 = OK, 2 = CRITICAL |

More plugins will be added over time.

## Installation

Clone the repo and copy the plugin you need into your monitoring server's plugin directory (e.g. `/usr/lib/nagios/plugins/` or `/usr/lib64/nagios/plugins/`):

```bash
git clone https://github.com/KekMuzaffer/monitoring-plugins.git
cp monitoring-plugins/check_tripwire_report/check_tripwire_report.sh /usr/lib/nagios/plugins/
chmod +x /usr/lib/nagios/plugins/check_tripwire_report.sh
```

## Requirements

- Bash
- Nagios or Icinga (or any monitoring system that supports standard plugin exit codes)

## Contributing

Issues and pull requests are welcome — especially new plugins that follow the same folder/exit-code structure.

## License

MIT — see [LICENSE](./LICENSE).

## Author

[KekMuzaffer](https://github.com/KekMuzaffer)
