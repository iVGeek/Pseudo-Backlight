# Pseudo-Backlight

Pseudo-backlight shouldn't need to exist, but it does.

Pseudo-backlight mimics a backlight for your display because..

You can't control it any other way in linux for reasons like:

# 1. ACPI is hard 😞:
# 2. Your OEM sucks 😢
# 3. Your eyes hurt :hurtrealbad:

### Wondering why/how in the multiverse? 🤔
Certain manufacturers' cutting-edge laptops may not allow you to control the backlight brightness. You may have tried a hundred random hacks, none of which worked, and Linux also does not have some obscure driver for your system.

If you have a /sys/class/backlight/acpi video0 but it doesn't work, pseudo-backlight can help you until someone figures out what insane thought process your OEM went through to decide not to support the ACPI standard. Hopefully, the developer who is attempting to solve the problem without documentation does not go MIA.

When you change the backlight using hotkeys or other methods, pseudo-backlight will use xbacklight to control the display brightness. If xbacklight isn't working and you're really struggling, ```` powershell xrandr (set USE XRANDR=True) ```` can be used to apply software brightness.

pseudo-backlight requires Python 3.

### How to Install.
```` powershell

sudo pip3 install pydbus;

mkdir -p ~/.config/systemd/user;

cp pseudo-backlight.service ~/.config/systemd/user;

sudo cp pseudo-backlight /usr/local/bin/;

systemctl --user enable pseudo-backlight;

systemctl --user start pseudo-backlight;

````
