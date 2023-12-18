# Serial Port Component for Lazarus

By Jurassic Pork  03/2013-03/2022

This library is Free software; you can rediStribute it and/or modify it under the terms of the GNU Library General Public License as published by the Free Software Foundation; either version 2 of the License, or (at your option) any later version.

This program is diStributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; withOut even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Library General Public License for more details.

You should have received a Copy of the GNU Library General Public License along with This library; if not, Write to the Free Software Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307, USA.

## Based on

- SdpoSerial v0.1.4
  CopyRight (C) 2006-2010 Paulo Costa
  <paco@fe.up.pt>

- Synaser library by Lukas Gebauer

- TcomPort component

## History

### new in v.0.6 version (03/2022)

- Fixes for OS-X (thanks to rphoover), `SynSer`(`synaser`) properties now persistent, v.0.3 of GPS simulator
- On OS-X you must set the property `SynSer`/`NonBlock` to `True`  in the properties of TLazserial component.

### new in v.0.5 version (03/2021)

- Memory leak on `get_serial_port_names` in `lazsynaser.pas` fixed

### new in v.0.4 version (02/2021)

- `DeviceClose` procedure fixed

### new in v.0.3 version

- Add conditional macros for `cpuarm` rpi in `lazsynaser.pas`
- Hide Ac`t`ive property from IDE Object inspector

## Features

- changed:
  - baudrate values.
  - stop bits new value: `1.5`

- new event: `onstatus`

- new property `FRcvLineCRLF`: if this property is `True`, you use `RecvString` in place of `RecvPacket` when you read data from the port.

- new procedure `ShowSetupDialog` to open a port settings form: the device combobox contain the enumerated ports.

- new procedure to enumerate real serial port on linux (in `synaser`).

## Demo

A simulator of serial port gps + serial port receiver: you can send NMEA frames (GGA GLL RMC) to the opened serial port (start gps simulator). You can change speed and heading.

In the memo you can see what is received from  the opened serial port.

In the status bar you can see the status events.

> Tested with Windows 10 and Ubuntu 20.04 Lazarus 2.0.10

## Virtual ports

if you haven't serial ports in your PC you can use virtual ports:

### Windows

To simulate a paired serial ports on Windows: `com0com`.

### Linux

- To simulate a paired serial ports on linux: `socat`

    Example: `socat -d -d PTY: PTY:`

- To connect to a bluetooth GPS on Linux

    Echo connection to a  bluetooth GPS(/dev/rfcomm0):

    ```console
    sudo rfcomm bind  0 xx:xx:xx:xx:xx:xx 1
    ```

![ScreenShot](https://user-images.githubusercontent.com/9909302/160068324-3467fac2-90e4-4625-9bfb-9cc0ef058bad.PNG)
