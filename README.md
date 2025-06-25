# Multi-Arch Sendria Container Image

This repository provides a **multi-architecture** Docker image for [Sendria](https://github.com/msztolcman/sendria), the popular SMTP server for catching and inspecting emails in your dev/test environment.  
Supported architectures: **amd64**, **arm64**, **armhf**.

---

## 📦 Features

- **Multi-Arch** build targeting:
  - `linux/amd64`
  - `linux/arm64`
  - `linux/arm/v7` (armhf)

---

## 🧑‍💻 Usage

```bash
docker pull ghcr.io/mmbesar/sendria-container:latest
docker run -d \
  --name sendria \
  -p 1025:1025 \
  -p 1080:1080 \
  ghcr.io/mmbesar/sendria-container:latest
```

* SMTP interface: `smtp://127.0.0.1:1025`
* Web UI: [http://127.0.0.1:1080](http://127.0.0.1:1080)

For full configuration options, see the original Sendria docs:

```bash
docker run --rm ghcr.io/mmbesar/sendria-container:latest sendria --help
```

---

## 🔧 Customization

* **Database file**
  Mount a volume if you’d like to persist emails between restarts:

  ```bash
  docker run -d \
    -v sendria-data:/data \
    -e DB_PATH=/data/mails.sqlite \
    -p 1025:1025 \
    -p 1080:1080 \
    ghcr.io/mmbesar/sendria-container:latest
  ```
* **Password-protected UI / SMTP AUTH**
  Pass `--gui-password` or `--smtp-user` / `--smtp-pass` flags—see `sendria --help`.

---


## 🙏 Credits & Thanks

* **Original project**: [msztolcman/sendria](https://github.com/msztolcman/sendria)
  *“Sendria (formerly MailTrap) is a SMTP server designed to run in your dev/test environment, catch any email … and display it in a web interface.”*
  Huge thanks to **Marcin Sztolcman** and all contributors to this project!

---

## 📄 License

This project is provided under the **MIT License**. See [LICENSE](LICENSE) for details.
