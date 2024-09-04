# Git Commit Assistant

Git Commit Assistant is a powerful tool that automates the process of creating meaningful and detailed commit messages for your Git repositories. It combines a bash script for Git operations and a Python script that uses the Groq API to generate commit messages based on your code changes.

## Table of Contents

1. [Features](#features)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Usage](#usage)
5. [Configuration](#configuration)
6. [How It Works](#how-it-works)
7. [Customization](#customization)
8. [Troubleshooting](#troubleshooting)
9. [Contributing](#contributing)
10. [License](#license)

## Features

- Automatic generation of detailed commit messages based on code changes
- Option to pull latest changes before committing
- Verbose mode for detailed operation logs
- Interactive confirmation of generated commit messages
- Fallback to manual commit message input

## Prerequisites

- Git (version 2.0 or higher)
- Python 3.6 or higher
- Groq API key

## Installation

1. Clone this repository:
   ```
   git clone https://github.com/yourusername/git-commit-assistant.git
   cd git-commit-assistant
   ```

2. Install the required Python packages:
   ```
   pip install groq
   ```

3. Set up your Groq API key as an environment variable:
   ```
   export GROQ_API_KEY="your_api_key_here"
   ```

4. Make the bash script executable:
   ```
   chmod +x git_commit_assistant.sh
   ```

## Usage

To use the Git Commit Assistant, navigate to your Git repository and run:

```
/path/to/git_commit_assistant.sh [options]
```

### Options

- `-p` or `--pull`: Pull the latest changes before committing
- `-v` or `--verbose`: Enable verbose mode for detailed logs

### Example

```
/path/to/git_commit_assistant.sh -p -v
```

This will pull the latest changes, generate a commit message based on your changes, and provide detailed logs of the process.

## Configuration

The commit message template can be customized by modifying the `COMMIT_MESSAGE_TEMPLATE` variable in the `groq_client.py` file.

## How It Works

1. The bash script checks for uncommitted changes in your repository.
2. If changes are found, it captures the diff using `git diff --cached`.
3. The Python script is called with the diff as an argument.
4. The Python script uses the Groq API to generate a detailed commit message based on the changes.
5. The bash script presents the generated message for your approval.
6. If approved, the changes are committed and pushed to the remote repository.

## Customization

### Modifying the Commit Message Template

You can customize the commit message template by editing the `COMMIT_MESSAGE_TEMPLATE` variable in `groq_client.py`. The template uses markdown format and can include any sections or prompts you find useful for your commit messages.

### Changing the Groq Model

To use a different Groq model, modify the `model` parameter in the `client.chat.completions.create()` call in `groq_client.py`.

## Troubleshooting

- **API Key Issues**: Ensure your Groq API key is correctly set as an environment variable.
- **Permission Denied**: Make sure the bash script is executable (`chmod +x git_commit_assistant.sh`).
- **Python Import Errors**: Verify that the Groq package is installed (`pip install groq`).

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
