# pyv: Simplified Python Virtual Environment Manager

## Overview

`pyv` is a lightweight, user-friendly shell function designed to streamline Python virtual environment management. With a single command, you can create or activate a virtual environment in your current working directory, making Python project setup incredibly simple.

## Features

- 🚀 Instant virtual environment creation
- 🔄 Quick activation of existing environments
- 📂 Works directly in the current working directory
- 🎨 Colorful, informative terminal output
- 🔒 Prevents conflicts with other Python environment managers

## Prerequisites

- Python 3 installed on your system
- Bash or Zsh shell

## Installation

1. Open your shell configuration file:
   ```bash
   # For Bash
   nano ~/.bashrc
   
   # For Zsh
   nano ~/.zshrc
   ```

2. Add the following function to the end of the file:
   ```bash
   pyv() {
       local VENV_NAME="venv"
       local VENV_PATH="${PWD}/${VENV_NAME}"

       unset VIRTUAL_ENV

       if [ -d "${VENV_PATH}" ] && [ -f "${VENV_PATH}/bin/activate" ]; then
           printf "\033[32mActivating virtual environment: %s\033[0m\n" "${VENV_NAME}" >&2
           source "${VENV_PATH}/bin/activate"
       else
           printf "\033[32mCreating virtual environment: %s\033[0m\n" "${VENV_NAME}" >&2
           python3 -m venv "${VENV_NAME}"
           source "${VENV_PATH}/bin/activate"
       fi
   }
   ```

3. Save the file and apply changes:
   ```bash
   # For Bash
   source ~/.bashrc
   
   # For Zsh
   source ~/.zshrc
   ```

## Usage

Navigate to your project directory and simply run:

```bash
pyv
```

### Scenarios

1. **First-time use in a project:**
   ```bash
   cd my_python_project
   pyv  # Creates a new 'venv' virtual environment and activates it
   ```

2. **Subsequent uses in the same project:**
   ```bash
   cd my_python_project
   pyv  # Activates the existing 'venv' virtual environment
   ```

## How It Works

- Checks for an existing `venv` directory in the current working directory
- Creates a new virtual environment if none exists
- Activates the virtual environment
- Provides a clear, colorful terminal message
- Prevents conflicts with other environment managers

## Deactivation

To exit the virtual environment, use the standard Python virtual environment command:

```bash
deactivate
```

## Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](../../issues).

## License

MIT License
---

**Tip:** Always remember to activate your virtual environment before working on a Python project to maintain clean, isolated dependencies!
