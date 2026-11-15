https://m365.cloud.microsoft/chat/conversation/eb362939-d0f4-4e75-a87c-a35091d8a6a4?fromcode=cmmr7zps7qs&culture=en-us&country=us&ocid=AIDcmml35ws9mz_SEM__k_6fe7baf5983811e1e091d22cceb22dc8_k_&refOrigin=Other&auth=1

# Set up a GitHub repository from a local project

Start in the folder containing your project. These steps create the Git repository locally first, then connect it to GitHub.

## 1. Prepare the project

Open a terminal in the project folder and check what is there:

```sh
git status
```

If Git says this is not a repository yet, that is expected. Before adding files, create a `.gitignore` appropriate for your language and tools. Do not commit credentials, API keys, `.env` files, or generated/dependency folders.

## 2. Initialize Git and make the first commit

Set the name and email that Git will record on your commits. To use them for all repositories:

```sh
git config --global user.name "Rich"
git config --global user.email "rich@unami.com"
```

To set them only for this repository, run these instead from the project folder (omit `--global`):

```sh
git config user.name "Your Name"
git config user.email "you@example.com"
```

Check the configured email with `git config user.email`. The repository-specific value takes precedence over the global value. Commits include this email, so use your GitHub-provided noreply address if you want to keep your personal email private.

```sh
git init -b main
git add .
git status
git commit -m "Initial commit"
```

Review `git status` before committing to make sure only intended files are staged.

## 3. Create an empty GitHub repository

On GitHub, create a new repository. Since the project already exists locally, leave options such as **Add a README**, **Add .gitignore**, and **Choose a license** unchecked. This avoids creating a separate initial commit on GitHub.

## 4. Connect and push the local repository

Copy the repository URL from GitHub (HTTPS or SSH), then run:

```sh
git remote add origin <repository-url>
git remote -v
git push -u origin main
```

Replace `<repository-url>` with the URL you copied, for example `https://github.com/USERNAME/REPOSITORY.git`. GitHub may ask you to authenticate; use your configured Git Credential Manager or SSH key rather than putting a password or token in the URL.

## Later updates

After making changes, review and push them with:

```sh
git status
git add <files>
git commit -m "Describe the change"
git push
```