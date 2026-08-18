# SkySynthAI Dataset Plan

## Objective

Select satellite imagery that is suitable for temporal frame interpolation experiments.

## Candidate Datasets

### GOES
Candidate primary development source.

Investigate:
- Satellite/platform
- Instrument and bands
- Temporal sampling
- Spatial resolution
- File format
- Geographic coverage
- Data access method
- Licensing/usage conditions

### Himawari-8
Candidate validation source.

Investigate the same criteria as GOES.

### INSAT-3D / INSAT-3DR
Candidate for future Indian-data adaptation.

Investigate:
- Availability
- Data access
- Relevant channels
- Temporal sampling
- Compatibility with the preprocessing/model pipeline

## Dataset Selection Criteria

The final dataset decision should be based on:

1. Public accessibility
2. Sufficient temporal frequency
3. Consistent chronological observations
4. Suitable spatial resolution
5. Image quality
6. Availability of metadata
7. Compatibility with preprocessing/model requirements
8. Ability to construct evaluation pairs with a known reference frame

## Evaluation Data Construction

A useful experimental setup is:

```text
Observed Frame A       Observed Frame B       Observed Frame C
       t0                      t1                      t2
        |                       |                       |
        +---------- input ------+                       |
                                |
                         Ground truth
```

For interpolation evaluation, the exact temporal arrangement must be defined so that the generated frame can be compared with an actual observed frame.

## Data Storage Policy

Raw satellite datasets should not be committed to GitHub.

The repository should contain:
- Dataset documentation
- Download/access instructions
- Metadata/schema examples
- Small test fixtures only, if legally and technically appropriate

Large raw imagery should remain outside the repository.
