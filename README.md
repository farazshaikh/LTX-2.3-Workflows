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
<video controls>
  <source src="https://cdn-uploads.huggingface.co/production/uploads/64afc36a09727d75e9ca79aa/UisZ7XyIYhQgcnIKnt8h0.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

The workflows are based on the extracted models from https://huggingface.co/Kijai/LTX2.3_comfy
The extracted models might run easier on your computer (as separate files). 
(but you can easily swap out the model loader for the ComfyUI default model loader if you want to load the checkpoint with "all in one" vae built-in etc) 


**LTX-2.3 Main Model Downloads (split models):**
- Main split models used in these workflows (LTX-2.3 dev & distilled safetensor, embeddings, audio & video vae & tiny vae):
https://huggingface.co/Kijai/LTX2.3_comfy

**Gemma - either safetensor or GGUF:**
1) Gemma 3 12B it safetensor: https://huggingface.co/Comfy-Org/ltx-2/tree/main/split_files/text_encoders

2) Gemma 3 12B it GGUF: https://huggingface.co/unsloth/gemma-3-12b-it-GGUF/ 

**Upscale Model**
1) ltx-2.3-spatial-upscaler (only need the 2x file) - :  https://huggingface.co/Lightricks/LTX-2.3/tree/main  


**LTX-2.3 GGUF models (for GGUF workflows)** - one of the source below:

1) Quantstack: https://huggingface.co/QuantStack/LTX-2.3-GGUF
2) Unsloth : https://huggingface.co/unsloth/LTX-2.3-GGUF
3) Vantage : https://huggingface.co/vantagewithai/LTX-2.3-GGUF 


**Tiny Vae by madebyollin (for sampler previews)**:
(Optional/Recommended. Without this vae you still get previews with latentrgb from KJnodes, at a lower res) 



If you are unsure where to put the files see <a href="https://huggingface.co/RuneXX/LTX-2.3-Workflows/discussions/10
">here</a>

---- 

**Needed nodes:**

+ https://github.com/kijai/ComfyUI-KJNodes  (NB! Must be up to date for LTX-2 support)

+ https://github.com/city96/ComfyUI-GGUF (NB! Must be up to date for LTX-2 support)

+ ComfyUI itself must be updated to very latest


---- 

**LTX-2.3**

Lighttricks LTX-2.3 main repro: https://huggingface.co/Lightricks/LTX-2.3  
Lightricks LTX-2.3 Collection (loras etc): https://huggingface.co/collections/Lightricks/ltx-23 

---- 

More workflows :

ComfyUI Official Workflows : https://blog.comfy.org/p/ltx-23-day-0-supporte-in-comfyui 

LTX-2 Video Official Workflows : https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3