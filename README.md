# dotfiles

fish, kitty, pi, and starship configs, managed with
[GNU Stow](https://www.gnu.org/software/stow/) — each package mirrors its
`$HOME` path and is symlinked into place.

| Package  | Home path                 |
| -------- | ------------------------- |
| fish     | `~/.config/fish`          |
| kitty    | `~/.config/kitty`         |
| pi       | `~/.pi/agent`             |
| starship | `~/.config/starship.toml` |

## Requirements

- **git**
- **stow**
- **fish**
- **kitty**

## Usage

```sh
git clone https://github.com/carlouinely/dotfiles ~/.dotfiles # 1
stow -t ~ fish kitty pi starship                              # 2
cd ~/.pi/agent/npm && npm ci                                  # 3
pi list                                                       # 4
npm install -g agent-browser                                  # 5
agent-browser --version                                       # 6
```

> **1. `git clone`** — Fetches the repo into `~/.dotfiles`, which the rest
> of this assumes is where it lives.
>
> **2. `stow`** — Symlinks each package directory to its `$HOME` path, so
> `pi/.pi/agent` becomes `~/.pi/agent` and your edits stay in this repo.
>
> **3. `npm ci`** — Pi's packages are declared in
> `pi/.pi/agent/settings.json` and pinned in `npm/package-lock.json`. That
> npm dir is what stow links to `~/.pi/agent/npm`, so `npm ci` installs the
> exact pinned versions pi needs at runtime, and the lockfile stays tracked
> here.
>
> **4. `pi list`** — Confirms pi can load everything from the symlinked dir.
>
> **5. `npm install -g agent-browser`** — A standalone browser CLI that pi's
> automation calls as a binary, so it lives on your system PATH rather than
> in the repo. `--version` confirms the install.
