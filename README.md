# Installation-components-mandatory-Before-Antigravity-Install-V-2
CHROMEOS Linux



PHASE 1: CHROMEOS INITIALIZATION
Open ChromeOS Settings > Advanced > Developers.
Click Turn on next to Linux development environment.
Allocate disk space (Recommend 30GB+ to accommodate tools, Docker images, and environments).
Click Install. Wait for the process to complete and the terminal to launch.
PHASE 2: CORE SYSTEM & SECURITY DEPENDENCIES
Execute this to establish the base layer, required UI libraries, and credential managers for secure agent authentication.
Bash
# Update base system
sudo apt update && sudo apt upgrade -y

# Install core development tools, UI libraries, and credential managers
sudo apt install -y curl wget git build-essential software-properties-common apt-transport-https ca-certificates \
libnss3 libxss1 libasound2 gnupg2 gnome-keyring libsecret-1-0

PHASE 3: RUNTIMES (PYTHON & NODE.JS)
Install the execution environments required by the IDE and local agent tools.
Bash
# Install Python 3 and virtual environment
sudo apt install -y python3 python3-pip python3-venv

# Install Node.js LTS
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt install -y nodejs

PHASE 4: DOCKER INSTALLATION
Deploy Docker for isolated building and testing of agent-generated code without altering your base Linux environment.
Bash
# Add Docker's official GPG key and repository
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/debian/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/debian $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker packages
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add current user to the docker group to run without sudo
sudo usermod -aG docker $USER

Note: You must close the terminal and reopen it for the Docker group permissions to take effect before attempting to use Docker commands.
PHASE 5: GOOGLE ANTIGRAVITY INSTALLATION
Install the IDE directly via Google's official APT repository for native update management.
Bash
# Add Google's repository key
sudo curl -fsSL https://us-central1-apt.pkg.dev/doc/repo-signing-key.gpg | sudo gpg --dearmor --yes -o /etc/apt/keyrings/antigravity-repo-key.gpg

# Add the Antigravity repository
echo "deb [signed-by=/etc/apt/keyrings/antigravity-repo-key.gpg] https://us-central1-apt.pkg.dev/projects/antigravity-auto-updater-dev antigravity-debian main" | sudo tee /etc/apt/sources.list.d/antigravity.list > /dev/null

# Update and install
sudo apt update
sudo apt install -y antigravity

PHASE 6: SECURE WORKSPACE & CONFIGURATION
Establish your private directory architecture and configure global Git settings.
Bash
# Create the secure Agentic Workflows structure
mkdir -p ~/AgenticWorkflows/Workspaces ~/AgenticWorkflows/MemoryBank

# Lock down permissions for private use (User-only access)
chmod 700 ~/AgenticWorkflows

# Create global environment variable file
touch ~/AgenticWorkflows/.env
chmod 600 ~/AgenticWorkflows/.env

# Navigate to the primary workspace
cd ~/AgenticWorkflows/Workspaces

# Initialize local git version control
git init
git config --global user.name "Private User"
git config --global user.email "private@localhost"
git config --global init.defaultBranch main

# Launch Google Antigravity
antigravity .

PHASE 7: CHROMEOS UI FINALIZATION
Port Forwarding: Navigate to ChromeOS Settings > Advanced > Developers > Linux development environment > Port forwarding. Add ports your tools will likely use (e.g., 3000, 5000, 8080).
System Snapshot: Navigate to Backup & restore in the Linux settings. Select Backup and create a .tarsa file of your clean, configured environment for easy rollback if needed.
