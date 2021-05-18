# Deep Learning for Detecting Building Defects Using Convolutional Neural Networks
Traditional methods for this type of work commonly comprise of engaging building surveyors to undertake a condition assessment which involves a lengthy site inspection to produce a systematic recording of the physical condition of the building elements, including cost estimates of immediate and projected long-term costs of renewal, repair and maintenance of the building. Current asset condition assessment procedures are extensively time consuming, laborious, and expensive and pose health and safety threats to surveyors, particularly at height and roof levels which are difficult to access. In this project we aims at evaluating the application of convolutional neural networks (CNN) towards an automated detection and localisation of key building defects, e.g., mould, deterioration, and stain, from images. The proposed model is based on pre-trained CNN classifier of VGG-16 (later compaired with ResNet-50, and Inception models), with class activation mapping (CAM) for object localisation.

### Transfer learning
An important technique in deep learning which is used to solve the problem of insufficient training data by transferring knowledge from one domain to another. A good practice in transferring knowledge, is to use a well-structured network which is pre-trained on a large data and use its knowledge as a weight initialiser for a new network. For example, using pre-trained VGGNET on ImageNet dataset which contains 14 million annotated images and contains more than 20,000 categories). Implementing transfer learning can be in one of two ways:
•	Feature extractor
In this arrangement, the fully-connected layers in the pre-trained network are removed and the neural network is treated as a fixed feature extractor (see Figure 5).  In the case of the VGGNET, the fully-connected layers generates 1000 different classes. The earlier layers (convolutional) in the pre-trained network are then trained on the new dataset as feature extractor only. For each input image, the VGGNET computes a 4096-D feature map which is then passed to the ReLU function In order to reduce the number of features required for later computation.  With all feature maps extracted from all the images in the training dataset, a Softmax classifier with n-classes (the number of classes in the new dataset) is placed on top of the pre-trained network and trained again on the new dataset.
•	Fine-tuning
In addition to replacing a new Softmax classifier on top of the pre-trained network and retraining it on the new dataset, in this scenario, it is possible to fine-tune a pre-trained network by using some of the earlier (convolution) layers as feature extractor while retrain the higher-level parts of the network on the new dataset.  Since earlier convolution layers in a network are able to detect generic features (e.g. edge detectors or colour blob detectors), this could be very useful to many tasks. Later convolution layers, however, are more specific to the details of the classes contained in the original dataset [41]. A fine-tuned network, hence, exploits the capabilities of early layers in pre-trained network to extract generic feature, while training later layers and the classifier on the more specific details of the new dataset.



![CAM) for object localisation](https://github.com/obu-sobe/Defects_Detection/blob/main/images/defects.png)
