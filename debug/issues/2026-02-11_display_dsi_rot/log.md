# DriveOS Debug – ROT Startpunkt

Datum:11.02.2026
Board:NXP i.MX8 EVK
SoM:
Kernel:
Bootmedium:
Display: Rundes Display an hdmi adapter

## Aktiver Layer
L4 (Device Tree)

## Minimaler Test
- ls /proc/device-tree/.../adv7535@3d/*  (keine *-supply, keine reset/enable gpios)
- dmesg | grep -iE "adv7535|backlight|deferred|supply|dummy regulator"

## Ergebnis
- pwm-backlight: supply power not found, using dummy regulator
- imx-lcdif-crtc.0: deferred probe pending
- dependency cycle fixed with adv7535

## Interpretation
- Pipeline bindet nicht vollständig wegen fehlender Supplies/Abhängigkeiten im DT.

## Nächster isolierter Schritt
Noch offen.
