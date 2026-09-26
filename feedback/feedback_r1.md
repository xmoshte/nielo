# Nielo — R1 Feedback

**To:** Arthur
**From:** Mwangi Alex
**Re:** Response to R1 Nielo schematic review

---

Hi Arthur,

I've gone through the changes you recommended, and below is a summary of how each has been addressed.

---

## 1. Power path through D1 (SS54)

A closer look at the SS54FSH datasheet shows a forward drop of 650 mV. With J1 (power input) supplied at ~5 V, the voltage reaching the CM5 would drop to roughly 4.35 V — short of its 4.75 V minimum requirement. This is a real issue, so I've removed D1 to ensure the 4.75 V threshold is met.

## 2. CM5 mating connectors in the BOM

The two 10164227-1001A1RLF mating connectors have been added to the BOM. Please review and confirm they're correct.

## 3. "Bunny ear" caps

C3, C4, and C7 are primarily used for capacitive load matching and impedance tuning. I carried them over from a design based on the ESP32-S3, which strictly recommends them — the CM5, however, does not call for bunny-ear caps. I've marked them DNP and excluded them from the BOM, but left the 0402 footprints in place in case impedance tuning is needed later.

## 4. USB host — J2

J2 is configured as USB host/source by pulling the CC lines up to +3V3 through 10 kΩ resistors, giving a sourcing capability of 3 A @ 5 V. Please verify this is correct — J2 is the connector that interfaces with the XVF3800.

## 5. VBUS_SS from AP22653

The AP22653 is a load switch that enables power to the XVF3800. Its VBUS_SS output feeds the J2 USB-C connector. The 1.7 A current limit is intentional — let me know if the XVF3800 needs more power headroom than that.

---

## Next Steps

I'll prepare the manufacturing files while I wait for any further issues you flag.

Best,
Mwangi Alex
