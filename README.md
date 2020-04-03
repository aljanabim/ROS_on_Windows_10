# How to make ROS Kinetic/Melodic work on Windows

This approach uses Windows Subsystems for Linux, WSL for short.

1. Go to Microsoft Store and install Ubnutu 18.04 LTS (for ROS Melodic) or Ubnutu 16.04 LTS (for ROS Kinetic) follow this [video](https://www.youtube.com/watch?v=av0UQy6g2FA)
2. Open the installed Ubuntu distro you just installed and install ROS on it
3. In install MobaXterm and follow the following [article](https://medium.com/@lixis630/extra-setup-on-wsl-for-ros-7c539463370a)

### Tips and tricks
Add the following lines to your ~/.bashrc

```bash
export DISPLAY=192.168.0.183:0.0 # or whatever you read on MobaXterm
alias open='explorer.exe .'
alias coding='cd /mnt/c( or any partion name like d or e)/[folder where your code is]'
```


# How to make Windows Terminal behave like Terminator on Ubnutu
Open Windows Terminal and press Ctrl+, and copy the setting in [profile.json](/profile.json)
