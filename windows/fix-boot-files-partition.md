### Fix boot files installed on other disk rather than OS disk . Windows 10.

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

1. Use [EaseUS Todo Backup](https://www.easeus.com/backup-software/) to backup all disks/partitions.

2. Create a partition for disk 1 using Diskpart.

```windows
$ create partition primary align=1024 size=500
$ format fs=ntfs unit=4096 quick
```

3. Restore boot partition to the new partition using EaseUS Todo Backup.

4. Delete the old boot partition using Diskpart.

```windows
$ Select Disk 2
$ Select Partition [number of the old boot partition]
$ DELETE partition
```

5. Under Windows 10 installation mode, use Command Prompt (cmd) to fix boot file.

```windows
$ bootrec /fixmbr     # 把 Windows 相容的 MBR 寫入系統磁碟分割
$ bootrec /fixboot    # 新的開機磁區 Windows 相容的開機磁區寫入系統磁碟分割
$ bootrec /rebuildbcd # 重建 BCD (Boot Configuration Database) 開機設定資料存放區
```

Reference:

- [【Win 10 練功坊】 天啊！解決 UEFI 無法開機的慘況](https://www.techbang.com/posts/49377-win-10-practice-workshops-day-solving-misery-uefi-will-not-power-on)
- [diskpart 硬碟分割指令](http://blog.ilc.edu.tw/blog/index.php?op=printView&articleId=505798&blogId=25793)
- [Windows 10 MBR 修復](https://home.gamer.com.tw/creationDetail.php?sn=3339579)
