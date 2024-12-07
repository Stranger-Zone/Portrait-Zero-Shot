---
tags:
- text-to-image
- lora
- diffusers
- template:diffusion-lora
widget:
- text: 'Super Portrait, A close-up portrait of a young man with dark brown eyes and dark brown eyebrows. He is wearing a green and yellow striped polo shirt with a black collar. His earring is adorned with a silver earring. The backdrop is a light blue color.'
  output:
    url: images/1.png
- text: 'Super Portrait, A close-up shot of a young blonde girl with blue eyes and a black beanie on her head. The beanie is adorned with a pink patch that reads "CUTIE REBEL" in bold white letters. The girls hair is pulled back in a ponytail and she is wearing a black turtleneck. The background is a vibrant brown color.'
  output:
    url: images/2.png
- text: 'Super Portrait, a close-up shot of a young mans face is adorned with a beige baseball cap adorned with red lettering. The mans eyes are a piercing blue, and he is wearing a pink t-shirt. His hair is dark brown, adding a touch of texture to his face. The backdrop is a vibrant shade of blue, creating a stark contrast to the mans head and the cap.'
  output:
    url: images/3.png
- text: 'Super Portrait, a close-up shot of a young girls face is featured prominently in the frame. The girls eyes are a piercing blue, and her hair is pulled back in a ponytail, adding a pop of color to her face. She is wearing a gray baseball cap, adorned with a white logo that reads "E-NILS" in a cursive font, while the rest of the text is in a darker shade of white. Her eyebrows are a lighter shade of blue, while her lips are a darker pink. She is wearing a long-sleeved gray sweater, with a slight smile on her lips. The backdrop is a vibrant orange, creating a stark contrast to the girls outfit.'
  output:
    url: images/4.png
- text: 'Super Portrait, A close-up of a young girl with almond-shaped hazel eyes and long jet-black hair tied in twin braids. She wears a bright red turtleneck sweater and a pair of small silver hoop earrings. The background is a soft peach, highlighting her vibrant outfit.'
  output:
    url: images/5.png
- text: 'Super Portrait, A close-up of a young man with dark brown eyes and wavy black hair. He is wearing a dark green trench coat with a high collar and a light brown scarf around his neck. The backdrop is a cloudy gray, adding an air of mystery to the scene.'
  output:
    url: images/6.png
base_model: black-forest-labs/FLUX.1-dev
instance_prompt: Super Portrait
license: creativeml-openrail-m
---
![CC1.png](https://cdn-uploads.huggingface.co/production/uploads/65bb837dbfb878f46c77de4c/OQkdEnSefpRhliGZ4VdlB.png)

<Gallery />

# Model description for Flux-Super-Portrait-LoRA

Image Processing Parameters 

| Parameter                 | Value  | Parameter                 | Value  |
|---------------------------|--------|---------------------------|--------|
| LR Scheduler              | constant | Noise Offset              | 0.03   |
| Optimizer                 | AdamW  | Multires Noise Discount   | 0.1    |
| Network Dim               | 64     | Multires Noise Iterations | 10     |
| Network Alpha             | 32     | Repeat & Steps           | 17 & 2650 |
| Epoch                     | 14   | Save Every N Epochs       | 1     |

    Labeling: florence2-en(natural language & English)
    
    Total Images Used for Training : 19 [ Flat 4K ]

## Best Dimensions & Inference

| **Dimensions** | **Aspect Ratio** | **Recommendation**       |
|-----------------|------------------|---------------------------|
| 1280 x 832      | 3:2              | Best                     |
| 1024 x 1024     | 1:1              | Default                  |

### Inference Range

- **Recommended Inference Steps:** 30–35

## Setting Up
```python
import torch
from pipelines import DiffusionPipeline

base_model = "black-forest-labs/FLUX.1-dev"
pipe = DiffusionPipeline.from_pretrained(base_model, torch_dtype=torch.bfloat16)

lora_repo = "strangerzonehf/Flux-Super-Portrait-LoRA"
trigger_word = "Super Portrait"  
pipe.load_lora_weights(lora_repo)

device = torch.device("cuda")
pipe.to(device)
```
## Trigger words

You should use `Super Portrait` to trigger the image generation.

## Download model

Weights for this model are available in Safetensors format.

[Download](/strangerzonehf/Flux-Super-Portrait-LoRA/tree/main) them in the Files & versions tab.
