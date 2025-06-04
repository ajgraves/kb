# openSUSE Stuff
This portion of my knowledge base is for openSUSE knowledge.

## Current usage
I'm currently using openSUSE on two of my systems. Both are Lenovo ThinkPad laptops (models are T490 and X250). Both are currently running [Kalpa desktop](https://kalpadesktop.org/), which is a KDE desktop running on top of [openSUSE's MicroOS](https://microos.opensuse.org/).

Given that I'm running an immutable variation of Linux, there will be some challenges that don't exist on other systems. This repo will mostly collect my solutions for those challenges.

## Distrobox
I use [Distrobox](https://distrobox.it/) quite heavily on my immutable setups, along with [Homebrew](https://brew.sh/) and [Flatpaks](https://flathub.org/).

## Current listing
**[appimage-runner](appimage-runner)** — `appimage-runner` is how I execute my [AppImage](https://appimage.org/) files. Kalpa does not have the fuse2 library installed, as it is old and unmaintained. However, AppImages require fuse2 to run. My solution to that is to create a distrobox that I simply named "appimage" and the programs run from within this distrbox. However, they are also integrated in to my desktop (i.e. they have ".desktop" files installed in `~/.local/share/applications`) so they can easily be launched from my desktop. However, the .desktop file needs to be modified so that it executes the AppImage from within the distrobox container. My solution was to write this simple wrapper script so that you can add it to the `Exec=` line of the .desktop file. NOTE: You do **NOT** want to add it to the `TryExec=` line, otherwise the .desktop will not show up in your app launcher.

**[auto-update-status](auto-update-status)** — Since MicroOS and, by extension, Kalpa, are capable of auto-updating using the `transactional-update.service` systemd unit, I wrote this little script for me to occasionally check the status of those auto-updates. It will output various logs and statuses to check on the latest updates.
