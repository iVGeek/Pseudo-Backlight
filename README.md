# Pseudo-Backlight

fake-backlight shouldn't need to exist, but it does.

fake-backlight fakes a backlight for your display because..

You can't control it any other way in linux
ACPI is hard
Your OEM sucks
Your eyes hurt

#What on earth is this?
Certain manufacturers' cutting-edge laptops may not allow you to control the backlight brightness. You may have tried a hundred random hacks, none of which worked, and Linux also does not have some obscure driver for your system.

If you have a /sys/class/backlight/acpi video0 but it doesn't work, pseudo-backlight can help you until someone figures out what insane thought process your OEM went through to decide not to support the ACPI standard. Hopefully, the developer who is attempting to solve the problem without documentation does not go MIA.

When you change the backlight using hotkeys or other methods, pseudo-backlight will use xbacklight to control the display brightness. If xbacklight isn't working and you're really struggling, xrandr (set USE XRANDR=True) can be used to apply software brightness.

pseudo-backlight requires Python 3.

#How to Install.

sudo pip3 install pydbus;

mkdir -p ~/.config/systemd/user;

cp pseudo-backlight.service ~/.config/systemd/user;

sudo cp pseudo-backlight /usr/local/bin/;

systemctl --user enable pseudo-backlight;

systemctl --user start pseudo-backlight;
