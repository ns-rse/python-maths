---
name: 04 - Square Root - Amend and Fixup
about: Instructions on amending and fixup the Zero Division branch.
title: "Square Root Amend and Fixup"
labels: enhancement, help wanted
assignees: ""
---

Use the checklist to tick off the sub-tasks as you complete them. Some of the tasks rely on material that has already
been covered in the lesson so try and use what you have learnt. The commands are provided if required though.

- [ ] Create and switch to the `<github-user>/<issue-number>-square-root-amend-fixup` branch.
- [ ] Rebase the branch onto `main` to ensure it is up-to-date (**Hint** - you may not have all changes that have been
      merged into `main` so use previous experience to `git rebase`).
- [ ] Copy and paste the example to the docstring of the `square_root()` function that shows the consequence of trying to
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
- [ ] Delete your local `<github-user>/<issue-number>-square-root-amend-fixup` branch

## Checkout the `<github-user>/<issue-number>-square-root-amend-fixup` branch

This branch doesn't exist so needs creating.

```bash
git switch -c <github-user>/<issue-number>-square-root-amend-fixup
```

## Rebase the branch onto `main`

We need to ensure we have an up-to-date version of `main` before we can rebase onto it.

```bash
git switch main
git pull
git switch -
git rebase main
```

## Add a warning about square roots of negative numbers

Currently the `arithmetic.square_root()` function has a problem, it returns the square root of negative numbers.

```bash
from pythonmaths import arithmetic
arithmetic.square_root(-2)
-1.4142135623730951
```

Obviously this is wrong as square roots of negative numbers should be complex.

We can improve the function by changing it to the following.

```python
if x < 0:
    print("WARNING : you have supplied a negative number, the square roof is complex.")
return x ** (1 / 2)
```

## Commit your changes

```bash
git add -u
git commit -m "Adds warning to square_root() if number is negative"
```

## Correct the spelling error

Did you spot it? The example above had `roof` instead of `root`. Correct this in the docstring so it reads as shown
below.

```python
print("WARNING : you have supplied a negative number, the square roof is complex.")
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

## Add another example to the `square_root()` function's example section

```bash
    >>> arithmetic.square_root(-2)
        WARNING : you have supplied a negative number, the square roof is complex.
        (8.659560562354934e-17+1.4142135623730951j)
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
you can use `HEAD~3` (the fixup itself is currently a commit and so you have to go back an extra commit relative to
`HEAD`).

```bash
git rebase -i --autosquash HEAD~4
```

A text editor should open and the commit with the message staring `fixup!` should have `fixup` and not `pick` next to
it. If that isn't the case change it to `fixup`. Save the file and exit the text editor (this should be `nano` in which
case use `Ctrl + o` followed by `Ctrl + x`).

## Remove the empty commit and push your changes

We can remove the empty commit with `git reset HEAD~1` and push our changes.

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

## Delete your local `<github-user>/<issue-number>-square-root-amend-fixup` branch

We can now switch to `main`, pull down the merged changes and delete the local copy of the `square-root-amend-fixup`

```bash
git switch main
git pull
git branch -d square-root-amend-fixup
```
