# SkySynthAI Program Flow

## Planned Execution Flow

```text
Start
  |
  v
Select satellite sequence
  |
  v
Load consecutive frames
  |
  v
Validate input
  |
  v
Preprocess frames
  |
  v
Run motion/interpolation models
  |
  v
Generate intermediate frame
  |
  v
Evaluate against reference frame (when available)
  |
  v
Store generated output and metrics
  |
  v
Display results
  |
  v
End
```

## Detailed Steps

### Step 1 — Input
The system receives a supported pair or sequence of satellite frames.

### Step 2 — Validation
Check:
- File readability
- Image dimensions
- Chronological ordering
- Required metadata
- Missing/corrupted frames

### Step 3 — Preprocessing
Apply the preprocessing required by the selected model and dataset.

### Step 4 — Frame Pairing
Select temporally ordered frames and, where possible, retain a real intermediate frame for evaluation.

Example:

```text
Frame A (t0) ---- Frame B (t1) ---- Frame C (t2)
        \             /
         \           /
          generated t1
```

Here Frame B can serve as a ground-truth reference when the task is designed to reconstruct it from Frames A and C.

### Step 5 — AI Processing
Run the verified optical-flow and/or frame-interpolation pipeline.

### Step 6 — Evaluation
Calculate PSNR, SSIM, and inference time when the experimental setup supports them.

### Step 7 — Visualization
Display:
- Input frames
- Generated intermediate frame
- Reference frame, if available
- Metrics
- Processing time

### Step 8 — Output
Save the generated frame and experiment metadata for reproducibility.
