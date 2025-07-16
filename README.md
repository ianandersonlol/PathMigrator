# PathMigrator

A simple tool to replace file paths in text files across directory structures. Originally designed to migrate from `/share/siegellab/` to `/quobyte/jbsiegelgrp/` but can be used for any path replacement task.

## Requirements

- Python 3.6 or higher
- No additional dependencies required

## Installation

1. Download or clone this repository
2. Make the script executable (optional):
   ```bash
   chmod +x pathmigrator.py
   ```

## Usage

### Basic Usage

Replace the default paths in the current directory:
```bash
python pathmigrator.py
```

Replace paths in a specific directory:
```bash
python pathmigrator.py /path/to/your/directory
```

### Custom Path Replacement

Replace any custom paths:
```bash
python pathmigrator.py --old-path "/old/path/" --new-path "/new/path/" /target/directory
```

### Preview Changes (Dry Run)

See what changes would be made without actually modifying files:
```bash
python pathmigrator.py --dry-run
```

### Examples

1. **Preview changes in current directory:**
   ```bash
   python pathmigrator.py --dry-run
   ```

2. **Replace custom paths in a specific directory:**
   ```bash
   python pathmigrator.py --old-path "/home/user/" --new-path "/Users/user/" ~/Documents
   ```

3. **Process a directory with dry run first:**
   ```bash
   # First, see what would change
   python pathmigrator.py --dry-run ~/my-project
   
   # Then apply the changes
   python pathmigrator.py ~/my-project
   ```

## What Files Are Processed

The tool automatically detects and processes text files including:
- Source code files (.py, .js, .c, .cpp, .java, .r, etc.)
- Configuration files (.ini, .cfg, .conf, .yaml, .yml, .json)
- Documentation files (.md, .rst, .txt)
- Data files (.csv, .log, .dat)
- Web files (.html, .css, .xml)
- Script files (.sh, .bash)

Binary files are automatically skipped to prevent corruption.

## Command Line Options

- `directory` - Target directory to process (default: current directory)
- `--dry-run` - Preview changes without modifying files
- `--old-path` - Path to replace (default: `/share/siegellab/`)
- `--new-path` - Replacement path (default: `/quobyte/jbsiegelgrp/`)

## Safety Features

- **Dry run mode**: Always test your changes first
- **Text file detection**: Only processes text files, skips binaries
- **Error handling**: Continues processing even if individual files fail
- **Encoding support**: Handles UTF-8 encoded text files
- **Summary reporting**: Shows how many files were checked and modified

## Tips

1. **Always use dry run first** to preview changes
2. **Backup your files** before running the tool
3. **Use absolute paths** for clarity
4. **Test on a small directory** first if unsure
5. **Check the summary** to verify expected number of changes

## Troubleshooting

- If you get permission errors, make sure you have write access to the target directory
- If the script doesn't find files to process, check that you're in the right directory
- Use `--dry-run` to debug what files would be processed
- The tool processes files recursively, so it will go through all subdirectories