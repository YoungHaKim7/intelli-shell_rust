# link

- [(GeekNews에 올라온 한글 뉴스251012IntelliShell - 쉘을 위한 IntelliSense](#intellishell---쉘을-위한-intellisense)
  - [(Github Link) Like IntelliSense, but for shells](#intelli-shell_rust)
- [Install](#install)
- [backup 파일 관리]
  - [export & import](#backup파일로-만들어서-관리하면-될듯)

- [핵심 단축키 빨리 익혀서 빨리 사용하자Core Hotkeys](#core-hotkeys)
  - [자세한 문서 더 자세히 보고 싶으면 여기](#help--doc)


<hr />

# codeberg-cli

- macOS 토큰 저장 경로
```bash
Library/Application Support/berg-cli
$ ls
TOKEN
```

# intelli-shell_rust[|🔝|](#link)
- Like IntelliSense, but for shells 
  - https://github.com/lasantosr/intelli-shell

# install[|🔝|](#link)

- bash
  - https://github.com/lasantosr/intelli-shell/blob/main/default_config.toml

```
# For sh-compatible shells on Linux/macOS/Windows (Bash, Zsh, Fish, Nu, Git Bash)
curl -sSf https://raw.githubusercontent.com/lasantosr/intelli-shell/main/install.sh | sh  

# 설치위치
.local/share/intelli-shell 
$ ls
bin/  storage.db3

# To customize your configuration, copy this file to your user configuration directory or create a new one:
# ~/.config/intelli-shell/config.toml (on Linux)
# ~/Library/Application Support/org.IntelliShell.Intelli-Shell/config.toml (on macOS)
# %APPDATA%\IntelliShell\Intelli-Shell\config\config.toml (on Windows)
# $XDG_CONFIG_HOME/intelli-shell/config.toml (if XDG_CONFIG_HOME is set)

```

- Rust설치가 되어 있다면 이걸로(binstall먼저 설치해야함)


```bash
# 사전설치
cargo install cargo-binstall

# and

cargo binstall intelli-shell --locked


# 설치화면
cargo binstall intelli-shell --locked
 INFO the current QuickInstall statistics endpoint url="https://cargo-quickinstall-stats-server.fly.dev/record-install"

Binstall would like to collect install statistics for the QuickInstall project
to help inform which packages should be included in its index in the future.
If you agree, please type 'yes'. If you disagree, telemetry will not be sent.
You can change this at any time by editing the binstall settings file.
Opt in to telemetry? yes/[no] yes
 INFO Settings saved path="/home/g/.cargo/binstall.toml"
 INFO resolve: Resolving package: 'intelli-shell'
 WARN The package intelli-shell v3.2.3 (x86_64-unknown-linux-gnu) has been downloaded from github.com
 INFO This will install the following binaries:
 INFO   - intelli-shell => /home/g/.cargo/bin/intelli-shell
Do you wish to continue? [yes]/no yes
 INFO Installing binaries...
 INFO Done in 26.333942924s

```

# backup(파일로 만들어서 관리하면 될듯)[|🔝|](#link) 

- export
```
intelli-shell export my_commands.bak
```

- import
  - https://lasantosr.github.io/intelli-shell/reference/import.html
```
intelli-shell import my_commands.bak
```

- default 명령어
  ```
  intelli-shell tldr fetch
  ```

```bas
There are no stored commands yet!
    - Try to bookmark some command with 'Ctrl + B'
    - Or execute 'intelli-shell tldr fetch' to download a bunch of tldr's useful commands
```

# Core Hotkeys[|🔝|](#link)
- https://lasantosr.github.io/intelli-shell/guide/basic_usage.html#core-hotkeys
- By default, IntelliShell sets up several hotkeys. These are the primary ways you will interact with the tool.

- Search `Ctrl`+`Space`: This is your main entry point. It opens an interactive search UI to find your bookmarked commands. If you have text on the command line, it will be used as the initial search query.

- macOS에서 키 안 먹으면 `intelli-shell search -i git` 직접 쉘창에 입력해 주자 
```bash
# i 뒤에 찾고 싶은거
intelli-shell search -i git

# 그냥 search mode
intelli-shell search -i 
```

- Bookmark `Ctrl`+`B`: When you've typed a command you want to save, this key opens a UI to bookmark it. The current text on your command line will be pre-filled as the command to be saved.

- Fix Command `Ctrl`+`X`: When a command fails, press the up arrow to recall it, then use this key to let AI analyze the command and the error message to suggest a working version.

- Variable Replace `Ctrl`+`L`: If the command on your line contains `{{variables}}`, this key opens the variable replacement UI to fill them in without needing to save the command first.

- Clear Line `Esc`: As a convenience, this key is bound to clear the entire command line. This can be disabled if it conflicts with your existing terminal habits.
 
# help & doc[|🔝|](#link)
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

- claude로 만듬[|🔝|](#link)

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

# **[IntelliShell - 쉘을 위한 IntelliSense](<https://news.hada.io/topic?id=23553&utm_source=discord&utm_medium=bot&utm_campaign=1480>)**[|🔝|](#link)
- 쉘 명령어를 **구조화된 스니펫과 템플릿**으로 관리할 수 있게 해주는 **지능형 명령 라이브러리 도구**  
  - 단순히 이전 명령을 찾는 것이 아니라, **반복되는 작업을 자동화**하고 **재사용 가능한 명령 모음집**을 구성  
  - 쉘 명령을 북마크하거나 AI를 이용해 자동으로 수정·생성할 수 있음  
- **Bash**, …
