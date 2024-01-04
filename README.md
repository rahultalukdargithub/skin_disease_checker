# Main Idea:

The main objective is to create an Android app for Skin Disease Detection using the YOLOv5 model. This involves several steps, including training the YOLOv5 model, converting it into a TensorFlow model, converting the TensorFlow model into a TensorFlow Lite (TFLite) model, setting up Android Studio, and building and running the object detection app. 

# Main Steps for Creating Android App:

Now to train the model with yolo v5 you just have to run the .ipynb file in colab or jupyter notebook wherever you want but give the path of the file in that ipynb file according to your file destination. In my case i have unzipped the dataset first then I did %cd yolov5 so that everything comes under yolov5 file.

After doing so you have to change the .pt file to .tflite in following way---->

Export YOLOv5 Weights to TensorFlow Lite Format:

Open the YOLOv5 folder in the command prompt.
Execute the command: "python export.py --data your_yaml_file.yaml --weights runs/train/exp/weights/best.pt --include tflite --img 640"(for img size always try to use a number which is divisible by both 32 and 64) to export the YOLOv5 weights to TensorFlow Lite format.
The exported model will be saved as a .tflite file in the "yolov5/runs/train/exp/weights" directory.
Test the Exported Data:

Test the exported data by running the command: "python detect.py --weights runs/train/exp/weights/best-fp16.tflite --img 640 --source data/images/"
Prepare Android App Assets:

Copy the "android" folder to the YOLOv5 folder.
Navigate to "android/app/src/main/assets" and paste the "best-fp16.tflite" file created during the export process.
Edit the "customclasses.txt" file in the same location by adding your class names (one class name per line).
Modify DetectorFactory.java:

Go to "android/app/src/main/java/org/tensorflow/lite/examples/detection/tflite" and edit the "DetectorFactory.java" file (dont forget to change the img size according to your img size in my case its 640), comparing it with the provided version, and save the changes.
Set Up Android Studio:

Download and install Android Studio.
Build and Run the App:

Open Android Studio and run the program to build and run the object detection app.
YOLO Commands (Training and Testing):

# References:

Python: https://www.python.org/downloads/

LabelImg: https://github.com/tzutalin/labelImg

YOLOv5: https://github.com/ultralytics/yolov5

LabelImg Annotation Tutorial: https://youtu.be/Tlvy-eM8YO4

YOLOv5 Training Tutorial: https://youtu.be/80Q3HIBy7Qg

YOLOv5 App Making Tutorial: https://youtu.be/ROn1_O2zEtk

Android File Download (GitHub Repository): https://github.com/AarohiSingla/TFLite-Object-Detection-Android-App-Tutorial-Using-YOLOv5.git
