# Opcodes
Everything is little-endian!

|1st byte|structure|description|
|-|-|-|
|`00`|`XXXX`|sets PC to `XXXX`|
|`01`|`XXXX`|sets PC to address stored in RAM at `XXXX`|
|`02`|`XY`|sets PC to `RX << 8 \| RY`|
|`03`|`XY`|copies `RX`'s value to `RY`|
|`04`|`XXXXY0`|copies `RY`'s value to `XXXX`|
|`04`|`XXXXY1`|copies value at `XXXX` to `RY`|
|`04`|`XXXXY2`|copies `RY`'s value to `XXXX` on disk|
|`04`|`XXXXY3`|copies value at `XXXX` on disk to `RY`|
|`05`|`XXXX`|gets disk size and stores it in RAM at `XXXX`-`XXXX+2` (3B)|
|`06`|`0XNN`|sets `RX` to `NN`|
|`06`|`1XNN`|sets `RX` to `RX+NN`, sets `Rf` to 1 if an overflow occured or 0 if it didn't|
|`06`|`2XNN`|sets `RX` to `RX-NN`, sets `Rf`|
|`06`|`3XNN`|sets `RX` to `NN-RX`, sets `Rf`|
|`06`|`4XNN`|sets `RX` to `RX*NN`, sets `Rf`|
|`06`|`5XNN`|sets `RX` to `RX\|NN`|
|`06`|`6XNN`|sets `RX` to `RX&NN`|
|`06`|`7XNN`|sets `RX` to `RX^NN`|
|`06`|`8X0N`|sets `RX` to `RX>>N`|
|`06`|`9X0N`|sets `RX` to `RX<<N`|
|`07`|`XY`|sets `RX` to `RX+RY`, sets `Rf`|
|`08`|`XY`|sets `RX` to `RX-RY`, sets `Rf`|
|`09`|`XY`|sets `RX` to `RY-RX`, sets `Rf`|
|`0a`|`XY`|sets `RX` to `RX*RY`, sets `Rf`|
|`0b`|`XY`|sets `RX` to `RX\|RY`|
|`0c`|`XY`|sets `RX` to `RX&RY`|
|`0d`|`XY`|sets `RX` to `RX^RY`|
|`0e`|`XY`|sets `RX` to `RX>>RY`|
|`0f`|`XY`|sets `RX` to `RX<<RY`|
|`10`||pops a value from the stack and sets PC to that value|
|`11`|`XXXX`|pushes PC to the stack and sets PC to `XXXX`|
|`12`|`XXXX`|pops the top of the stack to RAM address `XXXX` (2B)|
|`13`|`XXXX`|pushes value at RAM address `XXXX` (2B) to the stack|
|`14`|`XYZZZZ`|if `RX == RY`, go to `ZZZZ`|
|`15`|`XYZZZZ`|if `RX != RY`, go to `ZZZZ`|
|`16`|`XYZZZZ`|if `RX > RY`, go to `ZZZZ`|
|`17`|`XYZZZZ`|if `RX < RY`, go to `ZZZZ`|
|`18`|`XYZZZZ`|if `RX >= RY`, go to `ZZZZ`|
|`19`|`XYZZZZ`|if `RX <= RY`, go to `ZZZZ`|
|`1a`|`X0YYZZZZ`|if `RX == YY`, go to `ZZZZ`|
|`1a`|`X1YYZZZZ`|if `RX != YY`, go to `ZZZZ`|
|`1a`|`X2YYZZZZ`|if `RX > YY`, go to `ZZZZ`|
|`1a`|`X3YYZZZZ`|if `RX < YY`, go to `ZZZZ`|
|`1a`|`X4YYZZZZ`|if `RX >= YY`, go to `ZZZZ`|
|`1a`|`X5YYZZZZ`|if `RX <= YY`, go to `ZZZZ`|
|`1b`|`0X`|sets delay timer frequency to `RX` Hz|
|`1b`|`1X`|sets sound timer frequency to `RX` Hz|
|`1b`|`2X`|sets delay timer value to `RX` Hz|
|`1b`|`3X`|sets sound timer value to `RX` Hz|
|`1b`|`40`|waits for delay timer to finish|
|`1b`|`41`|waits for sound timer to finish|
|`1c`|`XX`|prints system character `XX`|
|`1d`|`XX`|prints custom character `XX`|
|`1e`|`XXYYYY`|sets custom character `XX` to character stored at `YYYY`-`YYYY+F`|
|`1f`|`XXYYYY`|go to `YYYY` if `XX` is pressed on the keyboard|
|`20`|`XY`|sets text color to `RX`'s value and background color to `RY`'s value|
|`21`||clears display|
|`22`|`XY`|goes to coordinates (`RX`, `RY`) for printing|