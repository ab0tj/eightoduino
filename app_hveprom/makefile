SYS = ..\sys
OBJ = .\obj
CFLAGS = -q -0 -fpc -s -d0 -od -ms -zm -i=$(SYS) -d_M8OD -dNO_MID -dNO_I2C -dNO_SPIFLASH -dNO_ADC
ASMFLAGS = -q -0 -fpc -s -d0
SYSCOBJS = stubs.obj uart.obj eod_io.obj cmain086.obj
SYSASMOBJS = cstrt086.obj util.obj

.c.obj: *.h
    wcc $(CFLAGS) $<

.asm.obj:
    wasm $(ASMFLAGS) $<

app.hex: main.obj $(SYSCOBJS) $(SYSASMOBJS)
    wlink name app.hex file { $< }

$(SYSCOBJS): $(SYS)\*.c $(SYS)\*.h
    wcc $(CFLAGS) $(SYS)\$*.c

$(SYSASMOBJS): $(SYS)\*.asm
    wasm $(ASMFLAGS) $(SYS)\$*.asm

clean: .symbolic
    rm -f *.obj *.hex *.err *.map *.bin
