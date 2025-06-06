# ComfyUI-FramePackWrapper_PlusOne

**[日本語](./README.ja.md)**

[ComfyUI-FramePackWrapper_PlusOne](https://github.com/tori29umai0123/ComfyUI-FramePackWrapper_PlusOne) is a fork derived from [ComfyUI-FramePackWrapper](https://github.com/kijai/ComfyUI-FramePackWrapper) and [ComfyUI-FramePackWrapper_Plus](https://github.com/ShmuelRonen/ComfyUI-FramePackWrapper_Plus), containing FramePack's single-frame inference node (with kisekaeichi support).

This repository was forked for public release at the request of @tori29umai0123 [as requested here](https://x.com/tori29umai/status/1928692381735432320).

## Features

- **1-Frame Inference**: Supports basic single frame inference and the kisekaeichi method. For technical details, please refer to the [musubi-tuner documentation](https://github.com/kohya-ss/musubi-tuner/blob/main/docs/framepack_1f.md).
- **F1 Sampler Support**: Uses the improved F1 video generation method for higher quality and better temporal coherence
- **LoRA Integration**: Full support for HunyuanVideo LoRAs with proper weight handling and fusion options
- **Timestamped Prompts**: Create dynamic videos with changing prompts at specific timestamps
- **Flexible Input Options**: Works with both reference images and empty latents for complete creative control
- **Resolution Control**: Automatic bucket finding for optimal video dimensions
- **Blend Control**: Smooth transitions between different prompts at timestamps

### Not yet supported

- 1-Frame Inference: f-mc (one frame multi-control) is not supported yet.

## Installation

1. Clone this repository into your ComfyUI custom_nodes folder:
```bash
cd ComfyUI/custom_nodes
git clone https://github.com/xhiroga/ComfyUI-FramePackWrapper_PlusOne.git
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Download the necessary model files and place them in your models folder:
- FramePackI2V_HY: [HuggingFace Link](https://huggingface.co/lllyasviel/FramePackI2V_HY)
- FramePack_F1_I2V_HY: [HuggingFace Link](https://huggingface.co/lllyasviel/FramePack_F1_I2V_HY_20250503)

## Model Files

### Main Model Options
- [FramePackI2V_HY_fp8_e4m3fn.safetensors](https://huggingface.co/Kijai/HunyuanVideo_comfy/blob/main/FramePackI2V_HY_fp8_e4m3fn.safetensors) - Optimized fp8 version (smaller file size)
- [FramePackI2V_HY_bf16.safetensors](https://huggingface.co/Kijai/HunyuanVideo_comfy/blob/main/FramePackI2V_HY_bf16.safetensors) - BF16 version (better quality)

### Required Components
- **CLIP Vision**: [sigclip_vision_384](https://huggingface.co/Comfy-Org/sigclip_vision_384/tree/main)
- **Text Encoder and VAE**: [HunyuanVideo_repackaged](https://huggingface.co/Comfy-Org/HunyuanVideo_repackaged/tree/main/split_files)

## Usage

See [example_workflows](./example_workflows).

| [1-Frame](./example_workflows/Oneframe.json) / [LoRA @tori29umai](https://huggingface.co/tori29umai/FramePack_LoRA/blob/main/Apose_V7_dim4.safetensors) | [1-Frame](./example_workflows/Oneframe.json) / [LoRA @kohya-ss](https://huggingface.co/kohya-ss/misc-models/blob/main/fp-1f-chibi-1024.safetensors) | [Kisekaeichi](./example_workflows/Oneframe_kisekaeichi.json) / [LoRA @tori29umai](https://huggingface.co/tori29umai/FramePack_LoRA/blob/main/body2img_V7_kisekaeichi_dim4_1e-3_512_768-000140.safetensors) |
| --- | --- | --- |
| ![kisekaeichi](./images/basic-apose.png) | ![chibi](./images/basic-chibi.png) | ![body2img](./images/kisekaeichi-body2img.png) |

## License

[MIT License](LICENSE)

## Credits

- [FramePack](https://github.com/lllyasviel/FramePack): @lllyasviel's original implementation.
- [ComfyUI-FramePackWrapper](https://github.com/kijai/ComfyUI-FramePackWrapper): @kijai's original implementation.
- [ComfyUI-FramePackWrapper_Plus](https://github.com/ShmuelRonen/ComfyUI-FramePackWrapper_Plus): @ShmuelRonen's F1-supported fork.
- [ComfyUI-FramePackWrapper_PlusOne](https://github.com/tori29umai0123/ComfyUI-FramePackWrapper_PlusOne): @tori29umai0123's 1-frame inference-supported fork.
