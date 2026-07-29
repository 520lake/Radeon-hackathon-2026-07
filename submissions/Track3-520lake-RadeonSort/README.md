# Track 3 Submission - RadeonSort

## Project

**RadeonSort: Robust Multi-Class Robotic Sorting with Failure Detection and
Automatic Recovery**

RadeonSort is a Physical AI simulation project for small warehouse sorting.
It runs a Franka Panda arm in Genesis on an AMD Radeon GPU with ROCm. The
system routes banana, lemon, and plum objects to three physical target bins,
verifies the result of each pick-and-place operation, and automatically
changes the grasp strategy after failure.

## Track

Track 3 - Physical AI Challenge: Robotics Simulation and Application Design
Based on AMD Radeon GPUs and ROCm

## Team

- Team: 520lake
- Member: 520lake (solo developer)
- Contribution: project direction, cloud environment setup, implementation,
  experiment execution, result verification, documentation, and submission

AI-assisted development tools were used for coding and documentation support.
All submitted simulation runs, videos, and quantitative results were executed
and verified by the participant.

## Key Contributions

- Multi-class routing to three physically bounded sorting bins
- Closed-loop placement verification
- Automatic recovery using grasp yaw, position, force, height, and speed
- High-friction soft-fingertip MJCF variant
- Slower transport policy for slippery objects
- Seeded reliability evaluation with JSON and CSV output
- Real failure evidence and an explainable video information panel

## Results

Evaluation used 30 randomized trials with position jitter of +/-0.025 m,
10 trials per object class, and at most two retries.

| Metric | Result |
|---|---:|
| First-attempt success rate | 86.67% |
| Final success rate after recovery | **96.67% (29/30)** |
| Banana final success rate | 100% |
| Lemon final success rate | 100% |
| Plum final success rate | 90% |
| Average retries per task | 0.20 |
| Average task time | 18.59 s |

## Deliverables

- Source code: <https://github.com/520lake/RadeonSort>
- Technical report: `RadeonSort-Technical-Report.pdf`
- Bilingual demonstration video:
  <https://github.com/520lake/RadeonSort/releases/download/v1.0.0/RadeonSort_Submission_Bilingual_v1.mp4>
- Versioned release:
  <https://github.com/520lake/RadeonSort/releases/tag/v1.0.0>
- Raw evaluation summary:
  <https://github.com/520lake/RadeonSort/blob/main/results/reliability_summary.json>
- Raw per-trial data:
  <https://github.com/520lake/RadeonSort/blob/main/results/reliability_trials.csv>

## Reproduction

The source repository contains:

- environment and cloud bootstrap instructions
- execution commands for the three-class sorting demo
- seeded reliability evaluation commands
- a compatibility patch for selecting the soft-fingertip robot MJCF
- raw output schemas and sample benchmark results

Follow the dedicated source repository README:
<https://github.com/520lake/RadeonSort>

## Pull Request Title

```text
Track 3, 520lake, RadeonSort
```
