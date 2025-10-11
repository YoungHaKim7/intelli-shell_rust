# intelli-shell_rust
- Like IntelliSense, but for shells 
  - https://github.com/lasantosr/intelli-shell

# install

```bash
cargo binstall intelli-shell --locked
```

# Core Hotkeys
- https://lasantosr.github.io/intelli-shell/guide/basic_usage.html#core-hotkeys
- By default, IntelliShell sets up several hotkeys. These are the primary ways you will interact with the tool.

- Search `Ctrl`+`Space`: This is your main entry point. It opens an interactive search UI to find your bookmarked commands. If you have text on the command line, it will be used as the initial search query.

- Bookmark `Ctrl`+`B`: When you've typed a command you want to save, this key opens a UI to bookmark it. The current text on your command line will be pre-filled as the command to be saved.

- Fix Command `Ctrl`+`X`: When a command fails, press the up arrow to recall it, then use this key to let AI analyze the command and the error message to suggest a working version.

- Variable Replace `Ctrl`+`L`: If the command on your line contains `{{variables}}`, this key opens the variable replacement UI to fill them in without needing to save the command first.

- Clear Line `Esc`: As a convenience, this key is bound to clear the entire command line. This can be disabled if it conflicts with your existing terminal habits.
 
# help & doc
- https://lasantosr.github.io/intelli-shell/

```bash
 intelli-shell help
Like IntelliSense, but for shells

Interactive commands are best used with the default shell bindings:
- `ctrl+space` to search for commands
- `ctrl+b` to bookmark a new command
- `ctrl+l` to replace variables from a command
- `ctrl+x` to fix a command that is failing

Usage: intelli-shell <COMMAND>

Commands:
  init        Generates the shell integration script
  new         Bookmarks a new command
  search      Search stored commands
  replace     Replace the variables of a command
  fix         Fix a command that is failing
  export      Exports stored user commands and completions to an external location
  import      Imports user commands and completions from an external location
  tldr        Manages tldr integration
  completion  Manages dynamic completions for variables
  update      Updates intelli-shell to the latest version if possible, or shows update instructions
  help        Print this message or the help of the given subcommand(s)

Options:
  -h, --help
          Print help (see a summary with '-h')

  -V, --version
          Print version

Examples:
  # Open an interactive interface to bookmark a new command (ctrl+b)
  intelli-shell new -i

  # Interactively search stored commands, initially filtering for "git" (ctrl+space)
  intelli-shell search -i git

  # Interactively replace variables in a command (ctrl+l)
  intelli-shell replace -i "echo {{message}}"

  # Fix a command that is failing (ctrl+x)
  intelli-shell fix "git comit amend"

  # Store a command non-interactively
  intelli-shell new "find . -name '*.py'" --alias "lp" --description "Find Python files" 

  # Export all user commands
  intelli-shell export user.commands

  # Interactively import user commands
  intelli-shell import -i user.commands

  # Fetch useful commands from tldr
  intelli-shell tldr fetch

  # Remove commands imported from tldr
  intelli-shell tldr clear

  # Adds a dynamic completion for any variable called {{branch}} on 'git' commands
  intelli-shell completion new --command git branch "git branch --format='%(refname:short)'"

  # Lists stored completions interactively
  intelli-shell completion list -i

```
