# USB Passthrough pada Qemu. 

## Persiapan

- Qemu.
- Perangkat USB flashdrive.
- OS virtual.

## Langkah-langkah

1. List perangkat USB beserta informasinya !

	> $ lsusb \
	> $ lsusb | grep NAMA_PERANGkAT

	![lsusb](https://github.com/ahmadraniri1994/Tutur-Tinular/blob/main/Qemu-usb/2022-01-01T18:58:51%2C139035885%2B07:00.png)

1. Lihat bagian **Bus** dan **Device** !

	> **Bus 002 Device 003**: ID 0930:6544 Toshiba Corp. TransMemory-Mini Kingston DataTraveler 2.0 Stick

1. Masukkan **Bus** dan **Device** pada baris perintah qemu !

	> qemu-system-x86_64 \
   -enable-kvm \
   -m 1000 \
   -nic user,model=virtio \
   -drive file=file.qcow2,media=disk,if=virtio \
   -device qemu-xhci,id=xhci \
   -device usb-host,bus=xhci.0,hostdevice=/dev/bus/usb/**BUS**/**DEVICE** \
   --display gtk 

   contoh :

	> qemu-system-x86_64 \
   -enable-kvm \
   -m 1000 \
   -nic user,model=virtio \
   -drive file=file.qcow2,media=disk,if=virtio \
   -device qemu-xhci,id=xhci \
   -device usb-host,bus=xhci.0,hostdevice=/dev/bus/usb/002/003 \
   --display gtk 
