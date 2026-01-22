# VirtualBox Shared Folder Setup

## Why I needed this
While working on my Splunk/SOC lab, I needed an easy way to move files
(log samples, zip files, screenshots) between my host machine and the
Linux virtual machine. For this, I used VirtualBox shared folders.

This document explains how I set it up and the issues I faced.

---

## Lab Details
- Virtual Machine: VirtualBox
- Guest OS: Ubuntu Linux
- User: `splunk`
- Use case: Sharing log files and datasets for Splunk analysis

---

## Host Machine Configuration
In VirtualBox settings:

- Shared Folder Name: `some_zips`
- Auto-mount: Disabled
- Make Permanent: Enabled

> Note: The shared folder name must match exactly in the Linux mount command.

---

## Steps I Followed (Inside the VM)

### 1. Add user to VirtualBox shared folder group
```bash
sudo adduser splunk vboxsf
