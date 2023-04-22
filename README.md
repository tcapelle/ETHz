# ETHz
Welcome to the ETH Zurich Hackathon 2023, this repository contains the code and instructions for the hackathon.

## Getting Started
- Clone this repository
- Choose a Machine with PyTorch preinstalled on JarvisLabs.
- Install the requirements: `pip install -r requirements.txt`
> You will need master dev version of diffusers (we are doing bleeding edge stuff here 🤣)

```bash
git clone https://github.com/huggingface/diffusers
cd diffusers
pip install -e .
```

## Creating a Dataset
To construct a dataset you will need to download images form the internet. 
Consider using a scraper like: 
- https://github.com/sALTaccount/SeaSalt-Downloader or https://github.com/Bionus/imgbrd-grabber.
- Filter low quality images using a tool or by hand.
- Put them all in a folder with no spaces in the name of the folder and no extra folders inside. Make sure your image folder only has the images and the text files.
- you have to decide if you want to tag the images or not: There are tools out there that can help you with that like: https://github.com/toriato/stable-diffusion-webui-wd14-tagger

## LoRA
We will mainly be using this: https://huggingface.co/blog/lora
You have two options to train your LoRA:
### Pure LoRA:
Using LoRA's training script, you will need an annotated dataset for that. LoRA is fast but requires you to annotate a dataset.
- Dataset: You will need a dataset that looks like this: https://huggingface.co/datasets/lambdalabs/pokemon-blip-captions, you can create one locally or use a dataset from the hub. You can check what the script expects here: https://huggingface.co/docs/datasets/image_dataset#imagefolder

The training script is in this repo, and it's just a modified version of the one in the blog post.
You can define the variables as environment variables or pass them as arguments to the script.

```bash
accelerate launch train_text_to_image_lora.py
```

- The other one is using Dreambooth-Lora, you will need a dataset of images without tags for that. The quality here is not as good as the one from the training script, but it's much faster to train.
The training script is in this repo, and it's just a modified version of the one in the blog post.

```bash
accelerate launch train_dreambooth_lora.py
```

> I changed some defaults and added a few more options to the script, you can see them by running `python train_lora.py --help`

## Models
There are multiple models trained on Anime/Cartoon/drawings out there,  this is a good model to start from
- [Waifu Diffusion](https://huggingface.co/hakurei/waifu-diffusion)
- I also like the `runwayml/stable-diffusion-v1-5` model, but it is not as good as the one above as it's trained on more artisitc images instead of anime/cartoon/drawings.

## Resources
- This blog has a bunch of info on how to train your Lora: https://rentry.org/lora_train
- Another sketchy blog post: https://rentry.org/59xed3
- Another model that looks good but has bad documentation: https://huggingface.co/NoCrypt/SomethingV2 
- A list of somewhat good Hyperparams: https://huggingface.co/khanon/lora-training/blob/main/junko/lora_chara_junko_v1c_131i9r-9i6r.json
- A blogpost by Cloneofsimo himself: https://replicate.com/blog/lora-faster-fine-tuning-of-stable-diffusion
- Dreambooth article: https://huggingface.co/blog/dreambooth