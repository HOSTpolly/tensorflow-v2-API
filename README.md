
TensorFlow v2 API
Description
tensorflow-v2-API is a repository containing examples and documentation for TensorFlow v2 API usage.

Table of Contents
Installation
Usage
Contributing
License

Installation
To install tensorflow-v2-API, follow these steps:

Clone the repository: git clone https://github.com/MrZend/tensorflow-v2-API.git
Navigate to the project directory: cd tensorflow-v2-API
Download anaconda from https://www.anaconda.com/download
Select Python 3.8 in Anaconda (conda install python=3.8)
conda install -c anaconda lxml
pyrcc5 -o libs/resources.py resources.qrc

Тренування:

python object_detection/model_main_tf2.py \ 
    --pipeline_config_path=${PIPELINE_CONFIG_PATH} \
    --model_dir='D:\\Kotya\\expirement_1\\training_process' \
    --alsologtostderr

Експорт:
python object_detection/exporter_main_v2.py \
    --input_type image_tensor \
    --pipeline_config_path=${PIPELINE_CONFIG_PATH} \
    --trained_checkpoint_dir='/d/Kotya/expirement_1/training_process' \
    --output_directory='/d/Kotya/expirement_1/inference_graph'

Конвертація:
tflite_convert \
    --saved_model_dir='D:\Kotya\expirement_1\inference_graph' \
    --output_file=ssd_mobilenet_v2_fpnlite_320.tflite \
    --input_shapes=1,320,320,3 \
    --input_arrays=normalized_input_image_tensor \
    --output_arrays='TFLite_Detection_PostProcess,TFLite_Detection_PostProcess:1,TFLite_Detection_PostProcess:2,TFLite_Detection_PostProcess:3' \
    --inference_type=QUANTIZED_UINT8 \
    --mean_values=128 \
    --std_dev_values=128 \
    --allow_custom_ops