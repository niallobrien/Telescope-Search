# Vscode - Telescope

Vscode - Telescope is a Visual Studio Code extension that provides a fast, interactive, and live file content search experience, inspired by Telescope for Neovim. It uses the power of `ripgrep` to deliver instant results and presents them in a clean, two-panel webview UI with a live code preview.

![Telescope Demo](https://raw.githubusercontent.com/TalhaAksoy/Telescope-Search/master/media/VSCode-Telescope.gif)

## Features

- **Real-time Search:** Optimized with 150ms debouncing for instant results as you type.
- **Fast & Efficient:**
  - Powered by `ripgrep` for high-performance searching.
  - Smart result limiting (max 500 results, 100 per file) prevents UI lag.
  - Optimized file tokenization renders only visible lines for 10x-100x faster previews.
- **Interactive UI:**
  - A dedicated webview panel for searching.
  - A list of results showing the file, line number (color-highlighted), and matching text.
  - A resizable preview panel with syntax highlighting that matches your current theme.
  - Auto-focus search field when returning to the panel for seamless workflow.
- **Keyboard & Mouse Navigation:**
  - Use `ArrowUp`/`ArrowDown` to navigate results and `Enter` to open the file.
  - Click an item to preview it, click it again to open.
- **Syntax Highlighting:**
  - The preview panel uses `shiki` to provide accurate and theme-aware syntax highlighting.
  - Full support for JavaScript, TypeScript, JSX, TSX, and many other languages.

## Prerequisites

This extension requires the command-line tool **`ripgrep`** to be installed on your system and available in your system's PATH. `ripgrep` is the engine that powers the search functionality.

### Installing `ripgrep`

- **macOS (via Homebrew):**

  ```sh
  brew install ripgrep
  ```

- **Windows (via Chocolatey or Scoop):**

  ```sh
  # Using Chocolatey
  choco install ripgrep

  # Using Scoop
  scoop install ripgrep
  ```

- **Linux (Debian/Ubuntu):**

  ```sh
  sudo apt-get install ripgrep
  ```

- **Other Platforms:** Please see the official [`ripgrep` installation instructions](https://github.com/BurntSushi/ripgrep#installation).

To verify the installation, open a terminal and run `rg --version`. You should see the version number printed.

## Installation

1.  Open Visual Studio Code.
2.  Go to the Extensions view (`Ctrl+Shift+X` or `Cmd+Shift+X`).
3.  Search for "Vscode - Telescope".
4.  Click "Install".

Alternatively, you can install it from the [VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TalhaAksoy.vscode-telescope). _(Note: You will need to publish the extension to the marketplace for this link to work.)_

## Usage

1.  Usage methods for VsCode - Telescope:

    - Press the keyboard shortcut: `Ctrl+Alt+T` (Windows/Linux) or `Cmd+Alt+T` (macOS).
    - Open the Command Palette (`Ctrl+Shift+P` or `Cmd+Shift+P`) and type "Telescope: Open Telescope Panel".

2.  The "Telescope Search" panel will open. Start typing in the search box at the bottom.

3.  Results will appear in the left panel as you type.

4.  Navigate the results with your mouse or arrow keys to see a live preview in the right panel.

5.  Press `Enter` or double-click a result to open the file and jump to the corresponding line.

## Development & Testing

If you wish to contribute to the development of this extension, you can set up a local development environment.

### Setup

1.  Clone the repository:

    ```sh
    git clone https://github.com/TalhaAksoy/Telescope-Search
    cd TelescopeSearch
    ```

2.  Install dependencies using `yarn` (as defined by the `.yarnrc` file):

    ```sh
    yarn install
    ```

3.  Compile the TypeScript code:
    ```sh
    npm run compile
    ```

### Running the Extension Locally

1.  Open the project folder in VS Code.
2.  Press `F5` to open a new Extension Development Host window with the extension running.
3.  In the new window, open a project folder and use the "Telescope: Open Telescope Panel" command to test the extension.

### Packaging for Installation

1.  Install the packaging tool:

    ```sh
    npm install -g @vscode/vsce
    ```

2.  Package the extension:

    ```sh
    vsce package
    ```

    This creates a `.vsix` file.

3.  Install the packaged extension:
    - Open VS Code
    - Press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux)
    - Type "Extensions: Install from VSIX..."
    - Select the generated `.vsix` file

## Performance Optimizations

This extension includes several performance optimizations for large codebases:

- **Search Debouncing:** 150ms delay prevents excessive searches while typing
- **Result Limiting:** Caps results at 500 items and 100 matches per file
- **Lazy Tokenization:** Only syntax-highlights ~100 lines around each match
- **Performance Logging:** Enable Developer Tools console to see `[PERF]` timing metrics
