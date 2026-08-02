# Track 3 Submission: RadeonHome

| Field | Value |
| --- | --- |
| Track | Track 3 — Physical AI Challenge |
| Team | lake |
| Team member | Wang Suhu (王苏湖) |
| Application | RadeonHome |
| Source repository | [520lake/RadeonHome](https://github.com/520lake/RadeonHome) |
| Submitted source revision | [`463e601`](https://github.com/520lake/RadeonHome/commit/463e6017fee7edee667db0aa79078550ae711208) |
| Technical report | [RadeonHome-Technical-Report.pdf](RadeonHome-Technical-Report.pdf) |
| Demonstration video | [4:17 complete-workflow video](https://github.com/520lake/RadeonHome/blob/main/output/video/RadeonHome_Track3_Demo_20260802.mp4) |
| Reproducibility guide | [Project README](https://github.com/520lake/RadeonHome#quick-reproduction) |

## Project summary

RadeonHome is a failure-aware household mobile-manipulation system running on
an AMD Radeon GPU with ROCm. A mobile Franka navigates a room, docks near a
task object, performs physical-contact grasping, transports the payload, and
verifies placement. The same Genesis run produces live RGB, metric depth,
continuous video, contact/slip measurements, and machine-readable JSON.

A local `Qwen/Qwen3-4B` service converts free-form household requests into a
constrained semantic task plan. An explicit allow-list validates every action,
object, target, and safety constraint before deterministic A* planning and the
physical controller can execute it. The model never emits coordinates, joint
commands, or motor commands.

## Key technical contributions

- A documented migration of the official fixed-base Franka MJCF asset to a
  collision-aware planar mobile base without bypassing physical contact.
- A closed loop from language interpretation through room navigation,
  docking, physical grasp, low supported carry, slip monitoring, retry, and
  verified placement.
- Honest, auditable evaluation: failed variants and limitations are retained,
  and an identical-seed ablation compares gripper-only transport, support-tray
  transport with slip checks, and support-tray transport without slip checks.
- Reproducible AMD evidence with ROCm/HIP versions, `gs.amdgpu` initialization,
  GPU utilization, VRAM, power, wall time, and control throughput.
- A local web dashboard exposing the accepted Qwen mapping, deterministic
  route, live Genesis RGB/depth, execution phase, resulting MP4, and JSON.

## AMD Radeon / ROCm evidence

The final environment used ROCm/HIP 7.2, a 48 GiB `gfx1100` AMD Radeon GPU,
PyTorch ROCm, and Genesis 1.3.0 with the `gs.amdgpu` backend. In the matched
final physical benchmark:

| Metric | Video disabled | Video enabled |
| --- | ---: | ---: |
| Control throughput | 48.68 steps/s | 38.26 steps/s |
| Mean / peak GPU utilization | 50.24% / 65% | 77.24% / 90% |
| Peak VRAM used | 8,862.33 MiB | 9,309.69 MiB |
| Mean / peak board power | 30.40 / 50 W | 55.19 / 78 W |

Raw telemetry and physical outcome JSON are committed in the dedicated source
repository under `results/final_mobile_migration_rocm_20260802/`.

## Deliverables

- Complete Python source, tests, cloud bootstrap, dashboard, simulator runners,
  ablation runner, report builder, and video builder
- English reproducibility README with dependency and command specifications
- English technical-report PDF and editable report/architecture sources
- 4:17 English-narrated demonstration with English/Chinese captions
- Real Genesis RGB/depth frames, MP4s, logs, result JSON, failure cases,
  ablation records, and ROCm telemetry

## Reproduction

Please follow the dedicated repository's
[Radeon Cloud reproduction instructions](https://github.com/520lake/RadeonHome#quick-reproduction).
The evaluator can run the deterministic regression suite, reproduce one
physical task, launch local Qwen and the dashboard, and rerun the matched
ablation and ROCm telemetry benchmark from the documented commands.

## Disclosure and limitations

The submitted physical controller is deterministic and is not presented as a
trained policy. Simulator semantic locations remain privileged inputs, the
corrected multi-profile smoke test uses one seed per profile, and tall-carton
unloading remains a documented failure mode. These limitations are reported
explicitly instead of being hidden behind selected videos.
