# Pis
*images*
- [Backup image for 16GB SDCard, Jessie](https://drive.google.com/drive/folders/1_equhzbgl44xIteVRlxmfu4HFsB2h06P?usp=sharing)
- [ORiginal VTAg Pi3 32G](https://drive.google.com/open?id=10BCtub5M6uTrdXMH0G2ZmeeP4FjZgO05)

## Pi3
* User: pi
* Password: NotreDame
* Wifis setup: 
    - NDSUAS
    - muizenberg
* cml copy to new 16GB SDcard formated to ext4 //If formated to FAT32 the image won't fit
    ```bash
    $ sudo umount /dev/sda1
    $ sudo dd bs=4M if=SDCard.img of=/dev/sda status=progress
    $ sync
    $ umount /dev/sda

    ```
### Ubuntu Mate on Pi3
	- Backup image
	- User: uvm
	- Password: BCO2&ag
	- Wifis setup
		* SSID: VTAg<number of pi> 1-6
		* psswd: BCO2&ag
* To create a new image from ubuntu.xz image:
   ``` bash
	$ unxz file.xz //-k if you want to keep the original

   ```
** [Networking for field drone pi setup](./UbuntuMateNetworking.md )**



##



## FreeCad models
* [Model of Pi3](./3dfiles/Pi3Model.fcstd)
(I did not create this, do not credit me)
* [3DR Iris+ PiCaseShell Mount With all source stages](./3dfiles/PiCaseShell_AllSteps.fcstd)
* [3DR Iris+ PiCaseShell Mount Simple](./3dfiles/PiCaseShell_simple.fcstd)
