### Part 1: Getting Started with Git

1. **Install Git:**
   - Download and install Git from [git-scm.com](https://git-scm.com/).
   - Verify installation by opening a terminal and typing `git --version`.

2. **Configure Git:**
   - Set your username and email:
     ```
     git config --global user.name "Your Name"
     git config --global user.email "your.email@example.com"
     ```
   - Set default text editor (optional):
     ```
     git config --global core.editor "nano"  # Replace with your preferred editor
     ```

3. **Initialize a Repository:**
   - Create a new Git repository in your project folder:
     ```
     git init
     ```

4. **Basic Git Workflow:**
   - Check status of your repository:
     ```
     git status
     ```
   - Add files to staging area:
     ```
     git add <file>  # Use "." to add all files
     ```
   - Commit changes to repository:
     ```
     git commit -m "Commit message"
     ```

5. **Working with Branches:**
   - Create a new branch:
     ```
     git branch <branch-name>
     ```
   - Switch to a branch:
     ```
     git checkout <branch-name>
     ```
   - Combine changes from another branch:
     ```
     git merge <branch-name>
     ```

6. **Remotes:**
   - Add a remote repository:
     ```
     git remote add origin <remote-url>
     ```
   - Push changes to a remote repository:
     ```
     git push -u origin <branch-name>
     ```
   - Pull changes from a remote repository:
     ```
     git pull origin <branch-name>
     ```

### Part 2: Using GitHub

1. **Create a GitHub Account:**
   - Sign up at [github.com](https://github.com/).

2. **Create a New Repository on GitHub:**
   - Click on "New" in your GitHub account.
   - Name your repository, add a description, and choose public or private.
   - Initialize with a README file if needed.

3. **Connecting Your Local Repository to GitHub:**
   - Link your local repository to the remote GitHub repository:
     ```
     git remote add origin <repository-url>
     ```
   - Push your commits to GitHub:
     ```
     git push -u origin <branch-name>
     ```

4. **Collaborating on GitHub:**
   - Invite collaborators to your repository:
     - Go to your repository on GitHub > Settings > Collaborators.
   - Forking a repository:
     - Click "Fork" on a repository to create your own copy to work on.
   - Pull Requests:
     - Make changes in your forked repository, then create a pull request (PR) to merge changes into the original repository.

5. **Managing Issues and Projects:**
   - Issues:
     - Create, label, and assign tasks or bugs.
   - Projects:
     - Organize tasks into boards, track progress, and assign tasks to contributors.

6. **GitHub Pages (Optional):**
   - Host a website directly from your GitHub repository using GitHub Pages.

### Part 3: Advanced Git Operations

1. **Rebasing:**
   - Incorporate changes from one branch into another:
     ```
     git checkout <branch-name>
     git rebase <base-branch>
     ```

2. **Resetting Changes:**
   - Discard changes in working directory:
     ```
     git checkout -- <file>
     ```
   - Undo commits (caution: can rewrite history):
     ```
     git reset <commit>
     git reset --hard HEAD~1  # Reset to previous commit
     ```

3. **Git Hooks:**
   - Automate tasks on Git events (e.g., pre-commit, post-checkout).

4. **Git Workflows:**
   - Explore different Git workflows (e.g., Gitflow, Forking Workflow).

### Additional Tips

- **Git GUI Clients:** Explore GUI clients like GitHub Desktop for a visual interface.
- **Git Best Practices:** Use meaningful commit messages, branch naming conventions, and regular pulls from the main branch.
- **Documentation:** Maintain a README.md file with project overview, setup instructions, and contact information.
---