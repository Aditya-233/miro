# Miro PDF — Arch Linux Pacman Repository

Automated Arch Linux binary repository for **Miro PDF Viewer** (`miro-pdf`), directly mirroring and building upstream [aur.archlinux.org/packages/miro-pdf](https://aur.archlinux.org/packages/miro-pdf).  
Maintained with automated GitHub Actions running official Arch Linux `makepkg`.

---

## How to Enable in Pacman

Add the following to your `/etc/pacman.conf`:

```ini
[custom-miro]
SigLevel = Optional TrustAll
Server = https://github.com/Aditya-233/miro/releases/download/repo
```

Then update pacman databases and install:

```bash
sudo pacman -Syu
sudo pacman -S miro-pdf
```

---

## Automated Updates

Whenever [aur.archlinux.org/packages/miro-pdf](https://aur.archlinux.org/packages/miro-pdf) updates:
1. GitHub Actions automatically syncs the exact AUR files (`PKGBUILD`, `miro-pdf.install`, `.SRCINFO`, `.nvchecker.toml`).
2. Builds the official package using `makepkg` inside an Arch Linux container (with checksum verification).
3. Updates the Pacman repository database (`custom-miro.db.tar.gz`) with `repo-add`.
4. Publishes it to the `repo` release.

Your system receives official AUR-identical binary updates automatically whenever you run `sudo pacman -Syu`.
