# "git story" + story-trailer precommit

To automatically add a trailer to your commit messages, linking it back to the story you're working on.

```
git story ST-93
git commit -m "allow consumers to limit size of paginated results"
```

And get this commit message:

> allow consumers to limit size of paginated results
>
> Jira: ST-93

## setup "git story"

Create a file for the git extension

```zsh
cp git-story-template git-story
```

Make it executable

```zsh
chmod +x git-story
```

Move git-story to a place executables should live

```zsh
sudo mv git-story /usr/local/bin
```

Now use it!
```
git story <story-id>
```

## automate jira trailer with "story-trailer"

In your `.pre-commit-config.yaml`, add the hook

```yaml
# by default, only 'pre-commit' is intalled
# if you do not already have "prepare-commit-msg",
# make sure to run "pre-commit  install" again
default_install_hook_types: [pre-commit,prepare-commit-msg]
repos:
-   ...your other hooks
-   repo: https://laksdjlfkjl/our-hooks-repo
    hooks:
    -   id: story-trailer
        name: Add jira ref to commit trailer
        entry: story-trailer
        stages: [prepare-commit-msg]
        language: script
```
