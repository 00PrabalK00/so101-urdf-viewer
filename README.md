# SO101 URDF Viewer

Browser viewer for the SO101 robot arm URDF, showing its coordinate frames for forward kinematics.

## Run

```bash
git clone https://github.com/00PrabalK00/so101-urdf-viewer.git
cd so101-urdf-viewer
python -m http.server 8765
```

Then open http://localhost:8765/viewer.html (needs internet to load three.js from unpkg).

## Features

- **FK frames only** mode: shows `{0}` base, `{1}`–`{6}` one per revolute joint (Z = rotation axis), `{E}` end-effector
- Joint sliders with URDF limits
- Thick, resizable frame axes (X red, Y green, Z blue), joint axis arrows, link/joint labels
- Transparent / hidden meshes, white background, **Save PNG** with labels
- Link/joint tree with origins, rpy and axes

| Frame | Link | Joint |
|---|---|---|
| {0} | base_link | – |
| {1} | shoulder_link | shoulder_pan θ1 |
| {2} | upper_arm_link | shoulder_lift θ2 |
| {3} | lower_arm_link | elbow_flex θ3 |
| {4} | wrist_link | wrist_flex θ4 |
| {5} | gripper_link | wrist_roll θ5 |
| {6} | moving_jaw_so101_v1_link | gripper θ6 (branches from {5}, jaw only) |
| {E} | gripper_frame_link | – |

## Credits

URDF, MJCF and meshes are from [TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100) (`Simulation/SO101`), Apache-2.0 licensed — see `LICENSE` and `README_upstream.md`.
