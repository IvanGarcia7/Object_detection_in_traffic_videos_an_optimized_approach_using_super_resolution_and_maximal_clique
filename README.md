# Object detection in traffic videos: an optimized approach using super-resolution and maximal clique algorithm

# Optimized object detection in traffic videos by super-resolution and maximal clique generation

In this repository, a new proposal has been developed. Our proposal is based on detecting several initial detections to generate a number of sub-images using super-resolution (SR) techniques, increasing the number of pixels of the elements contained in it, and re-infer using the same pre-trained CNN model. A reduced set of windows is calculated in the super-resolved image by analyzing a graph that describes the distances among the preliminary object detections. This analysis is done by finding maximal cliques in the graph. This way, the number of windows to be examined is diminished, which significantly speeds up the detection process. 
This framework has been successfully tested on real traffic sequences obtained from the U.S. Department of Transportation and VisDrone Dataset.

A demo is provided to run our proposal on the following jupyter notebook:

* https://github.com/IvanGarcia7/OSCOD/blob/main/DEMO.ipynb

Within the jupyter notebook, all the necessary steps are established to initialize the work environment, download the pre-trained super-resolution and object detection models and execute the proposal. 

# Workflow of the proposed technique:

![WORKFLOW](https://github.com/IvanGarcia7/OSCOD/blob/main/images/frameworkp1.jpg?raw=true)

Generation of the graph:

![WORKFLOW2](https://github.com/IvanGarcia7/OSCOD/blob/main/images/frameworkp2.png?raw=true)

# Execution Test:

## Input Image:

After downloading and loading the necessary models, we want to improve the detections on a given image as input, e.g. the Figure below:

![INPUT IMAGE](https://github.com/IvanGarcia7/OSCOD/blob/main/images/ex1-raw.jpg?raw=true)


After performing the successive detections, an output image will be generated. 

## Output:

![OUTPUT IMAGE](https://github.com/IvanGarcia7/OSCOD/blob/main/images/ex1-ours.jpg?raw=true)

Frame 3 of the first video denoted as sb-camera1-0820am-0835am processed by CenterNet HourGlass 104 Kpts with a confidence $>$ 50\%. Optimized proposal applied with $R$ = 50\%.


# Another example applied to the Visdrone dataset:

## RAW Input Image:

![INPUT IMAGE](https://github.com/IvanGarcia7/OSCOD/blob/main/images/ex2-raw.jpg?raw=true)


## OURS:

![OUTPUT IMAGE](https://github.com/IvanGarcia7/OSCOD/blob/main/images/ex2-ours.jpg?raw=true)

Frame 0000001\_05499\_d\_0000010 of the VisDrone dataset processed by EfficientDet D4 with a confidence $>$ 50\%. Optimized proposal applied with $R$ = 50\%.


# Evaluation:

To evaluate the mAP(Mean Average Precision) of the model, a function is included in the notebook to generate a json with the appropriate format. In the following path, we have loaded the annotations of the five video sequences (4 sequences corresponding to the NGSIM Dataset) used in the article.

* https://github.com/IvanGarcia7/NGSIM-Dataset-Annotations


# Docker Image:

A Docker image is included in order to install all the libraries required to run our proposal:

* https://github.com/IvanGarcia7/OSCOD/blob/main/Dockerfile

# Information:

If you use some of the sequences established in this repository or our proposal, don't forget to cite both the original datasets as well as the following articles:

*Previous Proposal:

```
@article{GarcaAguilar2021,
  doi = {10.1111/exsy.12930},
  url = {https://doi.org/10.1111/exsy.12930},
  year = {2021},
  month = dec,
  publisher = {Wiley},
  volume = {39},
  number = {2},
  author = {Iv{\'{a}}n Garc{\'{\i}}a-Aguilar and Rafael Marcos Luque-Baena and Ezequiel L{\'{o}}pez-Rubio},
  title = {Improved detection of small objects in road network sequences using
		            {CNN}
		            and super resolution},
  journal = {Expert Systems}
}
```

*This proposal:

```
@ARTICLE{Garcia-Aguilar2023-yu,
  title     = "Object detection in traffic videos: an optimized approach using
               super-resolution and maximal clique algorithm",
  author    = "Garc{\'\i}a-Aguilar, Iv{\'a}n and Garc{\'\i}a-Gonz{\'a}lez,
               Jorge and Luque-Baena, Rafael Marcos and L{\'o}pez-Rubio,
               Ezequiel",
  abstract  = "AbstractDetection of small objects is one of the main challenges
               to be improved in deep learning, mainly due to the small number
               of pixels and scene's context, leading to a loss in performance.
               In this paper, we present an optimized approach based on deep
               object detection models that allow the detection of a higher
               number of elements and improve the score obtained for their
               class inference. The main advantage of the presented methodology
               is that it is not necessary to modify the internal structure of
               the selected convolutional neural network model or re-training
               for a specific scene. Our proposal is based on detecting initial
               regions to generate several sub-images using super-resolution
               (SR) techniques, increasing the number of pixels of the
               elements, and re-infer over these areas using the same
               pre-trained model. A reduced set of windows is calculated in the
               super-resolved image by analyzing a computed graph that
               describes the distances among the preliminary object detections.
               This analysis is done by finding maximal cliques on it. This
               way, the number of windows to be examined is diminished,
               significantly speeding up the detection process. This framework
               has been successfully tested on real traffic sequences obtained
               from the U.S. Department of Transportation. An increase of up to
               44.6\% is achieved, going from an average detection rate for the
               EfficientDet D4 model of 14.5\% compared to 59.1\% using the
               methodology presented for the first sequence. Qualitative
               experiments have also been performed over the Cityscapes and
               VisDrone datasets.",
  journal   = "Neural Comput. Appl.",
  publisher = "Springer Science and Business Media LLC",
  volume    =  35,
  number    =  26,
  pages     = "18999--19013",
  month     =  sep,
  year      =  2023,
  copyright = "https://creativecommons.org/licenses/by/4.0",
  language  = "en"
}

```


# REQUIREMENTS:

* Tensorflow 2
* Tensorflow Object Detection
* OpenCV
* Numpy

