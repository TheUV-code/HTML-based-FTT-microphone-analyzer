# HTML-based FFT microphone analyzer

A single-file, browser-based FFT spectrum analyzer for measurement microphones.
Open `index.html` over **HTTPS or `localhost`**, because browsers only allow microphone access in a secure context.

```bash
python3 -m http.server 8000   # then open http://localhost:8000
```

## Features

- Live spectrum (log frequency axis) with an adjustable release time, oscilloscope and VU meter
- FFT size 1024–32768, Hann / Hamming / Blackman / Flat-top / Rectangular windows, 0–87.5 % overlap
- Selectable sample rate (44.1k–192k). If the device/browser refuses the rate, the app falls back and says so in the status line
- **Record Avg**: power (RMS) averaging over any number of frames
- **Hold**: freeze the live view
- **Save / recall / overlay**: save any trace, view it, or overlay all saved traces on the live view for comparison. The cursor tooltip shows each trace's value and its difference from the main trace
- **Export CSV / Import**: export the displayed trace, and import it again later as a reference trace
- **Calibration file**: two-column `frequency dB` text (miniDSP/REW style; header lines are ignored)
  - *Mic response (subtract)*: the file describes the mic's deviation (miniDSP, REW, most vendors). This is the default
  - *Correction (add)*: the file is a correction curve to add
- **dB offset**: shifts all displayed values, e.g. to turn dBFS into dB SPL after calibrating against a reference source

Amplitude scaling: a full-scale sine reads 0 dBFS with every window (coherent-gain corrected).

## Keyboard

| Key | Action |
| --- | --- |
| `H` | Hold / resume |
| `R` | Start / stop recording average |
| `S` | Save current trace |
| `←` / `→` | Move the cursor one bin (while hovering the graph) |

## Files

- `index.html`: current version
- `archive/`: earlier versions (1.2, 1.3), kept for reference
