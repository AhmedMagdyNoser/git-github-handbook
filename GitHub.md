# GitHub Handbook

**Git** is a version control system that lets you manage and keep track of source code history. It’s used for tracking code changes, tracking who made changes, and coding collaboration.

**GitHub** is a cloud-based hosting service that provides tools to manage Git repositories, enabling developers to collaborate online.

## Setting Up Remote Repository

1. Create an account on [GitHub](https://github.com)
   (preferably using the same email as your Git config)
2. Create a new repository and copy its URL
3. Link your local repo to GitHub:

   ```bash
   git remote add origin https://github.com/Username/RepoName.git
   ```

## Push to GitHub

Push your local commits to the remote `master` branch:

```bash
git push -u origin master
```

After the first push, you can simply use:

```bash
git add .
git commit -m "Update files"
git push # or > git push origin master
```

## Pull from GitHub

To keep your local repository up to date with changes from GitHub, you can **pull** updates.

`git pull` is actually a combination of two commands:

- **fetch** → downloads all the latest changes from the remote repository.
- **merge** → combines those updates into your current branch.

Instead of running both:

```bash
git fetch origin
git merge origin/master
```

You can simply use:

```bash
git pull origin
```

This ensures your local copy stays synchronized with the remote repository.

## GitHub Branches

If a new branch exists on the remote repository but doesn’t appear locally, fetch the latest branch information:

```bash
git fetch
```

Then, list all branches (both local and remote):

```bash
git branch -a
```

## Pull Request

A **Pull Request** is a way to suggest changes from one branch to another — usually from your feature branch into the main project branch (like `master`). It lets others review your code, discuss improvements, and approve it before merging. In short, a pull request is how you propose your updates and collaborate safely before they become part of the main codebase.

## GitHub Cloning

GitHub cloning refers to the process of creating a local copy of a remote GitHub repo on your computer.

```bash
git clone https://github.com/Username/RepoName.git
```

This command downloads the entire repository, including its history, branches, and files, allowing you to work on it locally.

## GitHub Forking

A **fork** is your own copy of someone else’s GitHub repository. It lets you make changes freely without affecting the original project. Forking is done on GitHub (not with a Git command). After you fork a repo, you can **clone** your version to your computer using:

```bash
git clone https://github.com/Username/RepoName.git
```

You can then edit the project, commit your changes, and push them back to **your fork** on GitHub:

```bash
git add .
git commit -m "Update something"
git push origin master
```

Once your updates are ready, go to your fork on GitHub and open a **Pull Request** to suggest your changes to the original repository. The project owner can then review, discuss, and merge your work.

## GitHub Pages

You can host your project directly from GitHub using **GitHub Pages**.
To enable it, go to your repository’s **Settings → Pages** tab and configure the build source.

### Deploying a React App to GitHub Pages

1. **Install the `gh-pages` package:**

   ```bash
   npm i -D gh-pages
   ```

2. **Add a homepage URL** to your `package.json` file (replace with your username and repo name):

   ```json
   "homepage": "https://Username.github.io/RepoName"
   ```

3. **Add deploy scripts** under the `"scripts"` section in your `package.json`:

   ```json
   "predeploy": "npm run build",
   "deploy": "gh-pages -d build"
   ```

4. **Deploy your app** using:

   ```bash
   npm run deploy
   ```

   Run this command again anytime you make updates to redeploy your latest version.

**Note:** If your React app uses routing, replace `<BrowserRouter>` with `<HashRouter>` to ensure proper navigation on GitHub Pages.
