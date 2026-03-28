# Git Remotes: Manage Remotes

## 1. Introduction: How to Work With Remotes

Remotes describe where your code lives when more than one person is working with it. This is typically a hosting platform like GitHub, GitLab, or Bitbucket — a central place where everyone with access can reach the codebase and develop it on their own machines.

This is how most teams operate. Every team member clones the same remote repository to their local machine, makes changes on their own branch, and pushes those changes back so the rest of the team can pull them down. This shared foundation is what keeps everyone aligned on the same codebase, and it is where Git's features like branching, merging, and rebasing become essential.

For further reading, see the [Git official documentation on remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes).

---

## 2. Tutorial: How to Clone a Remote Repository

Cloning creates a full local copy of a remote repository on your machine, including all branches and history.

* **Step 1:** Choose a directory for storage.
  - Before cloning, decide where on your machine the project will live. Create a dedicated directory for it — this makes managing multiple projects much easier in the long run.

* **Step 2:** Navigate to your chosen directory.
  - Use the `cd` command to move into your directory. Always use the full path to avoid ending up in the wrong place.

```bash
cd /C:/Users/user/Desktop/your-directory
```

* **Step 3:** Clone the repository.
  - Copy the repository URL from GitHub or your hosting platform, then run:

```bash
git clone <repository-url>
```

This will create a new folder inside your directory containing the full project. Git automatically sets up the remote called `origin` pointing back to the URL you cloned from.

---

## 3. Tutorial: How to Push Changes to a Remote

When you have made and committed changes locally, you push them to the remote repository so your teammates can access them.

> ***Note:*** This section assumes familiarity with `git status`, `git add`, and `git commit`. You can read more about those here: [Basic Git Commands](../examples/basics.md).

* **Step 1:** Make sure your changes are committed locally.

```bash
git add <FileName>
git commit -m "Your commit message"
```

* **Step 2:** Push your branch to the remote.

```bash
git push origin <your-branch-name>
```

> ***Note:*** It is rare to push changes directly to `main`. In most team workflows a pull request is opened on GitHub or a similar platform so that changes can be reviewed before merging. You can read more about that here: [GitHub Pull Requests](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests). You can also find more information about it here:

---

## 4. Tutorial: How to Pull Changes from a Remote

When a teammate has pushed changes to the remote, you need to pull them down to keep your local copy up to date.

* **Step 1:** Make sure you are on the branch you want to update.

```bash
git checkout main
```

* **Step 2:** Pull the latest changes from the remote.

```bash
git pull origin main
```

This fetches the latest changes from the remote and merges them into your current branch automatically. If your local branch has diverged from the remote, this may result in a merge conflict. You can read more about resolving those here: [Merge Conflicts](../troubleshooting/merge-conflicts.md).

> ***Note:*** Some teams prefer using `git fetch` followed by `git merge` or `git rebase` instead of `git pull`, as it gives you more control over how incoming changes are integrated. `git fetch` downloads the changes without applying them, letting you inspect them first.

---

## 5. Managing Remotes

Over time you may need to add, rename, or remove remotes — for example when a repository moves to a new URL, or when you want to track a fork alongside the original.

**View all configured remotes:**

```bash
git remote -v
```

**Add a new remote:**

```bash
git remote add <n> <url>
```

A common pattern when working with forks is to name the original repository `upstream` and your fork `origin`:

```bash
git remote add upstream https://github.com/original-owner/repo.git
```

**Rename a remote:**

```bash
git remote rename <old-name> <new-name>
```

**Remove a remote:**

```bash
git remote remove <n>
```

**Inspect a remote in detail:**

```bash
git remote show origin
```

This shows the fetch and push URLs, which branches are tracked, and whether your local branches are ahead or behind.

---

## 6. Reference: Remote Commands

| Command | Action |
| ------- | ------ |
| `git clone <url>` | Creates a local copy of a remote repository including all history and branches. |
| `git remote -v` | Lists all configured remotes with their fetch and push URLs. |
| `git remote add <n> <url>` | Adds a new remote with the given name pointing to the given URL. |
| `git remote rename <old> <new>` | Renames an existing remote. |
| `git remote remove <n>` | Removes a remote from the configuration. |
| `git remote show <n>` | Shows detailed information about a specific remote. |
| `git push origin <branch>` | Pushes a local branch to the remote repository. |
| `git push -u origin <branch>` | Pushes and sets the remote branch as the upstream tracking branch. |
| `git pull origin <branch>` | Fetches and merges changes from the remote branch into the current branch. |
| `git fetch origin` | Downloads changes from the remote without merging them. |
| `git fetch --all` | Fetches changes from all configured remotes. |