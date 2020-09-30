# TorchImageNet
ImageNet downloader and PyTorch Dataset implementation in PyTorch.

**Requirements:** Please see `requirements.yml` for details.
To install new environment called `imagenet`, run the following command:

```bash 
> conda env create -f requirements.yml
```

## Download imagenet data
Downloading imagenet samples works by running the script `download_imagenet_images.py [num_images]`. It will download the number of images specified by first downloading image urls from the [ImageNet API](http://www.image-net.org/api/text/imagenet.synset.geturls.getmapping?wnid=[wnid]), then randomly shuffeling all the urls, and finally downloading from these urls until `[num_images]` were successfully downloaded.

```bash 
> python download_imagenet_images.py 100
```
Will download 100 images to a subdirectory with the name `images`.

It takes quite a while... so let it run over night `;-)`.

## Use Data Set
To use the dataset, add the parent directory of the project to the `sys.path` list.
For example, if you cloned this repo into `/foo/bar`, i.e., this repo is located 
at `/foo/bar/torch_imagenet`, then `/foo/bar` should be in your path:

```python 
import sys
sys.append('/foo/bar')
```

Afterwards, you can import the `ImageNetDataset` as follows:

```python
from torch_imagenet import ImageNetDataset
```

Note that some of the downloaded images may be gray scale and thus only have
one channel. In such cases, the dataset may get some hickups. To fix this,
you can run 

```bash
> python identify_bad_images.py
```

This script will generate a pickle file with all the filenames of images that 
does not have exactly three channels. The `ImageNetDataset` will automatically 
pick up the file next time the dataset is used.


