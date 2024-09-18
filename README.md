## Steps

### Environ
- Start ubuntu 22.04 on virtual box 
- Install nasm and qemu
```
 sudo apt install nasm
 sudo apt install qemu
```
- Simplest boot sector ever
```
$ vim boot_sector.asm
; Infinite loop (e9 fd ff)
loop:
    jmp loop 

; Fill with 510 zeros minus the size of the previous code
times 510-($-$$) db 0
; Magic number
dw 0xaa55  
```
- Compile and Run
```
$ nasm -f bin boot_sector.asm -o boot_sector.bin
$ qemu-system-x86_64 ./boot_sector.bin 
```


