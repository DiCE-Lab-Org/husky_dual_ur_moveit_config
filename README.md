# husky_dual_ur_moveit_config

MoveIt 2 configuration for the Clearpath Husky A200-0876 with dual UR5e arms and Robotiq 2F-85 grippers.

Pairs with [husky_description](https://github.com/DiCE-Lab-Org/husky_description), which provides the URDF.

## Planning groups

- `arm_0` and `arm_1` are kinematic chains from each UR5e base link to its tool0 frame
- `arm_0_gripper` and `arm_1_gripper` each contain the single Robotiq driver knuckle joint
- End effectors `arm_0_eef` and `arm_1_eef` connect the grippers to their parent arms

Kinematics: KDL plugin for both arms. Virtual joint is fixed from `world` to `base_link`.

## Build

```bash
cd ~/ros2_ws
colcon build --packages-select husky_dual_ur_moveit_config --symlink-install
source install/setup.bash
```

## Demo

```bash
ros2 launch husky_dual_ur_moveit_config demo.launch.py
```

Brings up MoveIt with mock hardware in RViz so you can plan and execute without the real robot.
