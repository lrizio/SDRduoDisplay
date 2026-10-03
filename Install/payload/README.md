# SDRduo Display

A browser-based SDR receiver for the SDRplay RSPduo. No dedicated display
hardware and no separate SDR application: your Windows PC does the DSP and
serves a web page you open in a normal browser tab.

```
RSPduo --USB--> SDRplay API (your PC) --DSP--> FastAPI/WebSocket --> browser
                                                 (spectrum, waterfall,
                                                  audio, controls)
```

![SDRduo Display receiving the MW broadcast band](docs/img/receiver.png)

Project page: https://lrizio.github.io/SDRduoDisplay/

## Requirements

- Windows 10/11, 64-bit.
- An SDRplay RSPduo connected by USB.
- The SDRplay API (v3.15 or newer) installed and its `SDRplay API Service`
  running. This is SDRplay's own vendor software; it is **not** bundled
  here. Get it from https://www.sdrplay.com/software/.
- Python 3.10 or newer (the installer offers to install it if missing).
- Any modern browser (Chrome, Edge, Firefox).

## Installing

**Installer:** download the zip from the
[latest release](https://github.com/lrizio/SDRduoDisplay/releases/latest),
unzip it and run `setup.exe`. It copies the app to
`%LOCALAPPDATA%\SDRduoDisplay` (no administrator rights needed), creates a
private Python virtual environment, installs the dependencies and adds
Desktop and Start Menu shortcuts. The installer is not code-signed, so
Windows SmartScreen may warn the first time: click *More info*, then
*Run anyway*.

**From source:**

```bash
start_sdrduo.bat
```

The first run creates a `venv`, installs `requirements.txt`, then starts the
server and opens `http://127.0.0.1:8080` in your default browser. Later runs
reuse the venv.

To run manually instead:

```bash
venv\Scripts\activate
python run.py
```

## Current scope (v0.18)

- Single active VFO on Tuner A, fixed 2 Msps acquisition, giving a 2 MHz-wide
  panadapter around the tuned frequency.
- Modes: AM, FM (narrow), WFM (broadcast FM), USB, LSB, CW.
- Spectrum + scrolling waterfall, click or scroll-wheel to tune. Selectable
  span (2M down to 10k) and tuning step (10Hz-10k), both remembered across
  reloads. Floor/ceiling sliders control display contrast independently of
  RF gain.
- Band-select buttons for the VK amateur bands 160m-70cm (see
  `backend/bands.py`; the edges are approximate, not the authoritative ACMA
  band plan).
- On-screen keypad for frequency entry (unit-aware, MHz/kHz toggle, live
  preview) plus 8 memory preset slots (M1-M8), saved/recalled client-side.
- Manual gain reduction / LNA state sliders, or hardware AGC, with
  automatic GR/LNA re-sync on HF/VHF/UHF band crossings when AGC is on.
  The gain readout shows what the tuner is actually running.
- AF AGC, so audio level stays roughly constant across modes and signal
  strengths.
- Squelch (enable + threshold), S-meter (ham S-unit convention, not
  calibrated) and ADC-overload badge.
- Exit button in the UI for a clean shutdown (releases the SDRplay API
  device properly instead of requiring a console kill).
- Standalone Windows installer (built from `Install/`, see
  `Install/README.txt`).

## Not yet implemented

- Tuner B / simultaneous dual-band receive (the RSPduo can do both tuners at
  once; this version only drives Tuner A).
- Digital mode decoding (FT8 etc.) and recording.
- Persistence of frequency/mode between runs: it always starts on 20m
  SSB (display settings like span/step/memories/floor/ceiling do persist,
  client-side via `localStorage`).

## Documentation

- `docs/SDRduo Display User Guide.pdf` is the end-user guide (also in the
  release zip).
- `CHANGELOG.md` has the version history, including the reasoning and
  measurements behind each DSP change.
- `backend/` holds the code: `sdrplay_api.py` (ctypes binding),
  `receiver.py` (device control), `dsp.py` (spectrum + demodulators),
  `server.py` (FastAPI + WebSocket). `static/` is the browser UI.

## Licence and disclaimer

SDRduo Display is free software under the [MIT License](LICENSE). It is
provided **as is, without warranty of any kind**, and you use it at your own
risk. It is a receiver only and never transmits. Please read the full
[DISCLAIMER](DISCLAIMER.md).

SDRduo Display is an independent hobby project. It is not affiliated with,
endorsed by or supported by SDRplay Limited. "SDRplay" and "RSPduo" are
trademarks of their owner and are used only to identify the hardware this
software works with.

73 de VK3EI
