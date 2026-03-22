# Installation-components-mandatory-Before-Antigravity-Install-
CHROMEOS Linux


Before installing Google Antigravity, your ChromeOS Linux environment (Crostini) must be updated and equipped with baseline dependencies. This ensures the agentic models and editor have the necessary foundation to execute system commands and compile tools.

Open your ChromeOS Linux Terminal and execute these commands in order:

1. Update System Packages

Bash
sudo apt-get update && sudo apt-get upgrade -y
2. Install Core Dependencies

Bash
sudo apt-get install -y curl git wget build-essential software-properties-common
3. Install Python Environment (Crucial for Agentic Scripts)

Bash
sudo apt-get install -y python3 python3-pip python3-venv
EDITOR CONFIGURATION (BASED ON SCREENSHOT)
When you reach the "Configure Your Editor" screen for Google Antigravity, apply these exact settings to optimize for a user-first, agent-driven workflow:

1. Keybindings

Selection: Normal

Reasoning: Do not select Vim. Vim requires complex keyboard commands and memorization meant for traditional hand-coding. Normal ensures standard keyboard shortcuts (Ctrl+C, Ctrl+V) work as expected.

2. Extensions

Selection: Keep all boxes checked (Python, Go, Java, C/C++, C#, PHP, Ruby).

Reasoning: Even though you are not manually coding in these languages, your agent might need to execute, read, or compile tools written in them. Keeping these language extensions enabled gives the underlying model the maximum native capability to handle diverse file types and scripts without halting to ask for missing dependencies.



