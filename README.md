# ds301-final-project
DS 301 Project by Xikun Wang and He Li: a Multimodal humanitarina insight classifier 
## Description of our project: 

In the context of the disaster events, social platforms such as Twitter, Facebook become
valuable resources for real time information. These platforms update immediate updates
and facilitate rapid communication, which can be time-saving in emergency situations. Accurate classification of tweets into the correct category accordingly enables a swift and more
organized response from the aid organizations, enhancing the efficiency of humanitarian assistance and rescue operations. The objective of our project is to understand the type of
humanitarian information shared in tweet images and texts, which are collected during different disaster events including wildfires, earthquakes, floods, and hurricanes. The previous
studies of tweets classifications primarily concentrated on textual analysis or just focusing on images. Considering the limitations of unimodal, we will explore the multimodal analysis
that pairs informative text with corresponding images. 

## Architecture of the modal 
### Data set and preprocesing 
The dataset we use is from this link  https://github.com/firojalam/multimodal_social_media/blob/master/data/all_images_path.txt. We changed some unbalanced class with the labels that most related to their meanings. And then we split the training test and validation in approximately 70:15:15. We cleaned the text dataset by removing htmls, numbers, punctuations, and lowercase the text. We also added the data augmentation for image datasets.

### Methodology
We implemented the multimodal inspired by the pipeline in this research: https://arxiv.org/abs/2004.11838. The architecture depicted integrates both textual and visual data, employing separate pathways to process each modality before merging them for final classification. For text processing, embeddings from BERT are further refined through a BiLSTM network, leveraging the ability to capture sequential dependencies within the text. On the image side, two separate experiments are conducted with InceptionV3 and MobileNetV32, each chosen for their unique strengths—InceptionV3 for its deep and complex architecture capable of capturing nuanced image features, and MobileNetV2 for its efficient and lightweight design suitable for mobile applications. After feature extraction, the text and image pathways are combined using a concatenation operation, followed by batch normalization to stabilize the learning process. A MultiHead Attention mechanism is employed post-concatenation to allow the model to focus on relevant features across both modalities. The attention-enhanced features undergo a residual connection before being fed into a dense network, culminating in a final dense layer for classification. Hyperband combined model enables it to tailor its parameters to the specificities of the task at hand, optimizing performance across the multimodal dataset. We also added the finetuning method by freezing the pretrained layers.
![download](https://github.com/Averywang15116/ds301-final-project/assets/71258939/d5292913-edbb-4a19-87f0-723edaab1ed0)

## Result
The final result of the BERT-BiLSTM + InvceptionV3 model shows the accuracy of about 0.82, and the F-1 score around 0.81. And the result of BERT-BiLSTM + MobileNetV2 achieves slightly better accuracy about 0.83 and F-1 score of 0.83.

The model of running each files takes about 4 hours depending on your RAM storage. 



