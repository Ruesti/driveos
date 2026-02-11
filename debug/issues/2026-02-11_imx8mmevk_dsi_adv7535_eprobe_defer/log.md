# ROT Startpunkt – imx8mmevk DSI -> ADV7535 (EPROBE_DEFER)

Datum: 2026-02-11
Target: imx8mmevk
Subsystem: DRM / MIPI-DSI / Bridge (ADV7535)

Aktiver Layer:
- L3 (DRM bridge attach / driver bind)
Trigger/Umfeld:
- L4 (DT dependency graph / endpoints / supplies)

Minimaler Test:
dmesg -T | grep -iE "adv7535|mipi_dsi|lcdif|drm|bridge|endpoint|deferred|supply|regulator" | tail -n 60

ROT Marker (Auszug):
- [drm:drm_bridge_attach] *ERROR* failed to attach bridge ... mipi_dsi ... : -517
- imx_sec_dsim_drv ... failed to bind sec dsim bridge: -517
- platform imx-lcdif-crtc.0: deferred probe pending
- platform backlight: deferred probe pending

Interpretation (kurz):
DSI host kann den nächsten Bridge/Connector (ADV7535 chain) nicht attachen, da Ziel noch deferred (EPROBE_DEFER).
