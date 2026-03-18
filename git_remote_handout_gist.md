# Communicating with the Remote Repository

Short handout for the presentation topic **git remote, fetch, merge, and pull**.

## 1. What is a remote repository?

A **remote repository** is a version of your Git project that is stored on another system, usually on a platform such as **GitHub**.

It allows you to:
- collaborate with other people
- back up your work online
- synchronize changes between different computers

The default remote is often called **origin**.

---

## 2. `git remote`

`git remote` is used to manage connections to remote repositories.

### Useful commands

```bash
git remote -v
git remote add origin <url>
git remote remove origin
git remote set-url origin <new-url>
```

### Typical use

```bash
git remote -v
```

This shows which remote repository is connected to your local repository.

---

## 3. `git fetch`

`git fetch` downloads new information and commits from the remote repository, but it **does not merge them into your current branch**.

### Why use it?

Use `fetch` when you want to:
- check remote changes first
- avoid unexpected changes in your working branch
- keep more control over the update process

### Example

```bash
git fetch origin
```

After that, you can inspect the downloaded changes before integrating them.

---

## 4. `git merge`

`git merge` integrates changes from another branch into your current local branch.

### Example

```bash
git merge origin/main
```

This merges the fetched remote-tracking branch into your local branch.
origin/main is the remote-tracking branch for the remote origin.

### Important note

If local and remote changes affect the same lines, a **merge conflict** can occur.

---

## 5. `git pull`

In the default case, `git pull` is a shortcut for:

```bash
git fetch
git merge
```

So `pull`:
1. downloads remote changes
2. integrates them immediately into your current branch

### Example

```bash
git pull origin master
```

---

## 6. `fetch` vs `pull`

### `git fetch`
- downloads changes only
- does **not** change your current branch
- safer when you want to inspect changes first

### `git pull`
- downloads and merges immediately
- faster and more convenient
- less control than `fetch` + `merge` separately

### Key idea

> **`git pull` = `git fetch` + `git merge`**

---

## 7. Mini demo workflow

A simple and safe demo sequence:

```bash
git remote -v
git fetch origin
git log --oneline HEAD..origin/main
git merge origin/main
```

Optional shortcut:

```bash
git pull origin main
```

### What these commands do

- `git remote -v` shows the configured remote
- `git fetch origin` downloads new commits
- `git log --oneline HEAD..origin/main` shows commits on the remote that are not yet local
- `git merge origin/main` integrates the fetched changes
- `git pull origin main` performs fetch and merge in one step

---

## 8. Best practices

- Use **`git fetch` first** when you want more control.
- Use **`git pull`** when you want a quick update.
- Check `git remote -v` if you are unsure which remote is configured.
- Test your demo commands before the presentation.
- Open all required tabs and repositories in advance.
- Make sure authentication is already working, so no time is lost during the presentation.

---

## 9. Take-home messages

- A remote repository is the shared online version of your project.
- `git remote` manages remote connections.
- `git fetch` downloads changes without integrating them.
- `git merge` integrates changes into the current branch.
- `git pull` combines fetch and merge in one command.

