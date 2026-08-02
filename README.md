# GitHub Actions Practice & Learning 🚀

Welcome to the **GitHub Actions Practice** workspace! This repository is configured for hands-on learning and building CI/CD workflows using GitHub Actions within a reproducible **Devbox** environment.

---

## 📁 Repository Overview

```text
.
├── .github/
│   ├── dependabot.yml       # Automated weekly action updates
│   └── workflows/
│       ├── welcome.yml      # Beginner-friendly workflow demonstrating events & context
│       └── ci.yml           # Starter CI pipeline for testing & building
├── .vscode/
│   ├── settings.json        # Configures Devbox shell & YAML schema validation
│   └── extensions.json      # Workspace extension recommendations
├── .gitignore               # Configured for macOS, Devbox, Node, Python, and IDE state
├── devbox.json              # Devbox configuration (Docker, Node.js, act local runner)
└── README.md
```

---

## 🛠️ Environment Setup

This project uses **[Devbox](https://www.jetify.com/devbox)** to manage system dependencies deterministically without cluttering your host system.

### Packages Included
- **Docker** (`29.6.2`)
- **Node.js** (`24`)
- **act** (`latest`) — Local GitHub Actions runner

### Quick Start

1. **Start the Devbox Shell**:
   ```bash
   devbox shell
   ```

2. **IDE Integration (Antigravity IDE / VS Code)**:
   - The workspace is pre-configured ([.vscode/settings.json](file://.vscode/settings.json)) to open `devbox shell` by default in the integrated terminal.
   - Recommended extensions ([.vscode/extensions.json](file://.vscode/extensions.json)):
     - **GitHub Actions** (`github.vscode-github-actions`): Workflow syntax highlighting & status overview.
     - **YAML by Red Hat** (`redhat.vscode-yaml`): Real-time schema validation and auto-formatting for `.github/workflows/*.yml`.

---

## ⚡ Local Workflow Execution (`act`)

You can run and test your GitHub Actions locally on your Mac using **`act`** (installed via Devbox).

### Commands (inside Devbox shell):

* **List available workflows & jobs**:
  ```bash
  devbox run act:list
  # or directly: act -l
  ```

* **Dry run (simulate without executing)**:
  ```bash
  devbox run act:dry-run
  # or directly: act -n --container-architecture linux/amd64
  ```

* **Run workflows locally**:
  ```bash
  devbox run act:run
  # or directly: act --container-architecture linux/amd64
  ```

---

## 🤖 GitHub Actions Workflows

### 1. `welcome.yml` ([View Workflow](file://.github/workflows/welcome.yml))
Demonstrates core GitHub Actions concepts:
- **Triggers**: `push`, `pull_request`, and manual `workflow_dispatch`.
- **Context Variables**: Accessing `${{ github.repository }}`, `${{ github.actor }}`, `${{ runner.os }}`.
- **Actions**: Checking out repository code using `actions/checkout@v7`.

### 2. `ci.yml` ([View Workflow](file://.github/workflows/ci.yml))
A baseline Continuous Integration pipeline template for testing and building code.

---

## 📖 Key GitHub Actions Concepts

| Concept | Description |
| :--- | :--- |
| **Workflow** | Configured in `.github/workflows/*.yml`, defines automated jobs to execute. |
| **Event (`on`)** | The activity that triggers the workflow (e.g. `push`, `pull_request`, `workflow_dispatch`). |
| **Job (`jobs`)** | A set of steps executed on a runner instance (e.g. `ubuntu-latest`). |
| **Step (`steps`)** | An individual task running shell commands (`run`) or actions (`uses`). |
| **Action (`uses`)** | Reusable code block from the GitHub Marketplace (e.g. `actions/checkout@v7`). |

---

## 💡 How to Trigger Workflows on GitHub

1. **Push or Pull Request**: Push a commit or create a PR targeting `main` or `master`.
2. **Manual Execution**: Go to the **Actions** tab on GitHub -> Select **GitHub Actions Practice & Learning** -> Click **Run workflow**.
