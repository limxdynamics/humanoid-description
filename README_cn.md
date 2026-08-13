# 中文 | [English](README.md)

# LimX 人形机器人描述

LimX Dynamics 全尺寸人形机器人（HU_D03、HU_D04）的 URDF、MuJoCo MJCF 和 USD 模型文件。提供仿真就绪的机器人描述，支持 ROS、MuJoCo 和 NVIDIA Isaac Sim。

## 可用型号

| 型号 | 描述 | URDF | MuJoCo MJCF | USD |
| ---- | ---- | ---- | ----------- | --- |
| **HU_D03**（已停止维护） | 人形基础型号 | `HU_D03_03.urdf` | `HU_D03_03.xml` | `HU_D03_03.usd` |
| **HU_D04** | 带末端执行器选项的人形 | `HU_D04_01.urdf` | `HU_D04_01.xml` | `HU_D04_01.usd` |
| **HU_D04 + 夹爪** | HU_D04 配夹爪 | `HU_D04_01_with_gripper.urdf` | — | `HU_D04_01_with_gripper.usd` |
| **HU_D04 + 灵巧手** | HU_D04 配灵巧手 | `HU_D04_01_with_hand.urdf` | — | `HU_D04_01_with_hand.usd` |

> **注意：** MuJoCo MJCF 仅为基础 HU_D04 型号提供。夹爪/灵巧手变体仅有 URDF 和 USD。
>
> **注意：** HU_D03 已停止维护，请改用 HU_D04。

## 目录结构

每个型号目录（`HU_D03_description/`、`HU_D04_description/`）包含：

| 目录 | 内容 |
|------|------|
| `urdf/` | URDF + SRDF（关节参数：转子惯量、减速比） |
| `xml/` | MuJoCo MJCF XML |
| `usd/` | NVIDIA USD 文件 + `configuration/` 子目录 |
| `meshes/` | STL 网格文件 |
| `world/` | 仿真世界文件 |
| `CMakeLists.txt` | ROS 包构建文件 |
| `package.xml` | ROS 包清单 |

HU_D04 额外在 `urdf/` 和 `usd/` 中包含夹爪和灵巧手变体。

## 快速开始

### ROS 1/2

```bash
cd <workspace>/src
git clone https://github.com/limxdynamics/humanoid-description.git
cd ..
catkin_make  # 或 colcon build
```

### MuJoCo

```bash
python -m mujoco.viewer --mjcf=HU_D04_description/xml/HU_D04_01.xml
```

### Isaac Sim

通过 Isaac Sim 的参考装配功能导入 `HU_D04_description/usd/HU_D04_01.usd`。

## 许可证

Apache License 2.0 — 详见 [LICENSE](LICENSE)。

## 相关仓库

| 仓库 | 描述 |
| ---- | ---- |
| [humanoid-rl-deploy-ros](https://github.com/limxdynamics/humanoid-rl-deploy-ros) | ROS RL 部署 |
| [humanoid-rl-deploy-ros2](https://github.com/limxdynamics/humanoid-rl-deploy-ros2) | ROS 2 RL 部署 |
| [humanoid-mujoco-sim](https://github.com/limxdynamics/humanoid-mujoco-sim) | 人形 MuJoCo 仿真 |
| [humanoid-rl-isaaclab](https://github.com/limxdynamics/humanoid-rl-isaaclab) | Isaac Lab RL 训练 |

> 如果这些模型对你有帮助，欢迎给仓库点个 Star。
