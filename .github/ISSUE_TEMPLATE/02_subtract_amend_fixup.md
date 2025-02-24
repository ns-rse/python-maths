---
name: 02 - Subtract - Amend and Fixup
about: Instructions on amending and fixup the subtract functions.
title: "Subtract Amend and Fixup"
labels: enhancement, help wanted
assignees: ""
---

Use the checklist to tick off the sub-tasks as you complete them. Some of the tasks rely on material that has already
been covered in the lesson so try and use what you have learnt. The commands are provided if required though.

- [ ] Create and switch to the `<github-user>/<issue-number>-subtract-amend-fixup` branch.
- [ ] Rebase the branch onto `main` to ensure it is up-to-date (**Hint** - you may not have all changes that have been
      merged into `main` so use previous experience to `git rebase`).
- [ ] Copy and paste the example to the docstring of the `subtract()` function that shows the consequence of trying to
      divide by zero.
- [ ] Commit your changes with an appropriate error message.
- [ ] Correct the spelling error
- [ ] Amend the previous commit

You have now used `git commit --amend`, lets try `git commit --fixup`.

- [ ] Make an empty commit.
- [ ] Add another example to the `square_root()` function's example section.
- [ ] Commit the change as a fixup to the commit which added the first example.
- [ ] Perform an interactive rebase to automatically squash the changes.
- [ ] Remove the empty commit and push your changes.
- [ ] Make a pull request and once approved merge.
- [ ] Delete your local `<github-user>/<issue-number>-subtract-amend-fixup` branch

## Instructions

**NB** Code chunks below can be copied using the button that appears on the top right of the code box when you move the
mouse over it.

### Create the `<github-user>/<issue-number>-subtract-amend-fixup` branch

This branch doesn't exist so needs creating, make sure `main` is up-to-date before creating it.

```bash
git switch main
git pull
git switch -c <github_user>/<issue_number>-subtract-amend-fixup
```

### Add a warning about square roots of negative numbers

Currently the `arithmetic.subtract()` function doesn't have any examples in the "docstring" (the help for the function
that is within the `"""` markers).

Copy and paste the following into docstring of the `subtract()` function. This is _after_ the `Returns` section. Make
sure to include a blank row after the description of `Returns` section of the `subtract()`function in
the`pythonmaths/arithmetic.py` file. Note it deliberately contains a spelling error as we will be fixing them. Make sure
the code is correctly indented.

```bash

    Examples
    --------
    >>> from python_math import arithmatic
    >>> arithmetic.subtract(10, 2)
        8.0
    >>> arithmetic.subtract(5, 2.5)
        2.5
```

### Commit your changes

```bash
git add -u
git commit -m "feature: Adds examples to subtract() function docstring"
```

### Correct the spelling error

Did you spot it? The example above had `artihmatic` instead of `arithmetic` in the import line. Correct this in the
docstring so it reads as shown below.

```python
    >>> from python_math import arithmetic
```

### Amend the previous commit

Rather than making a new commit amend the previous commit with the change.

```bash
git add -u
git commit --amend
```

### Make an empty commit

```bash
git commit --allow-empty -m "Empty commit to try out fixup"
```

### Add another example to the `square_root()` function's example section

```bash
    >>> arithmetic.subtract(-7.1, -1.2)
        -5.9
```

### Commit the change as a fixup

You need to know the hash of the commit made above that you amended (use `git log --oneline`) or you can use the
relative reference `HEAD~1`

```bash
git add -u
git commit --fixup HEAD~1
```

### Perform an interactive rebase to automatically squash the changes

You will either need the hash of the commit _before_ the one you are fixing up (use `git logp` to find this) or
you can use `HEAD~3` (the fixup itself is currently a commit and so you have to go back an extra commit relative to
`HEAD`).

```bash
git rebase -i --autosquash HEAD~3
```

A text editor should open and the commit with the message staring `fixup!` should have `fixup` and not `pick` next to
it. If that isn't the case change it to `fixup`. Save the file and exit the text editor (this should be `nano` in which
case use `Ctrl + o` followed by `Ctrl + x`).

### Remove the empty commit and push your changes

We can remove the empty commit with `git reset HEAD~1` and push our changes.

```bash
git reset HEAD~1
git push
```

### Make a pull request and once approved merge

Go to GitHub and make a pull request to merge you changes in, assigning it your collaborator.

Remember you can use the [GitHub
Keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests)
to automatically close the related issue.

Once approved merge the pull request to `main`.

### Delete your local `<github-user>/<issue-number>-subtract-amend-fixup` branch

We can now switch to `main`, pull down the merged changes and delete the local copy of the branch you created.

```bash
git switch main
git pull
git branch -d <github-user>/<issue-number>-subtract-amend-fixup
```
