# 🖥️ Windows 10 in Docker Container

![Docker](https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white)
![KVM](https://img.shields.io/badge/KVM-FF6600?style=for-the-badge&logo=linux&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-10-0078D6?style=for-the-badge&logo=windows&logoColor=white)

A lightweight Docker container image that runs Windows 10 inside a KVM-accelerated virtual machine and exposes remote access via noVNC (web) and RDP. Designed for local testing, demos, and sandboxed environments.

Important: This project requires a valid Windows 10 ISO and a licensed copy of Windows. This repository does not provide Windows images or ISOs.

## Features

- Run Windows 10 inside a container with KVM acceleration
- Remote access via:
  - noVNC in the browser (HTTP)
  - RDP (3389/TCP)
- Persistent storage using Docker volumes
- Minimal host changes — uses /dev/kvm and Docker only

## Requirements

- Linux host with KVM support (verify /dev/kvm exists)
- Docker engine installed
- Root or Docker privileges to access /dev/kvm and create containers
- Windows 10 ISO (ISO file on host)
- Sufficient CPU, RAM, and disk (recommend >= 4 vCPUs, 8 GB RAM, and 60 GB disk)

## Quick start

1. Clone this repository
```bash
git clone https://github.com/hironull/Dockerwindows.git
cd Dockerwindows
```

## Stopping, starting & cleanup

- Stop:
```bash
docker stop windows10
```
- Start:
```bash
docker start windows10
```
- Remove container (data persists in the `windows_data` volume):
```bash
docker rm -f windows10
```
- Remove data volume (permanently deletes VM storage):
```bash
docker volume rm windows_data
```

## Customization

- Persist additional host folders by mounting volumes.
- Modify the image or container entrypoint to change QEMU options (RAM, CPU, disk format, GPU passthrough if available).

## Limitations

- KVM acceleration requires host support — this will not run with full performance on non-linux hosts.
- GPU passthrough, nested virtualization, and other advanced features may require extra host configuration.

Made by Hironull
