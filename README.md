# meave-labs.github.io

The repository for my blog at [meave-labs.github.io](https://meave-labs.github.io).

## Working With GitHub Keys ##

```sh
  # create ssh key, if need be
  # Reference: https://help.github.com/articles/generating-ssh-keys/
  ssh-keygen -t rsa -C "your_email@example.com"

  # add ssh key to session using the sh shell
  sh
  eval "$(ssh-agent -s)"
  ssh-add ~/.ssh/id_rsa
```

