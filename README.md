# NAME

jterm - A very simple "terminal program" for communicating with a serial port.

# SYNOPSIS

jterm \[options\] \[&lt;serial-device> \[&lt;baud-rate>\]\]

    Options:
      -h, --help           Show usage
      --quit-on-break      Quit if the serial device sends a "break".

    If <serial-device> is not specified then '/dev/ttyS0' will be used.
    if <baud-rate> is not specified then 115200 will be used.

# OPTIONS

- **-h**, **--help**

    Print the usage and exit.

- **--quit-on-break**

    If enabled, **jterm** will quit when receiving a
    [break](https://en.wikipedia.org/wiki/UART#Break_condition) from the serial
    device.

# DESCRIPTION

**jterm** connects to a serial port, transmitting the terminal's input to the
serial port's Rx and printing the serial port's Tx data to the terminal.

Once **jterm** connects it will capture _all_ terminal input—this includes
keys that are normally used for job control (`Control-C`, `Control-Z`,
`Control-\`, etc).

## Quitting

**To quit jterm enter `~.` on a new line.**

**NOTE**: `~.` is also the
sequence that **ssh** uses to disconnect so if you are running jterm from an
ssh session then you will need to enter 2 tildes (`~~`) (the ssh client
will see the 2 tildes and only send one across the ssh connection).

## Sending A File With XMODEM

To send a file over the serial port via the [XMODEM
protocol](https://en.wikipedia.org/wiki/XMODEM), enter `~x` on a new line
(see note above). **jterm** will prompt you for a filename and will then
attempt to send the specified file with the **sx** binary. This is part of
[lrzsz](https://ohse.de/uwe/software/lrzsz.html) which should be available
in your local package manager.
