# SkySynthAI System Architecture

## Purpose

This document describes the planned architecture for Version 1 of SkySynthAI.

## High-Level Architecture

```text
Satellite Dataset
        |
        v
Dataset Manager
        |
        v
Preprocessing
        |
        v
Frame Pair Selection
        |
        +-------------------------+
        |                         |
        v                         v
      RAFT                      RIFE
 Motion / Flow Analysis    Frame Interpolation
        |                         |
        +------------+------------+
                     |
                     v
              Generated Frame
                     |
                     v
                Evaluation
                     |
                     v
                Dashboard
```

## Modules

### 1. Dataset Manager
- Acquire or locate approved public satellite data.
- Organize chronological sequences.
- Validate files and metadata.
- Produce model-ready frame pairs.

### 2. Preprocessing
- Decode imagery.
- Resize to the model input dimensions.
- Normalize data according to the selected model requirements.
- Reject corrupted or incompatible frames.

### 3. Motion Analysis
RAFT will be investigated as an optical-flow estimator.

Expected output:
- Dense motion/flow information between frames.

### 4. Frame Interpolation
RIFE will be investigated for intermediate-frame generation.

Expected output:
- One or more synthesized frames between two observations.

### 5. Evaluation
Compare generated frames with reference frames when ground-truth intermediate observations are available.

Metrics:
- PSNR
- SSIM
- Inference time
- Qualitative visual inspection

### 6. Dashboard
The dashboard will eventually allow users to:
- Select/upload supported input frames.
- Start processing.
- View original and generated frames.
- View evaluation metrics.
- Inspect the resulting temporal sequence.

## Important Technical Note

RAFT and RIFE are separate model components with different roles. The project must verify their actual input/output interfaces from the selected implementations before deciding whether RAFT output is directly consumed by RIFE. The architecture diagram is therefore a conceptual module map, not yet a claim of a direct RAFT-to-RIFE tensor interface.

## Design Principle

Keep modules loosely coupled so that the interpolation method can be changed without rewriting the dataset, evaluation, and dashboard layers.
