# TorchImageNet
Simple ImageNet downloader and PyTorch Dataset implementation for use in deep learning.

**Requirements:** Please see `requirements.yml` for details.

## Download imagenet data
Downloading imagenet samples works by running the script `download_imagenet_images.py [num_images]`. It will download the number of images specified by first downloading image urls from the [ImageNet API](http://www.image-net.org/api/text/imagenet.synset.geturls.getmapping?wnid=[wnid]), then randomly shuffeling all the urls, and finally downloading from these urls until `[num_images]` were successfully downloaded.

```bash 
> python download_imagenet_images.py 100
```
Will download 100 images to a subdirectory with the name `images`.

It takes quite a while...




