# Getting started with Pytorch in CoLab

If you want to use CoLab GPU then you have to enable manually. 
Want to know how, check here : https://github.com/ysachit/CoLab-Pytorch/blob/master/Enable%20GPU%20on%20CoLab.md

## ModuleNotFoundError: No module named 'helper'

Helper module is custom module made by udacity. Is only contain 2-3 method like displaying a image etc. Either you can directly copy-paste the code or upload the helper file on colab.


1. Copy - Paste following code
    
        import matplotlib.pyplot as plt
        import numpy as np
        from torch import nn, optim
        from torch.autograd import Variable
        def imshow(image, ax=None, title=None, normalize=True):
        """Imshow for Tensor."""
        if ax is None:
            fig, ax = plt.subplots()
        image = image.numpy().transpose((1, 2, 0))
        if normalize:
            mean = np.array([0.485, 0.456, 0.406])
            std = np.array([0.229, 0.224, 0.225])
            image = std * image + mean
            image = np.clip(image, 0, 1)
    
        ax.imshow(image)
        ax.spines['top'].set_visible(False)
        ax.spines['right'].set_visible(False)
        ax.spines['left'].set_visible(False)
        ax.spines['bottom'].set_visible(False)
        ax.tick_params(axis='both', length=0)
        ax.set_xticklabels('')
        ax.set_yticklabels('')
    
        return ax
    
    
        def view_classify(img, ps, version="MNIST"):
        ''' Function for viewing an image and it's predicted classes.
        '''
        ps = ps.data.numpy().squeeze()
    
        fig, (ax1, ax2) = plt.subplots(figsize=(6,9), ncols=2)
        ax1.imshow(img.resize_(1, 28, 28).numpy().squeeze())
        ax1.axis('off')
        ax2.barh(np.arange(10), ps)
        ax2.set_aspect(0.1)
        ax2.set_yticks(np.arange(10))
        if version == "MNIST":
            ax2.set_yticklabels(np.arange(10))
        elif version == "Fashion":
            ax2.set_yticklabels(['T-shirt/top',
                                'Trouser',
                                'Pullover',
                                'Dress',
                                'Coat',
                                'Sandal',
                                'Shirt',
                                'Sneaker',
                                'Bag',
                                'Ankle Boot'], size='small');
        ax2.set_title('Class Probability')
        ax2.set_xlim(0, 1.1)
    
        plt.tight_layout()

 
 ## AttributeError: module 'PIL.Image' has no attribute 'register_extensions'

    # workaround 
    from PIL import Image
    def register_extension(id, extension): Image.EXTENSION[extension.lower()] = id.upper()
    Image.register_extension = register_extension
    def register_extensions(id, extensions): 
      for extension in extensions: register_extension(id, extension)
    Image.register_extensions = register_extensions
 
 ### Happy Coding. :)
