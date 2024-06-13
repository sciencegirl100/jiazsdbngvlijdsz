## Git Config

### Git Alias

To use add to ~/.gitconfig under "\[alias\]"

- list all untracked files that aren't in .gitignore

<!-- -->

    ls-untracked = "!git ls-files --other --exclude-standard"

- shorthand for "pull --rebase"

<!-- -->

    up = "!git pull --rebase"

- list all untracked files not in .gitignore and wait for for user to
  press enter, then "pull --rebase" and push changes

<!-- -->

    sync = "!sh -c 'git_sync(){ git ls-untracked ; echo press enter to continue; read junk ;git up $* ;git push $* ; } ;git_sync $@'"