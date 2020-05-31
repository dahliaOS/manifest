# Manifest
Manifests to build DahliaOS ontop of fuchsia

## How to use these manifests

dahlia: this is an all in one overlay for fuchsia. This builds Dahlia ontop of fuchsia.

pangolin-desktop: builds pangolin-desktop with fuchsia

gnu-coreutils: builds gnu-coreutils with fuchsia

pangolin-mobile: build pangolin-mobile with fuchsia

Your .jiri_manifest file should look like this (example).

```
<manifest>
  <imports>
    <import manifest="flower" name="integration" remote="https://fuchsia.googlesource.com/integration"/>
    <import manifest="pangolin-desktop" name="pangolin-desktop" remote="https://github.com/dahlia-os/manifest"/>
  </imports>
</manifest>

```
