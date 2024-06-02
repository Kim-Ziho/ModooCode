## Make guide
```
clang -c main.cc
```
**option**
-c : object file 생성
```
% objdump -S main.o 

main.o: file format mach-o arm64

Disassembly of section __TEXT,__text:

0000000000000000 <ltmp0>:
       0: ff 83 00 d1   sub     sp, sp, #32
       4: fd 7b 01 a9   stp     x29, x30, [sp, #16]
       8: fd 43 00 91   add     x29, sp, #16
       c: 08 00 80 52   mov     w8, #0
      10: e8 0b 00 b9   str     w8, [sp, #8]
      14: bf c3 1f b8   stur    wzr, [x29, #-4]
      18: 00 00 00 94   bl      0x18 <ltmp0+0x18>
      1c: 00 00 00 94   bl      0x1c <ltmp0+0x1c>
      20: e0 0b 40 b9   ldr     w0, [sp, #8]
      24: fd 7b 41 a9   ldp     x29, x30, [sp, #16]
      28: ff 83 00 91   add     sp, sp, #32
      2c: c0 03 5f d6   ret
```
`main.o`의 어셈블리를 보면 `foo`나 `bar`에 관한 상세 내용이 없다.  
따라서 실제 프로그램을 제작하기 위해서는 `main.o foo.o bar.o`를 합친다.  
이 과정을 링킹(Linking) 이라고 한다.
```
clang main.o foo.o bar.o -o main
```
**option** -o <file> : Write output to file
