# Log Filter Tool - Quick Reference

## Installation
```bash
git clone https://github.com/yourusername/log-filter-tool.git
cd log-filter-tool
```

## Basic Usage
```bash
python log_tool.py [OPTIONS]
```

## Options
| Option | Type | Description | Example |
|--------|------|-------------|---------|
| `--level` | string | Filter by log level | `--level ERROR` |
| `--service` | string | Filter by service name | `--service auth` |
| `--out` | string | Output filename | `--out results.txt` |

## Valid Log Levels
- `INFO`
- `WARN`
- `ERROR`

## Common Commands

### Filter by Level
```bash
python log_tool.py --level ERROR
python log_tool.py --level WARN
python log_tool.py --level INFO
```

### Filter by Service
```bash
python log_tool.py --service auth --out auth_logs.txt
python log_tool.py --service api --out api_logs.txt
python log_tool.py --service db --out db_logs.txt
```

### Combine Filters
```bash
python log_tool.py --level WARN --service api --out warn_api.txt
python log_tool.py --level ERROR --service db --out error_db.txt
```

### Use Default Output
```bash
python log_tool.py --level INFO
# Creates: filtered_logs.txt
```

## Output Format
All output files contain valid log entries in this format:
```
timestamp | LEVEL | service | message
```

## Terminal Output
After each run, you'll see:
```
Valid lines scanned: X
Lines written: Y
Output file: filename
```

## Log Format Rules

### Valid Line
```
2026-02-05 08:11:20 | ERROR | db | DB timeout while fetching user profile
```
✅ Has 4 fields separated by `|`
✅ Level is INFO, WARN, or ERROR
✅ All fields contain data

### Invalid Lines (Automatically Skipped)
```
BAD LINE WITHOUT SEPARATORS
```
❌ Missing separators

```
INCOMPLETE | LINE | HERE
```
❌ Only 3 fields

```
2026-02-05 08:11:50 | DEBUG | api | Debug mode message
```
❌ Invalid level (DEBUG)

## Tips
- Case-insensitive level matching: `--level error` works
- Service names are case-sensitive
- Invalid lines are silently ignored
- Empty output file is created if no matches found

## Examples

**All errors:**
```bash
python log_tool.py --level ERROR
```

**Authentication service logs:**
```bash
python log_tool.py --service auth --out auth_logs.txt
```

**Critical API warnings:**
```bash
python log_tool.py --level WARN --service api
```
