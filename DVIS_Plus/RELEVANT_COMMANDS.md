# Relevant Commands for training on NDT HurricaneVidNet Dataset

## Training DVIS++

## ResNet-50 Backbone, Offline
```bash
# Template of command
export DETECTRON2_DATASETS=/data/datasets/HurricaneVidNet_Dataset/
CUDA_VISIBLE_DEVICES=<Comma-separated list of GPUs to use> python train_net_video.py \
  --num-gpus <# of GPUs> \
  --dist-url tcp://127.0.0.1:50200 \
  --config-file configs/dvis_Plus/VSPW/DVIS_Plus_Offline_R50.yaml \
  --resume MODEL.WEIGHTS <Location of pretrained model (should be offline_r50_vspw_486.pth)> \
  SOLVER.IMS_PER_BATCH <# of GPUs>

# Example

```

