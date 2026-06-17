---
mocs:
    - "[[public-notes/03-resources/tools.moc.md|Tools & Environment]]"
tags:
    - dev/tools
---

Current packages installed:

## Summary
+ Base software: base, base-devel, dhcpcd, dosfstools, efibootmgr, grub, git, linux, linux-firmware, linux-headers, man, man-db, mtools, networkmanager, openssh-askpass, xf86-video-vesa
	+ microcode amd-ucode for amd cpus
	+ nvidia (Driver for GTX 1050ti)
+ Display manger (login manager): gdm
+ Window manager: awesome
+ Window composer: picom
+ App Launcher: rofi
+ Audio: pavucontrol, alsa-utils, puseaudio-alsa
+ Shell: zsh:
```
#set zsh as default shell
sudo pacman -s zsh
sudo chsh -s /usr/bin/zsh root
chsh -s /usr/bin/zsh $USER
```
+ Terminal: kitty
+ AUR: paru
+ sxhkd: hotkeys to execute scripts or launch apps
+ Fonts: ttf-fira-code, ttf-nerd-fonts-symbols
	+ Display emojis and Japanesse/ Korean / Chinese characters: noto-fonts-cjk noto-fonts-emoji noto-fonts
+ Polkit (root acces for applications, a window asking your password to authorize apps): polkit, polkit-gnome
+ File manager: zzzfm-bin (Replacing un-mantained spaceFM)
+ Auto-mount removable storage devices: udiskie (E.g. insert a usb and type `udiskie` in the terminal to be able to access it)
+ Browser: Firefox
+ Screenshots: Flameshot
+ Wallpaper selector: nitrogen
+ Themes:  papirus-icon-theme, arc-gtk-theme, breeze-gtk, breeze, lxappearance, qt5ct
+ Study: Obsidian, anki
+ Password admin: Keepassxd
+ CLI tools: bat, lsd, htop, pfetch, tree
+ Code Editors: vim, visual-studio-code-bin
+ Watch videos: vlc
+ RAR management: peazip
+ Office suite: Libre office
+ keyboard: numlockx

### Additional
+ Custom zsh prompt: oh-my-zsh
+ Wallpapers: Wall heaven, debian art
+ Color scheme: for terminal use kitty script (search themes in kitty documentation), search for extensions for themes in vscode and obsidian
## Complete list

```
alsa-utils 1.2.12-1
amd-ucode 20240703.e94a2a3b-1
anki 24.06.3-1
arc-gtk-theme 20221218-2
awesome 4.3-4
base 3-2
base-devel 1-1
bat 0.24.0-2
breeze 6.1.3-1
breeze-gtk 6.1.3-1
dhcpcd 10.0.8-1
dosfstools 4.2-4
efibootmgr 18-3
firefox 128.0.2-1
flameshot 12.1.0-3
gdm 46.2-2
git 2.45.2-1
grub 2:2.12-2
htop 3.3.0-3
keepassxc 2.7.9-3
kitty 0.35.2-1
linux 6.10.arch1-2
linux-firmware 20240703.e94a2a3b-1
linux-headers 6.10.arch1-2
lsd 1.1.2-1
lxappearance 0.6.3-5
man-db 2.12.1-1
mtools 1:4.0.44-1
networkmanager 1.48.4-1
nitrogen 1.6.1-6
nvidia 555.58.02-8
obsidian 1.6.7-1
openssh-askpass 2.1.0-4
papirus-icon-theme 20240501-1
paru 2.0.3-1
paru-debug 2.0.3-1
pavucontrol 1:6.0-1
pfetch 1.2.0-1
picom 11.2-1
polkit-gnome 0.105-11
qt5ct 1.8-2
rofi 1.7.5-3
sxhkd 0.6.2-3
tree 2.1.3-1
ttf-fira-code 6.2-2
ttf-nerd-fonts-symbols 3.2.1-1
udiskie 2.5.3-1
vim 9.1.0611-1
visual-studio-code-bin 1.91.1-1
vlc 3.0.21-1
xf86-video-vesa 2.6.0-2
xorg-bdftopcf 1.1.1-2
xorg-docs 1.7.3-2
xorg-font-util 1.4.1-2
xorg-fonts-100dpi 1.0.4-3
xorg-fonts-75dpi 1.0.4-2
xorg-fonts-encodings 1.1.0-1
xorg-iceauth 1.0.10-1
xorg-mkfontscale 1.2.3-1
xorg-server 21.1.13-1
xorg-server-common 21.1.13-1
xorg-server-devel 21.1.13-1
xorg-server-xephyr 21.1.13-1
xorg-server-xnest 21.1.13-1
xorg-server-xvfb 21.1.13-1
xorg-sessreg 1.1.3-2
xorg-setxkbmap 1.3.4-2
xorg-smproxy 1.0.7-2
xorg-x11perf 1.6.2-2
xorg-xauth 1.1.3-1
xorg-xbacklight 1.2.3-4
xorg-xcmsdb 1.0.6-2
xorg-xcursorgen 1.0.8-2
xorg-xdpyinfo 1.3.4-2
xorg-xdriinfo 1.0.7-2
xorg-xev 1.2.6-1
xorg-xgamma 1.0.7-2
xorg-xhost 1.0.9-2
xorg-xinit 1.4.2-2
xorg-xinput 1.6.4-2
xorg-xkbcomp 1.4.7-1
xorg-xkbevd 1.1.5-2
xorg-xkbprint 1.0.6-2
xorg-xkbutils 1.0.6-1
xorg-xkill 1.0.6-2
xorg-xlsatoms 1.1.4-2
xorg-xlsclients 1.1.5-2
xorg-xmodmap 1.0.11-2
xorg-xpr 1.2.0-1
xorg-xprop 1.2.7-1
xorg-xrandr 1.5.2-2
xorg-xrdb 1.2.2-2
xorg-xrefresh 1.1.0-1
xorg-xset 1.2.5-2
xorg-xsetroot 1.1.3-2
xorg-xvinfo 1.1.5-2
xorg-xwayland 24.1.1-1
xorg-xwd 1.0.9-2
xorg-xwininfo 1.1.6-2
xorg-xwud 1.0.6-2
xterm 393-1
zsh 5.9-5
zzzfm-bin 1.0.7-2

# new added
peazip
libreoffice
noto-fonts-cjk noto-fonts-emoji noto-fonts
pulseaudio-alsa
numlockx
```