# **Install-ROS2-Foxy-on-Ubuntu-20.04**

## **1. Ensure Your Windows 10 OS is Up to Date**
 > Settings -> System -> About
<img src="https://github.com/alanoudmk/Install-ROS-Noetic-on-WSL/assets/127528672/486e095d-68b7-4ca9-af96-f375bcaf0d60" width="200" height="100">

 It is recommended to update to Windows 10 or later for optimal performance.


***


## **2. Ensure you have downloaded Ubuntu and created Virtual Machine**
We will be using Ubuntu version 20.04.6 for our work.
[How to Download Ubuntu](https://github.com/alanoudmk/Install-Ubuntu-20.04.6-On-VirtualBox) 



***



## **3. Install ROS2 Foxy (Ubuntu Debian)**


 Open the **Terminal** and write the following commands: 
 
- Set Local
  
    _Ensure you have a UTF-8 supported locale. In minimal environments, the locale may be POSIX, but a different UTF-8 locale should work._
    ```
    locale  # check for UTF-8
    ```
    ```
      sudo apt update && sudo apt install locales
    ```
    ```
    sudo locale-gen en_US en_US.UTF-8
    ```
    ```
    sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
    ```
    ```
    export LANG=en_US.UTF-8
    ```
    ```
    locale  # verify settings
   ```
    
- Setup Sources

   _You will need to add the ROS 2 apt repository to your system._
  ```
   sudo apt install software-properties-common
  ```
  ```
  sudo add-apt-repository universe
   ```
   ```
  sudo apt update && sudo apt install curl -y
  ```
   ```
   sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
   ```
  ```
  echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
  ```

- Install ROS 2 Package
    ```
    Install ROS 2 packages
    ```
    ```
    sudo apt upgrade
    ```
    Desktop Install (Recommended): ROS, RViz, demos, tutorials.
    ```
    sudo apt install ros-foxy-desktop python3-argcomplete
    ```

- Enviroment Setup
  
    ```
    # Replace ".bash" with your shell if you're not using bash
    # Possible values are: setup.bash, setup.sh, setup.zsh
    source /opt/ros/foxy/setup.bash
    ```

- To verify you downloaded correctly, write:
  
 _Note:_ Only do this if you have **NOT** previously downloaded ROS1 Noetic.

```
  gedit ~/.bashrc
 ```

Make sure you find "source /opt/ros/noetic/setup.bash" at the end of the .bashrc file.
  
If not, just  *Add it*  to the end of the file, Then press the  *Save*   button.

Then go back to the *Terminal* and run the following command to ensure it's set up correctly:

```
ros2
```

***


## **Try Some Examples**

Open the *Terminal* write the following commands: 

- In one *Terminal*, source the setup file and then run a C++ talker:
  
    ```
    source /opt/ros/foxy/setup.bash
    ```
    ```
    ros2 run demo_nodes_cpp talker
    ```


- In another *Terminal* source the setup file and then run a Python listener:

   ```
    source /opt/ros/foxy/setup.bash
   ```
  ```
  ros2 run demo_nodes_py listener
  ```

You should see the talker saying that it’s Publishing messages and the listener saying I heard those messages. This verifies both the C++ and Python APIs are working properly. Hooray!


- to Exit:
    Simultaneously press the left _Ctrl_ key and the _C_ key

    
***


## **Useful Resources**

- [Full Instructions](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html) provided by the ROS organization.




 
