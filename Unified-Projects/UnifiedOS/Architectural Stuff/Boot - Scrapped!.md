Decided not to use grub, this is because it's easier to understand.

The kernel gets mapped to high virtual memory (```0xFFFFFFFF80000000```) as to allow full memory range for processes. Would be more important if on a 32 bit system.

```nasm TI="GDT (Faily Standard)"
align 16
GDT64:                           ; Global Descriptor Table (64-bit).
    .Null: equ $ - GDT64         ; The null descriptor.
    dw 0xFFFF                    ; Limit (low).
    dw 0                         ; Base (low).
    db 0                         ; Base (middle)
    db 0                         ; Access.
    db 0                         ; Granularity.
    db 0                         ; Base (high).
    .Code: equ $ - GDT64         ; The code descriptor.
    dw 0                         ; Limit (low).
    dw 0                         ; Base (low).
    db 0                         ; Base (middle)
    db 10011010b                 ; Access (exec/read).
    db 00100000b                 ; Granularity, 64 bits flag, limit19:16.
    db 0                         ; Base (high).
    .Data: equ $ - GDT64         ; The data descriptor.
    dw 0                         ; Limit (low).
    dw 0                         ; Base (low).
    db 0                         ; Base (middle)
    db 10010010b                 ; Access (read/write).
    db 00000000b                 ; Granularity.
    db 0                         ; Base (high).
    .UserData: equ $ - GDT64     ; The usermode data descriptor.
    dw 0                         ; Limit (low).
    dw 0                         ; Base (low).
    db 0                         ; Base (middle)
    db 11110010b                 ; Access (read/write).
    db 00000000b                 ; Granularity.
    db 0                         ; Base (high).
    .UserCode: equ $ - GDT64     ; The usermode code descriptor.
    dw 0                         ; Limit (low).
    dw 0                         ; Base (low).
    db 0                         ; Base (middle)
    db 11111010b                 ; Access (exec/read).
    db 00100000b                 ; Granularity, 64 bits flag, limit19:16.
    db 0                         ; Base (high).
    .TSS: ;equ $ - GDT64         ; TSS Descriptor
    .len:
    dw 108                       ; TSS Length - the x86_64 TSS is 108 bytes loong
    .low:
    dw 0                         ; Base (low).
    .mid:
    db 0                         ; Base (middle)
    db 10001001b                 ; Flags
    db 00000000b                 ; Flags 2
    .high:
    db 0                         ; Base (high).
    .high32:
    dd 0                         ; High 32 bits
    dd 0                         ; Reserved
GDT64Pointer:                    ; The GDT-pointer.
    dw $ - GDT64 - 1             ; Limit.
    dq GDT64                     ; Base.
```

### CPU
This section is quite important because it means that older generation CPUs will not be supported unless they support x86_64-V2 Extentions (SSE4 etc)

```nasm TI="CPU-64-bit"
mov rax, cr0
and ax, 0xFFFB    ; Clear coprocessor emulation
or ax, 0x2      ; Set coprocessor monitoring
mov cr0, rax

;Enable SSE
mov rax, cr4
or ax, 3 << 9   ; Set flags for SSE (x86_64-V2 extentions)
mov cr4, rax

mov rcx, 0x277 ; PAT Model Specific Register
rdmsr
mov rbx, 0xFFFFFFFFFFFFFF
and rax, rbx
mov rbx, 0x100000000000000
or rax, rbx  ; Set PA7 to Write-combining (0x1, WC)
wrmsr
```

```nasm TI="Compiler Faults"
global __cxa_atexit ; Would be defined by compiler but isn't in LLVM
__cxa_atexit:
  ret

section .bss
align 64
stack_bottom:
resb 32768
stack_top:

global __dso_handle ; Would be defined by compiler but isn't in LLVM
__dso_handle: resq 1
```