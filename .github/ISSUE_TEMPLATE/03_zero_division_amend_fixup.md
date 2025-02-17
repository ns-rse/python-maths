---
name: 03 - Zero Division - Amend and Fixup
about: Instructions on amending and fixup the Zero Division branch.
title: "Zero Division Amend and Fixup"
labels: enhancement, help wanted
assignees: ""
---

Use the checklist to tick off the sub-tasks as you complete them. Some of the tasks rely on material that has already
been covered in the lesson so try and use what you have learnt. The commands are provided if required though.

- [ ] Create the `<github_user>/<issue_number>-zero-division-amend-fixup` branch.
- [ ] Rebase the branch onto `main` to ensure it is up-to-date (**Hint** - you may not have all changes that have been
      merged into `main` so use previous experience to `git rebase`).
- [ ] Copy and paste the example to the docstring of the `divide()` function that shows the consequence of trying to
      divide by zero.
- [ ] Commit your changes with an appropriate error message.
- [ ] Correct the spelling error
- [ ] Amend the previous commit

You have now used `git commit --amend`, lets try `git commit --fixup`.

- [ ] Make an empty commit.
- [ ] Add another example to the `divide()` function's example section.
- [ ] Commit the change as a fixup to the commit which added the first example.
- [ ] Perform an interactive rebase to automatically squash the changes.
- [ ] Remove the empty commit and push your changes.
- [ ] Make a pull request and once approved merge.
- [ ] Delete your local `<github_user>/<issue_number>-zero-division-amend-fixup` branch

## Checkout the `<github_user>/<issue_number>-zero-division-amend-fixup` branch

This branch doesn't exist so needs creating.

```bash
git switch -c <github_user>/<issue_number>-zero-division-amend-fixup
```

## Rebase the branch onto `main`

We need to ensure we have an up-to-date version of `main` before we can rebase onto it.

```bash
git switch main
git pull
git switch -
git rebase main
```

## Add example of zero division to docstring

Copy and paste the following into the `Examples` section of the `divide()` function in the `pythonmaths/arithmetic.py`
file. Note it deliberately contains a spelling error as we will be fixing them. Make sure the code is correctly indented.

```bash
    >>> arithmetic.divide(3, 0)
        You can not divide by 0, please chose another value for 'y'.
```

## Commit your changes

```bash
git add -u
git commit -m "docs: Adding zero division example to divide docstring"
```

## Correct the spelling error

Did you spot it? The example above had `chose` instead of `choose` which is the actual error message returned. Correct
this in the docstring so it reads as shown below.

```bash
    >>> arithmetic.divide(3, 0)
        You can not divide by 0, please choose another value for 'y'.
```

## Amend the previous commit

Rather than making a new commit amend the previous commit with the change.

```bash
git add -u
git commit --amend
```

## Make an empty commit

```bash
git commit --allow-empty -m "Empty commit to try out fixup"
```

## Add another example to the `divide()` function's example section

Add another example to the `Examples` section of the `divide()` function in the `pythonmaths/arithmetic.py` file.

```bash
    >>> arithmetic.divide(1, 0.1)
        10
```

## Commit the change as a fixup

You need to know the hash of the commit made above that you amended (use `git log --oneline`) or you can use the
relative reference `HEAD~1`

```bash
git add -u
git commit --fixup HEAD~1
```

## Perform an interactive rebase to automatically squash the changes

You will either need the hash of the commit _before_ the one you are fixing up (use `git logp` to find this) or
you can use `HEAD~4` (the fixup itself is currently a commit and so you have to go back an extra commit relative to
`HEAD`).

```bash
git rebase -i --autosquash HEAD~4
```

A text editor should open and the commit with the message staring `fixup!` should have `fixup` and not `pick` next to
it. If that isn't the case change it to `fixup`. Save the file and exit the text editor (this should be `nano` in which
case use `Ctrl + o` followed by `Ctrl + x`).

## Remove the empty commit and push your changes

We can remove the empty commit with `git reset HEAD~1` and push your changes.

```bash
git reset HEAD~1
git push
```

## Make a pull request and once approved merge

Go to GitHub and make a pull request to merge you changes in, assigning it your collaborator.

Remember you can use the [GitHub
Keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests)
to automatically close the related issue.

Once approved merge the pull request to `main`.

## Delete your local `<github_user>/<issue_number>-zero-division-amend-fixup` branch

We can now switch to `main`, pull down the merged changes and delete the local copy of the `zero-division-amend-fixup`

```bash
git switch main
git pull
git branch -d ns-rse/5-zero-division-amend-fixup
```
