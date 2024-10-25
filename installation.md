# Ultimate Terminal Setup Guide: Zsh + Oh My Zsh + Powerlevel10k

A comprehensive guide to transform your terminal into a powerful and beautiful development environment.

## Prerequisites

- macOS (This guide is macOS-specific)
- Zsh installed and set as default shell
- Git installed
- Terminal.app or iTerm2

## Installation Steps

### 1. Install Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 2. Install Powerlevel10k Theme

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

### 3. Install Required Fonts

Download and install Meslo Nerd Font (required for powerlevel10k):

```bash
# Download all four variants
curl -L https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf -o ~/Downloads/"MesloLGS NF Regular.ttf"
curl -L https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf -o ~/Downloads/"MesloLGS NF Bold.ttf"
curl -L https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf -o ~/Downloads/"MesloLGS NF Italic.ttf"
curl -L https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf -o ~/Downloads/"MesloLGS NF Bold Italic.ttf"
```

After downloading:
1. Open Font Book
2. Click `+` button or use File > Add Fonts
3. Navigate to Downloads folder and install all four MesloLGS NF fonts

### 4. Configure Terminal Font

#### For Terminal.app:
1. Open Terminal preferences (Cmd + ,)
2. Go to Profiles > Text
3. Click Change button next to Font
4. Select "MesloLGS NF" from the font list

#### For iTerm2:
1. Open iTerm2 preferences (Cmd + ,)
2. Go to Profiles > Text
3. Click Font and select "MesloLGS NF"

### 5. Configure .zshrc

Edit your `~/.zshrc` file:

```bash
# Set theme
ZSH_THEME="powerlevel10k/powerlevel10k"

# Configure plugins
plugins=(
    git
    zsh-autosuggestions
    zsh-syntax-highlighting
    web-search
    history
    docker
    kubectl
    macos
)
```

### 6. Install Additional Plugins

```bash
# Install autosuggestions
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Install syntax highlighting
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### 7. Apply Changes

```bash
source ~/.zshrc
```

### 8. Configure Powerlevel10k

The configuration wizard will start automatically. If it doesn't:

```bash
p10k configure
```

Follow the configuration wizard to customize your prompt according to your preferences.

## Included Plugins

- **git**: Enhanced git integration and aliases
- **zsh-autosuggestions**: Fish-like autosuggestions based on command history
- **zsh-syntax-highlighting**: Syntax highlighting for commands as you type
- **web-search**: Quick web searches from terminal
- **history**: Improved command history functionality
- **docker**: Docker commands autocomplete and aliases
- **kubectl**: Kubernetes CLI support and aliases
- **macos**: macOS-specific commands and utilities

## Useful Aliases

Oh My Zsh comes with many built-in aliases. Here are some commonly used ones:

```bash
# Git
gst = git status
ga = git add
gcmsg = git commit -m
gp = git push
gpl = git pull

# Directory
.. = cd ..
... = cd ../..
~ = cd ~

# List files
l = ls -lah
ll = ls -lh
la = ls -lAh
```

## Customization

### Custom Aliases

Add your custom aliases to `~/.zshrc`:

```bash
# Example custom aliases
alias zshconfig="nano ~/.zshrc"
alias ohmyzsh="nano ~/.oh-my-zsh"
alias reload="source ~/.zshrc"
```

### P10k Customization

To modify Powerlevel10k settings after initial setup:
1. Edit `~/.p10k.zsh`
2. Or run `p10k configure` again

## Troubleshooting

### Missing Icons
- Ensure Meslo Nerd Font is installed
- Verify terminal is using MesloLGS NF font
- Run `p10k configure` to verify font installation

### Plugin Not Working
```bash
# Verify plugin installation
ls ~/.oh-my-zsh/custom/plugins

# Check .zshrc plugin configuration
nano ~/.zshrc

# Reload configuration
source ~/.zshrc
```

## Updates

```bash
# Update Oh My Zsh
omz update

# Update Powerlevel10k
git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k pull

# Update plugins
git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-autosuggestions pull
git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting pull
```

Remember to reload your terminal or run `source ~/.zshrc` after making any changes to your configuration.