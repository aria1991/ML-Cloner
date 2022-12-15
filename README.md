# ML-Cloner
Search through a user's repositories for ML python files and clone them automatically and create new Repo.
### About this method:
This script uses the **os module** to clone the user's repositories, create a new repository on GitHub, add the files to the repository, commit the changes, and push the code to the new repository. It uses the git command to perform these actions.

It also uses the **os.walk** function to recursively search through the cloned repositories for python files that contain "***machine learning***" in the filename. When it finds a repository that matches this criteria, it clones the repository, creates a new repository on GitHub, and pushes the code to the new repository.

### Step by step guide: 

 Install **git** on your computer if it is not already installed. You can check if git is installed by running the following command in a terminal or command prompt:
```python
git --version
```
> *If git is not installed, you can follow the instructions on the [Git website](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git "Git website") to install it.*

Open your favorite text editor ( Vs code is my favorite one)  and create a new file called ***clone-repos.py***
Paste the following code into ***clone-repos.py***:
```python
import os

# Replace USERNAME with the username of the user whose repositories you want to scan
USERNAME = "USERNAME"

# This is the URL of the user's repositories
url = f"https://github.com/{USERNAME}?tab=repositories"

# This is the directory where the repositories will be cloned to
REPO_DIRECTORY = "repos"

# This is the file extension for python files
PYTHON_FILE_EXTENSION = ".py"

# Clone all of the user's repositories
os.system(f"git clone {url} {REPO_DIRECTORY}")

# Loop through all of the repositories and find the ones that contain machine learning code
for root, dirs, files in os.walk(REPO_DIRECTORY):
    for file in files:
        # Check if the file is a python file and has "machine learning" in the filename
        if file.endswith(PYTHON_FILE_EXTENSION) and "machine learning" in file:
            # Clone the repository that contains the machine learning code
            repo_name = os.path.split(root)[-1]
            os.system(f"git clone https://github.com/{USERNAME}/{repo_name}.git")
            break

```
Replace **USERNAME** with the username of the user whose repositories you want to scan.

Save the file and close the text editor.

Open a terminal or command prompt and navigate to the directory where you saved clone-repos.py.

Run the following command to execute the script:
```python
python clone-repos.py

```
This will clone all of the user's repositories to a new directory called repos. It will then search through the repositories for python files that contain "machine learning" in the filename, and it will clone any repositories that match this criteria.

If you want to create a new repository with the machine learning code that you find, you can use the git command to create a new repository and push the code to it. For example:
```python
# Create a new repository on GitHub
os.system(f"git init")

# Add the files to the repository and commit the changes
os.system(f"git add .")
os.system(f"git commit -m 'Initial commit'")

# Push the code to the new repository
os.system(f"git push -u origin master")
break

```

 
