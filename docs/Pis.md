# Pis

## Pi3
- [Backup image for 16GB SDCard, Jessie](https://drive.google.com/drive/folders/1_equhzbgl44xIteVRlxmfu4HFsB2h06P?usp=sharing)
* User: pi
* Password: NotreDame
* Wifis setup: 
    - NDSUAS
    - muizenberg
* cml copy to new 16GB SDcard formated to ext4 //If formated to FAT32 the image won't fit
    ```bash
    $ sudo umount /dev/sda
    $ sudo dd bs=4M if=SDCard.img of=/dev/sda status=progress
    $ sync
    $ umount /dev/sda
    ```
## FreeCad models
* [Model of Pi3](./3dfiles/Pi3Model.fcstd)
(I did not create this, do not credit me)
* [3DR Iris+ PiCaseShell Mount With all source stages](./3dfiles/PiCaseShell_AllSteps.fcstd)
* [3DR Iris+ PiCaseShell Mount Simple](./3dfiles/PiCaseShell_simple.fcstd)
