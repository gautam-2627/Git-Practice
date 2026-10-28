# FlipkartClone
Flipkart Clone 
Git and GitHub: Complete Beginner's Guide
1. What is Git?

Git is a version control system that helps developers track changes in their code. It allows you to save different versions of a project, compare changes, and return to an earlier version when needed.

Benefits of Git
Tracks changes made to files.
Helps developers collaborate on projects.
Allows you to restore previous versions of code.
Maintains a history of commits.
Supports branching and merging.
Makes project management easier and more organized.
2. What is GitHub?

GitHub is an online platform that hosts Git repositories. It allows developers to store their code remotely, collaborate with others, and share projects.

Git vs. GitHub
Git	GitHub
A version control system	An online code-hosting platform
Works locally on your computer	Stores repositories online
Tracks file changes	Supports collaboration and code reviews
Works through commands and tools	Provides a web interface and collaboration tools
3. Check Whether Git Is Installed

Open Git Bash and run:

bash
git --version


This command displays the installed Git version.

Example output:

text
git version 2.x.x


If Git is not installed, download it from the official website:

https://git-scm.com/downloads

4. Configure Your Git Username and Email

Before making commits, configure your identity.

Set your username:

bash
git config --global user.name "Your Name"


Set your email address:

bash
git config --global user.email "your-email@example.com"


Check your configuration:

bash
git config --global --list


The --global option applies these settings to all repositories for your user account.

5. Create a GitHub Repository

Follow these steps to create a repository on GitHub:

Sign in to https://github.com/.
Click the + icon in the top-right corner.
Select New repository.
Enter a repository name.
Add a description if needed.
Choose whether the repository should be public or private.
Click Create repository.

A repository is a project folder that contains your files and their version history.

6. Clone a GitHub Repository

Cloning downloads a remote repository to your local computer.

For example:

bash
git clone https://github.com/gautam-2627/Git-Practice.git


This command creates a local folder named Git-Practice and downloads the repository contents.

Enter the Repository Folder
bash
cd Git-Practice

Check the Repository Status
bash
git status


This command shows the current branch and whether any files have changed.

View the Remote Repository URL
bash
git remote -v


This displays the remote repository addresses used for fetching and pushing changes.

7. What Is SSH?

SSH stands for Secure Shell. It provides an encrypted connection between your computer and a remote server.

When working with GitHub, SSH keys allow you to authenticate without entering your GitHub password every time you communicate with the repository.

An SSH key pair contains two files:

Private key: Stored securely on your computer. Never share it.
Public key: Added to your GitHub account.
8. Generate an SSH Key

Open Git Bash and run:

bash
ssh-keygen -t ed25519 -C "your-email@example.com"


Replace the example email with the email associated with your GitHub account.

When prompted for the file location, press Enter to accept the default location:

text
~/.ssh/id_ed25519


You may also be asked to set a passphrase to protect your private key.

The generated files are usually:

text
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub


The file ending in .pub is your public key.

Important: Never upload or share the private key file id_ed25519.

9. Copy the SSH Public Key on Windows

In Git Bash, run:

bash
clip < ~/.ssh/id_ed25519.pub


This copies the public key to your Windows clipboard.

To display the public key instead, run:

bash
cat ~/.ssh/id_ed25519.pub


Copy the entire line beginning with ssh-ed25519.

If the public key file does not exist, generate an SSH key before running these commands.

10. Add the SSH Key to GitHub

Follow these steps:

Open https://github.com/settings/keys.
Click New SSH key.
Enter a title, such as My Laptop.
Select Authentication Key as the key type.
Paste your public key into the Key field.
Click Add SSH key.
Complete any identity verification requested by GitHub.

Your SSH public key is now associated with your GitHub account.

11. Test the SSH Connection

Run the following command in Git Bash:

bash
ssh -T git@github.com


On the first connection, SSH may ask you to confirm GitHub's host fingerprint. Verify the fingerprint against GitHub's official documentation before accepting it.

A successful authentication typically displays a message similar to:

text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.


This means SSH authentication is working.

12. Change a Repository from HTTPS to SSH

If you cloned a repository using HTTPS, you can switch its remote URL to SSH.

First, enter the repository folder:

bash
cd Git-Practice


Change the remote URL:

bash
git remote set-url origin git@github.com:gautam-2627/Git-Practice.git


Verify the change:

bash
git remote -v


You should see the SSH URL for both fetch and push.

13. Basic Git Workflow

A typical Git workflow involves editing files, staging changes, committing them, and pushing commits to GitHub.

Step 1: Check the Status
bash
git status

Step 2: Add Files to the Staging Area

Add a specific file:

bash
git add README.md


Add all changes in the current directory:

bash
git add .


The staging area contains the changes you want to include in your next commit.

Step 3: Commit Your Changes
bash
git commit -m "Add project documentation"


A commit saves a snapshot of the staged changes in the local repository's history.

Step 4: Push Changes to GitHub
bash
git push


If the branch has no upstream configured yet, you may need:

bash
git push -u origin main


Replace main with your actual branch name if necessary.

14. Pull the Latest Changes

To download and integrate new changes from the remote repository, run:

bash
git pull


This helps synchronize your local branch with the remote branch.

15. View Commit History

Use the following command:

bash
git log


For a compact history, run:

bash
git log --oneline


These commands display previous commits and their messages.

16. Common Git Commands
Command	Purpose
git init	Initialize a new local repository
git clone <url>	Download a remote repository
git status	Check the current repository status
git add .	Stage changes in the current directory
git commit -m "message"	Create a commit
git push	Upload local commits
git pull	Fetch and integrate remote changes
git fetch	Download remote updates without integrating them
git log --oneline	Display a compact commit history
git branch	List local branches
git switch -c feature	Create and switch to a new branch
git remote -v	Show remote repository URLs
17. Common Errors and Their Solutions
Error 1: bash: $: command not found

Cause: You copied the $ symbol from a tutorial.

Solution: Type only the command, without the prompt symbol.

Incorrect:

bash
$ git status


Correct:

bash
git status

Error 2: fatal: protocol '200~https' is not supported

Cause: Extra characters were included in the pasted URL.

Solution: Run the clean command:

bash
git clone https://github.com/gautam-2627/Git-Practice.git

Error 3: Permission denied (publickey)

Possible causes:

The public key has not been added to GitHub.
The SSH key is not loaded or available to SSH.
The remote URL is incorrect.
SSH is using a different key.

Solution: Verify the remote URL and test the connection:

bash
git remote -v
ssh -T git@github.com

Error 4: fatal: not a git repository

Cause: The terminal is outside a Git repository.

Solution: Navigate into the repository directory:

bash
cd Git-Practice


Then run:

bash
git status

18. Recommended Daily Workflow

When working on a project, you can follow this sequence:

bash
git status
git pull
# Edit your files
git add .
git commit -m "Describe your changes"
git push


Review your changes before staging and committing them. If you are collaborating with others, resolve any merge conflicts before pushing.

Conclusion

Git and GitHub are essential tools for modern software development. Git tracks changes locally, while GitHub hosts repositories online and supports collaboration.

By learning to clone repositories, configure SSH authentication, stage files, commit changes, and push updates, you can manage your projects more efficiently and build a strong foundation for collaborative development.
