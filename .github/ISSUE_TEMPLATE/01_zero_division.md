---
name: 01 - Add Zero Division Exception
about: Instructions on adding a Zero Division exception to the divide function
title: "Add zero division exception and test"
labels: enhancement, help wanted
assignees: ""
---

Read through the instructions below then use the checklist to tick off the sub-tasks as you complete them.

- [ ] Create a branch that reflects your GitHub username, the issue number and the issue being addressed.
- [ ] Add a `try: ... except: ...` to the `divide function` in the `pythonmaths/arithmetic.py` module.
- [ ] Add a test that checks this exception is raised when the function is passed `0` as denominator.
- [ ] Save, stage, commit, and push your changes.


## Instructions

**NB** Code chunks below can be copied using the button that appears on the top right of the code box when you move the
mouse over it.

### Create Branch

Create a branch locally from the `main` branch to work on this task. Try using the suggested nomenclature of
`<github_username>/<issue_number>-<short_description>`, e.g.

```bash
git switch -c "ns-rse/1-zero-division"
```

### Add a `try: ... except: ...` to capture `ZeroDivisionError`

Replace line 55 in the `pythonmaths/arithmetic.py` file which currently reads.

```python
return x / y
```

With the following code which raises a custom exception message.

```python
try:
    return x / y
except ZeroDivisionError as e:
    raise ZeroDivisionError(
        "You can not divide by 0, please choose another value for 'y'."
    ) from e
```

### Add a test to check the exception is raised

Add the following to the `tests/test_arithmetic.py` which checks that the exception is raised.

```python
def test_divide_zero_division_exception() -> None:
    """Test that a ZeroDivisionError is raised by the divide() function."""
    with pytest.raises(ZeroDivisionError):
        arithmetic.divide(2, 0)
```

### Save, stage, commit your changes

**NB** Make sure to replace the message in the second line with a meaningful message.

```bash
git add -u    # This will add all files that are under version control and have been modified
git commit -m "feature: add zero division error"
```

### Push to `origin`

The changes only exist on your local branch and there is no tracking branch on the remote `origin` (GitHub). The
following will create a tracking branch upstream and push to it all in one go.

**NB** You will have to substitute the `<local_branch_name>` for whatever you opted to call the branch in the first
step.

```bash
git push
```

### Create a Pull Request

Navigate to your repository and create a Pull Request, adding your collaborator as a reviewer.

Remember you can use the [GitHub
Keywords](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/using-keywords-in-issues-and-pull-requests)
to automatically close the related issue.

Address any feedback or errors that arise in the GitHub Actions.

### Merge the Pull Request

Once approved merge the pull request and delete your local branch.

```bash
git switch main
git pull
git branch -d ns-rse/1-zero-division
```
