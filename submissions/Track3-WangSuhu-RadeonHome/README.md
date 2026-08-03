# Track 3 Submission: RadeonHome

> **Language-guided, failure-aware household mobile manipulation on AMD Radeon GPU**

| | |
|---|---|
| **Track** | Track 3 — Physical AI Challenge |
| **Team** | Wang Suhu (王苏湖) — Solo |
| **Application** | RadeonHome |

## Links

| Resource | URL |
|---|---|
| 📦 Source Code | https://github.com/520lake/RadeonHome |
| 🎥 Demo Video | https://youtu.be/1gE-kTozAdo |
| 📄 Technical Report | https://github.com/520lake/RadeonHome/blob/agent/mobile-manipulation-mvp/output/pdf/RadeonHome_Technical_Report_20260802.pdf |
| 🔬 ROCm Benchmark | https://github.com/520lake/RadeonHome/blob/agent/mobile-manipulation-mvp/docs/final_rocm_benchmark_20260802.md |
| 🔄 Upstream Contribution | https://github.com/wangxunx/franka_fruit_pick_demo/pull/2 |
| 🐳 Docker | `Dockerfile` included in source repo |

## Quick Reproduction

```bash
git clone -b agent/mobile-manipulation-mvp https://github.com/520lake/RadeonHome.git
cd RadeonHome
# Follow README.md for environment setup and evaluation commands
```

## Summary

RadeonHome is a failure-aware mobile manipulation system that runs entirely on one AMD Radeon GPU (ROCm + Genesis). It navigates a mobile Franka robot across a 6×6m room, physically grasps household objects, transports them while monitoring for slips, and autonomously recovers from failures.

- **15/17** physical-contact tasks completed (88.24%, 95% Wilson CI: 65.66%–96.71%)
- **11.48 mm** mean placement error
- Local Qwen3-4B LLM for task planning (no cloud API)
- Real-time slip detection with autonomous recovery
- ROCm telemetry: 50.24% avg GPU utilization, 99% peak
