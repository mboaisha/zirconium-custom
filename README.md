## Zirconium-Custom

- This is a custom image of [Zirconium](https://github.com/zirconium-dev/zirconium) with some personal touches
- Laptop is a Lenovo Thinkpad X1 Carbon, Gen6

### Plans
- More font choices
- Replace `foot` with something else such as `kitty` or `ghostty`
    - also figure out how to wire it all to `matugen`
- Add stuff you'd find in a `*-dx` image
    - VSCode, will probably use VSCodium instead.
    - Podman and Poadman Desktop
    - Distroshelf
    - virt-manager along with qemu and kvm
    - Maybe incus
    - devcontainer integration with `neovim` and `vscodium`
    - Ansible?
- Layer Steam client directly as opposed to using it as a flatpak
- Put in [Oh My Bash](https://github.com/ohmybash/oh-my-bash)
    - I would love to try alternate shells such as `zsh` and `fish`, but I want to stay with `bash` for now.
- Better Arabic / Right-To-Left Language support
- Preloaded wallpapers
- Change `motd`
- Configure the fetch
- Figure out how to get the fingerprint scanner / auth working


## Installation
To rebase an existing atomic Fedora installation to the latest build:

- First rebase to the unsigned image, to get the proper signing keys and policies installed:
  ```
  rpm-ostree rebase ostree-unverified-registry:ghcr.io/mboaisha/zirconium-custom:latest
  ```
- Reboot to complete the rebase:
  ```
  systemctl reboot
  ```
- Then rebase to the signed image, like so:
  ```
  rpm-ostree rebase ostree-image-signed:docker://ghcr.io/mboaisha/zirconium-custom:latest
  ```
- Reboot again to complete the installation
  ```
  systemctl reboot
  ```

## Verification

These images are signed with [Sigstore](https://www.sigstore.dev/)'s [cosign](https://github.com/sigstore/cosign). You can verify the signature by downloading the `cosign.pub` file from this repo and running the following command:

```bash
cosign verify --key cosign.pub ghcr.io/blue-build/template
```
