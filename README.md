# qemu-kvm-vfio-gaming

## OVMF 

"is a project to enable UEFI support for Virtual Machines" [link](https://www.linux-kvm.org/page/OVMF)

OVMF is provided by tianocore and can be downloaded pre-compiled [link](https://www.kraxel.org/repos/jenkins/edk2/)
compile it [yourself](https://github.com/tianocore/edk2). You need the ovfm-x64 for a Windows 10 x64 guest setup.

To extract the files from the rpm on Debian/Ubuntu, you can use [rpm2cpio](https://askubuntu.com/questions/52230/how-do-i-extract-a-rpm-file)

You need to include it in your kvm config to be able to use the UEFI bios in your guest system.
```xml
  <os>
    <type arch='x86_64' machine='pc-q35-4.2'>hvm</type>
    <loader readonly='yes' type='pflash'>path/to/OVFM.fd</loader>
    <nvram>/path/to/OVFM_VARS.fd</nvram>
    <boot dev='hd'/>
  </os>
```
OVFM.fd can be any variant of the downloaded OVFM.fd files.
OVFM_VARS.fd can be any file as long as it is a copy of OVFM_VARS.fs (or variant of it) and is used to persist the UEFI config.

## Notes

