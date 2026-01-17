# Git Helper

[<img align="right" width=150px src='../res/rackete_2.png'></img>](../README.md)

Contents:
- [Git Helper](#git-helper)
    - [Most important Git commands to remember](#most-important-git-commands-to-remember)
    - [Notes](#notes)
    - [Git Example Worklfow](#git-example-worklfow)
    - [Additional Git-Commands](#additional-git-commands)
      - [Branching:](#branching)
    - [Solve Merge Conflicts](#solve-merge-conflicts)
    - [Git GUI](#git-gui)
    - [Git Remote](#git-remote)
    - [Git Submodules](#git-submodules)

> click the **rocket** for going **back**

<br><br>

---
### Most important Git commands to remember

---


Cloning an existing repository:
```git
git clone <link>
```
- Creates a copy
- The link can be found on GitLab/GitHub next to the Clone button (copy HTTP, not ssh) 
- If you shared SSH with GitHub, then you also can use SSH instead of HTTP

<br><br>

Cloning an existing repository with a specific branch:
```git
git clone -b <branchname> <link>
```

<br><br>

Stage all changes (add all changes to make them to the new standard via commit + push):
```git
git add *
```

<br><br>

Add a message to your changes (this is  must!):
```git
git commit -m 'Description in a nutshell
- Why the change was beneficial
- What exactly was changed and to what extent
- ...'
```
- With `'` you can write multi-line comments, and the comment only ends at the next `'` + enter-press

<br><br>

Update the origin repository with the staged changes + the commit message:

```git
git push
```

```git
git push origin main
```
- Where `main` is the branch name (change it if needed)

If you want that Git remembers where to push then set the upstream:
```git
git push -u origin main
```
- Where `main` is the branch name (change it if needed)

Linking is also possible afterwards:
```bash
git branch --set-upstream-to=origin/main
```
- Where `main` is the branch name (change it if needed)

<br><br>

> Quick explaination to `git push origin main` and linking (and remotes):  `git push` just tells git to push your changes, but not where to push. Most of the time this is already setted up if you clone from GitHub but sometimes it can happen and the setup is wrong or not completed, so listen. The `origin main` part tells where to push the changes to. `origin` is the name of the remote and `main` is the specific branch. Remotes are just other git repositores, in this case most likely the repository on Github or GitLab. But you can also add more than one remote and push to both ([click here to see this in more detail](#git-remote)). What git branches are [is explained here](#branching).<br> The command `git branch --set-upstream-to=origin/main` or the `-u` in the push command now sets the remote and the branch as default. If you next time right `git push` or `git pull`, your repo is linked/set to the setted remote + branch.

<br><br>

Updating the local repository with the global changes:
```git
git pull
```

```git
git pull origin main
```

<br><br>

Getting informations about the state of the local repository compred to the global repository:
```git
git status
```

<br><br>

Deleting local changes (dangerous!):
```git
git reset --hard
```

<br><br>

---
### Notes

---

- Git only saves changes (but in some files it can not detect the changes and instead it saves the whole new file as change) + and saves these changes forever! You can always go back to your first changes you made.
- You must be in a Git repository using Git Bash or Git CMD for these commands (except git clone) to work.
- When you are in a Git repository using Git Bash/Git CMD, the branch is displayed, making it easy to identify.
- You can also **right-click** in a folder to start Git Bash in that folder (this can be helpful).
- Do not commit/push large files!!!
  - Images
  - Databases
  - PDF Files
  - All Files which changes while you do not change your code
  - But there are always exceptions
  - You should know that pushed changed will never leave the memory of your project and so your project will grow and grow
  - It is also not ideal to handle files where changes can't be detected by Git (For example if you change one pixel in an image, git can not detect/save this small change instead it have to save the whole new image as "change")

<br><br>

---
### Git Example Worklfow

---

John Doe has been assigned to a team and is supposed to set up a project with Git together with his teammates. But where does he start? <br>The Model School has already created a Git project (repository).

0. Don't forget VPN. Recommendation: Cisco AnyConnect (see PDF in Discord => Meeting place -> Pins)
1. [Install Git](https://git-scm.com/)
2. Configure Git settings<br>
   -> git config --global user.name [name]<br>-> git config --global user.email [email]
3. Clone/copy Git project to local computer<br>
   -> git clone [link]
4. Max Mustermann is now working on the project and programming diligently (as usual)
5. Now Max wants to apply the changes locally.<br>
   -> git add *<br>-> git commit -m “description”
6. Finally, he wants to share his local changes with his team<br>
   -> git push

If the origin repository has undergone changes in the meantime, you must first update your local repository (git pull) and then push your own changes.


<br><br>

---
### Additional Git-Commands

---

Loading a specific commit (seeing earlier states of your repo):
```git 
git checkout <commit sha>
```

<br><br>

Creating a new Git repository in the current folder:
```git
git init
```

<br><br>

Setting the name of the git user:
```git 
git config --global user.name <name>
```
- Example: `git config --global user.name xXAI-botXx`
- You can also set it different for single projects: `git config user.name <name>`
- Just use your GitHub name for example

<br><br>

Setting the email of the git user:
```git 
git config --global user.email <email>
```
- You can also set it different for single projects: `git config user.email <email>`

<br><br>

Showing the complete commit history:
```git 
git log
```
- several [options](https://git-scm.com/book/de/v2/Git-Grundlagen-Anzeigen-der-Commit-Historie) are available here

<br><br>

#### Branching:

Branches are just like alternative realities for the project. So you can make a branch, then implement a new feature and when its working you can merge your new changes (your branch) with the main branch. In that way multiple people can work on the same repository without destroying anything.<br>
You also can use branches to develope an alternative version of your software and still can update some changes through the branches. Or you can store completly different informations, for example storing code for a website in a branch (but this is more special and only recommended in a few cases, though it is not meant for that).

<br><br>

List of all available branches:
```git 
git branch
```

<br><br>

Creating a new branch from the current branch:
```git 
git branch <new-branch-name>
```

<br><br>

Creating a new branch from the specified base branch:
```git 
git branch <new-branch-name> <base-branch-name>
```

<br><br>

Loading a specified branch:
```git 
git checkout <branch-name>
```

<br><br>

Creating a new branch and loads it directly:
```git 
git checkout -b <new-branch-name>
```

<br><br>

Merging a specified branch into the current branch:
```bash 
git merge <branch>
```

<br><br>

Closing a specified branch:
```bash 
git branch -d <branch-name>
```

<br><br>

Rename a Branch:
```bash 
git branch -m <branch-name> <new-branch-name>
```

Or rename current branch:
```bash
git branch -m <new-branch-name>
```

<br><br>

Set default "main/master" branch name:
```bash
git config --global init.defaultBranch main
```


If you are working in another branch and have now finished your work, first switch to the ‘master’ branch (or whatever it is called) -> checkout command. Then merge the other branch with its changes into the current branch -> using the merg command.  The branch can then be closed. 

> Remember to make sure you have actually applied your changes to your working branch -> committed and pushed.


<br><br>

---
### Solve Merge Conflicts

---

A merge conflict appears if there are 2 or more changes and git does not know which of these changes should keep or how to combine these 2 changes.<br>
For example: " persons clone and change the same lines in a python file in different ways, then git does not know which of the changes should be used/how these changes should be merged. The merge conflict appears when one of the persons pushes his changes and the second person then have to pull (and then push) his changes but during the pull process git will raise a merge conflict and here is a way to solve it.

> You find the name of your current branch with `git status`.

1. **Commit your local changes** (and maybe push if possible -> for example in a forked repo it would still be possible)
   ```git
   git checkout main
   git fetch origin
   git pull origin main
   ```
2. (Only if you want to update an forked repo with his original) **Get the newest changes from a remote repo locally**
   ```git
   git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPO.git
   git fetch upstream
   git checkout main
   git merge upstream/main
   ```
   main = use the name of your main branch
   > Important: If you only want to update your main branch with a remote repo, then you can skip the next step (step 3), because you already start a merging here with the remote repo.
3. **Start Merge locally**
   ```git
   git checkout <YOUR_BRANCH_NAME>
   git merge main
   ```
   main = use the name of your main branch.<br>
4. **Understand the conflicts**
   Following command shows you open files with conflicts:
   ```git
   git status
   ```
   Then the files should contain marking like that:
   ```text
   <<<<<<< HEAD
   your changes
   =======
   Changes from main
   >>>>>>> main
   ```
   Where:
   - `<<<<<<< HEAD` → start of your critical code
   - `=======` → End of your critical changes and beginning of the critical changes of main
   - `>>>>>>> main` → end of the critical changes from main
5. **Solve conflict**<br>
   Now just keep and change the conflict areas as you wish and the situation needs. Maybe keep only one of the changes or you combine them. At the end of your solution there should be no `<<<<<<< HEAD`, `=======`, `>>>>>>> main` anymore.
6. **Push solved conflict**<br>
   Now you just have to commit and push your changes. You may want to use your IDE (VSCode, ...) for that or Git GUI or Git Commandline:
   ```git
   git add conflict_file_1 conflict_file_2
   git commit -m "solved merging XY changes by keeping Z and merging A with B because C"
   git push
   ```

Cancelling a merge is done by:
```git
git merge --abort
```

<br><br>

---
### Git GUI

---

Don't feel like memorizing commands and would rather see all changes clearly? That's exactly what Git GUI is for, and working with it is really easy.

<br><br>

**Getting started**<br>
Just like Git Bash, Git GUI can be opened by right-clicking directly in the desired folder/Git repository and the looking for a `Open with Git GUI`. Alternatively, you can start Git GUI and go to **Open Existing Repository** (on the start screen, you can also create a new repository or clone a repository).<br>
If you have an repository online on GitHub or GitLab, then click on **Clone Existing Repository**. Then choose the source repository (the http or ssh link) and pick the target folder + don't forget to add a folder name (Git GUI will create the folder for you). 

> Important: On the top-left corner there should be the information of the current local branch name. Make sure that it is the same branch name, as the one in your GitHub. **You might want to rename your branch (`branch > rename`) from `master` to `main`** as it is for me most of the times. Or sometimes want to checkout to another branch (`branch > checkout`). <br>Explanation: Git GUI clones your main branch but renames the local branch to master and when you push, GitHub will create you a new branch with the name master. Therefore a simple renaming solves this problem.<br><br>A longtime solution is to open git bash or add a git command vi Git GUI `tools > Add...` and run `git config --global init.defaultBranch main`.

<br><br>

**Operation**<br>
All changes should now be displayed in the *Unstaged Changes* area at the top left. If not, press the *Rescan* button (roughly in the middle, the top button of several buttons).<br>Now select all the changes you really want to change and stage them by selecting *>Commit>Stage to Commit* in the menu bar. In the *Commit* tab, you can also select *Unstage From Commit* to undo changes (return them to the Unstaged area).<br>Once all changes have been selected/staged, you can execute (commit) the changes in the local repository. To do this, press the *Commit* button. <br>If you also want to update your changes with the original repository, press the *Push* button (this can also be done at any later time).<br><br>If something has been changed in the original repository (not locally) and you want to apply these changes (because you want to push, for example), you need to do two things. <br>1. *> Remote > Fetch from*<br>2.*> Merge > Local Merge*<br>(This is actually what the git pull command does internally).

<br><br>

**Workflow example**
1. Open Git GUI at the desired location (where the project folder should appear). <br>    
   -> Right-click and open Git GUI. 
2. Select *Clone Existing Repository*<br>
   -> Source Directory: HTTP link from repository <br>
   -> Target Directory: Folder path/folder where the project will be placed + folder name<br>
3. Check the local branch name (main - master conflict -> maybe rename)
4. Now you can work diligently (create, edit, delete files)
5. Press *Rescan*
6. Stage all changes you want to commit (in the *Commit* tab).
7. Write a commit message and click *Commit*.
8. Update the repository (not always necessary).<br>    
   -> *Remote > Fetch From*<br>    
   -> *Merge > Local Merge*<br>
9. Click *Push*.

<br><br>

**Additional features**

- Under *> Repository*, you can visualize one or all branches (click on *Visualize ...*)
- Under *> Tools > Add...*, you can add Git commands that can be executed at the touch of a button<br>        -> *Name* is just any name<br>        
   -> *Command* is then the git command (`git add *` or `git pull origin main` ...)
- Under *> Branch*, you can create new branches or perform a checkout to other branches

<br><br>

**Notes**

- Do not commit/push large files!!!
- If push does not work, the repository must be updated.
   1. *Remote > Fetch From*
   2. *Merge > Local Merge*
- You can also choose a combination of Git Bash and Git GUI, as both have advantages and disadvantages
- Under *> Repository > Git Bash*, you can quickly open Git Bash
- Create a *git pull* command in *Tools*, which makes things a lot easier (see complicated method above)

<br><br>

**Important shortcuts**

- Ctrl+T/Ctrl+U: Stage/unstage selected file
- Ctrl+I: Stage all files (asks if you want to add new files if there are any)
- Ctrl+J: Revert changes
- Ctrl+Enter: Commit
- Ctrl+P: Push
- Ctrl+M: Local Merge
- F5: Rescan

<br><br>

---
### Git Remote

---

It is possible to transfer projects from Gitlab to Github and vice versa. For example, you can upload a secret project as a private Github project as a backup.

To do this:

```bash
git remote add github url-of-empty-github-projekt
git push github --all
git remote remove github
```
<br><br>

You can check with which Github Project your local Git Project is connect via:
```bash
git remote -v
```
Shows: REMOTE_NAME REMOTE_URL (PIPELINE -> push or pull/fetch)

<br><br>

You can then also change to which Github Project you want to push and pull from:
```bash
git remote set-url origin https://github.com/YOUR_NAME/your-project.git
```
Or via SSH:
```bash
git remote set-url origin git@github.com:YOUR_NAME/your-project.git
```

Check via: `git remote -v`

<br><br>

If you changed your Github name, this is for you: Changing all git repos and submodules in current folder. Go into your GitBash, `cd` to the fodler with git projects and paste following code (change the naming):
```bash
OLDNAME="xXAI-botXx"
NEWNAME="M-106"

for d in */.git; do
  (
    cd "${d%/.git}" || exit

    echo
    echo "============================================"
    echo "Repository: $(basename "$(pwd)")"
    echo "============================================"

    # ---- Main repo ----
    if git remote get-url origin | grep -q "$OLDNAME"; then
      git remote set-url origin "$(git remote get-url origin | sed "s/$OLDNAME/$NEWNAME/")"
      echo "Updated main repo remote"
    else
      echo "Main repo remote unchanged"
    fi

    # ---- Submodules ----
    git submodule foreach --recursive '
      if git remote get-url origin | grep -q "'"$OLDNAME"'"; then
        git remote set-url origin "$(git remote get-url origin | sed "s/'"$OLDNAME"'/'"$NEWNAME"'/")"
        echo "Updated submodule: $name"
      else
        echo "Submodule unchanged: $name"
      fi
    '

    # ---- Sync + update ----
    git submodule sync --recursive
    git submodule update --init --recursive

    # ---- Verification ----
    echo
    echo "--- Main repo remotes ---"
    git remote -v

    echo
    echo "--- Submodule remotes ---"
    git submodule foreach --recursive 'git remote -v'

  )
done
```

Example output:
```bash
tobia@TobiasPC MINGW64 /d/Informatik/Projekte
$ OLDNAME="xXAI-botXx"
NEWNAME="M-106"

for d in */.git; do
  (
    cd "${d%/.git}" || exit

    echo
    echo "============================================"
    echo "Repository: $(basename "$(pwd)")"
    echo "============================================"

    # ---- Main repo ----
    if git remote get-url origin | grep -q "$OLDNAME"; then
      git remote set-url origin "$(git remote get-url origin | sed "s/$OLDNAME/$NEWNAME/")"
      echo "Updated main repo remote"
    else
      echo "Main repo remote unchanged"
    fi

    # ---- Submodules ----
    git submodule foreach --recursive '
      if git remote get-url origin | grep -q "'"$OLDNAME"'"; then
        git remote set-url origin "$(git remote get-url origin | sed "s/'"$OLDNAME"'/'"$NEWNAME"'/")"
donegit submodule foreach --recursive 'git remote -v'

============================================
Repository: AI
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/AI.git (fetch)
origin  https://github.com/M-106/AI.git (push)

--- Submodule remotes ---

============================================
Repository: automatic_latex_photo_album
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/automatic_latex_photo_album.git (fetch)
origin  https://github.com/M-106/automatic_latex_photo_album.git (push)

--- Submodule remotes ---

============================================
Repository: computer-vision
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/computer-vision.git (fetch)
origin  https://github.com/M-106/computer-vision.git (push)

--- Submodule remotes ---

============================================
Repository: CPP
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/CPP.git (fetch)
origin  https://github.com/M-106/CPP.git (push)

--- Submodule remotes ---

============================================
Repository: Data-Engineer-Reference
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/Data-Engineer-Reference.git (fetch)
origin  https://github.com/M-106/Data-Engineer-Reference.git (push)

--- Submodule remotes ---

============================================
Repository: Deep-Learning-for-Medical-Images
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/Deep-Learning-for-Medical-Images.git (fetch)
origin  https://github.com/M-106/Deep-Learning-for-Medical-Images.git (push)

--- Submodule remotes ---

============================================
Repository: DirectX
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/DirectX.git (fetch)
origin  https://github.com/M-106/DirectX.git (push)

--- Submodule remotes ---

============================================
Repository: Docker
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Docker.git (fetch)
origin  https://github.com/M-106/Docker.git (push)

--- Submodule remotes ---

============================================
Repository: Emerging-Light-Engine
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Emerging-Light-Engine.git (fetch)
origin  https://github.com/M-106/Emerging-Light-Engine.git (push)

--- Submodule remotes ---

============================================
Repository: GANs
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/GANs.git (fetch)
origin  https://github.com/M-106/GANs.git (push)

--- Submodule remotes ---

============================================
Repository: Generative-Deep-Learning
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Generative-Deep-Learning.git (fetch)
origin  https://github.com/M-106/Generative-Deep-Learning.git (push)

--- Submodule remotes ---

============================================
Repository: Genetic-Algorithm
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Genetic-Algorithm.git (fetch)
origin  https://github.com/M-106/Genetic-Algorithm.git (push)

--- Submodule remotes ---

============================================
Repository: Graph-Manifold-Learn
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Graph-Manifold-Learn.git (fetch)
origin  https://github.com/M-106/Graph-Manifold-Learn.git (push)

--- Submodule remotes ---

============================================
Repository: Graph-Neural-Networks
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Graph-Neural-Networks.git (fetch)
origin  https://github.com/M-106/Graph-Neural-Networks.git (push)

--- Submodule remotes ---

============================================
Repository: Image-Physics-Simulation
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Image-Physics-Simulation.git (fetch)
origin  https://github.com/M-106/Image-Physics-Simulation.git (push)

--- Submodule remotes ---

============================================
Repository: Latex
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Latex.git (fetch)
origin  https://github.com/M-106/Latex.git (push)

--- Submodule remotes ---

============================================
Repository: Magic-Sovereign
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Magic-Sovereign.git (fetch)
origin  https://github.com/M-106/Magic-Sovereign.git (push)

--- Submodule remotes ---

============================================
Repository: MirrorNet
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/MirrorNet.git (fetch)
origin  https://github.com/M-106/MirrorNet.git (push)

--- Submodule remotes ---

============================================
Repository: Mouse-Keyboard-Activity
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Mouse-Keyboard-Activity.git (fetch)
origin  https://github.com/M-106/Mouse-Keyboard-Activity.git (push)

--- Submodule remotes ---

============================================
Repository: Noise-Modelling-Datageneration
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Noise-Modelling-Datageneration.git (fetch)
origin  https://github.com/M-106/Noise-Modelling-Datageneration.git (push)

--- Submodule remotes ---

============================================
Repository: Pointcloud-M-106
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/Pointcloud-M-106.git (fetch)
origin  https://github.com/M-106/Pointcloud-M-106.git (push)

--- Submodule remotes ---

============================================
Repository: prime_printer
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/prime_printer.git (fetch)
origin  https://github.com/M-106/prime_printer.git (push)

--- Submodule remotes ---

============================================
Repository: Project_Transformer
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Project_Transformer.git (fetch)
origin  https://github.com/M-106/Project_Transformer.git (push)

--- Submodule remotes ---

============================================
Repository: Pythonic-X-ray
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Pythonic-X-ray.git (fetch)
origin  https://github.com/M-106/Pythonic-X-ray.git (push)

--- Submodule remotes ---

============================================
Repository: Python-Reference
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Python-Reference.git (fetch)
origin  https://github.com/M-106/Python-Reference.git (push)

--- Submodule remotes ---

============================================
Repository: PyTorch-Reference
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/PyTorch-Reference.git (fetch)
origin  https://github.com/M-106/PyTorch-Reference.git (push)

--- Submodule remotes ---

============================================
Repository: PyTorch-Reference-External
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/PyTorch-Reference.git (fetch)
origin  https://github.com/M-106/PyTorch-Reference.git (push)

--- Submodule remotes ---

============================================
Repository: RAG_Evaluation
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/RAG_Evaluation.git (fetch)
origin  https://github.com/M-106/RAG_Evaluation.git (push)

--- Submodule remotes ---

============================================
Repository: Reinforcement_Course
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Reinforcement_Course.git (fetch)
origin  https://github.com/M-106/Reinforcement_Course.git (push)

--- Submodule remotes ---

============================================
Repository: RL-Stock-Trading
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/RL-Stock-Trading.git (fetch)
origin  https://github.com/M-106/RL-Stock-Trading.git (push)

--- Submodule remotes ---

============================================
Repository: Runtime-Guard
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Runtime-Guard.git (fetch)
origin  https://github.com/M-106/Runtime-Guard.git (push)

--- Submodule remotes ---

============================================
Repository: Super-Zeldario
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Super-Zeldario.git (fetch)
origin  https://github.com/M-106/Super-Zeldario.git (push)

--- Submodule remotes ---

============================================
Repository: TensorFlow-Reference
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/TensorFlow-Reference.git (fetch)
origin  https://github.com/M-106/TensorFlow-Reference.git (push)

--- Submodule remotes ---

============================================
Repository: tensor-rush
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/tensor-rush.git (fetch)
origin  https://github.com/M-106/tensor-rush.git (push)

--- Submodule remotes ---

============================================
Repository: torch-mask-rcnn-instance-segmentation
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/torch-mask-rcnn-instance-segmentation.git (fetch)
origin  https://github.com/M-106/torch-mask-rcnn-instance-segmentation.git (push)

--- Submodule remotes ---

============================================
Repository: Wind_Forge
============================================
Updated main repo remote

--- Main repo remotes ---
origin  https://github.com/M-106/Wind_Forge.git (fetch)
origin  https://github.com/M-106/Wind_Forge.git (push)

--- Submodule remotes ---

tobia@TobiasPC MINGW64 /d/Informatik/Projekte
$ cd ..

tobia@TobiasPC MINGW64 /d/Informatik
$ OLDNAME="xXAI-botXx"
NEWNAME="M-106"

for d in */.git; do
  (
    cd "${d%/.git}" || exit

    echo
    echo "============================================"
    echo "Repository: $(basename "$(pwd)")"
    echo "============================================"

    # ---- Main repo ----
    if git remote get-url origin | grep -q "$OLDNAME"; then
      git remote set-url origin "$(git remote get-url origin | sed "s/$OLDNAME/$NEWNAME/")"
      echo "Updated main repo remote"
    else
      echo "Main repo remote unchanged"
    fi

    # ---- Submodules ----
    git submodule foreach --recursive '
      if git remote get-url origin | grep -q "'"$OLDNAME"'"; then
        git remote set-url origin "$(git remote get-url origin | sed "s/'"$OLDNAME"'/'"$NEWNAME"'/")"
donegit submodule foreach --recursive 'git remote -v'

============================================
Repository: M-106
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/M-106.git (fetch)
origin  https://github.com/M-106/M-106.git (push)

--- Submodule remotes ---

============================================
Repository: Project-Helper
============================================
Updated main repo remote
Entering 'external/Image-Physics-Simulation'
Updated submodule: external/Image-Physics-Simulation
Entering 'external/Runtime-Guard'
Updated submodule: external/Runtime-Guard
Synchronizing submodule url for 'external/Image-Physics-Simulation'
Synchronizing submodule url for 'external/Runtime-Guard'
Submodule 'external/AI' (https://github.com/xXAI-botXx/AI) registered for path 'external/AI'
Submodule 'external/CPP' (https://github.com/xXAI-botXx/CPP) registered for path 'external/CPP'
Submodule 'external/Data-Engineer-Reference' (https://github.com/xXAI-botXx/Data-Engineer-Reference) registered for path 'external/Data-Engineer-Reference'
Submodule 'external/Deep-Learning-for-Medical-Images' (https://github.com/xXAI-botXx/Deep-Learning-for-Medical-Images) registered for path 'external/Deep-Learning-for-Medical-Images'
Submodule 'external/GANs' (https://github.com/xXAI-botXx/GANs) registered for path 'external/GANs'
Submodule 'external/HelpJl' (https://github.com/xXAI-botXx/HelpJl) registered for path 'external/HelpJl'
Submodule 'external/Latex' (https://github.com/xXAI-botXx/Latex) registered for path 'external/Latex'
Submodule 'external/Project_Transformer' (https://github.com/xXAI-botXx/Project_Transformer) registered for path 'external/Project_Transformer'
Submodule 'external/PyTorch-Reference' (https://github.com/xXAI-botXx/PyTorch-Reference) registered for path 'external/PyTorch-Reference'
Submodule 'external/PyTorch-Reference-Extern' (https://github.com/xXAI-botXx/PyTorch-Reference-Extern) registered for path 'external/PyTorch-Reference-Extern'
Submodule 'external/Python-Reference' (https://github.com/xXAI-botXx/Python-Reference) registered for path 'external/Python-Reference'
Submodule 'external/Reinforcement_Learning' (https://github.com/xXAI-botXx/Reinforcement_Learning) registered for path 'external/Reinforcement_Learning'
Submodule 'external/TensorFlow-Reference' (https://github.com/xXAI-botXx/TensorFlow-Reference) registered for path 'external/TensorFlow-Reference'
Submodule 'external/Wind_Forge' (https://github.com/xXAI-botXx/Wind_Forge.git) registered for path 'external/Wind_Forge'
Submodule 'external/computer-vision' (https://github.com/xXAI-botXx/computer-vision) registered for path 'external/computer-vision'
Submodule 'external/prime_printer' (https://github.com/xXAI-botXx/prime_printer) registered for path 'external/prime_printer'
Cloning into 'D:/Informatik/Project-Helper/external/AI'...
Cloning into 'D:/Informatik/Project-Helper/external/CPP'...
Cloning into 'D:/Informatik/Project-Helper/external/Data-Engineer-Reference'...
Cloning into 'D:/Informatik/Project-Helper/external/Deep-Learning-for-Medical-Images'...
Cloning into 'D:/Informatik/Project-Helper/external/GANs'...
Cloning into 'D:/Informatik/Project-Helper/external/HelpJl'...
Cloning into 'D:/Informatik/Project-Helper/external/Latex'...
Cloning into 'D:/Informatik/Project-Helper/external/Project_Transformer'...
Cloning into 'D:/Informatik/Project-Helper/external/PyTorch-Reference'...
Cloning into 'D:/Informatik/Project-Helper/external/PyTorch-Reference-Extern'...
Cloning into 'D:/Informatik/Project-Helper/external/Python-Reference'...
Cloning into 'D:/Informatik/Project-Helper/external/Reinforcement_Learning'...
Cloning into 'D:/Informatik/Project-Helper/external/TensorFlow-Reference'...
Cloning into 'D:/Informatik/Project-Helper/external/Wind_Forge'...
Cloning into 'D:/Informatik/Project-Helper/external/computer-vision'...
Cloning into 'D:/Informatik/Project-Helper/external/prime_printer'...
Submodule path 'external/AI': checked out '48982346e507e7d16ca18523ef0d79ece88b544a'
Submodule path 'external/CPP': checked out 'e9347dec090dc1faf0042c581d2e134a0bd7072a'
Submodule path 'external/Data-Engineer-Reference': checked out '83455e8d033848e3e3366df1a0adf2fb138a3ff3'
Submodule path 'external/Deep-Learning-for-Medical-Images': checked out '006ffd3183f07e2eca0f34108775fc25a919f627'
Submodule path 'external/GANs': checked out '30c3bcc0d05dd7f970b56c2ee156daf044ae53ff'
Submodule path 'external/HelpJl': checked out '69495725cb2780f3139e194c6407ec070b4061e6'
Submodule path 'external/Latex': checked out '2f27c6d041ab5b99957eece1378c954537dda9cf'
Submodule path 'external/Project_Transformer': checked out 'f2424492dc83f3d9917bf005408a9eb3f5394846'
Submodule path 'external/PyTorch-Reference': checked out '6bd0a241d388a99b0271511a4b222432d92ea3b5'
Submodule path 'external/PyTorch-Reference-Extern': checked out '502aa5c36666381206e05922ed5c3c3bca899554'
Submodule path 'external/Python-Reference': checked out '48770e5dc266c62d5d16ef078cd21a3603bcf6e3'
Submodule path 'external/Reinforcement_Learning': checked out '4a52fe3370b9e11826acdc74cb02abff6b59f57e'
Submodule path 'external/TensorFlow-Reference': checked out '5ab77afcfd0312f2e2df4127063920928f3faac1'
Submodule path 'external/Wind_Forge': checked out '5fbebc930174938ccd831a61eb3e9682f8c284c6'
Submodule path 'external/computer-vision': checked out '070e93a3bc77ec14cdf5dd0df6b8622c47ffcf77'
Submodule path 'external/prime_printer': checked out '15dcbde8a71751495c0414fa91ef45c43c0d1a85'

--- Main repo remotes ---
origin  https://github.com/M-106/Project-Helper.git (fetch)
origin  https://github.com/M-106/Project-Helper.git (push)

--- Submodule remotes ---
Entering 'external/AI'
origin  https://github.com/xXAI-botXx/AI (fetch)
origin  https://github.com/xXAI-botXx/AI (push)
Entering 'external/CPP'
origin  https://github.com/xXAI-botXx/CPP (fetch)
origin  https://github.com/xXAI-botXx/CPP (push)
Entering 'external/Data-Engineer-Reference'
origin  https://github.com/xXAI-botXx/Data-Engineer-Reference (fetch)
origin  https://github.com/xXAI-botXx/Data-Engineer-Reference (push)
Entering 'external/Deep-Learning-for-Medical-Images'
origin  https://github.com/xXAI-botXx/Deep-Learning-for-Medical-Images (fetch)
origin  https://github.com/xXAI-botXx/Deep-Learning-for-Medical-Images (push)
Entering 'external/GANs'
origin  https://github.com/xXAI-botXx/GANs (fetch)
origin  https://github.com/xXAI-botXx/GANs (push)
Entering 'external/HelpJl'
origin  https://github.com/xXAI-botXx/HelpJl (fetch)
origin  https://github.com/xXAI-botXx/HelpJl (push)
Entering 'external/Image-Physics-Simulation'
origin  https://github.com/xXAI-botXx/Image-Physics-Simulation.git (fetch)
origin  https://github.com/xXAI-botXx/Image-Physics-Simulation.git (push)
Entering 'external/Latex'
origin  https://github.com/xXAI-botXx/Latex (fetch)
origin  https://github.com/xXAI-botXx/Latex (push)
Entering 'external/Project_Transformer'
origin  https://github.com/xXAI-botXx/Project_Transformer (fetch)
origin  https://github.com/xXAI-botXx/Project_Transformer (push)
Entering 'external/PyTorch-Reference'
origin  https://github.com/xXAI-botXx/PyTorch-Reference (fetch)
origin  https://github.com/xXAI-botXx/PyTorch-Reference (push)
Entering 'external/PyTorch-Reference-Extern'
origin  https://github.com/xXAI-botXx/PyTorch-Reference-Extern (fetch)
origin  https://github.com/xXAI-botXx/PyTorch-Reference-Extern (push)
Entering 'external/Python-Reference'
origin  https://github.com/xXAI-botXx/Python-Reference (fetch)
origin  https://github.com/xXAI-botXx/Python-Reference (push)
Entering 'external/Reinforcement_Learning'
origin  https://github.com/xXAI-botXx/Reinforcement_Learning (fetch)
origin  https://github.com/xXAI-botXx/Reinforcement_Learning (push)
Entering 'external/Runtime-Guard'
origin  https://github.com/xXAI-botXx/Runtime-Guard.git (fetch)
origin  https://github.com/xXAI-botXx/Runtime-Guard.git (push)
Entering 'external/TensorFlow-Reference'
origin  https://github.com/xXAI-botXx/TensorFlow-Reference (fetch)
origin  https://github.com/xXAI-botXx/TensorFlow-Reference (push)
Entering 'external/Wind_Forge'
origin  https://github.com/xXAI-botXx/Wind_Forge.git (fetch)
origin  https://github.com/xXAI-botXx/Wind_Forge.git (push)
Entering 'external/computer-vision'
origin  https://github.com/xXAI-botXx/computer-vision (fetch)
origin  https://github.com/xXAI-botXx/computer-vision (push)
Entering 'external/prime_printer'
origin  https://github.com/xXAI-botXx/prime_printer (fetch)
origin  https://github.com/xXAI-botXx/prime_printer (push)

============================================
Repository: Project-Lake
============================================
Updated main repo remote
fatal: No url found for submodule path 'Deploy Machine Learning Models/deploying-machine-learning-models' in .gitmodules
fatal: No url found for submodule path 'Deploy Machine Learning Models/deploying-machine-learning-models' in .gitmodules

--- Main repo remotes ---
origin  https://github.com/M-106/Project-Lake.git (fetch)
origin  https://github.com/M-106/Project-Lake.git (push)

--- Submodule remotes ---
fatal: No url found for submodule path 'Deploy Machine Learning Models/deploying-machine-learning-models' in .gitmodules

============================================
Repository: xXAI-botXx
============================================
Main repo remote unchanged

--- Main repo remotes ---
origin  https://github.com/M-106/M-106.git (fetch)
origin  https://github.com/M-106/M-106.git (push)

--- Submodule remotes ---
```

<br><br>

---
### Git Submodules

---

Cloning a Git repository with submodules:
```bash
git clone <url>
git submodule update --init --recursive
```


Adding a submodule:
```bash
git submodule add <url>
```

Removing a submodule:
```bash
git rm module-folder-name
git commit -m "removed submodule"
git push
```

Updating Submodules:
```bash
git submodule update --recursive --remote
```

Get current status of submodules:
```bash
git submodule status
```


