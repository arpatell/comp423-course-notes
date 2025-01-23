# Setting up a dev container for Go

* Primary author: [Aaron Patel](https://github.com/arpatell)

---

## Intro
This is a guide for setting up a basic Go project. You will setup a Go project with a Git repository and dev container, and produce a "Hello, World!" program.

---

## Prerequisites

Before diving in, ensure you have the following installed:

- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/)
- [VS Code](https://code.visualstudio.com/) with the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

---

## Step 1: Create a Local Directory and Initialize Git

1. Open your terminal and create a directory for the project.
2. Run the following commands:

        mkdir go-hello-world

        cd go-hello-world

        git init

3. Add a GitHub repository

     1. Create a remote repo in Github named "go-hello-world" and set visibility to public
     2. In your project, add the Github repo as a remote:

        ```
        git remote add origin https://github.com/<your-username>/go-hello-world
        ```

        Replace `<your-username>` with your GitHub username.

---

## Step 2: Set Up a Development Container

1. Create a `.devcontainer` directory and a `devcontainer.json` file:

        mkdir .devcontainer

        touch .devcontainer/devcontainer.json

2. Add the following to the `devcontainer.json` file:

        {
          "name": "Go Dev Container",
          "image": "golang:1.20",
          "features": {},
          "mounts": ["source=/var/run/docker.sock,target=/var/run/docker.sock,type=bind"]
        }

3. Open your project in VS Code and reopen it in the container by clicking **Reopen in Container**.

---

## Step 3: Initialize the Go Project

1. Inside the dev container, run:

        go mod init github.com/<yourusername>/go-hello-world

      Replace `<your-username>` with your GitHub username.

    > This creates a `go.mod` file, which defines your Go module.

---

## Step 4: Add "Hello, World!"

1. Create a `main.go` file:

        touch main.go

2. Add the following code to `main.go`:

        package main

        import "fmt"

        func main() {
            fmt.Println("Hello, World!")
        }

---

## Step 5: Compile and Run the Project

1. To compile the project, run:

        go build -o hello

      > This creates an executable file named `hello`.

2. Run the executable:

        ./hello

    You should see this output:

        Hello, World!

---

## Step 6: Push to GitHub

1. Stage files, and add a README if you'd like:

        echo "your-md-text-here" > README.md

        git add .

2. Add configs and commit:

        git config user.name --global "your-username-here"

        git config user.email --global "your-email-here"
        
        git commit -m "your-message-here"

3. Push to remote:

        git branch -M main
        
        git push --set-upstream origin main

---

Congrats! You have completed the tutorial.