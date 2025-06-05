# RS485 Board

GitHub hardware [link](https://github.com/FYNCH-BIO/hardware/tree/master/Vial%20Platform/RS485)

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption><p>RS485 board is center with a red arrow pointing to it.</p></figcaption></figure>

## Overview

The [RS485](https://en.wikipedia.org/wiki/RS-485) board enables serial communication between the [Raspberry Pi](../raspberry-pi.md) (server) and the [Arduinos ](arduino.md)(controlling the parameters).

## Troubleshooting

The RS485 board has broken on very rare occasions.

### Symptoms

No communication between all Arduinos and the Raspberry Pi server

### Diagnosis

If only one Arduino is not communicating More likely to be something wrong with:

1. Arduino
2. [Motherboard](../../troubleshooting/vial-platform-troubleshooting/motherboard-troubleshooting-replacement.md) connections between Arduino and RS485 board

If you have tried a new Arduino with new code and verified motherboard connections work, it may be the RS485 board itself. Try a new RS485 board ordered from Fynch.
