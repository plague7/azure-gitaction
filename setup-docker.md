# Setup instructions

You will find below the instructions to set up you computer for Simplon IA School 

(based on the great job of Le Wagon [data setup](https://github.com/lewagon/data-setup/blob/master/WINDOWS.md)) 

Please **read them carefully and execute all commands in the following order**. 

If you get stuck, don't hesitate to ask a teacher for help :raising_hand:

Let's start :rocket:

<!---------------------------------------------------->
# OS Setup
<!---------------------------------------------------->

<details> 
  <summary>First, we will setup a new OS environment for development </summary>


## GitHub account

First, you will need a GitHub account. 

Have you signed up to GitHub? If not, [do it right away](https://github.com/join).

<!---------------------------------------------------->
## Windows version
<!---------------------------------------------------->

Now, we need to check that the Windows version installed on your computer is compatible with this setup instructions.

### Windows 10 or Windows 11

<details> 
  <summary>Check your Windows version</summary>

To be able to set up your computer, you need to have **Windows 10 or Windows 11** installed.

To check your Windows version:
- Press `Windows` + `R`
- Type  `winver`
- Press `Enter`

:heavy_check_mark: If the first words of this window are **Windows 10 or Windows 11** you're good to go :+1:

:x: If not, you cannot proceed with this setup. You have to upgrade to Windows 10 first :point_down:

<details>
  <summary> (Only to fix the problem) Upgrade to Windows 10</summary>

  - Download Windows 10 from [Microsoft](https://www.microsoft.com/software-download/windows10ISO)
  - Install it. It should take roughly an hour, but this depends on your computer.
  - When the installation is over, execute the commands above :point_up: to check that you now have **Windows 10**.
</details>

:warning: **If you have Windows 10 installed, you don't need to upgrade to Windows 11 to proceed with this setup**.

:information_source: [Windows 11 upgrade is rolling out now](https://www.microsoft.com/en-us/windows/get-windows-11), which means it may or may not be available for your computer just yet.

</details> 

### Latest updates

<details> 
  <summary>Check you have last updates</summary>

Once you're sure that you're using Windows 10 or 11, you need to install all the latest updates.

Open Windows Update:
- Press `Windows` + `R`
- Type  `ms-settings:windowsupdate`
- Press `Enter`
- Click on `Check updates`

:heavy_check_mark: If you see a green check mark and the message "You're up to date", you're good to go :+1:

:warning: If you have a red exclamation mark and the message "Update available", please install them and repeat the process until it says that you are up to date :loop:

:x: If you have an error message about Windows not being able to apply updates, please **contact a teacher**.

<details>
  <summary> (Only to fix the problem) Activate Windows Update Service to fix Updates</summary>

  Some antiviruses and pieces of software deactivate the Update service we need, resulting in the error you see. Let's fix that!
  - Press `Windows` + `R`
  - Type  `services.msc`
  - Press `Enter`
  - Double Click `Windows Update Service`
  - Set its `Startup` to `Automatic`
  - Click on `Start`
  - Click on `Ok`
  Then let's try updates again!
</details>


</details> 


### Minimum version

<details> 
  <summary>Check the release version</summary>

Some of the tools we need to install have been release with the `1903` version **or above** of Windows 10 so we need to make sure you have at least this one.

- Press `Windows` + `R`
- Type  `winver`
- Press `Enter`

Check the **Version number**:

:heavy_check_mark: If it says at least `1903`, you are good to go :+1:

:x: If it is below `1903`, please **contact a teacher**.

</details> 

<!---------------------------------------------------->
## Virtualization
<!---------------------------------------------------->

We need to ensure that the Virtualization options are enabled in the BIOS of your computer.

<details> 
  <summary>Steps </summary>

For many computers, this is already the case. Let's check:
- Press `Windows` + `R`
- Type  `taskmgr`
- Press `Enter`
- Click on the `Performance` tab
- Click on `CPU`

![Windows task manager](https://github.com/lewagon/setup/blob/master/images/windows_task_manager.png)
  


:heavy_check_mark: If you see "Virtualization: Enabled", you're good to go :+1:

:x: If the line is missing or if the virtualization is disabled, please **contact a teacher before trying to activate the Virtualization**

<details>
  <summary>(Only to fix the problem) Activate Virtualization</summary>

  We need to access the BIOS / UEFI of the computer to activate it.
  - Press `Windows + R`
  - Type  `shutdown.exe /r /o /t 1`
  - Press `Enter`
  - Wait for the computer to shutdown
  - Click on `Troubleshoot`
  - Click on `Advanced Options`
  - Click on `UEFI Firmware Settings`
  - Click on `Restart`

  You need to activate the virtualization option for your processor here:
  - Most of the time, in the advanced settings, the CPU settings, or the Northbridge settings
  - The option can be called differently according to your computer:
      - Intel: `Intel VT-x`, `Intel Virtualization Technology`, `Virtualization Extensions`, `Vanderpool`...
      - AMD: `SVM Mode` or `AMD-V`
  - Save the changes after activation and reboot the computer through the appropriate option
</details>



<details>
  <summary>(Only to fix the problem) Please, check again if  Virtualization options are enabled</summary>
  
  - Press `Windows` + `R`
  - Type  `taskmgr`
  - Press `Enter`
  - Click on the `Performance` tab
  - Click on `CPU`
</details>


</details> 

<!---------------------------------------------------->
## Windows Subsystem for Linux (WSL)
<!---------------------------------------------------->

WSL is the development environment we are using to run Ubuntu. You can learn more about WSL [here](https://docs.microsoft.com/en-us/windows/wsl/faq).

:information_source: The following instructions depend on your version of Windows. Please execute only the instructions corresponding to your version :point_down:



### Windows 11
<details>
  <summary> If you have Windows 11, follow these steps to install WSL </summary>

If you are running Windows 11, we will install WSL 2 and Ubuntu in one command through the Windows Terminal.

:warning: In the following instruction, please be aware of the `Ctrl` + `Shift` + `Enter` key stroke to execute **Windows Terminal** with administrator privileges instead of just clicking on `Ok`or pressing `Enter`.

- Press `Windows` + `R`
- Type  `wt`
- Press **`Ctrl` + `Shift` + `Enter`**

:warning: You may have to accept the UAC confirmation about the privilege elevation.

A blue terminal window will appear:
- Copy the following command (`Ctrl` + `C`)
- Paste it into the terminal window (`Ctrl` + `V` or by right-clicking in the window)
- Run it by pressing `Enter`

```powershell
wsl --install
```

:heavy_check_mark: If the command ran without any error, please restart your computer and continue below :+1:

:x: If you encounter an error message (or if you see some text in red in the window), please **contact a teacher**

</details>  
  

### Windows 10

<details>
  <summary> If you have Windows 10, follow these steps to install WSL </summary>

#### Install WSL 1

<details> 
  <summary>We will first install WSL 1 through the PowerShell Terminal (Steps) </summary>
  

:warning: In the following instruction, please be aware of the `Ctrl` + `Shift` + `Enter` key stroke to execute **Windows PowerShell** with administrator privileges instead of just clicking on `Ok`or pressing `Enter`.

- Press `Windows` + `R`
- Type  `powershell`
- Press **`Ctrl` + `Shift` + `Enter`**

:warning: You may have to accept the UAC confirmation about the privilege elevation.

A blue terminal window will appear:
- Copy the following commands one by one (`Ctrl` + `C`)
- Paste them into the PowerShell window (`Ctrl` + `V` or by right-clicking in the window)
- Run them by pressing `Enter`

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
```

```powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

:heavy_check_mark: If all three commands ran without any error, please restart your computer and continue below :+1:

:x: If you encounter an error message (or if you see some text in red in the window), please **contact a teacher**

</details>    
  
#### Upgrade to WSL 2

  
<details> 
  <summary>we will then upgrade WSL to version 2 (Steps) </summary>  
  

Once your computer has restarted, we need to download the WSL2 installer.

- Go to the [download page](https://aka.ms/wsl2kernel)
- Download "WSL2 Linux kernel update package"
- Open the file you've just downloaded
- Click `Next`
- Click `Finish`

![Update WSL from version 1 to 2](https://github.com/lewagon/setup/blob/master/images/windows_update_wsl.png)

:heavy_check_mark: If didn't encounter any error message, you're good to go :+1:

:x: If you encounter the error "This update only applies to machines with the Windows Subsystem for Linux", **right click** on the program and select `uninstall`; you shall be able to install it normally this time.


</details>  

  
#### Make WSL 2 the default Windows Subsystem for Linux


<details> 
  <summary>Finally, we will set WSL default version to 2 (steps).</summary>


Now that WSL 2 is installed, let's make it the default version:
- Press `Windows` + `R`
- Type  `cmd`
- Press `Enter`

In the window which appears, type:

```bash
wsl --set-default-version 2
```

:heavy_check_mark: If you see "The operation completed successfully", you can close this terminal and continue to follow the instructions below :+1:

:x: If the message you get is about Virtualization, please **contact a teacher**

<details>
  <summary>(Only if you have the problem) Enable Virtual Machine Platform Windows feature</summary>

  Follow the steps described [here](https://www.configserverfirewall.com/windows-10/please-enable-the-virtual-machine-platform-windows-feature-and-ensure-virtualization-is-enabled-in-the-bios/#:~:text=To%20enable%20WSL%202,%20Open,Windows%20feature%20on%20or%20off.&text=Ensure%20that%20the%20Virtual%20Machine,Windows%20will%20enable%20WSL%202) until you enable <strong>Virtual Machine Platform</strong> and <strong>Windows Subsystem for Linux</strong>
</details>

<details>
  <summary>(Only if you have the problem) Enable Hyper-V Windows feature</summary>

  Follow the steps described [here](https://winaero.com/enable-use-hyper-v-windows-10/) until you enable the group <strong>Hyper-V</strong>

  :information_source: If you are running Windows 10 **Home edition**, Hyper-V feature is not available for your operating system. It's non-blocking and you can still continue to follow the instructions below :ok_hand:
</details>

</details>

</details>  


<!---------------------------------------------------->
## Ubuntu
<!---------------------------------------------------->

Please Read carefully all the steps before executing them, in some cases there are some warnings to consider later in the text

### Installation

<details> 
  <summary>
  steps 
  </summary>

:information_source: The following instructions depend on your version of Windows. Please execute only the instructions corresponding to your version :point_down:

#### Windows 11

<details>
  <summary> If you have Windows 11, follow these instructions </summary>

If you are running Windows 11, after restarting you computer, you should see a terminal window saying WSL is resuming the Ubuntu installation process. When it's done, Ubuntu will be launched.

</details>

#### Windows 10

<details>
  <summary> If you have Windows 10, follow these instructions </summary>

If you are running Windows 10, let's install Ubuntu throught the Microsoft Store:

- Click on `Start`
- Type  `Microsoft Store`
- Click on `Microsoft Store` in the list
- Search for `Ubuntu` in the search bar
- **Select version without any number, just plain "Ubuntu"**
- Click on `Install`

:warning: Don't install **Ubuntu 18.04 LTS** nor **Ubuntu 20.04**!

<details>
  <summary> (Only to fix the problem) Uninstall wrong versions of Ubuntu</summary>

  To uninstall a wrong version of Ubuntu, you just have to go to the Installed Program List of Windows 10:
  - Press `Windows` + `R`
  - Type  `ms-settings:appsfeatures`
  - Press `Enter`

  Find the software to uninstall and click on the uninstall button.
</details>

Once the installation is finished, the `Install` button becomes a `Launch` button: click on it.

</details> 
</details> 


### First launch

<details> 
  <summary>steps</summary>

At first launch, you will be asked some information:
- Choose a **username**:
    - one word
    - lowercase
    - no special characters
    - for example: `lewagon` or your `firstname`
- Choose a **password**
- Confirm your password

:warning: When you type your password, nothing will show up on the screen, **that's normal**. This is a security feature to mask not only your password as a whole but also its length. Just type your password and when you're done, press `Enter`.

You can close the Ubuntu window now that it is installed on your computer.

</details> 



### Check the WSL version of Ubuntu

<details> 
  <summary>steps</summary>

- Press `Windows` + `R`
- Type  `cmd`
- Press `Enter`

Type the following command:

```bash
wsl -l -v
```

:heavy_check_mark: If the version of Ubuntu WSL is 2, you are good to go :+1:

:x: If the version of Ubuntu WSL is 1, we will need to convert it to version 2.

<details>
  <summary>(Only to fix the problem) Convert Ubuntu WSL V1 to V2</summary>

  In the Command Prompt window, type:

  ```bash
  wsl --set-version Ubuntu 2
  ```

  :heavy_check_mark: After a few seconds, you should get the following message: `The conversion is complete`.

  :x: If it does not work, we need to be sure that Ubuntu files are not compressed.
</details>

<details>
  <summary>(Only to fix the problem) Check for Uncompressed Files</summary>

  - Press `Windows` + `R`
  - Type  `%localappdata%\Packages`
  - Press `Enter`
  - Open the folder named `CanonicalGroupLimited.UbuntuonWindows...`
  - Right Click on the `LocalState` folder
  - Click on `Properties`
  - Click on `Advanced`
  - Make sure that the option `Compress content` is **not** ticked, then click on `Ok`.

  Apply changes to this folder only and try to convert the Ubuntu WSL version again.

  :x: If the conversion still does not work, please **contact a teacher**.
</details>

You can now close this terminal window.

</details> 


</details>  

<!---------------------------------------------------->
<!---------------------------------------------------->
# Development tools setup
<!---------------------------------------------------->
<!---------------------------------------------------->

<details> 
  <summary>Second, we will install the tools we need</summary>
  

## Be sure to have a correct browser

<details> 
  <summary>Install the Google Chrome browser </summary>


if you haven't got it already and set it as a __default browser__.

Follow the steps for your system from this link :point_right: [Install Google Chrome](https://support.google.com/chrome/answer/95346?co=GENIE.Platform%3DDesktop&hl=en-GB)

__Why Chrome?__

We recommend to use it as your default browser as it's most compatible with testing or running your code, as well as working with Cloud Platforms (GCP, AWS or Azure). Another alternative is Firefox, however we don't recommend using other tools like Opera, Internet Explorer or Safari.


</details> 

<!---------------------------------------------------->
## Visual Studio Code
<!---------------------------------------------------->

<details> 
  <summary>Install an IDE to develop with python </summary>


### Installation

<details> 
  <summary>
  Let's install Visual Studio Codetext editor.
  </summary>


Documentation [Visual Studio Code](https://code.visualstudio.com)

- Go to [Visual Studio Code download page](https://code.visualstudio.com/download).
- Click on "Windows" button
- Open the file you have just downloaded.
- Install it with few options:

<img src="images/windows_vscode_installation.png" alt="drawing" width="600"/>

<!--
![VS Code installation options](https://github.com/lewagon/setup/blob/master/images/windows_vscode_installation.png)
---->



When the installation is finished, launch VS Code.

</details> 

### Connecting VS Code to Ubuntu

<details> 
  <summary>instal remote WSL</summary>


To make VS Code interact properly with Ubuntu, let's install the [Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) VS Code extension.

Open your **Ubuntu terminal**.

Copy-paste the following commands in the terminal:

```bash
code --install-extension ms-vscode-remote.remote-wsl
```

Then open VS Code from your terminal:

```bash
code .
```

:heavy_check_mark: If you see `WSL: Ubuntu` in a green box in the bottom left corner of the VS Code window, you're good to go :+1:


<img src="images/windows_remote_wsl.png" alt="drawing" width="800"/>

<!--
![WSL Ubuntu Remote](https://github.com/lewagon/setup/blob/master/images/windows_remote_wsl.png)
---->

:x: Otherwise, please **contact a teacher**

</details> 

</details> 


<!---------------------------------------------------->
## Windows Terminal
<!---------------------------------------------------->

<details> 
  <summary>Let's install a correct terminal for WSL2</summary>

### Installation

<details> 
  <summary>
  :information_source: The following instructions depend on your version of Windows.
  </summary>

<br>
If you are running Windows 11, the Windows Terminal is already installed and you can proceed to the next section :point_down:

If you are running Windows 10, let's install Windows Terminal, a real modern terminal:

<details> 
  <summary> steps
  </summary>

- Click on `Start`
- Type  `Microsoft Store`
- Click on `Microsoft Store` in the list
- Search for `Windows Terminal` in the search bar
- **Select Windows Terminal"**
- Click on `Install`

:warning: DO NOT install **Windows Terminal Preview**, just **Windows Terminal**!

<details>
  <summary> (If you find problems) Uninstall wrong version of Windows Terminal</summary>

  To uninstall a wrong version of Windows Terminal, you just have to go to the Installed Program List of Windows 10:

  - Press `Windows` + `R`
  - Type  `ms-settings:appsfeatures`
  - Press `Enter`

  Find the software to uninstall and click on the uninstall button.
</details>

Once the installation is finished, the `Install` button becomes a `Launch` button: click on it.
</details> 
</details> 

### Ubuntu as the default terminal

<details> 
  <summary>
  Let's make Ubuntu the default terminal of your Windows Terminal application.
  </summary>



Press `Ctrl` + `,`

It should open the terminal settings:

<img src="images/windows_terminal_settings.png" alt="drawing" width="600"/>

<!--
![Windows Terminal Settings](https://github.com/lewagon/setup/blob/master/images/windows_terminal_settings.png)
---->



- Change the default profile to "Ubuntu"
- Click on "Save"
- Click on "Open JSON file"

We have circle in red the part you will change:

<img src="images/windows_terminal_settings_json.png" alt="drawing" width="600"/>

<!--
![Windows Terminal JSON settings file](https://github.com/lewagon/setup/blob/master/images/windows_terminal_settings_json.png)
---->



First, let's ask Ubuntu to start directly inside your Ubuntu Home Directory instead of the Windows one:
- Locate the `"name": "Ubuntu",`
- Add the following line after it:

```bash
"commandline": "wsl.exe ~",
```

:warning: Do not forget the comma at the end of the line!

Then, let's disable warning for copy-pasting commands between Windows and Ubuntu:
- Locate the line `"defaultProfile": "{2c4de342-...}"`
- Add the following line after it:

```bash
"multiLinePasteWarning": false,
```

:warning: Do not forget the comma at the end of the line!

You can save these changes by pressing `Ctrl` + `S`

:heavy_check_mark: Your **Windows Terminal** is now setup :+1:

This terminal has tabs: you can choose to open a new terminal tab by clicking on the **+** next to the current one.

**From now on, every time we will refer to the terminal or the console it will be this one.** DO NOT use any other terminal anymore.

</details> 

</details> 

<!---------------------------------------------------->
## VS Code Extensions
<!---------------------------------------------------->

<details> 
  <summary>
  Now, let's setup  VS code to develop in python
  </summary>

### Installation

<details> 
  <summary>
  Let's install some useful extensions to VS Code.
  </summary>



```bash
code --install-extension ms-vscode.sublime-keybindings
code --install-extension emmanuelbeziat.vscode-great-icons
code --install-extension MS-vsliveshare.vsliveshare
code --install-extension ms-python.python
code --install-extension KevinRose.vsc-python-indent
code --install-extension ms-python.vscode-pylance
code --install-extension ms-toolsai.jupyter
```

Here is a list of the extensions you are installing:
- [Sublime Text Keymap and Settings Importer](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings)
- [VSCode Great Icons](https://marketplace.visualstudio.com/items?itemName=emmanuelbeziat.vscode-great-icons)
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare)
- [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Python Indent](https://marketplace.visualstudio.com/items?itemName=KevinRose.vsc-python-indent)
- [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
- [Jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter)

</details> 

### Live Share configuration

<details> 
  <summary>
  Setup the live share for remote debugging
  </summary>

[Visual Studio Live Share](https://visualstudio.microsoft.com/services/live-share/) is a VS Code extension which allows you to share the code in your text editor for debugging and pair-programming: let's set it up!

Launch VS Code from your terminal by typing `code` and pressing `Enter`.

Click on the little arrow at the bottom of the left bar :point_down:

<img src="images/vscode_live_share.png" alt="drawing" width="600"/>

<!--
![VS Code Live Share](https://github.com/lewagon/setup/blob/master/images/vscode_live_share.png)
---->


- Click on the "Share" button, then on "GitHub (Sign in using GitHub account)".
- A popup appears asking you to sign in with GitHub: click on "Allow".
- You are redirected to a GitHub page in you browser asking you to authorize Visual Studio Code: click on "Continue" then "Authorize github".
- VS Code may display additional pop-ups: close them by clicking "OK".

That's it, you're good to go!

</details> 

</details> 

<!---------------------------------------------------->
## Command line tools
<!---------------------------------------------------->

<details> 
  <summary>
  Setup your terminal with a friendly shell configuration
  </summary>

### Zsh & Git

<details> 
  <summary>
  Let's setup Zsh shell environment
  </summary>

Instead of using the default `bash` [shell](https://en.wikipedia.org/wiki/Shell_(computing)), we will use `zsh`.

We will also use [`git`](https://git-scm.com/), a command line software used for version control.

Let's install them, along with other useful tools:
- Open an **Ubuntu terminal**
- Copy and paste the following commands:

```bash
sudo apt update
sudo apt install -y curl git imagemagick jq unzip vim zsh
```

These commands will ask for your password: type it in.

:warning: When you type your password, nothing will show up on the screen, **that's normal**. This is a security feature to mask not only your password as a whole but also its length. Just type in your password and when you're done, press `Enter`.

</details> 

### GitHub CLI installation

<details> 
  <summary>
  Let's now install GitHub official CLI (Command Line Interface). 
  </summary>


It's a software used to interact with your GitHub account via the command line (Documentation [GitHub official CLI](https://cli.github.com) ).

In your terminal, copy-paste the following commands and type in your password if asked:

```bash
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install -y gh
```

To check that `gh` has been successfully installed on your machine, you can run:

```bash
gh --version
```

:heavy_check_mark: If you see `gh version X.Y.Z (YYYY-MM-DD)`, you're good to go :+1:

:x: Otherwise, please **contact a teacher**

</details> 

</details> 



<!---------------------------------------------------->
## Oh-my-zsh
<!---------------------------------------------------->

<details> 
  <summary>
  Let's install the `zsh` plugin.
  </summary>

Documentation [Oh My Zsh](https://ohmyz.sh/)

In a terminal execute the following command:

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

If asked "Do you want to change your default shell to zsh?", press `Y`

At the end your terminal should look like this:

<img src="images/oh_my_zsh.png" alt="drawing" width="600"/>

<!--
![Ubuntu terminal with OhMyZsh](https://github.com/lewagon/setup/blob/master/images/oh_my_zsh.png)
---->



:heavy_check_mark: If it does, you can continue :+1:

:x: Otherwise, please **ask for a teacher**

</details> 


<!---------------------------------------------------->
## GitHub CLI
<!---------------------------------------------------->

<details> 
  <summary>
  Install and setup the GitHub CLI 
  </summary>



CLI is the acronym of [Command-line Interface](https://en.wikipedia.org/wiki/Command-line_interface).

In this section, we will use [GitHub CLI](https://cli.github.com/) to interact with GitHub directly from the terminal.

It should already be installed on your computer from the previous commands.

First in order to **login**, copy-paste the following command in your terminal:

:warning: **DO NOT edit the `email`**

```bash
gh auth login -s 'user:email' -w
```

gh will ask you few questions:

`What is your preferred protocol for Git operations?` With the arrows, choose `SSH` and press `Enter`. SSH is a protocol to log in using SSH keys instead of the well known username/password pair.

`Generate a new SSH key to add to your GitHub account?` Press `Enter` to ask gh to generate the SSH keys for you.

If you already have SSH keys, you will see instead `Upload your SSH public key to your GitHub account?` With the arrows, select your public key file path and press `Enter`.

`Enter a passphrase for your new SSH key (Optional)`. Type something you want and that you'll remember. It's a password to protect your private key stored on your hard drive. Then press `Enter`.

:warning: When you type your passphrase, nothing will show up on the screen, **that's normal**. This is a security feature to mask not only your passphrase as a whole but also its length. Just type your passphrase and when you're done, press `Enter`.

You will then get the following output:

```bash
! First copy your one-time code: 0EF9-D015
- Press Enter to open github.com in your browser...
```

Select and copy the code (`0EF9-D015` in the example), then press `Enter`.

Your browser will open and ask you to authorize GitHub CLI to use your GitHub account. Accept and wait a bit.

Come back to the terminal, press `Enter` again, and that's it.

To check that you are properly connected, type:

```bash
gh auth status
```

:heavy_check_mark: If you get `Logged in to github.com as <YOUR USERNAME> `, then all good :+1:

:x: If not, **contact a teacher**.

</details> 

<!---------------------------------------------------->
## Azure Cloud CLI
<!---------------------------------------------------->

<details>
    <summary>
        <strong>Let's install azure CLI in your terminal</strong>
    </summary>

Install the `az` (azure) CLI to communicate with (Azure Cloud Platform)[https://azure.microsoft.com/] through your terminal. 

We will follow the linux installation of Azure CLI with apt (link)[https://docs.microsoft.com/fr-fr/cli/azure/install-azure-cli-linux?pivots=apt]. 


- Get the libraries and dependencies

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl apt-transport-https lsb-release gnupg
```

- Download and install microsoft key

```bash
curl -sL https://packages.microsoft.com/keys/microsoft.asc |
    gpg --dearmor |
    sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg > /dev/null
```

- Add the Azure CLI software repository:

```bash
AZ_REPO=$(lsb_release -cs)
echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" |
    sudo tee /etc/apt/sources.list.d/azure-cli.list
```

- Update repository and install the azure-cli package

```bash
sudo apt-get update
sudo apt-get install azure-cli
```

- Try to update the CLI and log to your "Simplon" account

```bash
az upgrade
az login
```

- Now you should be connected with your accoung created by simplon to use the credits. Try the following code (you should find True as answer)

```bash
 az group exists --name ARA_P15_Lyon
```



If you want to know more, 👉 [Go to the Install documentation](https://docs.microsoft.com/fr-fr/cli/azure/install-azure-cli)

</details>
  
<!---------------------------------------------------->
## Dotfiles
<!---------------------------------------------------->

<details>
    <summary>
        <strong>Let's configure your terminal shell</strong>
    </summary>

Hackers love to refine and polish their shell and tools. We'll start with a great default configuration provided by [Le Wagon](http://github.com/lewagon/dotfiles), stored on GitHub. As your configuration is personal, you need your own repository storing it, so you first need to fork it to your GitHub account.

:arrow_right: [Click here to **fork**](https://github.com/lewagon/dotfiles/fork) the `lewagon/dotfiles` repository to your account (you'll need to click again on your picture to confirm _where_ you do the fork).

Forking means that it will create a new repo in your GitHub account, identical to the original one. You'll have a new repository on your GitHub account, `your_github_username/dotfiles`. We need to fork because each of you will need to put specific information (e.g. your name) in those
files.


Open your terminal and run the following command:

```bash
export GITHUB_USERNAME=`gh api user | jq -r '.login'`
echo $GITHUB_USERNAME
```

You should see your GitHub username printed. If it's not the case, **stop here** and ask for help.
There seems to be a problem with the previous step (`gh auth`).

Time to fork the repo and clone it on your laptop:

```bash
mkdir -p ~/code/$GITHUB_USERNAME && cd $_
gh repo fork lewagon/dotfiles --clone
```

Run the `dotfiles` installer.

```bash
cd ~/code/$GITHUB_USERNAME/dotfiles && zsh install.sh
```

Check the emails registered with your GitHub Account. You'll need to pick one
at the next step:

```bash
gh api user/emails | jq -r '.[].email'
```

Run the git installer:

```bash
cd ~/code/$GITHUB_USERNAME/dotfiles && zsh git_setup.sh
```

:point_up: This will **prompt** you for your name (`FirstName LastName`) and your email. Be careful
you **need** to put one of the email listed above thanks to the previous `gh api ...` command. If you
don't do that, Kitt won't be able to track your progress.

Please now **quit** all your opened terminal windows.
</details>


<!---------------------------------------------------->
## Disable SSH passphrase prompt
<!---------------------------------------------------->

<details>
    <summary>
        <strong>optimize remote logins</strong>
    </summary>

You don't want to be asked for your passphrase every time you communicate with a distant repository. So, you need to add the plugin `ssh-agent` to `oh my zsh`:

First, open the `.zshrc` file:

```bash
code ~/.zshrc
```

Then:
- Spot the line starting with `plugins=`
- Add `ssh-agent` at the end of the plugins list

The list should look like:

```bash
plugins=(gitfast last-working-dir common-aliases zsh-syntax-highlighting history-substring-search pyenv ssh-agent)
```

:heavy_check_mark: Save the `.zshrc` file with `Ctrl` + `S` and close your text editor.


</details>  

</details>


<!---------------------------------------------------->
<!---------------------------------------------------->
# Setup your python environment
<!---------------------------------------------------->
<!---------------------------------------------------->

<details> 
  <summary>Third, we will install python dependencies and toolkit</summary>
  

<!---------------------------------------------------->
## Installing Python (with [`pyenv`](https://github.com/pyenv/pyenv))
<!---------------------------------------------------->

<details> 
  <summary>
  Install main dependencies to work with python in a virtual framework
  </summary>


Ubuntu comes with an outdated version of Python that we don't want to use. You might already have installed Anaconda or something else to tinker with Python and Data Science packages. All of this does not really matter as we are going to do a professional setup of Python where you'll be able to switch which version you want to use whenever you type `python` in the terminal.

First let's install `pyenv` with the following Terminal command:

```bash
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
exec zsh
```

Ignore the `pyenv: no such command 'virtualenv-init' for now`.

Let's install some [dependencies](https://github.com/pyenv/pyenv/wiki/common-build-problems#prerequisites) needed to build Python from `pyenv`:

```bash
sudo apt-get update; sudo apt-get install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev \
python-dev python3-dev
```

Let's install the [latest stable version of Python](https://www.python.org/doc/versions/) supported by simplon program:

```bash
pyenv install 3.8.12
```

This command might take a while, this is perfectly normal. Don't hesitate to help other students seated next to you!

OK once this command is complete, we are going to tell the system to use this version of Python **by default**. This is done with:

```bash
pyenv global 3.8.12
exec zsh
```

To check if this worked, run `python --version`. If you see `3.8.12`, perfect! If not, ask a the teacher to help you debug the problem thanks to `pyenv versions` and `type -a python` (`python` should be using the `.pyenv/shims` version first).

</details> 

<!---------------------------------------------------->
## Python Virtual Environment
<!---------------------------------------------------->

<details> 
  <summary>
  Create a new python virtual environment
  </summary>

Before we start installing relevant Python packages, we will isolate the setup for the Bootcamp into a **dedicated** virtual environment. We will use a `pyenv` plugin called [`pyenv-virtualenv`](https://github.com/pyenv/pyenv-virtualenv).

First let's install this plugin:

```bash
git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
exec zsh
```

Let's create the virtual environment we are going to use during the whole bootcamp:

```bash
pyenv virtualenv 3.8.12 simplon
```

Let's now set the virtual environment with:

```bash
pyenv global simplon
```

Great! Anytime we'll install Python package, we'll do it in that environment.

</details> 

<!---------------------------------------------------->
## Python packages
<!---------------------------------------------------->
<details> 
  <summary>
  Install the python packages on the new virtual environment
  </summary>

Now that we have a pristine `simplon` virtual environment, it's time to install some packages in it.

First, let's upgrade `pip`, the tool to install Python Packages from [pypi.org](https://pypi.org). In the latest terminal where the virtualenv `simplon` is activated, run:

```bash
pip install --upgrade pip
```

Then let's install the main packages to do data science :

``` bash
pip install -r https://raw.githubusercontent.com/lewagon/data-setup/master/specs/releases/linux.txt
```

</details> 


<!---------------------------------------------------->
## Configuring Jupyter Notebook to open in your browser
<!---------------------------------------------------->
<details> 
  <summary>
  Let's generate the configuration file for <b>Jupyter Notebook</b>...
  </summary>



``` bash
jupyter notebook --generate-config
```

⚠️ Please copy the path returned by the previous command.

We will now edit the generated Jupyter configuration file:

``` bash
code $HOME/.jupyter/jupyter_notebook_config.py
```

Locate the following line in the configuration file:

``` python
# c.NotebookApp.use_redirect_file = True
```

And replace it with this one:

``` python
c.NotebookApp.use_redirect_file = False
```

Let's try to run Jupyter:

``` bash
jupyter notebook
```

This command should have opened a Jupyter page in your browser:


<!--
![](images/wsl_jupyter_notebook.png)
---->
<img src="images/wsl_jupyter_notebook.png" alt="drawing" width="800"/>



If it is not the case, please call the teacher.

To stop the Jupyter server in the terminal, press `Ctrl` + `C`, enter y, then press Enter.

</details> 



<!---------------------------------------------------->
## `jupyter` notebook extensions
<!---------------------------------------------------->

<details> 
  <summary>We need to install some cool extensions</summary>

Pimp your `jupyter` notebooks with awesome extensions:

```bash
# install nbextensions
jupyter contrib nbextension install --user
jupyter nbextension enable toc2/main
jupyter nbextension enable collapsible_headings/main
jupyter nbextension enable spellchecker/main
jupyter nbextension enable code_prettify/code_prettify
```




### Custom CSS

<details> 
  <summary>Improve the jupyter style</summary>

Improve the display of the [`details` disclosure elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/details) in your notebooks.

Open `custom/custom.css` in the config directory:
```bash
cd $(jupyter --config-dir)
mkdir -p custom
touch custom/custom.css
code custom/custom.css
```
Edit `custom.css` with:

```css
summary {
    cursor: pointer;
    display:list-item;
}
summary::marker {
    font-size: 1em;
}
```

You can close VS Code.

</details> 
</details> 

<!---------------------------------------------------->
## sanity check
<!---------------------------------------------------->

<details> 
  <summary>Then, let's check the whole setup</summary>

### `jupyter` check up

<details> 
  <summary>We have to check that jupyter works correctly</summary>

Let's reset your terminal:

```bash
exec zsh
```

Now, check you can launch a notebook server on your machine:

```bash
jupyter notebook
```

Your web browser should open on a `jupyter` window:

<!--
![jupyter.png](images/jupyter.png)
---->
<img src="images/jupyter.png" alt="drawing" width="800"/>


Click on `New`:

<!--
![jupyter_new.png](images/jupyter_new.png)
---->
<img src="images/jupyter_new.png" alt="drawing" width="800"/>


A tab should open on a new notebook:

<!--
![jupyter_notebook.png](images/jupyter_notebook.png)
---->
<img src="images/jupyter_notebook.png" alt="drawing" width="800"/>


</details> 

### `nbextensions` check up

<details> 
  <summary>Check the jupyter extensions</summary>

Perform a sanity check for `jupyter notebooks nbextensions`. Click on `Nbextensions`:

<!--
![jupyter_nbextensions.png](images/jupyter_nbextensions.png)
---->
<img src="images/jupyter_nbextensions.png" alt="drawing" width="800"/>


Untick _"disable configuration for nbextensions without explicit compatibility"_ then check that _at least_ all `nbextensions` circled in red are enabled:


<!--
![nbextensions.png](images/nbextensions.png)
---->
<img src="images/nbextensions.png" alt="drawing" width="800"/>


You can close your web browser then terminate the jupyter server with `CTRL` + `C`.

</details> 



### Python setup check up

<details> 
  <summary>Let's check your python setup</summary>

Check your Python version with the following commands (these are based on LeWagon checker code):

```bash
zsh -c "$(curl -fsSL https://raw.githubusercontent.com/lewagon/data-setup/master/checks/python_checker.sh)" 3.8.12
```

Run the following command to check if you successfully installed the required packages:
```bash
zsh -c "$(curl -fsSL https://raw.githubusercontent.com/lewagon/data-setup/master/checks/pip_check.sh)"
```

Now run the following command to check if you can load these packages:
```bash
python -c "$(curl -fsSL https://raw.githubusercontent.com/lewagon/data-setup/master/checks/pip_check.py)"
```

Make sure you can run Jupyter:

```bash
jupyter notebook
```

And open a `Python 3` notebook.

Make sure that you are running the correct python version in the notebook. Open a cell and run :
``` python
import sys; sys.version
```

Here you have it! A complete python virtual env with all the third-party packages you'll need for the whole bootcamp.

</details> 
</details>  
</details>  

<!---------------------------------------------------->
<!---------------------------------------------------->
# Optimize your setup
<!---------------------------------------------------->
<!---------------------------------------------------->


<details> 
  <summary>Let's improve the WSL2 development workflow </summary>


## Windows settings

<details> 
  <summary>Let's make easier to use WLS2 on Windows</summary>
  
  
### Exchange files between Windows and Ubuntu

We need an easy way to transfer files from Windows to Ubuntu and vice versa.

In order to do that, let's create shortcuts to Ubuntu directories in the Windows **File Explorer**:
- Open the Windows File Explorer (or use the shortcut `WIN` + `E`)
- In the Address Bar, enter `\\wsl$\` (or `\\wsl$\Ubuntu` if it does not work)
- You now have acces to the Ubuntu file system
- Dive into the Ubuntu file system in order to look for directories of interest
- Drag the desired folders into the Address Bar in order to create shortcuts


<img src="images/windows_ubuntu_file_system_shortcut.gif" alt="drawing" width="800"/>

<!--
![How to add a shortcut to Ubuntu file system on Windows](https://github.com/lewagon/setup/blob/master/images/windows_ubuntu_file_system_shortcut.gif)
---->

### Open the Windows File Explorer from the Ubuntu terminal

Another option to move files around is to open the Windows **File Explorer** from the Ubuntu terminal:
- Open an Ubuntu terminal
- Go to the directory you wish to explore
- Run the `explorer.exe .` command (alternatively, use `wslview .`)
- If you get an input output error message, run `wsl --shutdown` in a Windows PowerShell and reopen an Ubuntu terminal



<!--
![How to launch Windows Explorer from Ubuntu terminal](https://github.com/lewagon/setup/blob/master/images/windows_explorer_from_terminal.png)
---->

<img src="images/windows_explorer_from_terminal.png" alt="drawing" width="800"/>


### Find your way in the Ubuntu File System

You might want to figure out the exact location of a Windows directory in the Ubuntu file system, or the other way around.

In order to convert a Windows path to and from an Ubuntu path:
- Open an Ubuntu terminal
- Use the `wslpath "C:\Program Files"` command in order to translate a Windows path into an Ubuntu path
- Use the `wslpath -w "/home"` command in order to translate an Ubuntu path into a Windows path
- In particular, the `wslpath -w $(pwd)` command returns the Windows path of the current Ubuntu directory

<!--
![How to access a Windows path from Ubuntu terminal](https://github.com/lewagon/setup/blob/master/images/windows_path_from_terminal.png)
---->

<img src="images/windows_path_from_terminal.png" alt="drawing" width="800"/>

### Pin apps to your taskbar

You are going to use most of the apps you've installed today really often. Let's pin them to your taskbar so that they are just one click away!

To pin an app to your taskbar, launch the app, right-click on the icon in the taskbar to bring up the context menu and choose "Pin to taskbar".

<img src="images/windows_taskbar.png" alt="drawing" width="500"/>

<!--
![How to pin an app to the taskbar in Windows](https://github.com/lewagon/setup/blob/master/images/windows_taskbar.png)
---->

You must pin:
- Your terminal
- Your file explorer
- VS Code
- Your Internet browser
- Discord



</details>  
  
<!---------------------------------------------------->
## Visual C++ Redistributable
<!---------------------------------------------------->

Some Python packages require a compiler to function properly. 

<details> 
  <summary>Let's install one</summary>

[For x64 systems](https://aka.ms/vs/16/release/vc_redist.x64.exe)


[For x86 systems](https://aka.ms/vs/16/release/vc_redist.x86.exe)

If you're unsure about which system you're using please ask a teacher.


</details>  

</details>  
  
  
<!---------------------------------------------------->
<!---------------------------------------------------->
# Docker 🐋
<!---------------------------------------------------->
<!---------------------------------------------------->
  
<details> 
  <summary>Finally, we will end installing docker</summary>

  
Docker is an open platform for developing, shipping, and running applications.

_if you already have Docker installed on your machine please update with the latest version_
  

### Install Docker
  
<details> 
  <summary>Let's install the version for WSL2</summary>


Go to [Docker for WSL2](https://docs.docker.com/docker-for-windows/wsl/).

Download and install the Docker Desktop WSL 2 backend.

Once done, start Docker.

You should be able to run in a Ubuntu terminal:

```bash
docker run hello-world
```

The following message should print:

<img src="images/docker_hello.png" alt="drawing" width="500"/>


<!--
<img src="https://github.com/lewagon/data-setup/blob/master/images/docker_hello.png" alt="drawing" width="500"/>
---->

</details>  

</details>  
  


### Now you are ready to rock :smile:

