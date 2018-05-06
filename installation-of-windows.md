# Installation of windows

- [Installation of windows](#installation-of-windows)
  - [Disk partitions](#disk-partitions)
  - [Fix boot files installed on other disk rather than on OS disk in Windows 10](#fix-boot-files-installed-on-other-disk-rather-than-on-os-disk-in-windows-10)
  - [Installing windows 7](#installing-windows-7)

---

## Disk partitions

- MBR (Master Boot Record):

  ```windows
  # Press "Shift + F10" in installing windows.
  $ diskpart
  $ list disk
  $ select disk <disk number>
  $ clean
  $ exit
  ```

- GPT (GUID Partition Table):

  ```windows
  # Press "Shift + F10" in installing windows.
  $ diskpart
  $ list disk
  $ select disk <disk number>
  $ clean
  $ convert gpt
  $ exit
  ```

[Top](#installation-of-windows)

---

## Fix boot files installed on other disk rather than on OS disk in Windows 10

- Descriptions:

  Before:

  |  Disks |              Partition 1             |              Partition 2             |
  |:------:|:------------------------------------:|:------------------------------------:|
  | Disk 1 | Volume C. Windows 10. 65% partition. | Uncontrolled space. 35% partition.   |
  | Disk 2 | Volume Null. Boot. 500MB partition.  | Uncontrolled space. 99.9% partition. |

  After:

  |  Disks |              Partition 1             |             Partition 2             |             Partition 3            |
  |:------:|:------------------------------------:|:-----------------------------------:|:----------------------------------:|
  | Disk 1 | Volume C. Windows 10. 65% partition. | Volume Null. Boot. 500MB partition. | Uncontrolled space. 35% partition. |
  | Disk 2 | Uncontrolled space. 100% partition.  |                                     |                                    |

- Steps:

  1. Use [EaseUS Todo Backup](https://www.easeus.com/backup-software/) to backup all disks/partitions.

  2. Create a partition for disk 1 using Diskpart.

      ```shell
      create partition primary align=1024 size=500
      format fs=ntfs unit=4096 quick
      ```

  3. Restore boot partition to the new partition using EaseUS Todo Backup.

  4. Delete the old boot partition using Diskpart.

      ```shell
      Select Disk 2
      Select Partition [number of the old boot partition]
      DELETE partition
      ```

  5. Under Windows 10 installation mode, use Command Prompt (cmd) to fix boot file.

      ```shell
      # 把 Windows 相容的 MBR 寫入系統磁碟分割
      $ bootrec /fixmbr

      # 新的開機磁區 Windows 相容的開機磁區寫入系統磁碟分割
      $ bootrec /fixboot

      # 重建 BCD (Boot Configuration Database) 開機設定資料存放區
      $ bootrec /rebuildbcd
      ```

- Reference:

  1. [【Win 10 練功坊】天啊！解決 UEFI 無法開機的慘況](https://www.techbang.com/posts/49377-win-10-practice-workshops-day-solving-misery-uefi-will-not-power-on)

  2. [diskpart 硬碟分割指令](http://blog.ilc.edu.tw/blog/index.php?op=printView&articleId=505798&blogId=25793)

  3. [Windows 10 MBR 修復](https://home.gamer.com.tw/creationDetail.php?sn=3339579)

[Top](#installation-of-windows)

---

## Installing windows 7

- Steps:

  1. Download [ABR (Activation Backup and Restore)](https://directedge.us/content/abr-activation-backup-and-restore).

  2. Run **activation_backup.exe** to collect certificate (*backup-cert.xrm-ms*) and product key (*backup-key.txt*).

  3. Download LAN driver installer ([Realtek PCIe GBE Family Controller LAN Driver](https://realtek-download.com/realtek-pcie-gbe-family-controller/)).

  4. Download [Microsoft Windows and Office ISO Download Tool](https://heidoc.net/joomla/technology-science/microsoft/67-microsoft-windows-and-office-iso-download-tool) for downloading Windows 7 COEM following your windows version and languege.

  5. Burn Windows 7 COEM to DVD or USB.

  6. Download [Driver Booster](https://www.iobit.com/en/driver-booster.php) for installing other drivers.

  7. Install Windows 7 COEM and **DON'T enter product key** (in other words, skip windows activation page).

  8. After install windows 7, run **activation_restore.exe** to restore certificate and product key by *backup-cert.xrm-ms* and *backup-key.txt*.

  9. Run LAN driver installer.

  10. Install and run Driver Booster.

- Other softwares:

  - [7-Zip](http://www.7-zip.org/) (Community edition)

  - [Best Antivirus 2017](http://www.toptenreviews.com/software/security/best-antivirus-software/)

  - [CCleaner](https://www.piriform.com/ccleaner)

  - [Driver Booster](https://www.iobit.com/en/driver-booster.php)

  - [Eusing Cleaner](http://www.eusing.com/free_system_cleaner/system_cleaner.htm)

  - [Eusing Free Registry Cleaner](http://www.eusing.com/free_registry_cleaner/registry_cleaner.htm)

  - [Google Chrome](https://www.google.com/chrome/)

  - [Microsoft Office](https://products.office.com/) (Business edition)

  - [Mozilla Firefox](https://www.mozilla.org/)

  - [WinRAR](https://www.rarlab.com/) (Business edition)

  - [Speccy](https://www.piriform.com/speccy)

  - [Windows 7 Logon Background Changer](http://www.julien-manici.com/windows_7_logon_background_changer/)

  - [WPS Office](https://www.wps.com/) (Community edition)

[Top](#installation-of-windows)
