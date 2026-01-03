# Lonely - Plymouth Theme

A custom, clean, and dark boot animation theme for Plymouth.
It features a 10-frame PNG sequence throbber, a rounded-corner progress bar, and a pulsing "Loading..." text effect.

![Preview](source.gif)

## Features
- **Smooth Animation:** 10-frame PNG sequence loop.
- **Dynamic Progress Bar:** Rounded corners using image cropping.
- **Pulse Effect:** Text gently fades in and out using a sine-wave function.
- **Smart Centering:** Automatically centers on any screen resolution.
- **Clean Exit:** Smooth fade-out transition when boot completes.

## Installation

### 1. Download the Theme
Clone this repository or download the files.

```bash
git clone https://github.com/AntarcDev/lonely.git
cd lonely
```
### 2. Copy to Plymouth Directory

Create the theme directory and move the files:
```bash
sudo mkdir -p /usr/share/plymouth/themes/lonely
sudo cp -r * /usr/share/plymouth/themes/lonely/
```
### 3. Set and Apply Theme

Tell Plymouth to use this theme and rebuild your initramfs.

For Arch Linux:
```bash
sudo plymouth-set-default-theme -R lonely
```
Note: The -R flag automatically runs mkinitcpio. If it doesn't, run sudo mkinitcpio -P manually.

For Fedora/Debian/Ubuntu:
```bash
sudo plymouth-set-default-theme -R lonely
sudo update-initramfs -u
```
## Testing

You can preview the theme without rebooting by running the Plymouth daemon in debug mode. This will run the animation for 10 seconds and then quit:
```bash
sudo plymouthd --debug; sudo plymouth --show-splash; sleep 10; sudo plymouth --quit
```
## Customization

You can adjust animation speeds by editing the .script file:
```bash
sudo nano /usr/share/plymouth/themes/lonely/lonely.script
```

- **Animation Speed:** Search for progress_counter += 0.2. Change 0.1 (slower) or 0.5 (faster).

- **Pulse Speed:** Search for Math.Sin(progress_counter * 0.1). Change 0.1 to adjust the text breathing speed.

- **Text:** Search for Image.Text("Loading Antarcsys..." to change the displayed text.

- **Fonts:** If the text doesn't appear, you can force a font by changing the text line to: Image.Text("...", 1, 1, 1, "Sans", 20);