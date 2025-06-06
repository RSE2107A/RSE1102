# Installing ROS 2 Jazzy on Ubuntu (Binary Install)

This tutorial explains how to install ROS 2 **Jazzy** on **Ubuntu Linux** using **pre-built binary packages**.

> **Note**  
> The pre-built binary **does not include all ROS 2 packages**.  
> - All packages in the **ROS base** variant are included.  
> - Only a subset of packages from the **ROS desktop** variant are included.  
> - For the full list, refer to the [`ros2.repos`](https://github.com/ros2/ros2/blob/jazzy/ros2.repos) file.  
> - DEB packages are also available.

---

## System Requirements

ROS 2 Jazzy currently supports:

- **Ubuntu Noble (24.04)**
- Architectures:
  - 64-bit x86 (amd64)
  - 64-bit ARM (arm64)

---

## System Setup

### 1. Set Locale

Ensure your system locale supports UTF-8.

```bash
locale  # Check current locale settings

sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

export LANG=en_US.UTF-8

locale  # Verify that UTF-8 is enabled
```

---

### 2. Enable Required Repositories

#### Enable Universe Repository

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

#### Add ROS 2 APT Repository

Install the `ros2-apt-source` package to automatically set up the ROS 2 repositories:

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update

```
#### Install ROS2
```bash
sudo apt install ros-jazzy-desktop-full
sudo apt install ros-dev-tools
source /opt/jazzy/setup.bash
echo "source /opt/ros/jazzy/setup.bash" >> ~/.bashrc

```
> _More repository configuration steps will follow (e.g., importing GPG keys and installing ROS 2 packages)._  
> _(This snippet ends here, but you can extend the markdown to include those as needed.)_

