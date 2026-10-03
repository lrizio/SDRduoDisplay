# Disclaimer

SDRduo Display is a free, non-commercial hobby project written by an amateur radio operator for
other amateurs and listeners. By downloading, installing or using it you accept the terms below.
If you do not accept them, do not use the software.

## No warranty

SDRduo Display, its installer and its documentation are provided **"as is" and "as available"**,
without warranty of any kind, express or implied, including fitness for a particular purpose,
accuracy, reliability, availability or non-infringement. The full terms are in the
[MIT License](LICENSE).

## Limitation of liability

To the maximum extent permitted by law, the author and contributors are not liable for any direct,
indirect, incidental, special, consequential or other loss or damage arising from the use of, or
inability to use, SDRduo Display. This includes loss of data, damage to equipment or software,
hearing damage from unexpectedly loud audio, licence or regulatory infringements, injury or
property damage. You use it entirely at your own risk. Nothing here excludes any right that cannot
be excluded under the consumer law that applies to you.

## Your hardware

SDRduo Display controls an SDRplay RSPduo through the vendor's API, including its gain, LNA and
AGC settings. Connecting any receiver to an antenna carries the usual risks (strong nearby
transmitters, static, lightning). Protecting your receiver, your PC and yourself is your
responsibility. Keep the volume low when you first enable audio or change mode.

## Not a measuring instrument

The S-meter, signal levels, spectrum and frequency readouts are **uncalibrated** and for hobby
interest only. Do not rely on them for measurements, compliance testing or anything where accuracy
matters.

## Not for safety-of-life use

Do not rely on SDRduo Display to monitor distress, emergency, aviation, marine or any other
safety-related communications.

## Lawful reception and band information

The software can tune anywhere the RSPduo can. What you may lawfully receive, record or pass on
differs from country to country. The band buttons are a simplified approximation of the Australian
amateur bands, may be out of date, and **are not legal advice**. You are solely responsible for
complying with the laws and licence conditions that apply to you.

## Third parties and trademarks

SDRduo Display is an independent project. It is **not affiliated with, endorsed by, sponsored by or
supported by SDRplay Limited**. "SDRplay" and "RSPduo" are trademarks of their owner and are used
only to identify the hardware this software works with. Please do not ask SDRplay for support with
this program.

The SDRplay API and driver are SDRplay's own software, are not included here, and are subject to
SDRplay's own licence terms. The installer also downloads third-party open-source packages
(FastAPI, Uvicorn, NumPy, SciPy and their dependencies) from the Python Package Index, and can
optionally install Python through winget. Each is covered by its own licence.

## Network use and privacy

* SDRduo Display does not collect telemetry, analytics or personal data, and has no server of its
  own on the internet. The author receives nothing from your copy of the program.
* The program runs a small web server on your own PC, bound to `127.0.0.1` (this computer only),
  port 8080. It is not reachable from other devices unless you change that yourself. It has no
  login or encryption, so if you do expose it to a network, anyone who can reach it can control
  the receiver and shut it down. That is at your own risk.
* While running it makes no internet connections. Internet access is used only during
  installation, to download the Python packages listed above.
* Settings such as span, step and memories are stored only in your browser on your PC.
* SDRduo Display is a receiver. It never transmits.

## Unsigned software

The Windows installer is a PowerShell script compiled to `setup.exe`. It is not code-signed, so
Windows SmartScreen may warn you the first time you run it, and some antivirus products flag
script-compiled executables of this kind. Only download SDRduo Display from this project's
official GitHub page. If you prefer, you can read the installer source in `Install/`, or run the
program directly from the source code instead.

## Changes

These terms may be updated with new releases. The version included with the release you downloaded
applies to that release.
