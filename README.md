# Ant Bot: Bio-Inspired Hexapod Navigation (Research Summary)

Ant Bot is a ROS 2 hexapod simulation that borrows two ideas from desert ants: **tripod-gait walking** and **path integration**, meaning it keeps track of its own heading and distance so it can walk straight home without GPS or a map. The robot model is a URDF/Xacro of [my hexapod platform](https://github.com/adithya2204/hexapod-terrain-platform), simulated in Gazebo with `ros2_control` and an Inertial Measurement Unit (IMU).

![Ant Bot at its start position in Gazebo](Start%20position.png)

---

## How a run works

```mermaid
flowchart LR
    A["Start at origin"] --> B["Explore<br/>(random walk, tripod gait)"]
    B --> C["Integrate heading and<br/>distance travelled"]
    C --> D["Turn towards home<br/>(yaw correction)"]
    D --> E["Walk back to origin"]
```

1. The robot leaves the origin and explores using a tripod gait.
2. As it walks, the `ant_navigator` node keeps a running estimate of where home is, from its heading (IMU yaw) and the distance it has walked.
3. To return, it turns to face home, corrects its yaw, and walks back to the origin.

## System

| Part | Role |
|---|---|
| Tripod gait controller | Alternates the two leg tripods (R1, R3, L2 and L1, L3, R2) for stable walking and steering |
| `ant_navigator` | Exploration, then homing to the origin by path integration with heading estimation |
| Yaw stabilisation | Extra correction to cut drift and vibration during full rotations and homing |
| Simulation | URDF/Xacro model with Gazebo plugins, IMU sensing and `ros2_control` interfaces |

The tripod and wave gaits were also run on the physical hexapod. The navigation results come from simulation.

## Observations

In simulation trials:

- Tripod locomotion stayed stable under direction commands
- The robot returned to the origin using path integration
- Heading held better during rotations once yaw correction was added
- Drift dropped after yaw realignment

## Demonstration

[Demo video (Google Drive)](https://drive.google.com/file/d/1WqY7ZmOZIHpbWZRTRdDwb_wMEqJCbax2/view?usp=sharing): exploration, heading estimation, homing and yaw correction on the way back.

---

## Status

The implementation is private while the work is under review for publication. If you're interested in collaborating, validating the work or discussing it, please get in touch.

## Tools

ROS 2 Humble · Gazebo Classic · Python (NumPy, transforms3d) · `ros2_control` · URDF/Xacro

## Related

- [hexapod-terrain-platform](https://github.com/adithya2204/hexapod-terrain-platform): the physical hexapod this model is based on

---

## Author

**Adithya Pothula**, Robotics Researcher (Autonomous Navigation and Legged Systems)

GitHub: [adithya2204](https://github.com/adithya2204) · [Google Scholar](https://scholar.google.com/citations?hl=en&user=NI9WpkQAAAAJ)

## License

BSD 3-Clause. See [LICENSE](LICENSE).
