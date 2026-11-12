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
