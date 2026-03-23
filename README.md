# Turing RK1 Bootloader

## Overview
The Turing RK1 Bootloader project is designed to simplify the boot process of the Turing Operating System. It initializes hardware components and prepares the environment for the main operating system to load.

## How to Use Locally
To use the Turing RK1 Bootloader locally, follow the steps below:
1. **Clone the Repository**: Clone this repository to your local machine using the command:
   ```bash
   git clone https://github.com/danste22/turing-rk1-bootloader.git
   ```
2. **Install Dependencies:** Navigate to the project directory and install the required dependencies:
   ```bash
   cd turing-rk1-bootloader
npm install
   ```
3. **Run the Bootloader:** Execute the bootloader with the command:
   ```bash
   npm start
   ```

## Using the Devcontainer
The Turing RK1 Bootloader comes with a pre-configured development container for easier setup. To use it:

1. **Install Docker:** Ensure that Docker is installed on your machine.
2. **Open in VSCode:** Open the project in Visual Studio Code and install the Dev Containers extension.
3. **Reopen in Container:** Use the command palette (F1) and select Remote-Containers: Reopen in Container.
4. **Develop:** You can now develop within the containerized environment that has all necessary dependencies.

## Automated Workflow
The automated workflow ensures that the code is tested and integrated smoothly. Below is a diagram created with Mermaid to illustrate the workflow:
  ```mermaid
  flowchart LR
    A[Start] --> B[Code Changes Made]
    B --> C{Run Tests?}
    C -->|Yes| D[Execute Test Suite]
    C -->|No| E[Skip Tests]
    D --> F{Tests Pass?}
    F -->|Yes| G[Deploy to Production]
    F -->|No| H[Notify Developers]
    E --> G
    G --> I[End]
    H --> I
```

## Manual Testing of the Workflow
To manually test the workflow, follow these steps:

1. **Trigger the workflow:** Make a change to the codebase and push to the main branch.
2. **Observe CI Results:** Check the Continuous Integration (CI) results on GitHub Actions under the "Actions" tab of the repository.
3. **Verify Deployment:** Confirm that the application has deployed correctly and all tests have passed.
By following this documentation, you can effectively utilize the Turing RK1 Bootloader and contribute to its development!
