# Photorealistic Image Pipeline

A project to generate photorealistic images from text prompts using diffusion models and super-resolution techniques. Designed for experimentation with text-to-image pipelines under resource constraints, focusing on photorealism, prompt steerability, and GPU memory efficiency.

## Features

- Text-to-image generation using diffusion models
- Upscaling to 2048x2048 resolution with EDSR
- Fully automated pipeline implemented in Python
- Experimentation with multiple diffusion models to find the optimal trade-off between quality and resource usage

## Models Used

- `stabilityai/sdxl-turbo` (final implementation)
- `CompVis/stable-diffusion-v1-4`
- `stable-diffusion-v1-5`
- `stabilityai/stable-diffusion-2-1`

## Key Challenges

1. **Hardware Constraints**
   - Limited to 16GB GPU RAM, restricting usage of advanced diffusion models

2. **Platform-Specific Issues**
   - Resolved import errors in `diffusers.utils.dynamic_modules_utils.py` on Google Colab
   - Faced compatibility issues with `diffusers` on LightningGPT and Kaggle Notebook

3. **Upscaling Module**
   - Challenges with `cv2.dnn_superres` module in Google Colab resolved through debugging

## Getting Started

### Prerequisites

- Python 3.10
- Google Colab or equivalent setup with GPU support
- Libraries:
  - `torch`
  - `diffusers`
  - `opencv-python`
  - `Pillow`

## Usage

1. **Run the Google Colab Notebook**
   - Open and run the `notebook.ipynb` file in Google Colab

2. **Generate an Image**
   - Update the `prompt_input` variable in the notebook with your desired text prompt.

3. **Upscale the Image**
   - The pipeline automatically upscales the generated image to 2048x2048 using EDSR

4. **Save the Result**
   - The final image is saved as `upscaled_image_2048x2048.png`

## Limitations

- Limited GPU RAM constrained usage of newer models like SDXL 1.0+
- Prompt steerability is restricted due to reliance on older models
- Upscaling adds sharpness but may not fully compensate for input image quality

## Future Work

- Experiment with GPUs >24GB for advanced models
- Explore GAN-based super-resolution techniques like ESRGAN
- Fine-tune models for improved photorealism and prompt alignment