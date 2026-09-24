# Git + HTML Practical Homework

## First repository, branches, remote, and pull request

Engineering Methods · FIIT STU · 2026/27

---

## Learning outcomes

By the end, you should be able to:

- initialize a local Git repository
- distinguish working, staged, and committed changes
- create coherent commits
- create, switch, and merge branches
- connect a GitHub repository as `origin`
- push a branch and open a pull request
- locate the same operations in a Git GUI

---

## Starter project

You receive exactly two project files:

```text
git-html-starter/
  index.html
  styles.css
```

Open `index.html` in a browser before changing anything.

Do not initialize Git until Task 1 tells you to.

---

## Task 0 — verify Git

```bash
git --version
git config --global user.name
git config --global user.email
```

If your name or email is missing:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

Use an email address appropriate for your GitHub account and privacy settings.

Use the guide from lecture to setup SSH connection with GitHub

---

## Task 1 — initialize the repository

In the starter directory:

```bash
git init -b main
git status
```

Discuss:

- Which files are untracked?
- What changed on disk?
- What is the current branch?

Do not stage anything yet.

---

## Task 2 — inspect and create the baseline

Read both files first.

Then:

```bash
git add index.html styles.css
git diff --staged
git commit -m "Create starter project page"
git status
```

The final status should say that the working tree is clean.

---

## Task 3 — make one content change

In `index.html`:

1. Replace `Your team project` with your working project title.
2. Replace the placeholder description with one sentence about the problem.
3. Save the file.

Inspect and commit:

```bash
git diff
git add index.html
git diff --staged
git commit -m "Describe team project idea"
```

---

## Task 4 — make one presentation change

In `styles.css`, change the `--accent` color to a valid color of your choice.

Then:

```bash
git diff
git add styles.css
git commit -m "Customize project accent color"
```

Why is this a separate commit from Task 3?

---

## Task 5 — inspect history

```bash
git log --oneline
git show HEAD
git log --oneline --graph --decorate --all
```

Identify:

- the newest commit
- the commit that changed only content
- the commit that changed only presentation
- the commit currently named by `main`

---

## Task 6 — create a feature branch

```bash
git switch -c feature/contact-card
git branch
```

In `index.html`, replace the placeholder name and email in the contact card.

Then:

```bash
git add index.html
git commit -m "Add project contact details"
```

Confirm that the commit exists only on the feature branch.

---

## Task 7 — compare branches

Switch to `main`:

```bash
git switch main
```

Open or refresh the page. The contact change should disappear.

Switch back:

```bash
git switch feature/contact-card
```

Refresh again. The change should return.

Branches change which committed version is checked out.

---

## Task 8 — merge locally

```bash
git switch main
git merge feature/contact-card
git log --oneline --graph --decorate --all
```

Open the page and verify the contact card.

After checking the result:

```bash
git branch -d feature/contact-card
```

---

## Task 9 — create an empty GitHub repository

On GitHub, create a new repository.

Recommended name:

```text
mip-git-practice
```

Create it **empty**:

- no README
- no `.gitignore`
- no license

This avoids creating an unrelated remote history before the first push.

---

## Task 10 — connect `origin`

Copy your repository URL and run:

```bash
git remote add origin https://github.com/YOUR-ACCOUNT/mip-git-practice.git
git remote -v
git push -u origin main
```

---

## Task 11 — create a branch for review

```bash
git switch -c feature/deadline
```

In `index.html`, replace the placeholder project deadline with:

```text
4 October 2026, 23:59
```

Then:

```bash
git add index.html
git commit -m "Add project focus deadline"
git push -u origin feature/deadline
```

---

## Task 12 — open a pull request

On GitHub:

1. Open a pull request from `feature/deadline` into `main`.
2. Give it a clear title.
3. Explain what changed and why.
4. State how you verified it.
5. Ask your partner to review the diff.

Do not merge until your partner has read the change.

---

## Task 13 — review and merge

Reviewer checklist:

- Is the target branch `main`?
- Does the diff contain only the intended change?
- Is the deadline correct?
- Is the HTML still readable?
- Is the commit message meaningful?

After review, merge the pull request on GitHub.

---

## Task 14 — synchronize locally

Your local `main` does not yet know about the GitHub merge.

```bash
git switch main
git pull --ff-only
git log --oneline --graph --decorate --all
```

Then remove the local feature branch:

```bash
git branch -d feature/deadline
```

If GitHub offers to delete the remote branch after merging, you may do so.

---

## Task 15 — repeat one operation in a GUI

Open the same repository in VS Code, GitHub Desktop, or another Git client.

Using the GUI:

1. Change one short sentence.
2. Inspect the diff.
3. Stage the file.
4. Commit it with a meaningful message.

Before clicking each control, name the equivalent Git concept or CLI command.

---

## Stretch task — create and resolve a conflict

Only begin after the required tasks are complete.

1. Create two branches from the same commit.
2. Change the same `<h1>` line differently in each branch.
3. Commit both versions.
4. Merge the first branch into `main`.
5. Merge the second branch.
6. Read the conflict markers and create the desired final heading.
7. Stage and commit the resolution.

Do not solve a conflict by blindly choosing “ours” or “theirs.”

---

## Next steps

Continue with [GitByBit](https://gitbybit.com/), created by the author of Refactoring.Guru.

---
