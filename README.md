# Auto RL-Swarm

Automated setup for RL-Swarm with GPU detection and optimized configurations.

## 🚀 Quick Start

```bash
# Clone the repository
cd $HOME && [ -d rl-swarm ] && rm -rf rl-swarm
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm

# Create virtual environment and run
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

## 🌐 Rent GPU (Quick Pod)

If you don't have a local GPU:

1. Visit [Quick Pod Website](https://quickpod.ai)
2. Sign up using email address
3. Go to your email and verify your Quick Pod account
4. Click on Add button in the corner to deposit fund
5. You can deposit using crypto currency (from your EVM wallet) or using Credit Card
6. Go to template section and select **CUDA 12.6**
7. Clone the CUDA 12.6 template
8. Edit the Docker Options as shown below:
   ```
   -p 8888:8888 -p 3000:3000
   ```
9. Click on Select GPU and search **RTX 4090** and choose it
10. Change your template via My Template Section
11. Choose a GPU and click on Create POD button
12. Your GPU server will be deployed soon
13. Click on Connect option and then choose Connect to web terminal

## 🛜 Cloudflare Tunnel (Optional)

For remote access:

```bash
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
cloudflared tunnel --url http://localhost:3000
```

## 📥 Installation

### Install Dependencies

```bash
# Install sudo
apt update && apt install -y sudo

# Install other dependencies
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install -y yarn

# Install Node.js and npm if not installed already
curl -sSL https://raw.githubusercontent.com/zunxbt/installation/main/node.sh | bash
```

### Clone and Run

```bash
# Clone this repository
cd $HOME && [ -d rl-swarm ] && rm -rf rl-swarm
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm

# Create a screen session
screen -S gensyn

# Run the swarm
python3 -m venv .venv && source .venv/bin/activate && ./run_rl_swarm.sh
```

## 🎯 Features

- **Automatic GPU Detection**: Detects your NVIDIA GPU and suggests optimal configurations
- **Smart Configuration Selection**: Uses specialized configs from `special configs/` directory
- **VRAM-Optimized**: Prevents VRAM errors with GPU-specific configurations
- **Flexible Setup**: Choose between automatic (recommended) or manual setup modes

## 📋 Prerequisites

- NVIDIA GPU with CUDA support
- Ubuntu/Debian-based system (or WSL)
- Internet connection

## 🛠️ Installation

### Option 1: Quick Setup (Recommended)

```bash
# Clone the repository
cd $HOME && [ -d rl-swarm ] && rm -rf rl-swarm
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm

# Create virtual environment and run
python3 -m venv .venv
source .venv/bin/activate
./run_rl_swarm.sh
```

### Option 2: Cloud GPU Setup

If you don't have a local GPU, you can rent one from Quick Pod:

#### 1. Rent GPU from Quick Pod
1. Visit [Quick Pod Website](https://quickpod.ai)
2. Sign up using your email address
3. Verify your account via email
4. Add funds using cryptocurrency or credit card

#### 2. Configure GPU Server
1. Go to **Template Section** and select **CUDA 12.6**
2. Clone the CUDA 12.6 template
3. Edit Docker Options: `-p 8888:8888 -p 3000:3000`
4. Select GPU: Search for **RTX 4090** and choose it
5. Save template via **My Template Section**
6. Click **Create POD** to deploy your GPU server

#### 3. Connect and Install
1. Click **Connect** → **Connect to web terminal**
2. Install dependencies:
```bash
# Install sudo and update system
apt update && apt install -y sudo

# Install Python, Node.js, and other dependencies
sudo apt update && sudo apt install -y python3 python3-venv python3-pip curl wget screen git lsof
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
sudo apt update && sudo apt install -y yarn

# Install Node.js
curl -sSL https://raw.githubusercontent.com/zunxbt/installation/main/node.sh | bash

# Clone and run RL-Swarm
cd $HOME && [ -d rl-swarm ] && rm -rf rl-swarm
git clone https://github.com/gensyn-ai/rl-swarm.git
cd rl-swarm

# Create screen session and run
screen -S gensyn
python3 -m venv .venv && source .venv/bin/activate && ./run_rl_swarm.sh
```

### Option 3: Cloudflare Tunnel (Optional)

For remote access, you can set up a Cloudflare tunnel:

```bash
# Install Cloudflare tunnel
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb

# Create tunnel
cloudflared tunnel --url http://localhost:3000
```

## 🎯 Usage

1. **Run the script**: `./run_rl_swarm.sh`
2. **Choose setup mode**:
   - **Automatic (Recommended)**: Let the script detect your GPU and suggest optimal settings
   - **Manual**: Configure settings manually
3. **Follow the prompts** to select:
   - Testnet connection
   - Swarm type (Math or Math Hard)
   - Model parameters (0.5B, 1.5B, 7B, 32B, or 72B)

## 🔧 How It Works

The automatic setup:
1. Detects your NVIDIA GPU using `nvidia-smi`
2. Searches for GPU-specific configurations in `hivemind_exp/configs/gpu/special configs/`
3. Suggests optimal swarm type based on GPU capabilities
4. Lists available model sizes for your GPU
5. Uses the selected configuration to prevent VRAM errors

## 📁 Project Structure

```
rl-swarm/
├── hivemind_exp/
│   └── configs/
│       └── gpu/
│           └── special configs/     # GPU-specific configurations
├── run_rl_swarm.sh                  # Main setup script
└── README.md                        # This file
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is licensed under the same license as the original [RL-Swarm](https://github.com/gensyn-ai/rl-swarm) project.

## 🙏 Acknowledgments

- Original RL-Swarm project by [Gensyn](https://github.com/gensyn-ai)
- GPU configurations optimized for various NVIDIA cards
