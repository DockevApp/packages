<h1 align="center">Dockev for Linux</h1>

<p align="center">
  Official package repositories for <a href="https://github.com/DockevApp/Dockev"><b>Dockev</b></a>, the desktop app for Docker.
</p>

<p align="center">
  <img alt="Latest version" src="https://img.shields.io/github/v/release/DockevApp/Dockev?label=version&color=2563eb">
  <img alt="Architecture" src="https://img.shields.io/badge/arch-x86__64-475569">
  <img alt="apt" src="https://img.shields.io/badge/apt-signed-16a34a">
  <img alt="dnf" src="https://img.shields.io/badge/dnf-signed-16a34a">
  <img alt="pacman" src="https://img.shields.io/badge/pacman-signed-16a34a">
</p>

<p align="center">
  <a href="#debian--ubuntu-apt">Debian / Ubuntu</a> ·
  <a href="#fedora--rhel-dnf">Fedora / RHEL</a> ·
  <a href="#opensuse-zypper">openSUSE</a> ·
  <a href="#arch-linux-pacman">Arch</a> ·
  <a href="#verify-the-signing-key">Verify key</a> ·
  <a href="#other-platforms">Other platforms</a>
</p>

---

## Debian / Ubuntu (apt)

Ubuntu 22.04+, Debian 12+, Linux Mint 21+, Pop!_OS, elementary OS, Zorin OS.

**1. Add the signing key**

```sh
sudo install -d -m 0755 /etc/apt/keyrings
curl -fsSL https://dockevapp.github.io/packages/dockev.gpg \
  | sudo tee /etc/apt/keyrings/dockev.gpg >/dev/null
```

**2. Add the repository**

```sh
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/dockev.gpg] https://dockevapp.github.io/packages/apt stable main" \
  | sudo tee /etc/apt/sources.list.d/dockev.list
```

**3. Install**

```sh
sudo apt update
sudo apt install dockev
```

<details>
<summary><b>Update / uninstall</b></summary>

```sh
# update
sudo apt update && sudo apt upgrade

# uninstall
sudo apt remove dockev
sudo rm /etc/apt/sources.list.d/dockev.list /etc/apt/keyrings/dockev.gpg
```

</details>

---

## Fedora / RHEL (dnf)

Fedora 39+, RHEL / Rocky / AlmaLinux 9+.

**1. Add the repository**

```sh
sudo curl -fsSL -o /etc/yum.repos.d/dockev.repo https://dockevapp.github.io/packages/rpm/dockev.repo
```

**2. Install** (accept the Dockev signing key when dnf asks)

```sh
sudo dnf install dockev
```

<details>
<summary><b>Update / uninstall</b></summary>

```sh
# update
sudo dnf upgrade dockev

# uninstall
sudo dnf remove dockev
sudo rm /etc/yum.repos.d/dockev.repo
```

</details>

---

## openSUSE (zypper)

Tumbleweed, Leap 15.6+.

```sh
sudo zypper addrepo https://dockevapp.github.io/packages/rpm/dockev.repo
sudo zypper refresh   # accept the Dockev signing key when asked
sudo zypper install dockev
```

<details>
<summary><b>Update / uninstall</b></summary>

```sh
# update
sudo zypper update dockev

# uninstall
sudo zypper remove dockev
sudo zypper removerepo dockev
```

</details>

---

## Arch Linux (pacman)

Arch Linux, EndeavourOS, CachyOS, Manjaro (x86_64).

**1. Trust the signing key**

```sh
curl -fsSL https://dockevapp.github.io/packages/dockev.asc | sudo pacman-key --add -
sudo pacman-key --lsign-key 763C239656A34CCA308F79C521D7187E5D6F387F
```

**2. Add the repository**

```sh
sudo tee -a /etc/pacman.conf >/dev/null <<'EOF'

[dockev]
SigLevel = Required
Server = https://dockevapp.github.io/packages/arch/$arch
EOF
```

**3. Install**

```sh
sudo pacman -Syu dockev
```

<details>
<summary><b>Update / uninstall</b></summary>

```sh
# update
sudo pacman -Syu

# uninstall
sudo pacman -Rns dockev
# then delete the [dockev] section from /etc/pacman.conf
```

</details>

---

## Verify the signing key

apt, rpm and pacman packages are signed with the same key. Check that its fingerprint matches:

```sh
curl -fsSL https://dockevapp.github.io/packages/dockev.asc | gpg --show-keys
```

```
763C 2396 56A3 4CCA 308F 79C5 21D7 187E 5D6F 387F
```

## Other platforms

| Platform | Install |
|---|---|
| **macOS** | [Homebrew tap](https://github.com/DockevApp/homebrew-dockev) |
| **Windows** | [Scoop bucket](https://github.com/DockevApp/scoop-bucket) |
| **Direct download** (AppImage, .deb, .rpm) | [GitHub Releases](https://github.com/DockevApp/Dockev/releases/latest) |
