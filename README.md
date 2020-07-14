# Computer Pointer Controller Project

In this project we controls the computer's mouse pointer with eye gaze.
We have used 4 pre-trained model that is provided by Open Model Zoo.
The project's main aim is to check usage of OpenVino ToolKit on different hardware
which includes the following:

- openvino inference API
- OpenVino WorkBench
- VTune Profiler

## Project Set Up and Installation

1. Download [OpenVino ToolKit](https://software.intel.com/content/www/us/en/develop/tools/openvino-toolkit/choose-download.html) and install it locally.

2. Clone the repository from this URL: https://github.com/Polarbeargo/Computer-Pointer-Controller-Project.git
           
3. In Windows Command Prompt from working directory to install prerequisites or Execute <i>run.sh</i> from working directory to install prerequisites.

         cd Computer-Pointer-Controller
         pip install -r requirements.txt
         cd C:\Program Files (x86)\IntelSWTools\openvino\bin
         setupvars.bat
         or
         ./run.sh


## Demo

We have provided three ways to run the application
1. Static Image JPEG/PNG
2. Video File

Execute following command from the root directory of the project with your configuration.
    
    python starter/src/demo.py -fd models/intel/face-detection-adas-binary-0001/FP32-INT1/face-detection-adas-binary-0001.xml -lr models/intel/landmarks-regression-retail-0009/FP16/landmarks-regression-retail-0009.xml -hp models/intel/head-pose-estimation-adas-0001/FP16/head-pose-estimation-adas-0001.xml -ge models/intel/gaze-estimation-adas-0002/FP16/gaze-estimation-adas-0002.xml -d CPU -i starter/bin/demo.mp4 -flags ff fl fh fg

## Documentation

###### Command Line Arguments for Running the app

Argument|Type|Description
| ------------- | ------------- | -------------
-f | Mandatory | Path to .xml file of Face Detection model.
-l | Mandatory | Path to .xml file of Facial Landmark Detection model.
-hp| Mandatory | Path to .xml file of Head Pose Estimation model.
-ge| Mandatory | Path to .xml file of Gaze Estimation model.
-i| Mandatory | Path to video file or enter cam for webcam
-it| Mandatory | Provide the source of video frames.
-debug  | Optional | To debug each model's output visually, type the model name with comma seperated after --debug
-ld | Optional | linker libraries if have any
-d | Optional | Provide the target device: CPU / GPU / MYRIAD / FPGA

###### Directory Structure

- <b>bin</b> folder contains the media files
- <b>models</b> folder contains pre-trained models from Open Model Zoo
    - intel
        1. face-detection-adas-binary-0001
        2. gaze-estimation-adas-0002
        3. head-pose-estimation-adas-0001
        4. landmarks-regression-retail-0009
- <b>src</b> folder contains python files of the app
    
    + [demo.py](./starter/src/demo.py) : Main driver script to run the app
    + [face_detection.py](./starter/src/face_detection.py) : Face Detection related inference code
    + [facial_landmarks_detection.py](./starter/src/facial_landmarks_detection.py) : Landmark Detection related inference code
    + [gaze_estimation.py](./starter/src/gaze_estimation.py) : Gaze Estimation related inference code
    + [head_pose_estimation.py](./starter/src/head_pose_estimation.py) : Head Pose Estimation related inference code
    + [input_feeder.py](./starter/src/input_feeder.py) : input selection related code
    + [mouse_controller.py](./starter/src/mouse_controller.py) : Mouse Control related utilities.
    
- <b>README.md</b> File that you are reading right now.
- <b>requirements.txt</b> All the dependencies of the project listed here
- <b>run.sh</b> one shot execution script that covers all the prerequisites of the project.

## Benchmarks
*TODO:* Include the benchmark results of running your model on multiple hardwares and multiple model precisions. Your benchmarks can include: model loading time, input/output processing time, model inference time etc.

## Results
Benchmark results on Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz:

* face-detection-adas-binary-0001  
   
Precision: INT8  

Precision: FP16  

Precision: FP32  

* gaze-estimation-adas-0002 

Precision: INT8  

Precision: FP16  

Precision: FP32  

* head-pose-estimation-adas-0001

Precision: INT8  

Precision: FP16  

Precision: FP32  

* landmarks-regression-retail-0009 

Precision: INT8  

Precision: FP16  

Precision: FP32  

## Stand Out Suggestions
This is where you can provide information about the stand out suggestions that you have attempted.
