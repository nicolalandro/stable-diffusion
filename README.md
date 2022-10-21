# Stable Diffusion

## How to use
* Prepare env:
```
conda env create -f environment.yaml
conda activate ldm
```
* download [sd-v1-4.ckpt](https://huggingface.co/CompVis/stable-diffusion-v-1-4-original):
  * accept licence
  * go to Files and versions
  * select file and download
* copy into models/ldm/stable-diffusion-v1/model.ckpt
* run  text to img: 
```
CUDA_VISIBLE_DEVICES="1" PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=python python scripts/txt2img.py --prompt "a photograph of an astronaut riding a horse" --plms
```
* run img to img
```
PYTORCH_CUDA_ALLOC_CONF="max_split_size_mb:25" CUDA_VISIBLE_DEVICES="1" PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=python python scripts/img2img.py --prompt "A photo of a fantasy landscape, trending on artstation" --init-img "assets/stable-samples/img2img/sketch-mountains-input_crop.jpg" --strength 0.8
```
* inpainting:
```
wget -O models/ldm/inpainting_big/last.ckpt https://heibox.uni-heidelberg.de/f/4d9ac7ea40c64582b7c9/?dl=1

CUDA_VISIBLE_DEVICES="1" PROTOCOL_BUFFERS_PYTHON_IMPLEMENTATION=python python scripts/inpaint.py --indir assets/stable-samples/inpainting/ --outdir outputs/inpaint --steps 100
```


