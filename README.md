# SkySynthAI

## AI-Based Temporal Enhancement of Geostationary Satellite Imagery

SkySynthAI is a proposed AI-based platform for improving the temporal continuity of geostationary satellite imagery. The system investigates the generation of intermediate satellite frames between consecutive observations using deep-learning-based motion analysis and frame interpolation.

> **Current project scope:** temporal frame enhancement. General weather forecasting, cyclone prediction, flood prediction, and land-cover classification are outside Version 1 scope.

## Problem

Geostationary satellites capture imagery at fixed time intervals. Rapidly evolving atmospheric phenomena can change substantially between observations, creating temporal gaps in the visual sequence.

SkySynthAI aims to use existing satellite observations to generate realistic intermediate frames rather than requiring additional satellite hardware.

## Proposed Pipeline

```text
Satellite Dataset
        |
        v
Dataset Management
        |
        v
Image Preprocessing
        |
        v
Frame Pair Selection
        |
        +----------------------+
        |                      |
        v                      v
      RAFT                   RIFE
 Motion Analysis       Frame Interpolation
        |                      |
        +----------+-----------+
                   |
                   v
          Generated Frame
                   |
                   v
             Evaluation
          PSNR / SSIM / Time
                   |
                   v
             Visualization
```

The exact technical relationship between RAFT and RIFE will be finalized after reviewing the model papers and implementations. They should not be assumed to form a direct sequential interface until verified.

## Project Modules

1. **Dataset Management** — acquisition, organization, validation, and sequence preparation.
2. **Preprocessing** — resizing, normalization, validation, and tensor preparation.
3. **Motion Analysis** — RAFT-based optical-flow experiments.
4. **Frame Interpolation** — RIFE-based intermediate-frame generation.
5. **Evaluation** — PSNR, SSIM, inference time, and qualitative comparison.
6. **Dashboard** — upload, processing, visualization, and result presentation.

## Dataset Strategy

The current plan is to investigate:

- **GOES** — candidate primary development dataset.
- **Himawari-8** — candidate validation dataset.
- **INSAT-3D/3DR** — candidate future/adaptation dataset.

Dataset selection is not considered final until accessibility, licensing, temporal resolution, image format, spatial resolution, and compatibility with the chosen models have been verified.

**Do not commit raw satellite datasets to Git.**

## Technology Stack

- Python
- PyTorch
- RAFT
- RIFE
- OpenCV
- GDAL (if required by the selected data format)
- Flask or FastAPI for the backend
- HTML/CSS/JavaScript for the dashboard

## Repository Structure

```text
SkySynthAI/
├── data/
├── src/
│   ├── preprocessing/
│   ├── optical_flow/
│   ├── interpolation/
│   └── evaluation/
├── models/
├── experiments/
├── dashboard/
├── notebooks/
├── literature/
├── docs/
├── tests/
├── requirements.txt
├── environment.yml
├── .gitignore
└── README.md
```

## Development Status

**Stage:** Project foundation / research and design.

Next milestones:

1. Review five research papers.
2. Compare and finalize datasets.
3. Verify RAFT and RIFE interfaces.
4. Build preprocessing pipeline.
5. Implement model experiments.
6. Add evaluation.
7. Integrate dashboard.
8. Test and document the final system.

## Team Workflow

Use feature branches rather than committing experimental work directly to `main`.

Example:

```text
main
├── member1/dataset-preprocessing
├── member2/raft
├── member3/rife-evaluation
└── member4/dashboard
```

Changes should be reviewed and merged into `main` only after basic testing.

## Research References

The five-paper literature review will be maintained in `literature/`.

See:

- `literature/literature_review.md`
- `literature/papers.csv`

## Documentation

- `docs/architecture.md` — system architecture and module responsibilities.
- `docs/program_flow.md` — execution flow from input to output.
- `docs/dataset.md` — dataset candidates and selection criteria.

## Scope Rule

Version 1 focuses on **AI-based temporal enhancement of satellite imagery**. Novel algorithms, modified model architectures, or patent-oriented improvements should be treated as future research rather than silently added to the minor-project scope.
