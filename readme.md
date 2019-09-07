The ipython notebook contains code for salt identidfication in images. 
It was a Kaggle competition hosted by TGS (geoscience data company) whose aim is to build an algorithmthat automatically 
and accurately identifies if a subsurface target is salt or not 

Main approach: The approach was to use a pretrained resnet34 model and then build a unet on top of it. 
● Adam optimizer with weight decay. 
● Progressive resizing of train/val image sizes from 128x128, and then finally to 256x256. 
● One-cycle training with momentum. This technique was extremely useful 
● Use of hypercoluns without dropout:( https://arxiv.org/pdf/1411.5752.pdf.) 

The loss function I used was .binary cross entropy with logits. Here are my climb up steps: Training: 
● RandomFlip augmentation 
● Batch sizes: 64, 128, 256 with cycle length = 30 
● cyclical learning rate = 0.01 
● Weight decay = 0.0001 
● Test time augmentation with horizontal flip 

