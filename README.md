# git story + story-trailer precommit

This repo contains two utilities:
1. a git extension `git story` to set the context of the story being worked on.
2. a pre-commit hook `story-trailer` that works with [pre-commit](https://pre-commit.com/) to automatically add story trails to your commit messages.

<br>

## ⚙️ setup `git story`

Create a file for the git extension.

⚠️ Always read any script before downloading or executing script from the internet ⚠️

```zsh
sudo curl https://raw.githubusercontent.com/jessicamann/precommit-hooks/main/git-story-template -o /usr/local/bin/git-story && sudo chmod +x /usr/local/bin/git-story
```

Now use it!
```
git story
```

## 🤖 add "story-trailer" hoook to your repo

In your `.pre-commit-config.yaml`, add the hook

```yaml
# by default, only 'pre-commit' is installed
# if you do not already have "prepare-commit-msg",
# make sure to run "pre-commit  install" again
default_install_hook_types: [pre-commit,prepare-commit-msg]
repos:
-   ...your other hooks
-   repo: https://github.com/jessicamann/precommit-hooks
    rev: v0.0.1
    hooks:
    -   id: story-trailer
```
