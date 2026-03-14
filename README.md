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

# LTX 2.3 RuneXX Workflow Demos

**[Live Demo Site](https://farazshaikh.github.io/LTX-2.3-Workflows/)**

Original workflows by [RuneXX on HuggingFace](https://huggingface.co/RuneXX/LTX-2.3-Workflows). These demos were generated using modified versions tuned for **RTX 6000 (48GB VRAM)** with performance and quality adjustments.

**Running on lower VRAM (RTX 5070 / 12-16GB)** -- use a lower quantized Gemma encoder (e.g. `gemma-3-12b-it-Q2_K.gguf`), or offload text encoding to an API. Enable **tiled VAE decode** and the **VRAM management node** to fit within memory.

---

## Workflow Types

- **Text to Video (T2V)** -- Craft a prompt from scratch. Make the character speak by prompting "He/She says ..."
- **Image to Video (I2V)** -- Same as T2V but you provide the initial image and thus the character. The character's lips must be visible if you are requesting dialogue in the prompt.
- **Image + Audio to Video** -- Insert both image and audio as reference. The image must be described and the audio must be transcribed in the prompt. Use the upstream pattern: `"The woman is talking, and she says: ..."` followed by `"Perfect lip-sync to the attached audio."`

## Keyframe Variants

For every workflow that uses images, there are three keyframe variants:

| Variant | Abbreviation | Description |
|---------|-------------|-------------|
| First Frame | FF / I2V | Only the first frame as reference |
| First + Last Frame | FL / FL2V | First and last frame as reference, model interpolates between them |
| First + Middle + Last Frame | FML / FML2V | Three keyframes as reference, giving the model the most guidance |

## Upscaling

LTX 2.3 uses a **dual-pass architecture** where the second pass performs spatio-temporal upscaling. The LTX 2.0 version had significant artifacts in the second pass, but 2.3 has fixed these issues -- **always run two-pass** for best results.

**Single pass trade-off** -- single pass produces lower resolution output but can make characters look more realistic. Useful for quick previews or when VRAM is limited.

**Post-generation upscaling:**

| Upscaler | Description |
|----------|-------------|
| **FlashVSR** (recommended) | Fast video super-resolution. vMonad MediaGen `flashvsr_v2v_upscale` |
| **ClearRealityV1** | 4x super-resolution upscaler. vMonad MediaGen `upscale_v2v` |
| **Frame Interpolation** | RIFE-based frame interpolation for smoother motion. vMonad MediaGen `frame_interpolation_v2v` |

## Prompting Tips

- **Frame continuity** -- keyframes must have visual continuity (same person, same setting). Totally unrelated frames will render as a jump cut.
- **Vision tools are essential** -- with frames, audio, and keyframes you cannot get the prompt correct without vision analysis. The prompt must specifically describe everything in the images, the speech timing, and SRT.
- **Voiceover vs. live dialogue** -- getting prompts wrong typically results in voiceover-like output instead of live dialogue. Two fixes: *shorten the prompt and focus on describing the speech action*, or *use the dynamism LoRA at strength 0.3-0.6* (higher strength gives a hypertrophied muscular look).
- **Face-forward keyframes** -- all frames should have the subject facing the camera with clear facial features to prevent AI face hallucination.
- **No object injection** -- nothing should appear in prompts that isn't already visible in the keyframes (prevents scene drift).
- **Derive frames from each other** -- middle derived from first, last derived from middle using image editing (e.g. qwen_image_edit) to maintain consistency.

---

## Model Downloads

The workflows are based on the extracted models from https://huggingface.co/Kijai/LTX2.3_comfy
The extracted models might run easier on your computer (as separate files).
(but you can easily swap out the model loader for the ComfyUI default model loader if you want to load the checkpoint with "all in one" vae built-in etc)

**LTX-2.3 Main Model Downloads (split models):**
- Main split models used in these workflows (LTX-2.3 dev & distilled safetensor, embeddings, audio & video vae & tiny vae):
https://huggingface.co/Kijai/LTX2.3_comfy

**Gemma - either safetensor or GGUF:**
1. Gemma 3 12B it safetensor: https://huggingface.co/Comfy-Org/ltx-2/tree/main/split_files/text_encoders
2. Gemma 3 12B it GGUF: https://huggingface.co/unsloth/gemma-3-12b-it-GGUF/

**Upscale Model:**
1. ltx-2.3-spatial-upscaler (only need the 2x file): https://huggingface.co/Lightricks/LTX-2.3/tree/main

**LTX-2.3 GGUF models (for GGUF workflows)** - one of the sources below:
1. Quantstack: https://huggingface.co/QuantStack/LTX-2.3-GGUF
2. Unsloth: https://huggingface.co/unsloth/LTX-2.3-GGUF
3. Vantage: https://huggingface.co/vantagewithai/LTX-2.3-GGUF

**Tiny Vae by madebyollin (for sampler previews):**
Optional/Recommended. Without this vae you still get previews with latentrgb from KJnodes, at a lower res.

If you are unsure where to put the files see [here](https://huggingface.co/RuneXX/LTX-2.3-Workflows/discussions/10).

---

## Required Nodes

- https://github.com/kijai/ComfyUI-KJNodes (must be up to date for LTX-2 support)
- https://github.com/city96/ComfyUI-GGUF (must be up to date for LTX-2 support)
- ComfyUI itself must be updated to the latest version

---

## References

- Lightricks LTX-2.3 main repo: https://huggingface.co/Lightricks/LTX-2.3
- Lightricks LTX-2.3 Collection (LoRAs etc): https://huggingface.co/collections/Lightricks/ltx-23
- ComfyUI Official Workflows: https://blog.comfy.org/p/ltx-23-day-0-supporte-in-comfyui
- LTX-2 Video Official Workflows: https://github.com/Lightricks/ComfyUI-LTXVideo/tree/master/example_workflows/2.3
