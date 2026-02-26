# Git Tips

This file covers different, advanced use cases of git with practical shell examples.

## Pull Requests

### Finding source of conflicts

💡 **Did you ever wondered where a PR conflict comes from?**

With a lot of stuff merged on the default branch, e.g. `develop`, between opening the PR and finally merging it quite some time can pass.

On the command line you can run the following for the conflicting file, which will give you
* **author**
* **commit message**
* **commit date** and
* some more meta infos about the conflicting file since the specified date

Regarding the date, it would be clever to enter the PR opening date 🤷

```shell
git log --since="2026-02-03" --stat -- <path/to/file>
```

Now you can simply check the content of the logged commits on GitHub which makes it WAY easier to solve the conflict. If you like the console VERY much, you can also view the changes directly there by replacing `--stat` by `-p` 👍

