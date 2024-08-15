# git story + story-trailer precommit

To automatically add a trailer to your commit messages, linking it back to the story you're working on.

```
git story TEAM-93
git commit -m "allow consumers to limit size of paginated results"
```

And get this commit message:

> allow consumers to limit size of paginated results
>
> Story: TEAM-93

## ⚙️ setup `git story`

Create a file for the git extension

```zsh
sudo curl https://raw.githubusercontent.com/jessicamann/precommit-hooks/main/git-story-template -o /usr/local/bin/git-story && sudo chmod +x /usr/local/bin/git-story
```

Make it executable

```zsh
chmod +x git-story
```

Now use it!
```
git story <story-id>
```

## 🤖 automate story link trailer with "story-trailer"

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
