# Object-detection-by-training-custom-dataset

our company got an project from japanies mercedes benz car company.....where we have to detect and count how many plates are passing to dustbin as this work previously done manually...as canteen owner gets paid by couting number of plates...benz had an issue ,as they thought canteen owner is lying...so they call us to use deep learning solution,to detect and count real plate passing to dustbin via conveyor belt

NOTE:Due to privacy concerns i cant upload the train and test data with their annotated form..but by taking my companies permission...i am uploading the training and real time test scripting here,,,as we also taken that script from publically available url...
The Link is:
https://github.com/EdjeElectronics/TensorFlow-Object-Detection-API-Tutorial-Train-Multiple-Objects-Windows-10


this is an extraordinary tutorial which was trained on playing cards...
now we used that and trained that script on our plate data which was labelled and annoted

The sequence is same but change is,we does not train that script on local machine as my laptop is not installed with GPU till ,instead i modify that script according to google colab and run in colab with GPU..

The sequence is:
1.Initially i gather pictures from the video send by the company...i took various images and store them to specific folder
2.After that to generate train data, i used  labellmg tool to annotate data and name the label 'plate'..
3.Then i split data into train and test...as 80 -20%
4.after that i ran xml_to_csv.py file where i get an csv file with an coordinated of bounding rectangle as features with class label
5.Now i have train_label.csv file and test_label.csv file
6.then i ran generate_tfrecord.py file,before that i made some changes in that such as ...change class label=1 and modify code...
7.now i got train.record and test.record file which serve as the input to model as train and test during training.
8.the i generate labelmap.pbtxt file which contaion label id and label name and saved with same extension.
9.now i modify faster_rcnn_inception_v2_config file
this is important file as this contains the labelmap.pbtxt path,train data path,test data path, number of class label..
carefully done modification and saved...

10.Now i uploaded the all four file generated here to google drive ,they are
train.record
test.record
labellmap.pbtxt
faster_rcnn_inception_v2_config

11.Now start with  google colab....
12.
