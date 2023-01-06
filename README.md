# NetBird UI Flatpak Proof-of-Concept
An attempt at repackaging the NetBird-UI into a flatpak.

I decided to try to repackage the [NetBird-UI](https://github.com/netbirdio/netbird) into a flatpak as a reason to learn how flatpaks work and to possibly provide NetBird with a proof of concept. The flatpak version is fully functional however I do get some errors & warnings in the console that I will describe below alongside build instructions.

I am unlikely to upload this to flathub myself unless people really want this for some reason. **IF YOU WANT TO UPLOAD TO FLATHUB PLEASE CHANGE THE APP-ID.**

## Pics
Status Tray Menu             |  Settings Window        |   Menu Item
:-------------------------:|:-------------------------:|:-----------------------:
![image](https://user-images.githubusercontent.com/26135914/211106570-da155fb1-a2c8-4972-877f-c94c2d96a55d.png) |  ![image](https://user-images.githubusercontent.com/26135914/211106797-5308d189-db4f-44e1-aea1-0cdbfc36eb41.png)   | ![image](https://user-images.githubusercontent.com/26135914/211107665-f8097e75-19fc-4f55-a885-875e2b112a91.png)


## Build Instructions
https://docs.flatpak.org/en/latest/first-build.html

Install:
`org.gnome.Platform//43`

`org.gnome.Sdk//43`

Clone this repo:
`git clone git@github.com:dannymate/netbird-ui-flatpak.git`

To build:
`flatpak run org.flatpak.Builder build --force-clean --disable-rofiles-fuse io.netbird.netbird_ui.yml`
Note: Replace `flatpak run org.flatpak.Builder` with `flatpak-builder` if not using the flatpak version.

Install Build:
`flatpak run org.flatpak.Builder --user --install --force-clean build io.netbird.netbird_ui.yml`

To Run:
`flatpak run io.netbird.netbird_ui`

To export build:
`flatpak build-export export build`

To bundle the build as a .flatpak:
`flatpak build-bundle export netbird-ui.flatpak  io.netbird.netbird_ui`

To Install Flatpak:
`flatpak install <path_to_netbird0ui.flatpak>`

You should get .desktop icon show up in your app menu.

## Console Errors
On start: 

`Gtk-Message: Failed to load module "canberra-gtk-module"`: I have tried installing the libcanberra in shared-modules but no dice.

`Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates: assertion 'window->update_and_descendants_freeze_count > 0' failed`: No idea what this is referencing.

When Disconnecting:

`ERRO[0040] get service status: rpc error: code = Unknown desc = reset connection`: Again not sure how to fix this.
