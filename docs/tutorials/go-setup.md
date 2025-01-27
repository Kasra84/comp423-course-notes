# Setting up a dev container for Go

* Primary author: [Kasra Zamani](https://github.com/Kasra84)
* Reviewer: [Ethan Bonsall](https://github.com/ethanbonsall)
## What You Will Learn
### By completing this tutorial, you will:

1. Set up a basic Go Development Container in VS Code to streamline development.
2. Create a basic Go program
3. Gain insight into the tools and practices used in open-source and professional software projects.

## Prerequisites
### Before we dive in, make sure you have:

1. A GitHub account: If you don’t have one yet, sign up at [GitHub](https://github.com/).
2. Git installed: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
3. Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com/).
4. Docker installed: Required to run the dev container. [Get Docker here](https://www.docker.com/products/docker-desktop/).

## Part 1. Project Setup: Creating the Repository
### Step 1. Create a Local Directory and Initialize Git
 1. Open your terminal or command prompt.

 2. Create a new directory for your project.


```
 mkdir go-setup
 cd go-setup

```

 3. Initialize a new Git repository:

`git init`

 4. Create a README file:


```
echo "# Go Setup" > README.md
git add README.md
git commit -m "Initial commit with README"
```
### Step 2. Create a Remote Repository on GitHub
#### (1) Log in to your GitHub account and navigate to the Create a New Repository page.

#### (2) Fill in the details as follows:

- Repository Name: Go Tutorial
- Description: "Tutorial to setup a go container."
- Visibility: Public

#### (3) Do not initialize the repository with a README, .gitignore, or license.

#### (4) Click Create Repository.

### Step 3. Link your Local Repository to GitHub
#### (1) Add the GitHub repository as a remote:


`git remote add origin https://github.com/<your-username>/Go-Tutorial.git`
!!! info "Replace <your-username> with your GitHub username."

#### (2) Check your default branch name with the subcommand git branch. If it's not main, rename it to main with the following command: git branch -M main. Old versions of git choose the name master for the primary branch, but these days main is the standard primary branch name.

#### (3) Push your local commits to the GitHub repository:


`git push --set-upstream origin main`

#### (4) Back in your web browser, refresh your GitHub repository to see that the same commit you made locally has now been pushed to remote. You can use git log locally to see the commit ID and message which should match the ID of the most recent commit on GitHub. This is the result of pushing your changes to your remote repository.


## Part 2. Setting Up the Development Environment

### What is a Development (Dev) Container?
A dev container ensures that your development environment is consistent and works across different machines. It uses Docker to create isolated setups with the tools, libraries, and dependencies needed for your project. Think of it as a "mini computer" inside your computer, configured specifically for Go development.

Why is this valuable? In software development, mismatched environments can lead to bugs and wasted time. A dev container eliminates the "it works on my machine" problem, ensuring everyone on a team has an identical setup. It also simplifies onboarding by letting new team members start working with minimal setup.

For this tutorial, we will configure a dev container for Go development, ensuring we have the correct Go version and necessary tools.

---

### Step 1. Add Development Container Configuration
1. In VS Code, open the `go-setup` directory created in Part 1.
2. Install the **Dev Containers** extension for VS Code.
3. Create a `.devcontainer` directory:
   mkdir .devcontainer
4. Inside .devcontainer, create a devcontainer.json file:
    touch .devcontainer/devcontainer.json
5. Add the following content to devcontainer.json:
```
    {
  "name": "Go Dev Container",
  "image": "mcr.microsoft.com/devcontainers/go",
  "customizations": {
    "vscode": {
      "extensions": ["golang.go"]
    }
  }
}

```

### Step 2. Reopen the Project in the Dev Container

1. In VS Code, press Ctrl+Shift+P (or Cmd+Shift+P on Mac) to open the Command Palette.
2. Search for and select "Dev Containers: Reopen in Container".
3. Wait for the container to build and start. This might take a few minutes the first time.

### Step 3. Verify the Environment

1. Open the terminal in VS Code and run:
    `go version`

2. You should see the Go: version installed in the container.

## Part 3. Creating and Running a New Project

### Step 1. Initialize a New Go Module
1. In the terminal, navigate to your `go-setup` directory
2. Initialize a Go module:
   
   `go mod init go-setup`

### Step 2. Write and Run a Program That "Prints Hello COMP423"

1. Create a new file named "main.go"
    `touch main.go`
2. Open main.go and give it the input:

```go

package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

3. In the terminal, you can now run the program by inputting:
        `go run main.go` this will print `Hello COMP423`


### Step 3. Compile and Execute the Program

1. Compile the go program into an executable binary by typing:
    `go build main.go`
2. Now that you have the executable `main` file, you can run the executable:
    `./main` this should print `Hello COMP423` as well. 

### The Difference Between `go run` and `go build`

1. The `go run` command is primarily for quick compilation and execution
   in the case you want to immediately test the code. 
2. The `go build` command compiles and creates an executable binary file.
