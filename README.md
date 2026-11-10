# BICAFMv2 + YOLO26n Research Repository

Research-code and manuscript scaffold for *Boundary–Interior–Context Aware Feature Representation for Lightweight Open-Manhole Detection Using YOLO26n*.

## Reproducibility warning
The supplied manuscript describes BICAFMv2 conceptually and explicitly says its exact operators, tensor dimensions, normalization and fusion sequence must be taken from the final implementation. The original `bic_afm_v2.py` and exact model YAML were not supplied. This repository therefore contains a clearly marked placeholder, not an invented implementation. Add the verified source before training or claiming reproducibility.

The manuscript-reported aggregate metrics are not independently recalculated here. Individual seed logs, raw predictions, exact checkpoint provenance, component ablations, object-scale AP, matched profiling and full rain-condition comparisons still require evidence.

## Structure
- `src/bicafm/`: BICAFMv2 integration placeholder.
- `scripts/`: training and evaluation entry points.
- `configs/`: dataset/model/experiment templates.
- `paper/`: IEEE LaTeX working conversion and original DOCX.
- `results/raw/` and `results/processed/`: separate evidence storage.
- `docs/evidence_status.md`: provenance checklist.

## Setup
```bash
python -m venv .venv
# Windows: .venv\\Scripts\\activate
# Linux/macOS: source .venv/bin/activate
pip install -r requirements.txt
```
Pin exact PyTorch, CUDA and Ultralytics versions from verified experiment logs before final reproduction.

## Dataset layout
```text
OpenManhole_Dataset/
  train/images/ train/labels/
  valid/images/ valid/labels/
  test/images/  test/labels/
```
Update `configs/data.yaml`. Do not commit dataset images unless redistribution is permitted.

## Training (only after adding verified module and YAML)
```bash
python scripts/train.py --model-yaml configs/yolo26n_bicafmv2_p3.yaml --data configs/data.yaml --seed 2024
```
The checked-in module and YAML are placeholders and intentionally prevent accidental unverified training.

## Evaluation
```bash
python scripts/evaluate.py --weights checkpoints/bicafmv2/best.pt --data configs/data.yaml --split test
```

Keep matched baseline/BICAFMv2 runs separate by seed; preserve raw logs; report individual seed values and mean ± sample SD. Use identical hardware and inference settings for profiling. RAI-OM/RIO are exploratory companion analyses and must not be represented as BICAFMv2 module components.

## License
No license is selected. Confirm code ownership, third-party terms and dataset redistribution rights before public release.
