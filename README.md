
# The RoWell Rescue Robot for Borewell Hazards
#### A project by Sirisha Jotheeswaran Padmasekhar 

## Project Description 
Borewell has been our major source of water since the time of 1990s. We as humans has evolved to find solutions to make use of resources the earth is willing to provide us or maybe even more at sometimes. But are we stuck in a cycle of finding solutions that then become the source of new problems? This project focuses on being an advocate to address the major social-issue that has raised in parts of the world. 

The portmanteau word "RoWell" derived from Robot-Borewell drives way to inculcate robot vision processing and integrate robotic learning to borewell systems. Due to negligence and ignorance, people forget to cover the boreholes after draining underground water and pulling out the pipes. The lack of knowledge remains as the root cause of the problem. The recent statistics states that there are over 37 Million borewells in India and almost 70% of rescue operate fail. The death rate from 2015 to 2021 has accelerated. The objective of the research is to bridge the technological gap by adapting to Deep Learning Based Approach for the Rowell robot to explore any given environment, detect and classify high risk, low risk and safe borewells in real-time and alert the government officials to inspect and raise awareness to people in the community of high and low risk locations. Furthermore, integrating to Maps platforms allows us to locate borewells  in real-time. The current work focuses solely on the quote, "Prevention is better than cure".  

The Rowell  Robot is autonomous and Data-driven. The volatile nature of the environment has raised concerns for its tediousness and lowered precision. The one stage object detection method(s) are used to overcome these restrictions since they employ a single neural network for both detection and classification which is faster and significantly accurate compared to traditional two-way object detection methods.The requirement matrix (reference/requirement matrix.jpg) allows us to evaluate one stage detector algorithms with our metrics. On evaluation Yolov3, yolov5, yolov7, efficientDet and ResNet is the best algorithms for performance evaluation. The algorithms  are comparatively been able to perform the tasks with accuracy and precision, and is cost effective, utilizes wide angle vision to detect small objects and can detect borewells in real-time which allows us to deploy our project with utmost efficiency. 

This project focuses on the following:

1. Train one stage detector models to detect and classify borewells and evaluate the performance ratio. 
2. Integration of maps using GoogleMaps API. 
3. Set up email alert system using Zoho mails API. 
4. Set up whatsapp alert system using Twilio API.
5. Aerial Image mapping using GAN 

## Dataset

The goal is to not find bigger data but to find the right data for desired analytics. The borewell dataset from [Kaggle](https://www.kaggle.com/datasets/saktheeswaranswan/borewell-dataset-416-resize-tensorflow-yolo-voc?select=borewell+dataset) contains real-time borewell images annotated using roboflow.ai, an open-source annotation tool used to label data in categories as, “completely safe borewells”, “open borewells”, “unsafe borewells”. It is recommended to use COCO Data format with input image size as 416x416


## Documentation

Training a deep neural network require a lot of resources, however, GPU can perform multiple computations, distributing the training processes which enables our model to speed the process. It uses fewer resources without compromising on the efficient and power. All the models are trained with GPU in [Google Collab Notebook](https://drive.google.com/file/d/1a3saiY0QbfrKBGyuK5qE1Sp6-ms__L34/view?usp=sharing). To re-train, we are in need to purchase Colab pro subscription. The latest yolo version bring a lot of traction, as its user - friendly and uses transfer learning to train on any given dataset. 

Before, training yolo v5 and Yolo v7 models, the following instructions/installations needs to be setup:

1. Data preperation - Dataset in Coco/ pascal VOC format with 416x416 as input size needs to be uploaded in drive ( See,report for data structure). 
2. Mount our google drive to colab notebook. 
3. Clone yolov5 and yolo v7 repository by simply running the following code in terminal. 
   For Yolov5:
               !git clone https://github.com/ultralytics/yolov5
Enter the directory with the command: %cd yolov5

 For yolov7: 
            !git clone https://github.com/WongKinYiu/yolov7.git
 Enter the directory with the command: %cd yolov7

4. Install all the required packages by running the file requirement.txt in terminal using the command: pip install -r requirements.txt 
5. Prepare data.yaml file. This file contains, the location of training data, validation data and a list of class names. 
For example, 
Train: ../drive/mydrive/yolov5/data/train
Val:../drive/mydrive/yolov5/data/val
class = [completly_close_safe,open_danger,unsafe_warning]

6. Once the data.yaml file is ready, train the model [Yolov5](https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data) [Yolov7](https://github.com/WongKinYiu/yolov7)
7. After training the output is saved in runs/train/exp
8. Fine tuning technique can be applied to re-train the model with the best learning from previous training by using best.pt as weights. The result of training can be found in runs/train/exp
9. Write a web scraping code, to download random image for testing. This is done using bing-image-downloader python library. 
10. Run detect.py file in terminal to obtain how well a the model can provide inference in real time. 
11. To train yolov3, efficientDet and ResNet algorithm using transfer learning, download weights of these model from here. 
12. Repeat the training step by changing different weights.
13. Now, the yolov3, yolov5,yolov7, efficientDet and ResNet model is trained and confidence value at inference has been generated. 
14. Code for performance comparison has been evaluated and integration system can be found [here](https://drive.google.com/file/d/1a3saiY0QbfrKBGyuK5qE1Sp6-ms__L34/view?usp=sharing)

For system Integration, the first step is to obtain unique API key by following the steps below:

## API Authentication

The general rule of thumb is to not share API Key in code or other sources. Eventhough, the API Key is provided in the source code, the API keys are re-generated to protect critical information from public. 

### Steps to create API key for Google Maps API : 

 1. Open Google Maps Platform
 2. On the Credentials page, click Create credential → API key.
 3. API Key is successfully generated.
 4. Use the unique API Key to configure Google Maps.

### Create Authentication Token (OAuth) Token for Zoho Mail API: 

1. Create a personal account on Zoho Mail
2. Login with your credentials
3. Fill API key registration form
4. Click the "Generate API Key" button.
5. Zoho mail API Key is successfully generated.

For Google map API, one of the mejour challenges was the unavailability of metadata. Therefore, fake metadata has been generated for testing purposes. 

### Create geotag for random images by following the steps below:

#### How to geotag?

1. Upload an image / multiple images in the tool.
2. On the top-right display, we have maps at which we can mark a possible location at which a borewell might exist.
3. On the left-side we can see the latitude and longitude details of the image.
4. Click on write EXIF tags.
5. Download the Image.
6. Right click on the image → Properties
7. We can now see the metadata or the location of the image.

### The next step is to replace the API key with the unique generated api key and run the cell to get desired output. 

The same process if generated apikey for zoho mails and twilio and run the cell in the [Google Collab Notebook](https://drive.google.com/file/d/1a3saiY0QbfrKBGyuK5qE1Sp6-ms__L34/view?usp=sharing) to get desired output. 

Email and messages and googlemap api integration has been sucessfully carried out. 

## Acknowledgements

I would like to express my deepest gratitude to my primary supervisor Prof.Mr.Sreeganesh thottempudi (Professor at SRH University of applied sciences) and my secondary supervisor Mr. Adithya Mohan, (Robotic Engineer at Quantum Systems GmBH) who has helped me every step of the way in providing the resources and support needed to implement my learnings from Masters degree in Big data and artificial Intelligence, which allowed me to successful complete my Dissertation. In addition, I would like to thank, the administration, examination board and other faculty of the university who has answered to my queries with dedication and patience. Lastly, this endeavor would'nt have been possible without the support of my parents and siblings who have always motivated me to acheive my goals. 

## Author

- [@SirishaJotheeswaranPadmasekhar](https://github.com/SirishaJotheeswaranPadmasekhar)


## Appendix

A survey of 77 responses was recorded. Majority stated that this project will have a positive impact in the society and real-time implementation will reduce the risk of borewell accidents. The borewell detection and classification was highly accurate. This survey was personally created and recorded using [Google forms](https://forms.gle/cNYN2bCju8YCyPxR7) 

