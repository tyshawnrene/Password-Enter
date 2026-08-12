**Password-Enter**

A small Python utility that automates entering a username and iterating through a list of candidate passwords on an Android device via ADB. It is intended for authorized testing and automation of login UIs where tapping coordinates and simple text input are required.

**Features**
- **ADB-driven input:** Uses the `ppadb` library to send touch and text input events through Android Debug Bridge (ADB).
- **Batch password attempts:** Reads a newline-separated password list and attempts each entry in sequence.
- **Configurable coordinates:** Tap/swipe coordinates are defined in `main.py` and can be adjusted per device or app layout.

**Prerequisites**
- **ADB installed** and available on your PATH. Verify with `adb devices`.
- **Python 3.8+**.
- Install the Python dependency with:

```bash
pip install pure-python-adb
```

**Quickstart**
1. Connect your Android device via USB (or make sure it is reachable via ADB).
2. Prepare a plaintext password file (one password per line).
3. Open a terminal in the project folder and run:

```bash
python main.py
```

Follow the prompts for the path to your password file and the username to try.

**Configuration**
- Open [main.py](main.py) and edit the coordinate variables to match the app fields on your device. Example variables in the script:

- `username_coords` — coordinates to tap the username field.
- `password` — coordinates to tap the password field.
- `password2` — swipe used to long-press or clear the field (configured as an input swipe).
- `deletebutton` — coordinates to tap a delete/clear button if needed.
- `login` — coordinates to tap the login button.

Coordinates are simple space-separated integers used with `adb shell input tap` and `adb shell input swipe`.

**Safety and Legal**
This tool automates login attempts. Use it only on devices and accounts you own or where you have explicit permission to perform automated authentication testing. Unauthorized access attempts are illegal and unethical.

**Notes & Limitations**
- The script assumes a single connected device via ADB and uses the first device detected.
- Timing and delays (`time.sleep`) may need tuning for slower devices or networked apps.
- The tool performs no advanced error handling or rate-limiting—use responsibly.

**Contributing**
If you want enhancements (e.g., coordinate calibration helper, UI, or safety controls), open an issue or submit a pull request.

**Author**
Original script by Tyshawn Rene.

