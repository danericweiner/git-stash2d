# git-stash2d
`git-stash2d` -- Stash the changes between two commits to the file system.

Similar to `git-format-patch`/`git-apply` except patches are stored in an external, human-readable, directory structure so patches can be easily edited (or manually merged) with a program like [Beyond Compare](https://www.scootersoftware.com/).

------

## Synopsis

```shell
$ git stash2d save <commit> <commit> <directory> [<path>]
$ git stash2d apply <stash>
```

## Description

Use `stash2d` when you want to record the state of a commit and it's associated baseline commit. The command saves your local modifications to the file system in a baseline and code directory structure. 

The modifications stashed away by this command can be restored (potentially on top of a different commit) with `stash2d apply`. 

The stash you create is stored in the directory specified.

## Options

- `save <commit> <commit> <directory> [<path>]`


  Save the file modifications between two commits to a new stash entry in the specified directory. The `<path>` is optional and will only consider modifications to files below that path.

- `apply <stash> [<path>]`


  Apply a single stash on top of the current working tree state, i.e., do the inverse operation of `stash2d save`. The `<path>` is optional and will apply a stash saved with a `<path>` argument.

  Applying the stash can fail with conflicts; in this case you need to resolve the conflicts by hand. `<stash>` may be any folder structure that looks like a stash created by `stash2d save`.
