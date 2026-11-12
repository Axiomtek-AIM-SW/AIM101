# Update date：2026/11/10
# https://github.com/DEEPX-AI/dx-all-suite

### Run the first YOLO model quickly
```shell
# DX-Runtime (target device with a DEEPX NPU: NPU driver + dx_rt + firmware)
sudo apt update && sudo apt install -y curl git python3.12-venv
curl -fsSL https://raw.githubusercontent.com/DEEPX-AI/dx-runtime/main/oneline-install.sh | sh
sudo reboot
```
```shell
python3 -m venv --system-site-packages ~/dx
cd ~/dx && source ~/dx/bin/activate
PYTAG=cp$(python -c 'import sys;print(f"{sys.version_info[0]}{sys.version_info[1]}")')
pip install /usr/share/libdxrt-bin/python/dx_engine-*-${PYTAG}-${PYTAG}-*.whl
cd ~/dx/ && git clone https://github.com/DEEPX-AI/dx-app.git
cd ~/dx/dx-app && ./setup_sample_models.sh --models YoloV8N
pip install opencv-python
python src/python_example/object_detection/yolov8/yolov8-n_640x640/yolov8-n_640x640_sync.py \
  --model assets/models/yolov8-n_640x640.dxnn \
  --image sample/img/sample_street.jpg
```
### Benchmark
```shell
run_model -m ~/dx/dx-app/assets/models/yolov8-n_640x640.dxnn -t 10
```
```
Using I/O Buffer Count=6

Runtime Framework Version: v3.5.0
Device Driver Version: v2.7.0
PCIe Driver Version: v2.7.0

modelFile: assets/models/yolov8-n_640x640.dxnn
inputFile: 
outputFile: output.bin
benchmark: 0
loops: 30
Device specification: 'all' (default)
Run model target mode : Benchmark Mode
Inference by time: duration=10(s)

=== Model File: /home/ax/deepx/dx-app/assets/models/yolov8-n_640x640.dxnn ===

Model Input Tensors:
  - images
Model Output Tensors:
  - onnx::Concat_328
  - onnx::Concat_335
  - onnx::Concat_343
  - onnx::Concat_350
  - onnx::Concat_358
  - onnx::Concat_365

Tasks:
  [ ] -> npu_0 -> []
  Task[0] npu_0, NPU, NPU memory usage 77,453,120 bytes (input 1,228,800 bytes, output 4,838,400 bytes), mem_usage:151,181,120 bytes
  Inputs
     -  images, UINT8, [1, 640, 640, 3 ]
  Input DMA size: 1,228,800 bytes
  Outputs
    -  onnx::Concat_328, FLOAT, [1, 64, 80, 80 ]
    -  onnx::Concat_335, FLOAT, [1, 80, 80, 80 ]
    -  onnx::Concat_343, FLOAT, [1, 64, 40, 40 ]
    -  onnx::Concat_350, FLOAT, [1, 80, 40, 40 ]
    -  onnx::Concat_358, FLOAT, [1, 64, 20, 20 ]
    -  onnx::Concat_365, FLOAT, [1, 80, 20, 20 ]
  Output DMA size: 6,451,200 bytes


Inference by time: total-inference-time=10.024(s) total-loops=2289
=============================================
* Benchmark Result (2307 inputs)
  - FPS : 230.29                           
=============================================
```
