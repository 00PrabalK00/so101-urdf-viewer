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

- **FK frames only** mode: shows `{0}` base, `{1}`–`{5}` one per arm joint (Z = rotation axis), `{E}` end-effector
- Joint sliders with URDF limits
- Thick, resizable frame axes (X red, Y green, Z blue), joint axis arrows, link/joint labels
- Transparent / hidden meshes, white background, **Save PNG** with labels
- Link/joint tree with origins, rpy and axes
- **Transforms panel**: each consecutive ⁱ⁻¹Tᵢ (raw URDF origin/rpy/axis/limits, symbolic matrix, live numeric matrix), full ⁰T_E and end-effector position, link-length dimension lines in 3D; colour-coded matrix grids; frame convention switch: **Z-up** (default, every frame parallel to {0} at zero pose, Z up, X forward) **URDF** (Z = joint axis) or **DH** (standard/Spong DH table, A₁…A₅, d/a dimension lines in 3D, live URDF cross-check)

| Frame | Link | Joint |
|---|---|---|
| {0} | base_link | – |
| {1} | shoulder_link | shoulder_pan θ1 |
| {2} | upper_arm_link | shoulder_lift θ2 |
| {3} | lower_arm_link | elbow_flex θ3 |
| {4} | wrist_link | wrist_flex θ4 |
| {5} | gripper_link | wrist_roll θ5 |
| {E} | gripper_frame_link | – (gripper jaw = revolute tool DOF, no FK frame) |

## DH parameters (standard / Spong, mm)

Aᵢ = Rz(θᵢ)·Tz(dᵢ)·Tx(aᵢ)·Rx(αᵢ), qᵢ = motor/URDF angle, base offset ᴮT₀ = Trans(38.84, 0, 0).

| i | θᵢ | dᵢ | aᵢ | αᵢ |
|---|---|---|---|---|
| 1 | −q1 | 116.60 | 30.40 | −90° |
| 2 | q2 − 76.03° | 0 | 116.00 | 0° |
| 3 | q3 + 73.82° | 0 | 135.00 | 0° |
| 4 | q4 + 92.21° | −0.18 | 0 | 90° |
| 5 | −q5 + 1.21° | 159.23 | 7.90 | 0° |

Open `viewer.html?conv=dh` to start in DH mode.

## Credits

URDF, MJCF and meshes are from [TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100) (`Simulation/SO101`), Apache-2.0 licensed — see `LICENSE` and `README_upstream.md`.
