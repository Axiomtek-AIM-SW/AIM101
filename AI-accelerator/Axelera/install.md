![](https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/images/Ax_Page_Banner_2500x168_01.png)
The following steps are based on Axelera SDK Release version v1.4.0. It is recommended to refer to the latest release version available at the provided URL for corresponding installation instructions. (Update Date: 2025/10/02)
### https://github.com/axelera-ai-hub/voyager-sdk/

## 1-1.Axelera - SDK Installation (Release version v1.5.1)
### Refer : docs/tutorials/install.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.5/docs/tutorials/install.md
```shell
cd ~/
git clone https://github.com/axelera-ai-hub/voyager-sdk.git
cd ~/voyager-sdk
./install.sh --all --media
source venv/bin/activate
sudo reboot
```
It is recommended to refer to the latest release version available at the provided URL for corresponding installation instructions. 


## 1-2.Axelera - enable_updates
### Please follow the steps below. Note that Steps 1-2 and 1-3 are optional and may be skipped based on your requirements.
### Refer : docs/tutorials/enable_updates.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.5/docs/tutorials/enable_updates.md
```shell
cd ~/voyager-sdk
source venv/bin/activate
wget https://axelera-public.s3.eu-central-1.amazonaws.com/aipu_firmware_enabler/voyager-sdk-v1.4.0/enable_bootloader_update.sh
chmod +x enable_bootloader_update.sh
./enable_bootloader_update.sh
sudo poweroff

# Note: Please ensure that the device is completely powered off before turning it back on.
```
## 1-3.Axelera - firmware_flash_update
### Refer : docs/tutorials/firmware_flash_update.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/tutorials/firmware_flash_update.md
```shell
cd ~/voyager-sdk
source venv/bin/activate
$AXELERA_DEVICE_DIR/firmware/interactive_flash_update.sh
sudo poweroff

# Note: Please ensure that the device is completely powered off before turning it back on.
```
Repeat Run $AXELERA_DEVICE_DIR/firmware/interactive_flash_update.sh
```shell
cd ~/voyager-sdk
source ~/voyager-sdk/venv/bin/activate
$AXELERA_DEVICE_DIR/firmware/interactive_flash_update.sh
```
```
>>> Metis Flash Update Script
>>> =========================
>>> Auto-detecting and updating all connected devices...

>>> Detected 1 device(s) from axdevice
>>> ==============================================
>>> Found 1 device(s):
>>>   - metis-0:1:0
>>> ==============================================

>>> Running: triton_multi_ctx --device metis-0:1:0 --bc-version
>>> Raw board controller version output:
zephyr version: 4d712f10d2f5
app name:   board_bringup
app version:    v7.1
>>> Extracted board controller version: '7.1'
>>> Device metis-0:1:0 is fully updated

>>> ==============================================
>>> UPDATE SUMMARY
>>> ==============================================
>>> Total devices: 1
>>> Devices needing firmware update: 0
>>> Devices needing board controller update: 0
>>> Devices fully updated: 1
>>> Devices failed: 0
>>> ==============================================

>>> ==============================================
>>> ALL DEVICES ARE FULLY UPDATED!
>>> ==============================================
>>> All 1 connected card(s) have their firmware and
>>> board controllers updated to the latest versions.

>>> Final status:
>>>   - metis-0:1:0: FULLY UPDATED ✓
>>> 
>>> No further action required.
>>> ==============================================
```
## 1-4.Axelera - Run First Demo
```shell
cd ~/voyager-sdk
source venv/bin/activate

./inference.py yolo11s-coco-onnx media/traffic1_720p.mp4
```
## 1-5.Axelera - custom weights deployment
### Refer : docs/tutorials/custom_weights.md
### https://github.com/axelera-ai-hub/voyager-sdk/blob/release/v1.4/docs/tutorials/custom_weights.md
