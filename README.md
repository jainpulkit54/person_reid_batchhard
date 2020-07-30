# person_reid_batchall

A triplet network takes in three images as input i.e., an anchor image, a positive image (i.e., image having label same as the anchor) and a negative image (i.e., image having label different from the anchor). The objective here is to learn embeddings such that the positive images are closer to the anchor as compared to the negative images. 

The Batch Hard variant of the triplet loss is mathematically expressed as:<br>
<img src = "images/batchhard_loss.png"></img>

Source: <a href = "https://arxiv.org/abs/1703.07737">Alexander Hermans, Lucas Beyer, Bastian Leibe, “In Defense of the Triplet Loss for Person Re-Identification”</a><br>

### Dataset

The dataset on which this model has been trained is <b>Market-1501</b>. Dataset description can be found on <a href = "https://www.aitribune.com/dataset/2018051063">this link</a>. The dataset can be downloaded from the kaggle website.

### Network Architecture and Data Augmentation
The network architecture used is:<br>
<i>Pretrained ResNet-50 > Linear 1024 > BatchNorm > ReLU > Linear 128</i><br>
The dataset is augmented on the go (during training) by using Random Horizontal Flips.<br>

### Tensorboard Visualization

The training logs obtained are as follows:<br>
<b>Batch Hard with Hard Margin:</b><br>
<img src = "images/logs_batchhard_hardmargin.png"></img>
<b>Batch Hard with Soft Margin:</b><br>
<img src = "images/logs_batchhard_softplus.png"></img>

Moreover the training logs can be visualized by following instructions as:<br>
1) Go to the source directory.<br>
2) Type the command:<br>
For Batch Hard with Hard Margin:<br>
<code>$ tensorboard --logdir logs_market1501_batchhard</code><br>
For Batch Hard with Soft Margin:<br>
<code>$ tensorboard --logdir logs_market1501_batchhard_softplus</code><br>
3) Go to a browser and type:<br>
<code>http://localhost:6006/</code>

### Performance Evaluation
The performance evaluation code is taken from <a href = "https://github.com/VisualComputingInstitute/triplet-reid">this repository</a>.<br>
The results are summarized in the table below:<br>

<b>Batch Hard with Hard Margin:</b>
|mAP|top-1|top-2|top-5|top-10|
|---|-----|-----|-----|------|
|41.12%|63.03%|72.89%|82.96%|89.46%|

<b>Batch Hard with Softplus:</b>
|mAP|top-1|top-2|top-5|top-10|
|---|-----|-----|-----|------|
|40.89%|59.62%|70.84%|81.71%|87.35%|

### Weights
The weights obtained using this repository can be downloaded using the following links:<br>
<b>Batch Hard with Hard Margin:</b><br>
https://drive.google.com/file/d/1KF43SrAsX8Hn5xQBtr9TnFddFbfBO5XN/view?usp=sharing<br>
<b>Batch Hard with Softplus:</b><br>
https://drive.google.com/file/d/1NaM4Id31FUdiKgoFoiYr4C42zhk_ngaF/view?usp=sharing
