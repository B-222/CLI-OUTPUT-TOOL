# Log Filter CLI Tool

A command-line tool for filtering and analyzing cloud service logs. This tool reads log files, validates entries, and filters them based on log level and service name.

## Features

- ✅ Reads and validates log file entries
- ✅ Filters by log level (INFO, WARN, ERROR)
- ✅ Filters by service name
- ✅ Combines multiple filters
- ✅ Exports filtered results to a file
- ✅ Provides summary statistics

## Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/log-filter-tool.git
cd log-filter-tool
```

2. Ensure you have Python 3.6+ installed:
```bash
python --version
```

## Usage

### Basic Commands

**Filter by log level:**
```bash
python log_tool.py --level ERROR
```

**Filter by service:**
```bash
python log_tool.py --service auth --out auth_logs.txt
```

**Combine filters:**
```bash
python log_tool.py --level WARN --service api --out warn_api.txt
```

### Command-Line Arguments

| Argument | Description | Required | Default |
|----------|-------------|----------|---------|
| `--level` | Filter by log level (INFO, WARN, ERROR) | No | None |
| `--service` | Filter by service name | No | None |
| `--out` | Output filename | No | filtered_logs.txt |

## Log Format

Valid log entries must follow this format:
```
timestamp | level | service | message
```

**Example:**
```
2026-02-05 08:11:20 | ERROR | db | DB timeout while fetching user profile
```

### Validation Rules

A log line is considered valid if:
- It has exactly 4 fields separated by `|`
- The log level (case-insensitive) is one of: INFO, WARN, ERROR
- All fields are non-empty after stripping whitespace

Invalid lines are automatically ignored.

## Example Usage

### Example 1: Filter ERROR logs

**Command:**
```bash
python log_tool.py --level ERROR
```

**Output (filtered_logs.txt):**
```
2026-02-05 08:11:20 | ERROR | db | DB timeout while fetching user profile
2026-02-05 08:12:30 | ERROR | billing | Payment gateway unreachable
2026-02-05 08:13:15 | ERROR | auth | Invalid token detected
```

**Terminal Output:**
```
Valid lines scanned: 10
Lines written: 3
Output file: filtered_logs.txt
```

### Example 2: Filter by service

**Command:**
```bash
python log_tool.py --service auth --out auth_logs.txt
```

**Output (auth_logs.txt):**
```
2026-02-05 08:11:02 | INFO | auth | User login success
2026-02-05 08:12:01 | WARN | auth | Multiple failed login attempts
2026-02-05 08:13:15 | ERROR | auth | Invalid token detected
```

**Terminal Output:**
```
Valid lines scanned: 10
Lines written: 3
Output file: auth_logs.txt
```

### Example 3: Combine filters

**Command:**
```bash
python log_tool.py --level WARN --service api --out warn_api.txt
```

**Output (warn_api.txt):**
```
2026-02-05 08:11:25 | WARN | api | Slow response detected (920ms)
2026-02-05 08:13:00 | WARN | api | Rate limit approaching threshold
```

**Terminal Output:**
```
Valid lines scanned: 10
Lines written: 2
Output file: warn_api.txt
```

## Project Structure

```
log-filter-tool/
│
├── log_tool.py          # Main CLI tool
├── logs.txt             # Sample input file
├── filtered_logs.txt    # Default output file (generated)
├── README.md            # This file
├── run_proof.txt        # Example runs (for submission)
└── .gitignore          # Git ignore file
```

## Development

### Running Tests

Test the tool with the provided sample data:

```bash
# Test level filtering
python log_tool.py --level ERROR

# Test service filtering
python log_tool.py --service auth --out auth_logs.txt

# Test combined filtering
python log_tool.py --level WARN --service api
```

### Code Structure

The tool consists of these main functions:

- `parse_line()` - Parses and validates log line format
- `is_valid_level()` - Validates log level
- `matches_filters()` - Checks if a log entry matches filter criteria
- `build_arg_parser()` - Sets up command-line argument parsing
- `main()` - Main execution flow

## Requirements

- Python 3.6 or higher
- No external dependencies (uses only standard library)

## License

This project is created for educational purposes as part of PL202 coursework.

## Contributing

This is an individual assignment project. Contributions are not accepted.

## Author

Created as part of PL202 - Day 2 assignment
