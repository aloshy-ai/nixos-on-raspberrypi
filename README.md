# NixOS on RaspberryPi 4

## Setting up Host Machine

If you don't have NixOS installed on your machine, run the following command. It 's unique for all popular OSes.

```bash
sh <(curl -L https://nixos.org/nix/install) --daemon
```

## Install Cachix client

If you don't have Cachix installed on your machine, run the following command. It helps to speed up the build process, by avoiding the need to build common dependencies from source.

```bash
nix-env -iA cachix -f https://cachix.org/api/v1/install
```
