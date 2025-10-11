# link


<hr />

# intelli-shell_rust
- Like IntelliSense, but for shells 
  - https://github.com/lasantosr/intelli-shell

# install

```bash
cargo binstall intelli-shell --locked
```

# backup(파일로 만들어서 관리하면 될듯)

- export
```
intelli-shell export my_commands.bak
```

- import
  - https://lasantosr.github.io/intelli-shell/reference/import.html
```
intelli-shell import my_commands.bak
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

- claude로 만듬

```
I've successfully added 100 additional git commands with descriptions to your my_commands.bak file. The
  commands cover a wide range of Git functionality including:

  - Basic repository operations (init, clone, status, add, commit)
  - Branch management (branch, switch, merge, rebase)
  - History and diff operations (log, diff, show, blame)
  - Remote repository operations (remote, fetch, pull, push)
  - Tagging (tag)
  - Stashing (stash)
  - Patching (format-patch, apply)
  - Configuration (config)
  - Advanced operations (bisect, reflog, cherry-pick)

  Each command follows the format you specified with a # comment describing the command's purpose and the
  actual git command below it.
```

# **[IntelliShell - 쉘을 위한 IntelliSense](<https://news.hada.io/topic?id=23553&utm_source=discord&utm_medium=bot&utm_campaign=1480>)**
- 쉘 명령어를 **구조화된 스니펫과 템플릿**으로 관리할 수 있게 해주는 **지능형 명령 라이브러리 도구**  
  - 단순히 이전 명령을 찾는 것이 아니라, **반복되는 작업을 자동화**하고 **재사용 가능한 명령 모음집**을 구성  
  - 쉘 명령을 북마크하거나 AI를 이용해 자동으로 수정·생성할 수 있음  
- **Bash**, …
