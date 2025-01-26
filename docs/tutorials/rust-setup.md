# Setting up a dev container for Rust

* Primary author: [Reece Corter](https://github.com/reece333)
* Reviewer: [Benjamin Corter](https://github.com/bjcorter)

!!! note "Overview"

    This tutorial will help you:
    - Create a **blank directory** and initialize a new **Git repository** into it
    - Set up a **Dev Container** with the official Rust image and 'rust-analyzer'
    - Write a basic program that will print **Hello COMP423**
    - Understand the difference between 'cargo build' and 'cargo run'

## Prerequisites 

- [Visual Studio Code](https://code.visualstudio.com/download)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- Basic Git knowledge

!!! warning "No Rust install on Host"

    **DO NOT** install Rust locally. We will install & run everything in a dev container.

---

## Step 1: Create a Blank Directory & Initialize Git Repo

```bash
mkdir rust-hello
cd rust-hello
git init
```

## Step 2: Dev Container Configuration

1. Create a folder named `.devcontainer` and navigate into it:

```bash
mkdir .devcontainer
cd .devcontainer
```

2. Create a file named `devcontainer.json` with the following contents:

```json
{
    "name": "Rust DevContainer",
    "image": "mcr.microsoft.com/devcontainers/rust:1",
    "customizations": {
      "vscode": {
        "settings": {},
        "extensions": ["rust-lang.rust-analyzer"]
      }
    }
  }
```

---

## Step 3: Reopen in Dev Container