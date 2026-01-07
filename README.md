# VS Code Setup and Collaboration Guide

## Part 1: Installation and Basic Setup

### Installing VS Code

1. **Download VS Code**
   - Visit [code.visualstudio.com](https://code.visualstudio.com)
   - Download the installer for your operating system (Windows, macOS, or Linux)
   - Run the installer and follow the prompts
   - **Recommended:** Check "Add to PATH" during installation (Windows)

2. **First Launch**
   - Open VS Code
   - You'll see the Welcome screen with helpful starting points
   - The interface has three main areas:
     - **Activity Bar** (left side): Access different views
     - **Side Bar**: Shows content based on your Activity Bar selection
     - **Editor**: Where you write code

### Installing Language Support

#### For C++

1. Click the **Extensions** icon in the Activity Bar (or press `Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Search for "C/C++"
3. Install the **C/C++** extension by Microsoft
4. Install the **C/C++ Extension Pack** for additional tools
5. Install **C++ Runner** extension for easier compilation and execution
   - This provides a simple "Run" button and handles compilation automatically
   - Particularly helpful for beginners who want to avoid manual compilation commands

**Setting up a C++ compiler:**
- **Windows:** Install MinGW-w64 or use Microsoft Visual C++
- **macOS:** Install Xcode Command Line Tools: `xcode-select --install`
- **Linux:** Install g++: `sudo apt install g++` (Ubuntu/Debian)

**Note:** C++ Runner will detect your installed compiler automatically and configure build settings for you.

#### For Java

1. In Extensions, search for "Java"
2. Install the **Extension Pack for Java** by Microsoft (this includes multiple Java tools)
3. **Install Java Development Kit (JDK):**
   - Download JDK 17 or later from [adoptium.net](https://adoptium.net)
   - Install and note the installation path
   - VS Code should auto-detect the JDK, or you can configure it in settings

#### For Python

1. In Extensions, search for "Python"
2. Install the **Python** extension by Microsoft
3. **Install Python:**
   - Download from [python.org](https://python.org) (version 3.8 or later)
   - **Important:** Check "Add Python to PATH" during installation
4. After installation, open a `.py` file and VS Code will prompt you to select a Python interpreter

### Verifying Your Setup

Create a test file for each language to verify everything works:

**C++ test (test.cpp):**
```cpp
#include <iostream>
int main() {
    std::cout << "C++ works!" << std::endl;
    return 0;
}
```

**Java test (Test.java):**
```java
public class Test {
    public static void main(String[] args) {
        System.out.println("Java works!");
    }
}
```

**Python test (test.py):**
```python
print("Python works!")
```

Run each file using the Run button (▷) that appears in the top-right corner.

## Part 2: Live Share for Real-Time Collaboration

### Installing Live Share

1. Open Extensions (`Ctrl+Shift+X` / `Cmd+Shift+X`)
2. Search for "Live Share"
3. Install **Live Share** by Microsoft
4. You may need to sign in with a Microsoft or GitHub account

### Starting a Collaboration Session (Host)

1. Click the **Live Share** icon in the Activity Bar (or status bar at bottom)
2. Click **"Share"** (you may need to sign in first)
3. A shareable link will be copied to your clipboard automatically
4. Share this link with your team members via email, chat, etc.
5. You'll see participants join in the Live Share panel

**What collaborators can do:**
- Edit files simultaneously (you'll see their cursors with their names)
- Follow your cursor or navigate independently
- Access the terminal (if you grant permission)
- Run and debug code together

### Joining a Collaboration Session (Guest)

1. Click the **Live Share** icon
2. Click **"Join"**
3. Paste the link shared by the host
4. You'll be connected and can see the host's workspace

### Advanced Live Share Features

#### Shared Terminals
- **Host:** In the Live Share panel, click "Share Terminal"
- Choose "Read-only" or "Read/write" access
- Guests can now see and use the terminal

#### Shared Servers (for web development)
- If you run a local server (like for a web app), Live Share can share it
- Guests can access `localhost:3000` (for example) and see your running application
- Useful for testing full-stack projects together

#### Focus and Following
- Click a participant's name to follow their cursor
- Use this to guide team members through code or get help
- Press `Esc` to stop following

#### Audio Calls (Optional)
- Install the **Live Share Audio** extension for voice chat
- Not required, but can replace separate video call tools

### Best Practices for Collaboration

- **Use meaningful cursor comments:** Type your thoughts as you code
- **Communicate changes:** Use Live Share's chat or external communication
- **Establish roles:** Decide who codes while others review, or split files
- **Save frequently:** All participants see changes, but the host should save
- **Set permissions carefully:** Be cautious with terminal write access

## Part 3: Git and Version Control

### Installing Git

1. Download Git from [git-scm.com](https://git-scm.com)
2. Run the installer
3. **Important:** During installation, when asked to choose the default editor, select **"Use Visual Studio Code as Git's default editor"** instead of Vim
   - This makes Git operations (like commit messages) open in VS Code instead of the terminal-based Vim editor
   - Much more user-friendly for beginners
4. Use default options for other installation steps
5. Verify installation by opening a terminal and typing: `git --version`
6. **If VS Code was open during Git installation, close and restart it now** so it can detect Git properly

### Configuring Git

Open a terminal in VS Code (`Ctrl+`` or Terminal > New Terminal`) and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Basic Git Workflow in VS Code

#### Initialize a Repository

1. Open your project folder in VS Code
2. Click the **Source Control** icon in the Activity Bar (or `Ctrl+Shift+G`)
3. Click **"Initialize Repository"**
4. Your folder is now a Git repository

#### Making Commits

**Understanding the process:**
Git uses a two-step process to save your work. Think of it like packing a box to ship:
- **Staging** = choosing which items to put in the box
- **Committing** = sealing the box and labeling it with a description

This lets you group related changes together, even if you've modified many files.

**Steps to make a commit:**

1. Edit your files as normal
2. Go to Source Control view - you'll see changed files under "Changes"
3. **Stage your changes:**
   - Hover over individual files and click **"+"** to stage specific files
   - Or click **"+"** next to "Changes" to stage all modified files
   - Staged files move to the "Staged Changes" section
   - *Why stage?* You might have changed 5 files but only want to commit 3 related ones together
4. **Write a commit message** in the text box at the top
   - This describes what changes you're committing and why
   - Example: "Add input validation to login form"
   - The message is attached to all the staged changes as a single commit
5. Click the **✓ Commit** button (or press `Ctrl+Enter`)
   - This permanently saves the staged changes with your message
   - Your "Staged Changes" section will now be empty

**Good commit message practices:**
- Be descriptive: "Fix bug in sorting algorithm" not "fixed stuff"
- Use present tense: "Add feature" not "Added feature"
- Keep first line under 50 characters
- Think: "This commit will..." and complete the sentence

#### Working with Branches

Branches let team members work on features independently.

**Create a new branch:**
1. Click the branch name in the bottom-left status bar (usually says "main")
2. In the menu that appears, select **"Create new branch..."** or **"Create new branch from..."**
   - Alternatively, you can use the Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`) and type "Git: Create Branch"
3. Type a descriptive branch name (e.g., "feature-login", "fix-database-error") and press Enter
4. Your new branch is now active and you'll see the new name in the status bar

**Switch branches:**
- Click the branch name in the status bar and select a different branch

**Merge branches:**
1. Switch to the branch you want to merge into (usually "main")
2. Open Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`)
3. Type "Git: Merge" and select **"Git: Merge..."** from the options
4. Choose the branch you want to merge from the list

### Using GitHub for Team Projects

#### Setting Up a GitHub Repository

1. Create a free account at [github.com](https://github.com)
2. Click **"New repository"**
3. Name it, add a description, and click **"Create repository"**
4. GitHub will show commands to link your local repository

#### Connecting Your Local Repository to GitHub

In VS Code terminal, run these commands (replace with your repository URL):

```bash
git remote add origin https://github.com/yourusername/your-repo.git
git branch -M main
git push -u origin main
```

#### First-Time GitHub Authentication

The first time you push to GitHub, you'll need to authenticate:

1. After running `git push`, a popup window will appear asking you to log into GitHub
2. Log in with your GitHub credentials
3. A browser window will open asking you to **"Authorize Git Credential Manager"**
4. Click to authorize, then you'll see a **"Confirm access"** page
5. Click the button to verify by email
6. Retrieve the confirmation code from your email and enter it
7. You'll see **"Authentication succeeded"** in the browser
8. Back in VS Code terminal, you'll see the push complete successfully

**Good news:** This only happens once per computer. Git Credential Manager securely saves your credentials, so future pushes and pulls work automatically without all these steps.

#### Everyday GitHub Workflow

**Push your changes (send to GitHub):**
1. Commit your changes locally (as described above)
2. Click the **"..."** menu in Source Control view
3. Select **"Push"** (or click the sync button in the status bar)

**Pull changes (get updates from teammates):**
1. Click the **"..."** menu in Source Control view
2. Select **"Pull"** (or click the sync button)
3. Your local files will update with the latest changes

**The sync button (⟳):**
- Located in the status bar next to the branch name
- Pulls changes from GitHub, then pushes your commits
- Quick way to stay synchronized

#### Example Workflow: Two Students Collaborating

Let's walk through a realistic scenario where two students work on the same `main.cpp` file.

**Initial Setup (Both Students):**
- Both students have cloned the same GitHub repository
- The repository has a `main.cpp` file with basic code
- Both are starting on the `main` branch

**Student A's Task:** Update the existing `main()` function to add input validation

**Student A - Step by step:**

1. **Pull latest changes first** (always do this before starting work)
   - Click Source Control icon in Activity Bar (or `Ctrl+Shift+G`)
   - Click the **"..."** menu
   - Select **"Pull"**
   - Wait for "Successfully pulled..." message

2. **Open the file**
   - Click Explorer icon in Activity Bar
   - Open `main.cpp`

3. **Make the changes**
   - Edit the `main()` function to add input validation
   - Example: Add `if (input < 0) { return -1; }`

4. **Stage and commit**
   - Go to Source Control view
   - You'll see `main.cpp` under "Changes"
   - Click **"+"** next to `main.cpp` to stage it
   - Type commit message: "Add input validation to main function"
   - Click **✓ Commit** button (or press `Ctrl+Enter`)

5. **Push to GitHub**
   - Click the **"..."** menu in Source Control view
   - Select **"Push"**
   - Or click the sync button (⟳) in the status bar
   - Wait for confirmation in the terminal

**Student B's Task:** Add a new `calculateAverage()` function

**Student B - Step by step:**

1. **Pull latest changes**
   - Click Source Control icon
   - Click **"..."** menu → **"Pull"**
   - **Important:** This gets Student A's changes that were just pushed
   - Student B now has the updated `main()` function with validation

2. **Open the file**
   - Click Explorer icon
   - Open `main.cpp`
   - Student B sees Student A's input validation code already there

3. **Make the changes**
   - Scroll to the bottom of the file
   - Add the new function:
   ```cpp
   double calculateAverage(int arr[], int size) {
       double sum = 0;
       for(int i = 0; i < size; i++) {
           sum += arr[i];
       }
       return sum / size;
   }
   ```

4. **Stage and commit**
   - Go to Source Control view
   - `main.cpp` appears under "Changes"
   - Click **"+"** to stage
   - Type commit message: "Add calculateAverage function"
   - Click **✓ Commit**

5. **Push to GitHub**
   - Click **"..."** → **"Push"**
   - Changes successfully pushed

**Result:**
- `main.cpp` on GitHub now has BOTH changes
- Student A's input validation in `main()`
- Student B's new `calculateAverage()` function
- No conflicts because they modified different parts of the file

**Student A - Seeing Student B's work:**

1. **Pull the latest changes**
   - Click **"..."** → **"Pull"** in Source Control view
   
2. **Open `main.cpp`**
   - Student A now sees the `calculateAverage()` function that Student B added
   - Both students' changes are now in the same file

**What if they edited the same lines?**

If both students had modified the exact same lines of code, a **merge conflict** would occur when the second person tries to pull. See the "Handling Merge Conflicts" section below for how to resolve this.

**Key Takeaways:**
- **Always pull before you start coding** - get the latest changes first
- **Commit and push frequently** - don't wait days to share your work
- **Pull regularly** - stay updated with your teammates' changes
- **Good commit messages help** - teammates can see what you changed
- **Different parts of the file = no conflicts** - Git handles this automatically
- **Same lines = merge conflict** - VS Code will help you resolve it

### Handling Merge Conflicts

When two people edit the same part of a file, Git creates a merge conflict.

**Resolving conflicts in VS Code:**

1. When you pull or merge, VS Code will highlight conflicted files
2. Open the file - you'll see sections marked like this:
   ```
   <<<<<<< HEAD
   Your changes
   =======
   Their changes
   >>>>>>> branch-name
   ```
3. VS Code shows options above the conflict:
   - **Accept Current Change** (keep yours)
   - **Accept Incoming Change** (keep theirs)
   - **Accept Both Changes** (keep both)
   - **Compare Changes** (see differences)
4. Choose the appropriate option or manually edit
5. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
6. Stage and commit the resolved file

### Advanced Git Features in VS Code

#### GitLens Extension (Highly Recommended)

1. Install the **GitLens** extension from the Extensions marketplace
2. Adds powerful Git features:
   - See who changed each line (inline blame annotations)
   - View file history
   - Compare branches and commits
   - Visual repository graphs

#### Viewing History

- Right-click a file in the Explorer
- Select **"Open Timeline"** to see all commits affecting that file
- Click any commit to see changes

#### Stashing Changes

If you need to switch branches but aren't ready to commit:

1. Open Command Palette (`Ctrl+Shift+P`)
2. Type "Git: Stash"
3. Your changes are temporarily saved
4. Later, use "Git: Apply Stash" to restore them

## Part 4: Combining Live Share and Git

The most powerful workflow combines both tools:

### Recommended Team Workflow

**Option 1: Paired Programming with Git**
1. One person hosts a Live Share session
2. Team codes together in real-time
3. Host commits and pushes changes to GitHub
4. Other team members pull the changes later

**Option 2: Feature Branch Collaboration**
1. Each team member creates their own feature branch
2. Work independently on branches
3. Use Live Share when you need help or code review
4. Merge completed features back to main branch
5. Pull regularly to stay updated

**Option 3: Hybrid Approach**
1. Use Live Share for planning and initial coding together
2. Split tasks and work on separate branches
3. Reconvene with Live Share to review and merge
4. Keep main branch stable with tested, working code

### Tips for Successful Team Projects

1. **Communicate your workflow:** Agree on when to use Live Share vs. working independently
2. **Commit often:** Small, frequent commits are easier to manage than large ones
3. **Pull before you code:** Always pull the latest changes before starting work
4. **Use descriptive branch names:** "sarah-database-setup" or "feature-user-authentication"
5. **Code reviews:** Use Live Share to walk through each other's code before merging
6. **Don't commit broken code to main:** Test your code before pushing to the main branch
7. **Document your work:** Add comments and update README files

## Quick Reference

### VS Code Keyboard Shortcuts

- **Command Palette:** `Ctrl+Shift+P` (Windows/Linux) or `Cmd+Shift+P` (macOS)
- **Open File:** `Ctrl+P` / `Cmd+P`
- **Toggle Terminal:** `Ctrl+`` / `Cmd+``
- **Save All:** `Ctrl+K S` / `Cmd+K S`
- **Split Editor:** `Ctrl+\` / `Cmd+\`
- **Find in Files:** `Ctrl+Shift+F` / `Cmd+Shift+F`

### Git Commands

- **Stage all changes:** `git add .`
- **Commit:** `git commit -m "message"`
- **Push:** `git push`
- **Pull:** `git pull`
- **Check status:** `git status`
- **View log:** `git log --oneline`
- **Create branch:** `git checkout -b branch-name`
- **Switch branch:** `git checkout branch-name`

### Troubleshooting Common Issues

**"Git not found"**
- Restart VS Code after installing Git
- Verify Git is in your PATH: `git --version` in terminal

**"Unable to push"**
- You may need to pull first if others have pushed changes
- Check that you have permission to push to the repository

**Live Share link not working**
- Ensure both users are signed in to Live Share
- Try generating a new link
- Check firewall settings (Live Share uses specific ports)

**Extensions not working**
- Reload VS Code: Command Palette > "Developer: Reload Window"
- Check for extension updates
- Disable conflicting extensions

## Next Steps

Once comfortable with the basics:

1. Explore **settings sync** to share VS Code configuration across devices
2. Learn about **debugging** in VS Code (breakpoints, watch variables)
3. Try **tasks and launch configurations** for custom build processes
4. Investigate **GitHub Pull Requests** extension for code review workflows
5. Set up **Continuous Integration** (CI) with GitHub Actions

---

**Additional Resources:**
- [VS Code Documentation](https://code.visualstudio.com/docs)
- [Live Share Documentation](https://docs.microsoft.com/visualstudio/liveshare/)
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com)
