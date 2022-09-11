# ImaginAIry 🤖🧠

AI imagined images.

Tested on Linux and OSX(M1).

```bash
>> pip install imaginairy
>> imagine "a scenic landscape" "a photo of a dog" "photo of a fruit bowl" "portrait photo of a freckled woman"
🤖🧠 received 4 prompt(s) and will repeat them 1 times to create 4 images.
Loading model onto mps backend...
Generating 🖼  : "a scenic landscape" 512x512px seed:557988237 prompt-strength:7.5 steps:40 sampler-type:PLMS
    PLMS Sampler: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 40/40 [00:29<00:00,  1.36it/s]
    🖼  saved to: ./outputs/000001_557988237_PLMS40_PS7.5_a_scenic_landscape.jpg
Generating 🖼  : "a photo of a dog" 512x512px seed:277230171 prompt-strength:7.5 steps:40 sampler-type:PLMS
    PLMS Sampler: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 40/40 [00:28<00:00,  1.41it/s]
    🖼  saved to: ./outputs/000002_277230171_PLMS40_PS7.5_a_photo_of_a_dog.jpg
Generating 🖼  : "photo of a fruit bowl" 512x512px seed:639753980 prompt-strength:7.5 steps:40 sampler-type:PLMS
    PLMS Sampler: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 40/40 [00:28<00:00,  1.40it/s]
    🖼  saved to: ./outputs/000003_639753980_PLMS40_PS7.5_photo_of_a_fruit_bowl.jpg
Generating 🖼  : "portrait photo of a freckled woman" 512x512px seed:500686645 prompt-strength:7.5 steps:40 sampler-type:PLMS
    PLMS Sampler: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 40/40 [00:29<00:00,  1.37it/s]
    🖼  saved to: ./outputs/000004_500686645_PLMS40_PS7.5_portrait_photo_of_a_freckled_woman.jpg
```
<img src="assets/000019_786355545_PLMS50_PS7.5_a_scenic_landscape.jpg" width="256" height="256">
<img src="assets/000032_337692011_PLMS40_PS7.5_a_photo_of_a_dog.jpg" width="256" height="256">
<img src="assets/000056_293284644_PLMS40_PS7.5_photo_of_a_bowl_of_fruit.jpg" width="256" height="256">
<img src="assets/000078_260972468_PLMS40_PS7.5_portrait_photo_of_a_freckled_woman.jpg" width="256" height="256">

# Features
 
 - It makes images from text descriptions!
 - Generate images either in code or from command line.
 - It just works (if you have the right hardware... and aren't on windows)
 - Noisy logs are gone (which was surprisingly hard to accomplish)
 - WeightedPrompts let you smash together separate prompts ()

# How To

```python
from imaginairy import imagine_images, imagine_image_files, ImaginePrompt, WeightedPrompt

prompts = [
    ImaginePrompt("a scenic landscape", seed=1),
    ImaginePrompt("a bowl of fruit"),
    ImaginePrompt([
       WeightedPrompt("cat", weight=1),
       WeightedPrompt("dog", weight=1),
    ])
]
for result in imagine_images(prompts):
    # do something
    result.save("my_image.jpg")
    
# or

imagine_image_files(prompts, outdir="./my-art")

```

# Requirements

- Computer with CUDA supported graphics card. ~10 gb video ram
OR
- Apple M1 computer

# Improvements from CompVis
 - img2img actually does # of steps you specify

# Models Used
 - CLIP
 - LDM - Latent Diffusion
 - Stable Diffusion 
   - https://github.com/CompVis/stable-diffusion
   - https://huggingface.co/CompVis/stable-diffusion-v1-4

# Todo
 - add docs
 - deploy to pypi
 - add tests
 - set up ci (test/lint/format)
 - notify https://github.com/CompVis/stable-diffusion/issues/25
 - remove yaml config
 - performance optimizations https://github.com/huggingface/diffusers/blob/main/docs/source/optimization/fp16.mdx 
 - Interface improvements
   - init-image at command line
   - prompt expansion?
   - webserver interface (low priority, this is a library)
 - Image Generation Features
   - upscaling
   - face improvements
   - image describe feature
   - outpainting
   - inpainting
   - cross-attention control: 
     - https://github.com/bloc97/CrossAttentionControl/blob/main/CrossAttention_Release_NoImages.ipynb
   - tiling
   - output show-work videos
   - image variations https://github.com/lstein/stable-diffusion/blob/main/VARIATIONS.md
   - zooming videos? a la disco diffusion

 