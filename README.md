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


### Troubleshooting
If faced with error messages related to D-bus read this [article](https://x410.dev/cookbook/wsl/setting-up-wsl-for-linux-gui-apps/)

If faced with error related to Segmentation error **Segmentation fault (core dumped)** 
add the following to your ~/.bashrc 
```bash
export LIBGL_ALWAYS_INDIRECT=
```
The solution was found [here](https://github.com/ros-visualization/rviz/issues/1438)
With the help of [this](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-a-linux-vps)

# How to make Windows Terminal behave like Terminator on Ubnutu
Open Windows Terminal and press Ctrl+,
Copy the setting in  
# How to make Windows Terminal behave like Terminator from Ubuntu
Open Windows Terminal and press Ctrl+, and copy the setting in [profile.json](/profile.json)


# Make SSH and Github work without asking for Passphrase all the time
Add this to ~/.bashrc
```bash 
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```

# My specific ROS sourcings  
Add these to ~/.bashrc

```bash
source /opt/ros/kinetic/setup.bash
source /mnt/d/coding/svea_research/devel/setup.bash
```