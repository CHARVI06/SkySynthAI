# Data Directory

This directory is reserved for SkySynthAI datasets.

## Do not commit raw satellite imagery

Large GOES, Himawari, or INSAT datasets should not be stored in Git.

Expected local structure:

```text
data/
├── raw/
├── processed/
└── sequences/
```

Use `docs/dataset.md` for the dataset-selection plan.

Once the dataset is finalized, this file will contain:
- Official data source
- Access instructions
- Required subsets
- Expected directory structure
- Metadata requirements
