# ETHz
Welcome to the ETH Zurich Hackathon 2023, this repository contains the code and instructions for the hackathon.

## Getting Started
- Clone this repository
- Choose a Machine with PyTorch preinstalled on JarvisLabs.
- Install the requirements: `pip install -r requirements.txt`
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
- One is using LoRA's training script, you will need an annotated dataset for that.
- The other one is using Dreambooth-Lora, you will need a dataset of images without tags for that. The quality here is not as good as the one from the training script, but it's much faster to train.
The training script is in this repo, and it's just a modified version of the one in the blog post.
> I changed some defaults and added a few more options to the script, you can see them by running `python train_lora.py --help`

## Models
There are multiple models trained on Anime/Cartoon/drawings out there,  this is a good model to start from
- [Waifu Diffusion](https://huggingface.co/hakurei/waifu-diffusion)
- I also like the `runwayml/stable-diffusion-v1-5` model, but it is not as good as the one above as it's trained on more artisitc images instead of anime/cartoon/drawings.

## Resources
- This blog has a bunch of info on how to train your Lora: https://rentry.org/lora_train