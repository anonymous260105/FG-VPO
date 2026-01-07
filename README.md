# Fine-Grained Visual Contrast-Driven Preference Optimization for Mitigating Hallucinations in LVLMs

This repository is provided for anonymous peer review.

## Environment Setup

To set up the environment for this project, follow these steps:

```bash
conda create -n fgvpo python=3.10
conda activate fgvpo
pip install -r requirements.txt
```

## Download Base Models

Create a folder `base_models` and download the required models, `llava-v1.5-7b` and `vision_tower-clip336`, from the web.

```bash
# Create the base_models directory
mkdir -p /path/to/your/project/base_models

# Download the llava-v1.5-7b model
wget https://huggingface.co/llava/llava-v1.5-7b/resolve/main/llava-v1.5-7b.bin -P /path/to/your/project/base_models/

# Download the vision_tower-clip336 model
wget https://huggingface.co/llava/vision_tower-clip336/resolve/main/vision_tower-clip336.bin -P /path/to/your/project/base_models/
```

## Merge FG-VPO Model

Run the following command to merge the base model with the fine-tuned LoRA model:

```bash
python run/merge/merge_llava_lora.py \
  --model-path ./base_models/llava-v1.5-7b \
  --lora-model-path ./output/llava_fgvpo/checkpoint-final/adapter_model/lora_policy \
  --save-model-path ./output/llava_fgvpo/llava_fgvpo_merged
```

