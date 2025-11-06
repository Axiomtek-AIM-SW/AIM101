![](https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/images/Ax_Page_Banner_2500x168_01.png)
The following steps are based on Axelera SDK Release version v1.4.0. It is recommended to refer to the latest release version available at the provided URL for corresponding installation instructions. (Update Date: 2025/10/02)
### https://github.com/axelera-ai-hub/voyager-sdk/

## 1-1.Axelera - SDK Installation (Release version v1.4.0)
### Refer : docs/tutorials/install.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/tutorials/install.md
```shell
git clone https://github.com/axelera-ai-hub/voyager-sdk.git
cd voyager-sdk
./install.sh --all --media
source venv/bin/activate
```
It is recommended to refer to the latest release version available at the provided URL for corresponding installation instructions. 
Please follow the steps below to enable updates and perform a firmware flash update.

## 1-2.Axelera - enable_updates
### Refer : docs/tutorials/enable_updates.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/tutorials/enable_updates.md
```shell
cd voyager-sdk
source venv/bin/activate

wget https://axelera-public.s3.eu-central-1.amazonaws.com/aipu_firmware_enabler/voyager-sdk-v1.4.0/enable_bootloader_update.sh
chmod +x enable_bootloader_update.sh
./enable_bootloader_update.sh

# Note: Please ensure that the device is completely powered off before turning it back on.
```
## 1-3.Axelera - firmware_flash_update
### Refer : docs/tutorials/firmware_flash_update.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/tutorials/firmware_flash_update.md
```shell
cd voyager-sdk
source venv/bin/activate

$AXELERA_DEVICE_DIR/firmware/interactive_flash_update.sh

# Note: Please ensure that the device is completely powered off before turning it back on.
```
## 1-4.Axelera - Run First Demo
```shell
cd voyager-sdk
source venv/bin/activate

./inference.py yolo11s-coco-onnx media/traffic1_720p.mp4
```
## 1-5.Axelera - custom weights deployment
### Refer : docs/tutorials/custom_weights.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/tutorials/custom_weights.md
