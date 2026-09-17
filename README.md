# ⚡ Human Benchmark Reaction Time Bot

A small Python bot that automatically plays the [Human Benchmark reaction time test](https://www.humanbenchmark.com/tests/reactiontime).

The script opens the page and watches the color of one pixel on the screen. As soon as the background turns green, it clicks after a small random delay (50–87 ms) so the result looks human.

> ⚠️ Made for learning and fun (automation, reading pixels). Please don't use it to cheat on leaderboards.

---

## 📋 Requirements

- **Python 3.8 or newer**: [python.org/downloads](https://www.python.org/downloads/)
  - On Windows, check **"Add Python to PATH"** during installation.
- A web browser
- Ideally a **1920×1080** screen (see [Limitations](#-limitations))

## 📦 Dependencies

| Package | Purpose |
|---|---|
| [`pyautogui`](https://pypi.org/project/PyAutoGUI/) | Moves the mouse, clicks and reads pixel colors |
| [`Pillow`](https://pypi.org/project/pillow/) | Takes the screenshots that `pyautogui.pixel()` uses |

`time`, `random`, `webbrowser`, `subprocess` and `sys` come with Python, so you don't need to install them.

**Linux only:** also install these system tools:

```bash
sudo apt install python3-tk python3-dev scrot
```

**macOS:** allow your terminal under *System Settings → Privacy & Security → Accessibility* and *Screen Recording*.

---

## 🚀 Installation

1. **Get the project**

   ```bash
   git clone https://github.com/<your-username>/humanbenchmark-reaction-bot.git
   cd humanbenchmark-reaction-bot
   ```

   (or download the ZIP from GitHub: **Code → Download ZIP**)

2. **(Optional but recommended) create a virtual environment**

   ```bash
   python -m venv venv
   ```

   Activate it:
   - Windows: `venv\Scripts\activate`
   - macOS / Linux: `source venv/bin/activate`

3. **Dependencies**: nothing to do! If `pyautogui` or `Pillow` is missing, the script installs it automatically the first time it runs.

   To install them yourself instead:

   ```bash
   pip install -r requirements.txt
   ```

---

## 🎮 How to use

1. Close unnecessary windows and put your browser on your **primary monitor**.
2. Run the script:

   ```bash
   python ReactionTime.py
   ```

3. The script opens the test page in your default browser.
4. **You have 3 seconds**: make the window fullscreen (**F11**), then don't move the mouse.
5. The bot checks that it can see the game's blue screen, clicks to start and plays all 5 rounds by itself.
6. The site shows your results at the end.

The terminal shows your screen resolution and the colors the bot detects, which helps with debugging.

### 🛑 Emergency stop

Move the mouse to the **top-left corner of the screen** to trigger PyAutoGUI's *FailSafe*, which stops the script. You can also press **Ctrl + C** in the terminal.

---

## ⚙️ Settings

Open `ReactionTime.py` and edit:

| Variable / line | Default | Effect |
|---|---|---|
| `time.sleep(3)` | `3` | How long to wait for the browser to open. Increase it if your PC is slow. |
| `lvls` | `5` | Number of rounds to play. |
| `random.uniform(0.050, 0.087)` | 50–87 ms | Delay added before each click. |

---

## ❓ Troubleshooting

**"Game not detected!" message**
The pixel the bot reads isn't the game's blue (`#2b87d1`). Make sure that:
- the page has loaded and is fullscreen (F11);
- it's on your primary monitor;
- browser zoom is at 100% (**Ctrl + 0**);
- no cookie banner is covering the game area. If one is, accept or decline it before running the script again.

**The bot never clicks**
The bot can't find the green (`#4bdb6a`). Dark mode, a color filter (night light, f.lux) or a Windows display scaling other than 100% can change the colors on screen.

**`ModuleNotFoundError: No module named 'pyautogui'`**
The automatic install failed. Run `pip install -r requirements.txt` manually (inside your venv if you use one).

**`error: externally-managed-environment`** (some Linux distros, Homebrew Python)
Your system blocks installs outside a virtual environment. Create a venv (step 2) and run the script again.

**`'python' is not recognized...`** (Windows)
Try `py ReactionTime.py`, or reinstall Python with "Add Python to PATH" checked.

---

## ⚠️ Limitations

- Positions and colors are tuned for **1920×1080**. The bot may not work at other resolutions.
- The script reads a single pixel (horizontal center, upper quarter of the screen).
- If the site changes its colors, you'll need to update the hex codes in the script.

## 📄 License

Released under the MIT License. Feel free to use and modify it.
