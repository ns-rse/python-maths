---
name: 02 - Add Square Root Function
about: Instructions on adding a Square Root function to the Arithmetic module
title: "Add a square root function and test"
labels: enhancement, help wanted
assignees: ""
---

Read through the instructions below then use the checklist to tick off the sub-tasks as you complete them.

- [ ] Create a branch that reflects your GitHub username, the issue number and the issue being addressed.
- [ ] Add a `square_root()` function to the `pythonmaths/arithmetic.py` module.
- [ ] Add a test that checks the function works correctly.
- [ ] Save, stage, commit, and push your changes.


## Instructions

**NB** Code chunks below can be copied using the button that appears on the top right of the code box when you move the
mouse over it.

### Create Branch

Create a branch locally from the `main` branch to work on this task. Try using the suggested nomenclature of
`<github_username>/<issue_number>-<short_description>`, e.g.

```bash
git switch -c "ns-rse/2-square-root"
```

### Add a `square_root()` function to the `pythonmaths/arithmetic.py` module

Add the following to the bottom `pythonmaths/arithmetic.py`.

```python
def square_root(x: int | float) -> float:
    """Return the square root of a number.

    Parameters
    ==========
    x : int | float
        The number for which you wish to find the square root.

    Returns
    =======
    float
        The square root of x.

    Examples
    ========
    >>> from python_math import arithmetic
    >>> arithmetic.square_root(4)
        2.0
    >>> arithmetic.square_root(169)
        13.0
    """
    return x ** (1 / 2)
```

### Add a test to check the exception is raised

Add the following to the `tests/test_arithmetic.py` which checks the correct values are returned.

```python
@pytest.mark.parametrize(
    ("x", "target"),
    [
        pytest.param(4, 2, id="square root of 4"),
        pytest.param(9, 3.0, id="square root of 9"),
        pytest.param(25, 5.0, id="square root of 25"),
        pytest.param(2, 1.4142135623730951, id="square root of 2"),
    ],
)
def test_square_root(x: int | float, target: int | float) -> None:
    """Test the square_root() function."""
    pytest.approx(arithmetic.square_root(x), target)
```

### Save, stage, commit your changes

```bash
git add -u    # This will add all files that are under version control and have been modified
git commit -m "feature: Adds square_root() function and tests."
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

**NB** Please do **NOT** merge this pull request, we will be using this branch in its current state later on to
understand `git rebase`.
