# Object-detection-by-training-custom-dataset

our company got an project from japanies mercedes benz car company.....where we have to detect and count how many plates are passing to dustbin as this work previously done manually...as canteen owner gets paid by couting number of plates...benz had an issue ,as they thought canteen owner is lying...so they call us to use deep learning solution,to detect and count real plate passing to dustbin via conveyor belt

NOTE:Due to privacy concerns i cant upload the train and test data with their annotated form..but by taking my companies permission...i am uploading the training and real time test scripting here,,,as we also taken that script from publically available url...
The Link is:
https://github.com/EdjeElectronics/TensorFlow-Object-Detection-API-Tutorial-Train-Multiple-Objects-Windows-10


this is an extraordinary tutorial which was trained on playing cards...
now we used that and trained that script on our plate data which was labelled and annoted

The sequence is same but change is,we does not train that script on local machine as my laptop is not installed with GPU till ,instead i modify that script according to google colab and run in colab with GPU..

The sequence is:<br>
1.Initially i gather pictures from the video send by the company...i took various images and store them to specific folder<br>
2.After that to generate train data, i used  labellmg tool to annotate data and name the label 'plate'..<br>
3.Then i split data into train and test...as 80 -20%<br>
4.after that i ran xml_to_csv.py file where i get an csv file with an coordinated of bounding rectangle as features with class label<br>
5.Now i have train_label.csv file and test_label.csv file<br>
6.then i ran generate_tfrecord.py file,before that i made some changes in that such as ...change class label=1 and modify code...<br>
7.now i got train.record and test.record file which serve as the input to model as train and test during training.<br>
8.the i generate labelmap.pbtxt file which contaion label id and label name and saved with same extension.<br>
9.now i modify faster_rcnn_inception_v2_config file<br>
this is important file as this contains the labelmap.pbtxt path,train data path,test data path, number of class label..<br>
carefully done modification and saved...<br>

10.Now i uploaded the all four file generated here to google drive ,they are<br>
train.record<br>
test.record<br>
labellmap.pbtxt<br>
faster_rcnn_inception_v2_config<br>

11.Now start with  google colab....<br>
12.initially i made 2 dir namely training and inf_graph<br>
13.the mount google drive<br>
14.then copy train.record i.e. our 4 main files to training folder<br>
15.then download ...!wget http://download.tensorflow.org/models/object_detection/faster_rcnn_inception_v2_coco_2018_01_28.tar.gz<br>
pretrained model and un-zip it to pretrained folder<br>
16.then clone tensorflow model api file via !git clone https://github.com/tensorflow/models.git<br>
17.then start training by...!python3 object_detection/model_main.py --model_dir='/content/drive/My Drive/Colab Notebooks/PlateDetectionFasterRCNNv4/final_model' --pipeline_config_path='/content/training/faster_rcnn_inception_v2_coco.config'<br>
18.after training for almost  4 hours ..interrupt the training and download the "frozen_inference_graph.pb" file to local system<br>
19.Then open Object_detection_video.py file in sublime text editior and upload that model file to that script and detects the plates...count and updated same to database...<br>
20.There are few False positive results we were get...we told same to the company...<br>
21.But company satisfied with our work...as they get almost correct data of how many plates actually generate on daily basis....
