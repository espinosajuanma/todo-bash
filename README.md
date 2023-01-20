# `todo` - Bash Script

This utility allows you to manage tasks in the terminal.

## Requirements

- Bash 4 or higher
- Git
- Set `$EDITOR` environment variable to your editor
- Set `$PAGER` environment variable to your pager

## Installation

Clone this repository and copy the executable file to some directory of
your `$PATH`.

```bash
git clone https://github.com/espinosajuanma/todo-bash.git
cp ./todo-bash/todo /dest/path
```

## Usage

- `todo` - Shows a full list of tasks
  - Except `archived` ones
- `todo todo` - Shows only `todo` tasks
- `todo working` - Shows only `working` tasks
- `todo finished` - Shows only `finished` tasks
- `todo archived` - Shows only `archived` tasks

## Configurations

By default it will create the appropiate folder structure in: `todo
config.dir`.

If you have a remote repository to store the git repository in a
platform as github or gitlab you can set it. Every change after commit
will be pushed automatically.

- `todo remote [remote-repository]`
  - Example: `todo remove git@github.com:espinosajuanma/todo.git`

### CRUD Actions

- `todo add <title>` - Create a task and open the editor
- `todo edit [id]` - Open the editor to edit a task body
- `todo show [id]` - Open the editor to edit a task
  - Alias: `view`
- `todo remove [id]` - Remove definitely a task
  - Alias: `rm`
  - Recommendation use: `archive` instead
  - Use only for maintenance purposes

### Transitions

Transitions commands allows you to move one task from one status to
other.

- `todo start [id]` - Move a task from `todo` to `working`
- `todo pause [id]` - Move a task from `working` to `todo`
- `todo finish [id]` - Move a task from `working` to `finished`
- `todo restart [id]` - Move a task from `finished` to `todo`
- `todo archive [id]` - Move a task from any status to `archived`
- `todo recover [id]` - Move a task from `archived` to `todo`

### History

- `todo log` - Check the git history
  - Each crud action or transitions creates a commit

### Files

- Files have `.md` extension (markdown)
- First line of your task file will be the `title`
- Title ignores the first `# ` so you can use a markdown header
- Ids are an `isosec` or ISO Second
  - `date -u '+%Y%m%d%H%M%S'` - year, month, day, hour, minutes and
    seconds all together

### Multiple lists

You can create a symlink of the `todo` script or just copy it with
another name.

```bash
ln -s /path/to/todo /path/to/new-todo
```

## Future

The goal in a future is to migrate this tool to a Go Lang CLI tool using
Bonzai commands composer.

## External credits

- The bash boilerplate was made by [rwxrob](https://github.com/rwxrob/template-bash-command)
- [isosec](https://github.com/rwxrob/zet/tree/110a0b86436b4ee5f0b845cde3c87b36dba3faf5/20210502052620)
