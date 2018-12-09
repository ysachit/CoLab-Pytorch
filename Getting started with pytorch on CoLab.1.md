# Getting started with Pytorch in CoLab

If you want to use CoLab GPU then you have to enable manually. 
Want to know how, check here : https://github.com/ysachit/CoLab-Pytorch/blob/master/Enable%20GPU%20on%20CoLab.md

## Install Pytorch on CoLab

Colab does not come with Pytorch pre loaded. So you have to install it.

    # http://pytorch.org/
    from os.path import exists
    from wheel.pep425tags import get_abbr_impl, get_impl_ver, get_abi_tag
    platform = '{}{}-{}'.format(get_abbr_impl(),get_impl_ver(), get_abi_tag())
    cuda_output = !ldconfig -p|grep cudart.so|sed -e 's/.*\.\([0-9]*\)\.\([0-9]*\)$/cu\1\2/'
    accelerator = cuda_output[0] if exists('/dev/nvidia0') else 'cpu'
    !pip install -q http://download.pytorch.org/whl/{accelerator}/torch-0.4.1-{platform}-linux_x86_64.whl torchvision
    import torch
 
 ### Happy Coding. :)
