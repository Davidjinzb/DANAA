# Implementation of DANAA: Double Adversarial Neuron Attribution for Transferable Attacks

This repository contains the official implementation code for the research paper [DANAA: Towards Transferable Attacks with Double Adversarial Neuron Attribution](https://link.springer.com/chapter/10.1007/978-3-031-46664-9_31). The DANAA framework is designed to generate adversarial examples with enhanced transferability by leveraging the concept of double adversarial neuron attribution.

## Prerequisites

The implementation requires the following software and libraries:

- Python 3.6.13
- Keras 2.2.4
- NumPy 1.16.2
- TensorFlow 1.14.0
- TQDM 4.63.1
- Pillow 6.0.0
- SciPy 1.2.1

## Pre-trained Models

For the experiments, pre-trained models are employed. The following table lists the required models along with their download links:

Model  | Source
------------- | -------------
Inception v3  | [Download](http://download.tensorflow.org/models/inception_v3_2016_08_28.tar.gz)
Inception v4| [Download](http://download.tensorflow.org/models/inception_v4_2016_09_09.tar.gz)
Inception-ResNet-v2  | [Download](http://download.tensorflow.org/models/inception_resnet_v2_2016_08_30.tar.gz)
ResNet v2 152  | [Download](http://download.tensorflow.org/models/resnet_v2_152_2017_04_14.tar.gz)
Inception v3 adv | [Download](http://download.tensorflow.org/models/adv_inception_v3_2017_08_18.tar.gz)
Inception ResNet v2 adv  | [Download](http://download.tensorflow.org/models/adv_inception_resnet_v2_2017_12_18.tar.gz)
Inception v3 adv ens3  | [Download](http://download.tensorflow.org/models/ens3_adv_inception_v3_2017_08_18.tar.gz)
Inception v3 adv ens4  | [Download](http://download.tensorflow.org/models/ens4_adv_inception_v3_2017_08_18.tar.gz)
Inception ResNet v2 adv ens3  | [Download](http://download.tensorflow.org/models/ens_adv_inception_resnet_v2_2017_08_18.tar.gz)|


The non-adversarial models are sourced from [TensorFlow's Slim Model Library](https://github.com/tensorflow/models/tree/master/research/slim), while the adversarially trained models can be found in the [Adversarial ImageNet Models Repository](https://github.com/tensorflow/models/tree/archive/research/adv_imagenet_models). Download and place these models in the `models` directory within the repository.

## Execution Instructions

### Running DANAA Attacks

To execute the DANAA attack method, use the following command format, adjusting parameters as necessary for the desired model and settings:

```bash
python DANAA.py --model_name <model> --attack_method DANAA --layer_name <layer> --ens 30 --output_dir ./outputs/DANAA/ --scale 0.25
```

For instance, to run DANAA on the Inception V3 model, the command would be:

```bash
python DANAA.py --model_name inception_v3 --attack_method DANAA --layer_name InceptionV3/InceptionV3/Mixed_5b/concat --ens 30 --output_dir ./outputs/DANAA/ --scale 0.25
```

### Additional Attack Methods

The framework also supports comparison with other attack methodologies such as NAA, MIM, NRDM, FIA, and FDA. To execute these, simply replace the `--attack_method` parameter with the desired attack type.

### Verification

To verify the effectiveness of the generated adversarial examples, use the `verify.py` script as follows:

```bash
python verify.py --ori_path ./dataset/images/ --output_dir ./outputs/DANAA/
```

## Citing DANAA

For academic use, please cite the following paper. 

```
@inproceedings{jin2023danaa,
  title={DANAA: Towards transferable attacks with double adversarial neuron attribution},
  author={Jin, Zhibo and Zhu, Zhiyu and Wang, Xinyi and Zhang, Jiayu and Shen, Jun and Chen, Huaming},
  booktitle={International Conference on Advanced Data Mining and Applications},
  pages={456--470},
  year={2023},
  organization={Springer}
}
```

## Refenece
Code refer to: [NAA](https://github.com/jpzhang1810/NAA).

