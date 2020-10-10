<p align="center">
<a href="https://dahliaos.io">Website</a> ●
<a href="https://discord.gg/7qVbJHR">Discord</a> ●
<a href="https://github.com/dahlia-os/releases/releases">Releases</a> ●
<a href="https://paypal.me/officialdahliaos">Donate</a> ●
<a href="https://github.com/dahlia-os/documentation">Documentation</a>

# Manifest
![GitHub issues](https://img.shields.io/github/issues/dahlia-os/prickle-emulator?color=brightgreen)
![GitHub](https://img.shields.io/github/license/dahlia-os/prickle-emulator?color=bright-green)

Manifests to build dahliaOS on top of Fuchsia OS

## How to use these manifests

dahliaOS: This is an all in one overlay for Fuchsia OS

pangolin-desktop: builds pangolin-desktop with Fuchsia OS

gnu-coreutils: builds gnu-coreutils with Fuchsia OS

pangolin-mobile: build pangolin-mobile with Fuchsia OS

Your .jiri_manifest file should look like this example:

```
<manifest>
  <imports>
    <import manifest="flower" name="integration" remote="https://fuchsia.googlesource.com/integration"/>
    <import manifest="pangolin-desktop" name="pangolin-desktop" remote="https://github.com/dahlia-os/manifest"/>
  </imports>
</manifest>

```
