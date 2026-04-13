# LineSight

LineSight is a VS Code extension that shows the number of lines next to each file in the file explorer, helping you quickly understand the size of files in your project.

The extension is available on the VSCode Marketplace for installing:

https://marketplace.cursorapi.com/items?itemName=2048Labs.linesight

## Why I built this?

A common issue with LLM's is the size of the context window, and even though modern IDE's like Cursor support better chunking and indexing for large files, it still performs much better when working with smaller files.

LineSight allows you to quickly glance at line counts to understand when you need to refactor a particular file.

Efficient caching, progressive loading and prioritization make this extension very performant when running in the background.

Hope you find it useful :)

<img src="resources/images/logo.png" width="128" height="128" alt="LineSight Logo">

## Features

- **Line Count Badges**: Shows the number of lines next to each file in the explorer
- **Auto-Updates**: Line counts automatically update when files are edited
- **Refresh Button**: Provides a refresh button in the explorer title bar to manually update counts
- **Abbreviated Display**: Shows compact counts (like "2K", "+K", and "HK") as badges
- **Exact Counts in Tooltips**: Hover over a badge to see the exact line count
- **Customizable Badge Colors**: Supports theme color overrides for each line-count range
- **Skip Large Directories**: Ignores directories like node_modules and .git for better performance
- **Optimized Performance**: Minimal background overhead with smart caching and throttling

## Screenshot

![LineSight in action](resources/images/screenshot.png)

## Usage

Once installed, LineSight will automatically display line counts next to your files in the explorer panel.

- **Refresh Counts**: Click the refresh icon in the explorer title bar to manually refresh line counts
- **View Exact Count**: Hover over a line count badge to see the exact number of lines in the tooltip

## Performance Considerations

- For very large files (over 5MB), line counts are estimated based on file size
- Certain directories are skipped by default to improve performance: node_modules, .git, dist, build, out
- The extension uses smart caching to minimize CPU usage
- File watchers are limited to common code file types to reduce overhead
- Updates are debounced and throttled to prevent performance impact

## Installation

1. Install the extension from the VS Code Marketplace
2. Reload VS Code Window
3. Line counts will automatically appear next to files in the explorer

## Extension Settings

LineSight badge colors can be customized with VS Code theme color overrides in `settings.json`:

```json
{
  "workbench.colorCustomizations": {
    "linesight.count.zero": "#808080",
    "linesight.count.ones": "#6A9955",
    "linesight.count.tens": "#4EC9B0",
    "linesight.count.hundreds": "#DCDCAA",
    "linesight.count.thousands": "#CE9178",
    "linesight.count.tenThousands": "#F48771",
    "linesight.count.hundredThousands": "#C586C0",
    "linesight.count.millions": "#F44747"
  }
}
```

Badge ranges:

- `0`: `0`
- `1` to `9`: raw count
- `10` to `99`: raw count
- `100` to `999`: `1H` to `9H`
- `1,000` to `9,999`: `1K` to `9K`
- `10,000` to `99,999`: `+K`
- `100,000` to `999,999`: `HK`
- `1,000,000+`: `1M`, `2M`, and higher

## License

This extension is licensed under the MIT License. 
