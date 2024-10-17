
## **Day 1: What is Git?**

-   **Concept:** Explain version control and why it’s useful.
-   **Activity:** Set up a GitHub account and create a new repository.
-   **Practice:** Create a simple text file and use `git init`, `git add`, and `git commit`.

#### **1. Introduction to Git (15 minutes)**

**What is Git?**

-   Git is a version control system that helps you track changes in your files and collaborate with others.
-   Think of it like a magical notebook that saves every version of your work, allowing you to go back in time if you make a mistake.

**Why is Version Control Useful?**

-   **Tracking Changes:** You can see what changes were made and by whom.
-   **Collaboration:** Multiple people can work on the same project without overwriting each other’s work.
-   **Backup:** If something goes wrong, you can revert to a previous version.

----------

#### **2. Setting Up GitHub Account (15 minutes)**

**Creating a GitHub Account:**

-   Go to [GitHub](https://github.com/).
-   Click on "Sign up" and fill out the form (choose a username, enter an email, create a password).
-   Follow the prompts to complete the setup (you may need to verify your email).

**Creating a New Repository:**

-   After logging in, click the "+" icon in the top right corner and select "New repository."
-   Name your repository (e.g., `my-first-repo`).
-   Add a description (optional) and choose "Public" or "Private."
-   Click "Create repository."

----------

#### **3. Practice: Using Git Locally (30 minutes)**

**Step 1: Set Up Git Locally**

-   If you haven’t installed Git yet, download it from [git-scm.com](https://git-scm.com/) and follow the installation instructions.

**Step 2: Create a Simple Text File**

-   Open a text editor (like Notepad or VSCode).
-   Create a new file, write something simple (e.g., "Hello, Git!"), and save it as `hello.txt`.

**Step 3: Initialize Git**

1.  Open a terminal or command prompt.
2.  Navigate to the folder where you saved `hello.txt`. Use:
    
    bash
    
    Copy code
    
    `cd path/to/your/folder` 
    
3.  Initialize a Git repository:
    
    bash
    
    Copy code
    
    `git init` 
    

**Step 4: Add the File to Staging**

-   Stage your file for committing:
    
    bash
    
    Copy code
    
    `git add hello.txt` 
    

**Step 5: Commit Your Changes**

-   Commit the staged file with a message:
    
    bash
    
    Copy code
    
    `git commit -m "Add hello.txt with greeting"` 
    

----------

### **Wrap-Up (5 minutes)**

**Review:**

-   Ask the student to summarize what they learned about Git, GitHub, and the commands they used.
-   Encourage them to explore creating branches and collaborating on projects next!

### **Next Steps:**

-   If time allows, consider showing them how to push their local repository to GitHub using:
    
    bash
    
    Copy code
    
    `git remote add origin <repository-url>
    git push -u origin main` 
    
