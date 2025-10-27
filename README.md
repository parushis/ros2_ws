# ROS 2  Ignition Gazebo Bridge Setup

This guide explains how to **add new bridge topics**, **rebuild your workspace**, and **run the bridge** within a Conda-managed ROS 2 environment.

---

## Environment Setup

| Tool | Version | Notes |
|------|----------|-------|
| macOS | 14+ | Tested on Apple Silicon |
| Conda | 24.7+ | For ROS environment management |
| ROS 2 | Humble (via Conda) | Installed inside `ros_env` |
| Ignition Gazebo | Fortress | Installed via Homebrew |
| colcon | 0.15+ | For building workspaces |
| ros_gz_bridge | Latest compatible | Handles ROS ↔️ Gazebo bridging |

---

## Example Multi-Topic Bridge YAML

Edit your bridge configuration file:

```bash
vi ~/Documents/Nimbis/src/bridge_config/config/bridge.yaml

---

## Rebuild Workspace

cd ~/Documents/Nimbis
colcon build --symlink-install
source install/setup.zsh

---

## Run the Bridge

conda activate ros_env
source $CONDA_PREFIX/share/ros2/setup.zsh

ros2 run ros_gz_bridge parameter_bridge --ros-args -p config_file:=$HOME/src/bridge_config/config/bridge.yaml

---

## Verify 

ros2 topic list (inside the conda env.)
ign topic -l (outside the conda env.)


