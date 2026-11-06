# SDR++ Flatpak

This repo contains [SDR++](https://www.sdrpp.org) Flatpak packaging files. Testing has only been done with an RTL-SDR Blog V4 and Fedora Silverblue, so it's possible that not everything is working yet.

Note that you need to have **Flathub** configured as a Flatpak repo and *org.freedesktop.Sdk*, *org.freedesktop.Platform* and *flatpak-builder* installed to build the package. Check the YAML manifest for the required Flatpak SDK / runtime version.

## Building

1. `flatpak-builder --repo=repo --force-clean build org.sdrpp.SDRPlusPlus.yaml`
2. `flatpak build-bundle repo --runtime-repo=https://dl.flathub.org/repo/flathub.flatpakrepo SDRPlusPlus.flatpak org.sdrpp.SDRPlusPlus`

## Running

1. `flatpak install --user SDRPlusPlus.flatpak`
2. `flatpak run org.sdrpp.SDRPlusPlus`

## Notes

- Building in a Toolbx container likely needs `--disable-rofiles-fuse`
- Using `--ccache` is highly recommended for faster rebuilds
- Configuration files reside in `~/.var/app/org.sdrpp.SDRPlusPlus/.config/sdrpp`
- Disable or unload `dvb_usb_rtl28xxu` module when using Realtek RTL28xxU based devices
