# IMLAA

This Github repository is the IMLAA implementation code

# Requirements
- python 3.6.13
- keras 2.2.4
- numpy 1.16.2
- tensorflow 1.14.0
- tqdm 4.63.1
- pillow 6.0.0
- scipy 1.2.1

# Setup
Model  | Download Link
------------- | -------------
Inception V3  | [inception_v3_2016_08_28.tar.gz](http://download.tensorflow.org/models/inception_v3_2016_08_28.tar.gz)
Inception V4| [inception_v4_2016_09_09.tar.gz](http://download.tensorflow.org/models/inception_v4_2016_09_09.tar.gz)
Inception-ResNet-v2  | [inception_resnet_v2_2016_08_30.tar.gz](http://download.tensorflow.org/models/inception_resnet_v2_2016_08_30.tar.gz)
ResNet V2 152  | [resnet_v2_152_2017_04_14.tar.gz](http://download.tensorflow.org/models/resnet_v2_152_2017_04_14.tar.gz)
Inception v3 adv | [adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/adv_inception_v3_2017_08_18.tar.gz)
Inception ResNet v2 adv  | [adv_inception_resnet_v2_2017_12_18.tar.gz](http://download.tensorflow.org/models/adv_inception_resnet_v2_2017_12_18.tar.gz)
Inception v3 adv ens3  | [ens3_adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens3_adv_inception_v3_2017_08_18.tar.gz)
Inception v3 adv ens4  | [ens4_adv_inception_v3_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens4_adv_inception_v3_2017_08_18.tar.gz)
Inception ResNet v2 adv ens3  | [ens_adv_inception_resnet_v2_2017_08_18.tar.gz](http://download.tensorflow.org/models/ens_adv_inception_resnet_v2_2017_08_18.tar.gz)


The models in the table above without adversarial training are from [here](https://github.com/tensorflow/models/tree/master/research/slim); all models with adversarial training are from [here](https://github.com/) tensorflow/models/tree/archive/research/adv_imagenet_models). These models need to be downloaded and placed under the `models` dir.

# Run
- IMLAA

`python IMLAA.py --model_name inception_v3 --attack_method IMLAA --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --ens 30 --output_dir ./outputs/IMLAA/ --scale 0.25`

`python IMLAA.py --model_name inception_v4 --attack_method IMLAA --layer_name InceptionV4/InceptionV4/Mixed_5e/concat --ens 30 --output_dir ./outputs/IMLAA/ --scale 0.25`

`python IMLAA.py --model_name inception_resnet_v2 --attack_method IMLAA --layer_name InceptionResnetV2/InceptionResnetV2/Conv2d_4a_3x3/Relu --ens 30 --output_dir ./outputs/IMLAA/ --scale 0.25`

`python IMLAA.py --model_name resnet_v2_152 --attack_method IMLAA --layer_name resnet_v2_152/block2/unit_8/bottleneck_v2/add --ens 30 --output_dir ./ouputs/IMLAA/ --scale 0.25`

- IMLAA-PIDI

`python IMLAA.py --model_name inception_v3 --attack_method IMLAAPIDI --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --ens 30 --output_dir ./outputs/IMLAA/ --scale 0.25`

- NAA

`python NAA.py --model_name inception_v3 --attack_method NAA --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --ens 30 --output_dir ./outputs/NAA/`

- MIM

`python attacks.py --model_name inception_v3 --attack_method MIM --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --output_dir ./adv/NAA/`

To run other comparison exps such as `NRDM`, `FIA`, `FDA`, simply replace the `--attack_method` parameter.

- verify

`python verify.py --ori_path ./dataset/images/ --output_dir ./outputs/IMLAA/`

# Reference
Code refer to: [NAA](https://github.com/jpzhang1810/NAA)
