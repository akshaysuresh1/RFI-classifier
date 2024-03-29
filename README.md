# RFI-classifier

A PyTorch implementation of a supervised machine learning model to classify different morphologies of interference signals in radio telescope data.

**Project report:** [PDF](https://github.com/akshaysuresh1/RFI-classifier/blob/master/RFI_classifier.pdf)

**Contributors:**
* [Akshay Suresh](https://www.linkedin.com/in/akshaysureshas1) (mentor, project lead)
* [Ryan J. Hill](https://www.linkedin.com/in/ryan-james-hill) (Cornell University undergraduate research intern, Fall 2019)
* [Ethan S. Bair](https://blogs.bu.edu/esb265) (Cornell University undergraduate research intern, Fall 2019)

---

## Table of Contents
- [Project Goal](#project)
- [Methodology](#methods)
- [Takeaways](#results)
- [Areas for Improvement](#futurework)
- [Troubleshooting and Feedback](#troubleshooting)

## Project Goal <a name="project"></a>
Interference signals from human technologies frequently compound searches for exotic astrophysical phenomena. With modern radio telescopes generating data at > 100 GB/hr rates, automated methods are necessary to identify and flag data segments rife with interference. Unflagged data chunks can then be processed via subsequent pipelines tuned to specific science cases. <br>

Here, we experiment with multiple toy convolutional neural network (CNN) models to distinguish between various morphologies of interference signals in radio telescope data. 

## Methodology <a name="methods"></a>
As a first pass, we defined the following 5 classes for our signal classification task.
* `llnb`: Long-lived narrowband interference + background noise
* `slnb`: Short-lived narrowband interference + background noise
* `llbb`: Long-lived broadband interference + background noise
* `slbb`: Short-lived broadband interference + background noise
* `noise`: Background noise only

Simulated frequency-time diagrams of the first 4 signal classes are presented below. Slide credit: Ryan J. Hill
![Inteference signal morphologies](https://github.com/akshaysuresh1/RFI-classifier/blob/master/img/signal_classes.png?raw=True)

**NOTE**: In our study, we generated simulated data to ensure that our training and validation data are balanced across all classes. This choice allows us to evaluate model performance using the accuracy metric. Refer to the Appendix of our project report for the full confusion matrices obtained with different CNN models.

## Takeaways <a name="results"></a>
Figure credit: Ethan S. Bair
![Model accuract comparison](https://github.com/akshaysuresh1/RFI-classifier/blob/master/img/accuracy_6to10.png?raw=True)
Trialing CNNs of different depths, we observe a growth in network accuracy across all signal classes with increasing model depth. However, the incremental gain in network accuracy diminishes with every added layer. Setting a 95% accuracy threshold, the above plot suggests that an 8/9-layer CNN model would be adequate for our classification problem.

## Areas for Improvement <a name="futurework"></a>
1. Our definition of interference signal classes is overly simplistic and needs refinement based on inputs from real-world radio telescope data.
2. Models do not account for scenarios where multiple signal classes are present in a single frequency-time snippet. For instance, what if an astrophysical signal of interest overlaps in time with two bright interference signals of different bandwidths?
   * Perhaps multilabel classification is worth an exercise.
   * Alternatively, we can take a look at image segmentation problems.

## Troubleshooting and Feedback <a name="troubleshooting"></a>
Please submit an issue to voice any problems or requests. Constructive critcisms are always welcome. 

---
