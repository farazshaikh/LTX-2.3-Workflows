---
tags:
- ltx
- ltx-2
- comfyui
- comfy
- gguf
- ltx-video
- ltx-2-3
- ltxv
- text-to-video
- image-to-video
- audio-to-video
- video-to-video
---
The workflows are based on the extracted models from https://huggingface.co/Kijai/LTX2.3_comfy
The extracted models might run easier on your computer (as separate files). 
(but you can easily swap out the model loader for the ComfyUI default model loader if you want to load the checkpoint with "all in one" vae built-in etc) 


Model Downloads:
- Main split models used in these workflows (LTX-2.3 dev & distilled safetensor, embeddings, audio and video vae): 
https://huggingface.co/Kijai/LTX2.3_comfy

Gemma - either safetensor or GGUF:
- Gemma 3 12B it safetensor: https://huggingface.co/Comfy-Org/ltx-2/

- Gemma 3 12B it GGUF: https://huggingface.co/unsloth/gemma-3-12b-it-GGUF/ 


- Optional LTX-2.3 GGUF models (for GGUF workflows). One of the source below:
1) Quantstack: https://huggingface.co/QuantStack/LTX-2.3-GGUF
2) Unsloth : https://huggingface.co/unsloth/LTX-2.3-GGUF
3) Vantage : https://huggingface.co/vantagewithai/LTX-2.3-GGUF 

- Tiny Vae (for sampler previews):
https://github.com/madebyollin/taehv/blob/main/safetensors/taeltx2_3.safetensors  
(Optional/Recommended. Without this vae you still get previews with latentrgb from KJnodes, at a lower res)

---- 

Needed nodes:

+ https://github.com/kijai/ComfyUI-KJNodes  (NB! Must be up to date for LTX-2 support)

+ https://github.com/city96/ComfyUI-GGUF (NB! Must be up to date for LTX-2 support)

+ ComfyUI itself must be updated to very latest


---- 


Lighttricks LTX-2.3 main repro: https://huggingface.co/Lightricks/LTX-2.3  
Lightricks LTX-2.3 Collection (loras etc): https://huggingface.co/collections/Lightricks/ltx-23