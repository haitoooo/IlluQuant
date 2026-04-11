# IlluQuant Dataset

**IlluQuant** is a visual illusion benchmark dataset for evaluating Vision-Language Models (VLMs). This repository contains **only the dataset** (images and annotations).

## Dataset Overview

- **Illusion types**: Adelson Checker Shadow, Ebbinghaus, Fick, Hering, Jastrow, Müller-Lyer, Wundt, Zöllner, etc.
- **Image count**: 128 PNG stimuli under `image/`
- **Annotations**: Multiple JSON label files for different evaluation setups (illusion vs. non-illusion, scale, ladder, CoT, text-only, visual control).

## Directory Structure

```
IlluQuant/
├── image/                 # Stimulus images (.png)
├── label.json             # Full annotations (all items)
├── label_illusion.json    # Baseline illusion condition (same/different size, etc.)
├── label_scale.json       # Illusion strength scale (e.g. 1.1x–5x)
├── label_ladder.json      # Illusion-on-illusion (ladder) subset
├── label_cot.json         # Chain-of-thought style prompts (with steps)
├── text_only.json         # Text-only questions (no image path)
├── visual_control.json    # Visual control subset
├── README.md
└── LICENSE
```

## Annotation Format

Each item in the label files typically has:

| Field     | Description                    |
|----------|---------------------------------|
| `id`     | Unique sample ID               |
| `image`  | Path relative to repo root, e.g. `image/xxx.png` (absent in `text_only.json`) |
| `question` | Question text                |
| `option` | JSON string of answer options  |
| `answer` | Ground-truth answer            |
| `steps`  | (Only in `label_cot.json`) Step-by-step prompt list |

- **label.json**: All samples with `id`, `image`, `question`, `option`, `answer`.
- **label_illusion.json**: Baseline illusion trials (e.g. veridical vs. illusory).
- **label_scale.json**: Scaled illusion strength (e.g. 1.1x, 1.2x, …, 5x).
- **label_ladder.json**: Illusion-on-illusion (ladder) items.
- **label_cot.json**: Same as above plus `steps` for chain-of-thought evaluation.
- **text_only.json**: No `image`; questions ask to “imagine” the illusion (text-only baseline).
- **visual_control.json**: Control subset for non-illusion visual comparisons.

## Usage

1. Clone or download this repository.
2. Load the desired JSON (e.g. `label.json`, `label_illusion.json`) and resolve image paths with the `image/` directory.
3. Use with your VLM or evaluation pipeline; ground truth is in the `answer` field.

## Citation

If you use IlluQuant in your work, please cite the corresponding paper (to be updated with publication info).