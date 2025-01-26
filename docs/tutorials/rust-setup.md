# Setting up a dev container for Rust

* Primary author: [Reece Corter](https://github.com/reece333)
* Reviewer: [Benjamin Corter](https://github.com/bjcorter)

!!! note "Overview"
    This tutorial will help you:
    - Create a **blank directory** and initialize a new **Git repository** into it
    - Set up a **Dev Container** with the official Rust image and 'rust-analyzer'
    - Write a basic program that will print **Hello COMP423**
    - Understand the difference between 'cargo build' and 'cargo run' and their uses

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

1. In Visual Studio Code, **open** the `rust-hello` folder.
2. Press <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> & select **Dev Containers: Reopen in Container**.
3. Wait for the container to build.

When completed, run:

```bash
rustc --version
```

You should see something like `rustc 1.x.x (yyyy-mm-dd)'. (1.84.0 as of 2025-01-09)

---

## Step 4: Create a New Rust Project

From inside the Dev Container terminal:

```bash
cd /workspaces/rust-hello
cargo new --bin --vcs none hello-comp423
```

- '--bin' creates a binary (executable) project.
- '--vcs none prevents Cargo from creating another Git repo inside 'hello-comp423'.

---

## Step 5: Write "Hello COMP423" Program

Open 'hello-comp423/src/main.rs'. Replace any existing code with:

```rust
fn main(){
    println!("Hello COMP423");
}
```

---

## Step 6: Build & Run Program

### Option A: Build & Run Manually

```bash
cd hello-comp423
cargo build
./target/debug/hello-comp423
```

This should output:

```
Hello COMP423
```

!!! note "Relation to 'gcc' in COMP211"
    'cargo build' is similar to using 'gcc hello-comp423.c -o hello-comp423': it **compiles** the program but **does not** run automatically.

---

### Option B: Build & Run in One Step

```bash
cargo run
```

This command **compiles** (if needed) **and** executes the program. You will see:

```
Compiling hello-comp423 v0.1.0
Running 'target/debug/hello-comp423'
Hello COMP423
```

!!! info "Difference from 'cargo build'"
    - **'cargo build'**: only compiles your program.
    - **'cargo run'**:  compiles **and** immediately runs the compiled file in a single command.

---

## Summary
- **Step 1**: Create a new folder, git init.
- **Step 2**: Add '.devcontainer/devcontainer.json' with the Rust base image + 'rust-analyzer'.
- **Step 3**: Reopen in container, verify 'rustc --version'.
- **Step 4**: Create project with cargo new --bin --vcs none hello-comp423.
- **Step 5**: Write "Hello COMP423" in main.rs.
- **Step 6**: Compile with cargo build and run the resulting file manually (Option A), or use cargo run (Option B) to do it all in one step.

---