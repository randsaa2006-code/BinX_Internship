# Day 1 — Environment Setup & the Jupyter Workflow ⚙️

## Overview

This project focuses on setting up a reliable and reproducible Python environment for **Artificial Intelligence and Machine Learning workflows**.

The goal is to understand the importance of environment management, practice working with Jupyter Notebook, install essential Python libraries, and use Git/GitHub for version control and project tracking.

A properly configured environment is a fundamental step in AI/ML projects because it ensures that code, dependencies, and tools can be reproduced consistently across different systems.

---

## Learning Objectives 🎯

By the end of this notebook, I learned how to:

- Create and manage a Python virtual environment.
- Install and manage packages using pip.
- Understand the importance of reproducible environments in AI/ML projects.
- Work with Jupyter Notebook using code and Markdown cells.
- Document code and explanations inside notebooks.
- Verify installed library versions.
- Create a requirements.txt file for dependency tracking.
- Initialize and manage a Git repository.
- Commit and push project files to GitHub.

---

## Topics Covered 📚

### 1. Why Environment Setup Matters

Learned why setting up a reproducible environment is essential for AI and Machine Learning projects.

Key concepts:

- Different projects may require different library versions.
- Virtual environments prevent dependency conflicts.
- Reproducibility ensures that the same code can run successfully on different machines.

A well-configured environment is a standard practice in professional software development and Machine Learning workflows.

---

### 2. Python, pip, and Virtual Environments

Learned how to create an isolated Python environment for each project.

Created a virtual environment using:

```bash
python -m venv .venv
```

Activated the environment and installed required libraries:

```bash
pip install numpy pandas matplotlib jupyter
```

Used:

```bash
pip freeze > requirements.txt
```

to save all installed packages and their versions.

This allows the environment to be recreated easily in the future.

---

### 3. Jupyter Notebook Workflow

Learned how to work efficiently with Jupyter Notebook as an interactive environment for AI/ML experimentation.

Explored the difference between:

### Code Cells

Used to:

- Write and execute Python code.
- Display outputs directly below the cell.
- Test and experiment with solutions.

Example:

```python
print("Hello AI")
```

### Markdown Cells

Used to:

- Explain the purpose of the code.
- Document steps and results.
- Add structure and descriptions to notebooks.

A professional notebook combines Markdown explanations, executable code, and results to create a complete and understandable workflow.

---

### 4. Supporting Tools: VS Code, Git & GitHub

Learned how different tools support AI/ML development.

### VS Code

Used as a development environment for:

- Writing Python code.
- Managing projects.
- Working with Jupyter notebooks.

### Git & GitHub

Learned the basics of version control:

- Creating repositories.
- Tracking project changes.
- Creating commits.
- Uploading projects to GitHub.

GitHub helps maintain a professional portfolio and track progress throughout the learning journey.

---

## Hands-On Lab 🧪

### Step 1: Environment Creation

Created and activated a virtual environment.

Installed essential libraries:

- NumPy.
- Pandas.
- Matplotlib.
- Jupyter Notebook.

---

### Step 2: Jupyter Notebook Setup

Created a notebook containing:

- Markdown cells for explanations.
- Code cells for Python execution.

Practiced documenting code and organizing notebook structure.

---

### Step 3: Library Verification

Checked installed library versions to confirm that the environment was configured correctly.

Example:

```python
import numpy as np
import pandas as pd
import matplotlib

print(np.__version__)
print(pd.__version__)
print(matplotlib.__version__)
```

---

### Step 4: Dependency Management

Generated a `requirements.txt` file containing all installed packages and versions.

This ensures that the same environment can be recreated later.

---

### Step 5: Git Repository Setup

Initialized a Git repository and practiced:

- Adding files.
- Creating commits.
- Connecting the repository to GitHub.
- Pushing project files.

---

## Tools Used 🛠️

- Python 3.10+
- Virtual Environment (venv)
- pip
- Jupyter Notebook
- VS Code
- Git
- GitHub

---

## Summary 📌

During this project, I learned the importance of preparing a reliable development environment before starting any AI or Machine Learning work.

I gained practical experience in creating virtual environments, installing Python packages using pip, and managing project dependencies through `requirements.txt`. These practices help ensure that projects remain reproducible and avoid dependency conflicts.

I also learned how to work with Jupyter Notebook as an interactive development tool by combining code cells and Markdown cells to create clear and well-documented workflows.

Additionally, I practiced using supporting development tools such as VS Code and Git/GitHub. I learned how to initialize repositories, track changes, create commits, and upload projects for version control.

Through this hands-on experience, I built the foundation required for professional AI/ML development workflows and prepared a structured environment for the upcoming data science and Machine Learning projects.
