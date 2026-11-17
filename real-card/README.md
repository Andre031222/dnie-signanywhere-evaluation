# Measurements with physical DNIe cards

Checks of the card side of DNIe-SignAnywhere with physical **DNIe 2.0 and 3.0** cards, made by the corresponding author on 16 November 2026.

**Equipment.** Windows; USB CCID smart-card reader (Microsoft Usbccid driver); the client reaches the card through the PC/SC interface (`winscard.dll`) and the operating-system certificate store.

**Scope.** The tests used the tool's document-signing mode (PAdES), so they exercise the card, the PIN and the production certificate chain, but not the web challenge–response flow.

## Card signing time (`card_signing_times.csv`)

| | n | Median | Range |
| --- | :---: | :---: | :---: |
| DNIe 2.0 | 5 | 1.80 s | 1.69–1.98 s |
| DNIe 3.0 | 5 | 2.06 s | 1.80–2.10 s |
| All | 10 | **1.94 s** | 1.69–2.10 s |

One card signature takes about 30 000 times the server-side verification (0.064 ms), so the user experience is set by the card and the PIN entry.

## Behaviour checks (`behaviour_checks.csv`)

| Check | Observed |
| --- | --- |
| Wrong PIN (once) | no signature; the card reports the remaining attempts; the chip blocks after three consecutive errors |
| Reader disconnected | the client reports that no reader is present and offers no card certificate |
| Two cards present | the client lists the signing certificates of both cards |
| Production certificate chain | signatures from both card versions were reported **valid** (PAdES baseline B) by the national validator of Firma Perú |

Screenshots are not published because they show names and identity numbers; only aggregated results are included.
