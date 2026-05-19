# How-To

## Send directly from share menu on iOS
I created an iOS shortcut to send images, files, folder, URLs \
or text directly from the share-menu 
https://routinehub.co/shortcut/13990/

[//]: # (Todo: Add screenshots)

<br>

## Send directly from share menu on Android
The [Web Share Target API](https://developer.mozilla.org/en-US/docs/Web/Manifest/share_target) is implemented.

When the PWA is installed, it will register itself to the share-menu of the device automatically.

<br>

## Send directly via command-line interface
Send files or text with XimDrop via command-line interface. \
This opens XimDrop in the default browser where you can choose the receiver.

### Usage
```bash
ximdrop -h
```
```
Send files or text with XimDrop via command-line interface.
Current domain: https://ximdrop-dev.onrender.com/

Usage:
Open XimDrop:		ximdrop
Send files:		ximdrop file1/directory1 (file2/directory2 file3/directory3 ...)
Send text:		ximdrop -t "text"
Specify domain:		ximdrop -d "https://ximdrop.net/"
Show this help text:	ximdrop (-h|--help)

This ximdrop-cli version was released alongside v1.10.4
```

<br>

### Setup

#### Linux / Mac
1. Download the latest _ximdrop-cli.zip_ from the [releases page](https://github.com/schlagmichdoch/XimDrop/releases)
   ```shell
   wget "https://github.com/schlagmichdoch/XimDrop/releases/download/v1.11.2/ximdrop-cli.zip"
   ```
   or
   ```shell
   curl -LO "https://github.com/schlagmichdoch/XimDrop/releases/download/v1.11.2/ximdrop-cli.zip"
   ```
2. Unzip the archive to a folder of your choice e.g. `/usr/share/ximdrop-cli/`
   ```shell
   sudo unzip ximdrop-cli.zip -d /usr/share/ximdrop-cli/
   ```
3. Copy the file _.ximdrop-cli-config.example_ to _.ximdrop-cli-config_
   ```shell
   sudo cp /usr/share/ximdrop-cli/.ximdrop-cli-config.example /usr/share/ximdrop-cli/.ximdrop-cli-config
   ```
4. Make the bash file _ximdrop_ executable
   ```shell
   sudo chmod +x /usr/share/ximdrop-cli/ximdrop
   ```
5. Add a symlink to /usr/local/bin/ to include _ximdrop_ to _PATH_
   ```shell
   sudo ln -s /usr/share/ximdrop-cli/ximdrop /usr/local/bin/ximdrop
   ```

<br>

#### Windows
1. Download the latest _ximdrop-cli.zip_ from the [releases page](https://github.com/schlagmichdoch/XimDrop/releases)
2. Put file in a preferred folder e.g. `C:\Program Files\ximdrop-cli`
3. Inside this folder, copy the file _.ximdrop-cli-config.example_ to _.ximdrop-cli-config_
4. Search for and open `Edit environment variables for your account`
5. Click `Environment Variables…`
6. Under _System Variables_ select `Path` and click _Edit..._
7. Click _New_, insert the preferred folder (`C:\Program Files\ximdrop-cli`), click *OK* until all windows are closed
8. Reopen Command prompt window

**Requirements**

As Windows cannot execute bash scripts natively, you need to install [Git Bash](https://gitforwindows.org/).

Then, you can also use ximdrop-cli from the default Windows Command Prompt 
by using the shell file instead of the bash file which then itself executes 
_ximdrop-cli_ (the bash file) via the Git Bash.
```shell
ximdrop.sh -h
```

<br>

## Send multiple files and directories directly from context menu on Windows

### Registering to open files with XimDrop
It is possible to send multiple files with XimDrop via the context menu by adding ximdrop-cli to Windows `Send to` menu:
1. Download the latest _ximdrop-cli.zip_ from the [releases page](https://github.com/schlagmichdoch/XimDrop/releases)
2. Unzip the archive to a folder of your choice e.g. `C:\Program Files\ximdrop-cli\`
3. Inside this folder, copy the file _.ximdrop-cli-config.example_ to _.ximdrop-cli-config_
4. Copy the shortcut _send with XimDrop.lnk_
5. Hit Windows Key+R, type: `shell:sendto` and hit Enter.
6. Paste the copied shortcut into the directory
7. Open the properties window of the shortcut and edit the link field to point to _send-with-ximdrop.ps1_ located in the folder you used in step 2: \
   `"C:\Program Files\PowerShell\7\pwsh.exe" -File "C:\Program Files\ximdrop-cli\send-with-ximdrop.ps1"`
8. You are done! You can now send multiple files and directories directly via XimDrop:

   _context menu_ > _Send to_ > _XimDrop_

##### Requirements
As Windows cannot execute bash scripts natively, you need to install [Git Bash](https://gitforwindows.org/).

<br>

## Send multiple files and directories directly from context menu on Ubuntu using Nautilus

### Registering to open files with XimDrop
It is possible to send multiple files with XimDrop via the context menu by adding ximdrop-cli to Nautilus `Scripts` menu:
1. Register _ximdrop_ as executable via [guide above](#linux).
2. Copy the shell file _send-with-ximdrop_ to `~/.local/share/nautilus/scripts/` to include it in the context menu
   ```shell
   cp /usr/share/ximdrop-cli/send-with-ximdrop ~/.local/share/nautilus/scripts/
   ```
3. Make the shell file _send-with-ximdrop_ executable
   ```shell
   chmod +x ~/.local/share/nautilus/scripts/send-with-ximdrop
   ```
4. You are done! You can now send multiple files and directories directly via XimDrop:

   _context menu_ > _Scripts_ > _send-with-ximdrop_

<br>

## File Handling API
The [File Handling API](https://learn.microsoft.com/en-us/microsoft-edge/progressive-web-apps-chromium/how-to/handle-files)
was implemented, but it was removed as default file associations were overwritten ([#17](https://github.com/schlagmichdoch/XimDrop/issues/17),
[#116](https://github.com/schlagmichdoch/XimDrop/issues/116) [#190](https://github.com/schlagmichdoch/XimDrop/issues/190))
and it only worked with explicitly specified file types and couldn't handle directories at all.

[< Back](/README.md)
