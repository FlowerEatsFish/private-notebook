# Disk partition

## MBR (Master Boot Record)

```windows
# Press "Shift + F10" in installing windows.
$ diskpart
$ list disk
$ select disk <disk number>
$ clean
$ exit
```

## GPT (GUID Partition Table)

```windows
# Press "Shift + F10" in installing windows.
$ diskpart
$ list disk
$ select disk <disk number>
$ clean
$ convert gpt
$ exit
```
