# Development Environment Setup Guide

This guide provides step-by-step instructions to set up a development environment using Docker and Visual Studio Code (VSCode), including the necessary extensions and configuration files.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Docker**: [Download Docker](https://docs.docker.com/get-docker/)
- **Visual Studio Code (VSCode)**: [Download VSCode](https://code.visualstudio.com/Download)

## Step 1: Install Necessary Extensions in VSCode

Install the following extensions in VSCode to enhance your development experience:

- **Remote - Containers**: Enables you to use a Docker container as a full-featured development environment.

  You can install this extension directly from the VSCode Extensions view (`Ctrl+Shift+X`) by searching for "Remote - Containers" and clicking Install.

## Step 2: Create a Dockerfile
Create a folder somewhere on your computer where you want to store all of the files for this program. Inside of that folder is called the "root directory", this is the root of the program. Below is an example, an indent indicates that it is a subfolder within the directory. The "#" indicates a comment, explaining what each line does.
- /project-root-directory  # This is the root directory of your project
  
  - .devcontainer          # A folder for VS Code's development container configuration
    - devcontainer.json    # Configuration file for the development container
    - Dockerfile             # Dockerfile resides in the root directory
  - src                    # Example folder for your source code
    - app.py               # An example Python application file
  - README.md              # A README file for your project

Create a file named `Dockerfile` in your project's root directory. This file defines the Docker image for your development environment.

### Dockerfile Contents

```Dockerfile
# Use the official Ubuntu base image
FROM ubuntu:latest

# Set environment variables to avoid user interaction during installations
ENV DEBIAN_FRONTEND=noninteractive

# Install essential tools
RUN apt-get update && apt-get install -y \
    nano \
    wget \
    curl \
    git \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*

# Install pip packages globally
RUN pip3 install --no-cache-dir --break-system-packages \
    pandas \
    numpy

    
# Set the working directory
WORKDIR /usr/src/app

# Keep the container running
CMD ["tail", "-f", "/dev/null"]
```

This Dockerfile creates an Ubuntu Linus based container with essential tools like Git, Python, and others installed.

## Step 3: Set Up the .devcontainer Directory

Create a directory named `.devcontainer` in your project's root. See the example directory above. Inside this directory, create a file named `devcontainer.json`.

### .devcontainer/devcontainer.json Contents

```json
{
    "name": "ATRX_RPA_Design_2",
    "build": {
        "context": "..",
        "dockerfile": "Dockerfile"
    },
    "customizations": {
        "vscode": {
            "extensions": [
                "ms-python.python",
                "ms-vscode.cpptools"
            ],
            "settings": { 
                "terminal.integrated.shell.linux": "/bin/bash"
            }
        }
    },
    "forwardPorts": [
        5000
    ],
    "postCreateCommand": "echo 'Container Ready!'",
    "remoteUser": "root"
}
```

 This configuration file tells VSCode how to build and run the container defined in your Dockerfile, including extensions to install and ports to forward. Copy and paste the contents above into `devcontainer.json`.

## Step 4: Using the Development Container

- Open Docker Desktop and leave it running in the background
- Open your project with VSCode.
- Press `F1` to open the command palette.
- Type "Remote-Containers: Reopen in Container" and press Enter.

VSCode will build the Docker image (if necessary) and start a container. Your VSCode environment will then be connected to this container.

## Step 5: Managing Your Project with Git

Ensure Git is installed in your development environment, this should be done for you if you configured the project above correctly. Here are the basic Git commands to start managing your project's source code:

- **Stage Changes for Commit**
  ```bash
  git add -A
  ```

- **Commit Changes**
  ```bash
  git commit -m "Your commit message"
  ```

- **Push Changes to Remote Repository**
  ```bash
  git push
  ```

These commands allow you to track changes, commit them with a message, and push them to a remote repository like GitHub.

## Summary

This guide provided a comprehensive setup for a Docker-based development environment, accessible through VSCode. It included creating a Dockerfile, setting up a `.devcontainer` directory, and instructions on downloading necessary software and extensions. By following these steps, you can create a consistent and isolated development environment for your projects.

After this is all done go back to the main README and continue with the installation instructions
