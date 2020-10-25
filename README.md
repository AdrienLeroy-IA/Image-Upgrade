# What is this repo ?

This repository is a Keras implementation of [Deblur GAN](https://arxiv.org/pdf/1711.07064.pdf). Based on the work of Raphael Meudec (https://github.com/RaphaelMeudec). You can find a tutorial on how it works on [Medium](https://blog.sicara.com/keras-generative-adversarial-networks-image-deblurring-45e3ab6977b5). Below is a sample result (from left to right: blurred image, deblurred image)

![Sample results](./sample/results.png)

# Installation Linux

```
virtualenv venv -p python3
. venv/bin/activate
pip install -r requirements/requirements.txt
pip install -e .
```

# Installation Windows

```
py -3 -m venv .venv
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
.venv\scripts\activate
pip install -r requirements/requirements.txt
pip install -e .
```


# Dataset

Get the [GOPRO dataset](https://drive.google.com/file/d/1H0PIXvJH4c40pk7ou6nAwoxuR4Qh_Sa2/view?usp=sharing), and extract it in the `deblur-gan` directory. The directory name should be `GOPRO_Large`.

Use:
```
python scripts/organize_gopro_dataset.py --dir_in=GOPRO_Large --dir_out=images
```


# Training

```
python scripts/train.py --n_images=512 --batch_size=16 --log_dir /path/to/log/dir
```

Use `python scripts/train.py --help` for all options

# Testing

```
python scripts/test.py
```

Use `python scripts/test.py --help` for all options

# Deblur your own image

Put the blurred image in images/blurred. The deblurred image will be generated in images/deblureed.

```
python scripts/deblur_image.py --weight_path=generator.h5 --input_dir=images/blurred --output_dir=images/deblurred
```
