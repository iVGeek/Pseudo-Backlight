# Pseudo-Backlight

fake-backlight shouldn't need to exist, but it does.

fake-backlight fakes a backlight for your display because..

You can't control it any other way in linux
ACPI is hard
Your OEM sucks
Your eyes hurt

What on earth is this?
If you have a bleeding-edge laptop from certain manufacturers, you might not be able to control the backlight brightness. You might have tried a hundred random hacks, none of which helped, and Linux doesn't have some esoteric driver for your system either.

If you have a /sys/class/backlight/acpi_video0, but it does nothing, fake-backlight can help until someone figures out what insane thought process your oem went thru to arrive at their decision to not support the ACPI standard. Hopefully the developer trying to resolve the problem without any documentation doesn't off themselves in the process.

fake-backlight works with GNOME, and will use xbacklight to control the display brightness when you change the backlight using the hotkeys or other method. If xbacklight isn't working and you are really hurting, xrandr can be used (set USE_XRANDR=True) to apply software brightness.

fake-backlight requires Python 3.

Install:
sudo pip3 install pydbus;
mkdir -p ~/.config/systemd/user;
cp fake-backlight.service ~/.config/systemd/user;
sudo cp fake-backlight /usr/local/bin/;
systemctl --user enable fake-backlight;
systemctl --user start fake-backlight;
