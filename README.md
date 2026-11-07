# Fushi Lens — Steam Deck plugin

**Fushi Lens** is a [Decky Loader](https://decky.xyz) plugin for Steam Deck Game Mode.
Press a back button while you play: the plugin reads the text on screen with your
[Fushi](https://github.com/hajisensai/Fushi) app, and you can look up any word and
mine it to Anki without leaving the game.

This repo only holds release files and this guide. The source is in
[hajisensai/Fushi](https://github.com/hajisensai/Fushi/tree/develop/tools/decky-fushi-lens)
(`tools/decky-fushi-lens`). These builds are community builds, not official Fushi releases;
report problems with them in this repo.

## What you need

- A Steam Deck (SteamOS 3.x).
- **Fushi 3.3.0 or newer on another device on the same network**: the desktop app
  (Windows, macOS or Linux) or the headless `fushi_server`. The Deck only takes the
  screenshot; the text recognition, dictionaries and Anki run on that device.
- On that device:
  - **Interconnect turned on:** Settings → Interconnect → *Enable interconnect*.
  - **OCR models downloaded:** Settings → Models → OCR.
  - For mining: Anki set up in Fushi as usual.
- Your firewall must let the Deck reach the Fushi device on TCP port **38765**.

## 1. Install Decky Loader

Decky Loader adds a plugin menu to Game Mode. You only do this once.

1. **Switch to Desktop Mode:** press the **STEAM** button → **Power** → **Switch to Desktop**.
2. **Set a password** if you have never set one (the installer needs it). Open
   **Konsole** from the app menu, type `passwd`, press Enter and choose a password.
   Nothing appears on screen while you type; that's normal.
3. **Download the installer:** open a web browser, go to **https://decky.xyz** and click
   **Download**. You get a file called `decky_installer.desktop`.
4. **Run it:** open the Downloads folder in Dolphin (the file manager) and double-click
   `decky_installer.desktop`. Choose **Release** and enter your password when asked.
5. **Go back to Game Mode** with the **Return to Gaming Mode** icon on the desktop.

Decky is now in the **Quick Access** menu: press the **⋯** button (right of the screen)
and look for the **plug** icon at the bottom of the list.

After a SteamOS update Decky sometimes disappears. Run the installer again to bring it back;
your plugins and settings are kept.

## 2. Install Fushi Lens

Decky installs plugins from its store, from a link or from a zip file. Fushi Lens is not
in the store, so first turn on Developer Mode:

1. Quick Access (**⋯**) → **Decky** (plug icon) → the **gear** icon at the top.
2. **General** → turn on **Developer Mode**. A **Developer** tab appears.

Then pick **one** of these:

**A. From a link (easiest, no Desktop Mode needed)**

1. On the [Releases](../../releases) page, copy the link of the newest
   `fushi-lens-<version>.zip` (right-click → *Copy link*, for example on your PC).
2. On the Deck: Decky settings → **Developer** → **Install Plugin from URL** → paste or type
   the link → **Install**. Confirm the prompt.

**B. From the zip file**

1. In Desktop Mode, download `fushi-lens-<version>.zip` from [Releases](../../releases).
2. In Game Mode: Decky settings → **Developer** → **Install Plugin from ZIP File** →
   **Browse** → pick the zip in Downloads → confirm.

**Fushi Lens** now shows in the Decky plugin list.

To update, install the newer zip the same way: your pairing and settings are kept.
To remove: Decky settings → **Plugins** → **⋯** next to Fushi Lens → **Uninstall**.

## 3. Pair with Fushi (once)

1. On the Fushi device, open Settings → Interconnect and note its address (the PC's IP,
   for example `192.168.1.20`).
2. On the Deck: Quick Access → Decky → **Fushi Lens**. Type that address into
   **Fushi address (PC IP)** and press **Pair**.
3. Fushi shows a request and a **PIN**. Approve the device in Fushi, type the PIN into
   **PIN shown in Fushi** on the Deck and press **Confirm**.

The panel now says **Paired with …**.

## 4. Use it in a game

- Press **L4** (the upper-left back button) to read the screen. You can choose L4, R4, L5
  or R5 under **Controls → Read-screen button**, or press **Read the screen now** in the panel.
- **Stop the game from also seeing that button:** in the game's Steam Input settings
  (controller icon), set the same back button to **None**.

In the Lens:

| Button | Does |
|---|---|
| D-pad up / down, LB / RB | Pick a line (with the popup open: up / down scroll it) |
| D-pad left / right | Move along the line |
| **A** | Look up the word (again: close the popup) |
| **X** | Mine the word to Anki (popup open) |
| **Y** | Set the reading area for this game |
| **B** | Close the popup, or leave the Lens |
| Your read-screen button | Leave the Lens |

With **Tap to look up** on (Controls), you can also tap a character on the touchscreen.

**Reading area:** in visual novels, press **Y** and drag a box around the dialogue box
(or press **A** to use the text found now). Fushi Lens then reads only that part, which
is faster and skips menus. It is saved per game. **X** in that mode, or
**Read the whole screen** in the panel, goes back to the whole screen.

## Troubleshooting

| Problem | Try |
|---|---|
| Pairing does nothing or times out | Check that the Deck and the Fushi device are on the same network, interconnect is on, and port 38765 is allowed through the firewall |
| "OCR models are not ready on this host" | Download the OCR models in Fushi: Settings → Models → OCR |
| "No text found on screen" | Text may be too small or faint; set a reading area with **Y** around the dialogue |
| Back buttons do nothing ("Back buttons unavailable") | The plugin can't read the Deck's built-in controller (for example when docked with only an external controller). Use **Read the screen now** in the panel instead |
| The plugin is gone after a SteamOS update | Reinstall Decky Loader (step 1); Fushi Lens comes back by itself |

## Source and license

GPL-3.0, see [LICENSE](LICENSE), same as Fushi. Each release names the exact
[hajisensai/Fushi](https://github.com/hajisensai/Fushi) commit it was built from; build it
yourself with `npm ci && npm run build` in `tools/decky-fushi-lens`.
