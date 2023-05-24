To use Visual Studio with WSL2 through SSH, you would need to follow these steps:
I would recommend going directly to Step 1. (only do the optionnal part if the normal one is not working)

**Optionnal Step 0: Install an SSH server in WSL2**

1. Open WSL2 by typing `wsl` in the Windows command prompt or PowerShell.
2. Update the package lists for upgrades and new package installations: `sudo dnf update`
3. Install OpenSSH server: `sudo dnf install openssh-server`
4. Enable the SSH service to start on boot: `sudo systemctl enable sshd`
5. Start the SSH service: `sudo systemctl start sshd`

Note: Systemd is not fully supported in WSL2, and if the `systemctl` command doesn't work, you may need to manually start the SSH server with `/usr/sbin/sshd` every time you open WSL2.

**Step 1: Set up a new connection in Visual Studio**

1. Open Visual Studio.
2. Go to `Debug > Attach to Process`.
3. In the `Connection type` dropdown, select `SSH`.
4. In the `Connection target` box, select your wsl2.
4.1 *Optionnal* In the `Connection target` box, type `localhost`.
Note: If the above does not work, you may need to provide the IP address of the WSL2 instance. You can get this by typing `ip addr` in the WSL2 terminal and using the inet address under eth0.

**Optionnal Step 0.2: Authenticate with your WSL2 username and password**

You should now be prompted to enter your WSL2 username and password. If you haven't set a password, you can set one using the `passwd` command in WSL2.



Once you're connected, you should be able to select the process you want to attach to and debug your code as if it were running on a remote machine.
