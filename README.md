# Borg – Unraid Plugin  
**Allows you to install BorgBackup directly on Unraid for local backups**  
Author: x‑radeon | Version: 1.4.4

---

## 📦 What is Borg?

BorgBackup (Borg) is an open‑source deduplication backup program. Link [here](https://github.com/borgbackup/borg).  
This plugin installs the Borg binary in `/usr/local/bin/borg` so you can run it
directly from the Unraid command line, from cron jobs, or from any script without
the overhead of a Docker container or VM.

---

## ⚙️ Prerequisites

| Item | Requirement |
|------|-------------|
| Unraid OS | 7.2.0+ (probably works on older realses, but untested) |
| Network | Internet access to download the binary from GitHub |

---

## 🔧 Installation

1. **Copy Link to Plugin File**  
   ```bash
   https://raw.githubusercontent.com/x-radeon/unraid-borg/main/Borg.plg
   ```

2. **Add the plugin**  
   - In the Unraid web UI, go to *Plugins → Install Plugin…*  
   - Paste the URL you just copied.

3. **Verify**  
   - Verify the installation:  
     ```bash
     borg --version
     # should display Borg version 1.4.4
     ```

---

## 📜 Example Usage (See [Borg documentation](https://borgbackup.readthedocs.io/en/stable/index.html) for complete usage)

```bash
# Create a new repository
borg init --encryption=none /mnt/user/backups/borg_repo

# Create a backup
borg create /mnt/user/backups/borg_repo::mybackup-{now:%Y-%m-%d} /mnt/user/data

# List archives
borg list /mnt/user/backups/borg_repo

# Restore
borg extract /mnt/user/backups/borg_repo::mybackup-2024-03-31 /mnt/user/restored
```
---

## 🔧 Configuration

The plugin does not expose a settings page; it simply installs the binary.  
All usage is done via the Borg command line.  

If you need to change the binary location or use a specific version, fork and edit the
`Borg.plg` file directly.

---

## 📅 Changelog

- **2026‑03‑31** – Init Push; Borg Version 1.4.4 (https://github.com/borgbackup/borg/releases/tag/1.4.4)

---

## 🤝 Support & Feedback

- Create issues or feature requests in the GitHub repo:  
  https://github.com/x-radeon/unraid-borg/issues
- Discussion forum: *unraid‑borg* (link to be added later)

---

## 📄 License

This plugin is released under the Apache 2.0 License.  
See the `LICENSE` file in the repository.

---

Happy backing up!
