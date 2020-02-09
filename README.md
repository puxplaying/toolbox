# ToolBox
Collection of terminal applications for Manjaro (Bash TUI).

How to run:
- ```chmod a+rx toolbox```
- ```./toolbox```

This tool updates itself and included applications to the latest online release if a new version was found - with the [00] option.

All files are stored in ``` $HOME/.cache/toolbox ```

It downloads the included applications at first start or when the ``` $HOME/.cache/toolbox ```directory does not exist.

---

Included applications: [manjaro-update](https://github.com/puxplaying/manjaro-update/blob/master/README.md) - [releasecompare](https://github.com/puxplaying/releasecompare/blob/master/README.md) - [PacUI](https://github.com/excalibur1234/pacui/blob/master/README.md) - [Ranger (File Mananger)](https://github.com/ranger/ranger/blob/master/README.md) - [Browsh (Web Browser)](https://github.com/browsh-org/browsh/blob/master/README.md)

---

Requires: ```inxi``` - ```meld``` - ```pamac-cli``` (optional)

---

List of applications it makes use of:

- [1] [manjaro-update](https://github.com/puxplaying/manjaro-update/blob/master/README.md)
- [2] [releasecompare](https://github.com/puxplaying/releasecompare/blob/master/README.md)
- [3] [System Information](https://github.com/smxi/inxi/blob/master/README.txt) - ```inxi -Fxxxza --no-host``` | ```df -h``` | ```lsblk```
- [4] Show Journal Errors - ```journalctl -p 3 -xb```
- [5] Dmesg - ```sudo dmesg | less```
- [6] CPU Frequency Info - ```cpupower frequency-info```
- [7] [PacUI](https://github.com/excalibur1234/pacui/blob/master/README.md)
- [8] [Translate Shell](https://github.com/soimort/translate-shell/blob/develop/README.md) - ```gawk -f <(curl -Ls git.io/translate) -- -shell```
- [9] [Ranger (File Mananger)](https://github.com/ranger/ranger/blob/master/README.md)
- [10] [Browsh (Web Browser)](https://github.com/browsh-org/browsh/blob/master/README.md)

---

![alt text](https://github.com/puxplaying/ToolBox/blob/master/1.png)
