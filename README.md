# I3 Basic configuration 
## Configuration without dotfiles

[![N|Solid](https://anarchyinstaller.gitlab.io/assets/img/hero-img.png)](https://anarchyinstaller.gitlab.io/)

## ISO
https://anarchyinstaller.gitlab.io/

## Installation
### Step 1
```sh
sudo pacman -S git base-devel --needed
```
### Step 2
```sh
mkdir Sources
cd Sources
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
### Step 3
```sh
sudo pacman -S alacritty
```
```sh
sudo pacman -S xorg-server xorg-fonts-misc xorg-xinit xf86-video-qxl bspwm sxhkd dmenu nitrogen picom terminator chromium arandr rxvt-unicode ranger rofi firefox vlc i3-gaps --needed
```
### Step 4
```sh
yay -S sublime-text visual-studio-code-bin pywal google-chrome python3
```
### Step 5 Polybar
```sh
yay -S polybar
```
```sh
yay -S siji-git ttf-unifont
```
Change USER and GROUP for your user and group name.
```sh
mkdir .config/polybar
cp /usr/share/doc/polybar/config ~/.config/polybar
sudo chown USER:GROUP .config/polybar/config
```
```sh
vim .config/polybar/launch.sh
```
Copy paste into launch.sh
```sh
#!/usr/bin/env bash

# Terminate already running bar instances
killall -q polybar
# If all your bars have ipc enabled, you can also use 
# polybar-msg cmd quit

# Launch bar1 and bar2
echo "---" | tee -a /tmp/polybar1.log /tmp/polybar2.log
polybar bar1 2>&1 | tee -a /tmp/polybar1.log & disown
polybar bar2 2>&1 | tee -a /tmp/polybar2.log & disown

echo "Bars launched..."
```
```sh
chmod +x $HOME/.config/polybar/launch.sh
```
Insert into .config/i3/.config
```sh
exec_always --no-startup-id $HOME/.config/polybar/launch.sh
```

### Step 6 Polybar theme
```sh
yay -S rofi pywal calc networkmanager-dmenu mpd
```
```sh
git clone --depth=1 https://github.com/adi1090x/polybar-themes.git

cd polybar-themes
chmod +x setup.sh
./setup.sh
```

Add --shapes in i3 config 
```sh
exec_always --no-startup-id $HOME/.config/polybar/launch.sh --shapes
```
*if it gives an error delete the mpd of the config of the corresponding theme*

Execute theme
```sh
bash ~/.config/polybar/launch.sh --shapes
```

### Step 7 ohmyzsh
```sh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
``` 
Edit file .zshr and choose your theme (example "agnoster")

### Step 8 tmux
```sh
yay -S tmux
``` 
