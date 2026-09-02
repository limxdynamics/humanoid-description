# English | [中文](README_cn.md)

# LimX Humanoid Robot Description

URDF, MuJoCo MJCF & USD models for LimX Dynamics full-size humanoid robots (HU_D03, HU_D04). Provides simulation-ready robot descriptions for ROS, MuJoCo, and NVIDIA Isaac Sim.

## Available models

| Model                       | Description                        | URDF                          | MuJoCo MJCF     | USD                          |
| --------------------------- | ---------------------------------- | ----------------------------- | --------------- | ---------------------------- |
| **HU_D03** (discontinued)   | Humanoid base model                | `HU_D03_03.urdf`              | `HU_D03_03.xml` | `HU_D03_03.usd`              |
| **HU_D04**                  | Humanoid with end-effector options | `HU_D04_01.urdf`              | `HU_D04_01.xml` | `HU_D04_01.usd`              |
| **HU_D04 + Gripper**        | HU_D04 with gripper                | `HU_D04_01_with_gripper.urdf` | —               | `HU_D04_01_with_gripper.usd` |
| **HU_D04 + Dexterous Hand** | HU_D04 with dexterous hand         | `HU_D04_01_with_hand.urdf`    | —               | `HU_D04_01_with_hand.usd`    |

> **Note:** MuJoCo MJCF is only available for the base HU_D04 model. Gripper/hand variants have URDF and USD only.
>
> **Note:** HU_D03 has been discontinued and is no longer maintained. Please use HU_D04 instead.

## Directory structure

Each model directory (`HU_D03_description/`, `HU_D04_description/`) contains:

| Directory | Contents |
|-----------|----------|
| `urdf/` | URDF + SRDF (joint specs: rotor inertia, gear ratio) |
| `xml/` | MuJoCo MJCF XML |
| `usd/` | NVIDIA USD files + `configuration/` subdirectory |
| `meshes/` | STL mesh files |
| `world/` | Simulation world files |
| `CMakeLists.txt` | ROS package build file |
| `package.xml` | ROS package manifest |

HU_D04 additionally includes gripper and dexterous hand variants in `urdf/` and `usd/`.


## Quick start

### ROS 1/2

```bash
cd <workspace>/src
git clone https://github.com/limxdynamics/humanoid-description.git
cd ..
catkin_make  # or colcon build
```

### MuJoCo

```bash
python -m mujoco.viewer --mjcf=HU_D04_description/xml/HU_D04_01.xml
```

### Isaac Sim

Import the USD file from `HU_D04_description/usd/HU_D04_01.usd` via Isaac Sim's reference assembly.

## License

Apache License 2.0 — see [LICENSE](LICENSE).

## Related repositories

| Repository                                                   | Description                    |
| ------------------------------------------------------------ | ------------------------------ |
| [humanoid-rl-deploy-ros](https://github.com/limxdynamics/humanoid-rl-deploy-ros) | RL deployment with ROS         |
| [humanoid-rl-deploy-ros2](https://github.com/limxdynamics/humanoid-rl-deploy-ros2) | RL deployment with ROS 2       |
| [humanoid-mujoco-sim](https://github.com/limxdynamics/humanoid-mujoco-sim) | MuJoCo simulation for humanoid |
| [humanoid-rl-isaaclab](https://github.com/limxdynamics/humanoid-rl-isaaclab) | Isaac Lab RL training          |

> If you find these models useful, please consider starring this repository.
