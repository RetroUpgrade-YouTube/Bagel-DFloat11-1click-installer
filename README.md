This is a 1 Click installer based on the trellis 1 click installer with a embeded Python install , i hade to add and modify the batch files extensivly to make it work based on : <a href="https://github.com/IgorAherne/trellis-stable-projectorz">Igor Aherne 2025</a>

Usage just Click on the run-gradio.bat file , while installing it will ask you to scroll up and check your cuda version and chose the closest one to you 1-6 avalible cuda cu118,cu121,cu124,cu126 and cu128) 

Youtube Video will be posted <a href="https://www.youtube.com/@RetroUpgrade" >RetroUpgrade - Youtube</a> showing the usage of the installer. 
Video Guide and demo of the 1 click installer : comming soon 
<hr width="100%" size="2">

<p align="center">
  <img src="https://avatars.githubusercontent.com/u/200675744?s=400&u=84a3652eb38c28a5f5af154f31b5dbf3a287ea95" alt="DFloat11" height="160"/>
  <img src="https://lf3-static.bytednsdoc.com/obj/eden-cn/nuhojubrps/banner.png" alt="BAGEL" height="160"/>
</p>

# DFloat11 + BAGEL

This repository provides inference code for the [DFloat11-compressed BAGEL-7B-MoT model](https://huggingface.co/DFloat11/BAGEL-7B-MoT-DF11).

With **32% smaller size** than the original BFloat16 model, it delivers **bit-identical outputs** while maintaining efficient GPU inference. Thanks to DFloat11 compression, BAGEL can now run smoothly on a **single 24GB GPU** without any quality loss.

## 📊 Performance Comparison

| Metric                             | BAGEL-7B-MoT (BFloat16) | BAGEL-7B-MoT (DFloat11) |
| ---------------------------------- | ------------------------- | ------------------------- |
| Model Size                         | 29.21 GB                  | 19.89 GB                  |
| Peak GPU Memory<br>(1024x1024 image generation) | 30.07 GB                  | 21.76 GB                  |
| Generation Time<br>(on an A100 GPU)   | 54 seconds               | 58 seconds               |

## BAGEL: Unified Model for Multimodal Understanding and Generation

**BAGEL** is an open‑source multimodal foundation model with 7B active parameters (14B total) trained on large‑scale interleaved multimodal data. BAGEL outperforms the current top‑tier open‑source VLMs like Qwen2.5-VL and InternVL-2.5 on standard multimodal understanding leaderboards, and delivers text‑to‑image quality that is competitive with strong specialist generators such as SD3.
Moreover, BAGEL demonstrates superior qualitative results in classical image‑editing scenarios than the leading open-source models. More importantly, it extends to free-form visual manipulation, multiview synthesis, and world navigation, capabilities that constitute "world-modeling" tasks beyond the scope of previous image-editing models.
The figure below showcases BAGEL's qualitative performance.

For more information, please refer to the original [BAGEL repository](https://github.com/ByteDance-Seed/Bagel).

<p align="center"><img src="assets/teaser.webp" width="95%"></p>


## 🔥 Quick Start

1️⃣  Set up environment
```bash
git clone https://github.com/LeanModels/Bagel-DFloat11.git
cd Bagel-DFloat11
conda create -n bagel python=3.10 -y
conda activate bagel

pip install torch==2.6 torchvision
pip install flash-attn --no-build-isolation
pip install -r requirements.txt
```

2️⃣  Download pretrained checkpoint
```python
from huggingface_hub import snapshot_download

save_dir = "./BAGEL-7B-MoT-DF11"
repo_id = "DFloat11/BAGEL-7B-MoT-DF11"
cache_dir = save_dir + "/cache"

snapshot_download(cache_dir=cache_dir,
  local_dir=save_dir,
  repo_id=repo_id,
  local_dir_use_symlinks=False,
  resume_download=True,
)
```

3️⃣  Go to [`inference.ipynb`](inference.ipynb) to start playing with BAGEL!

4️⃣ Use Gradio WebUI to start playing with BAGEL!
```bash
pip install gradio
python app.py
```

## 📄 Learn More

* **Paper**: [70% Size, 100% Accuracy: Lossless LLM Compression for Efficient GPU Inference via Dynamic-Length Float](https://arxiv.org/abs/2504.11651)
* **GitHub**: [https://github.com/LeanModels/DFloat11](https://github.com/LeanModels/DFloat11)
* **HuggingFace**: [https://huggingface.co/DFloat11](https://huggingface.co/DFloat11)
