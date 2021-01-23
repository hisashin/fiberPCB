# Getting started with fiberPCB, Fiber Laser DIY PCB

- [Why fiberPCB?](#why-fiberPCB?)
- [Useful References](#useful-references)
- [All required tools and expendables](#all-required-tools-and-expendables)
- [How to choose fiber laser](#how-to-choose-fiber-laser)
- [How to choose laminator](#how-to-choose-laminator)
- [Detailed steps to make fiberPCB by KiCAD](#detailed-steps-to-make-fiberPCB-by-KiCAD)
- [Detailed steps to make fiberPCB by EAGLE](#detailed-steps-to-make-fiberPCB-by-EAGLE)

## Why fiberPCB?

Let's compare fiberPCB with alternatives.

* Online PCB service
  * Best way as long as you can wait delivery for few days to weeks.
  * Sometimes you cannot wait. In my case, PCB of [opensource Realtime PCR](https://github.com/hisashin/Ninja-qPCR) was so complex that I have to iterate orders to integrate functions like LED control, photosensing, multiplexing and ADC.
* Chemical etching
  * Cheap but need skills for small pitches like 10 mil (0.25mm).
  * Need to drill all holes and cut contor manually after etching.
  * Harmful to the environment.
* CNC milling
  * I had [$2300 CNC designed for PCB millling](https://www.youtube.com/watch?v=cwREOBL9E-A) and noticed that required time and cares are proportionate to the complexity of the pattern.
  * You must replace end mills not to cut holes and contor after cutting patterns. Or you have to replace it every 50 meter stroke. Machine with auto tool changer is expensive. [LPKF ProtoMat S104](https://www.youtube.com/watch?v=GRow5AqFxZA) is around $30,000.
  * To cut small pitches, you cannot engrave deeply. If depth is not enough, small copper partcle may bridge the gap. I'm totally fed up with such problems.
* Commercial PCB laser machine.
  * Ridiculously expensive. "Entry model" [LPKF Photolaser ST](https://www.youtube.com/watch?v=WMgXvRwbaLw) is over $100,000.
* CO2 Laser
  * I've never tried CO2 laser etching. Please send pull request if you can compare.
  * Cannot etch metal without spraying black.
  * Focal diameter is 100 times larger and edge might be unclear at small pitches.
  
## Useful References
* [Making fine pitch PCB prototypes with fiber laser](https://www.kurokesu.com/main/2021/01/07/making-fine-pitch-pcb-prototypes-with-fiber-laser/?fbclid=IwAR3_8MipkpVS9d9DjpUQ1I7AqjXdvbW7uQoy86yiT56GoPLZ7w0Zegjyjy0)
* [Youtubes](https://www.youtube.com/playlist?list=PLIcr1mnww28Doh5sBvfblVOn0Wxk1qtYr)
 
## All required tools and expendables
* Gerber Files (Free)
* [FlatCAM](http://flatcam.org/), Gerver->CAM conveter
  - Installation guide for [Win](http://flatcam.org/manual/installation.html#windows), [Linux](http://flatcam.org/manual/installation.html#linux) and [OS-X](http://flatcam.org/manual/installation.html#osx). 
  - [It requires a lot](http://flatcam.org/manual/installation.html#requirements) including dead Python2.7. [Pip install](https://pypi.org/project/flatcam/#description) crush when saving projects. so I recommend to setup in [Docker Ubuntu Desktop](https://github.com/queeno/docker-ubuntu-desktop).
  ```
  docker run -d -v (somewheare gerber exists):/gerbers -v (somewheare for flatcam projects):/projects -it --name flatcam -p 5901:5901 queeno/ubuntu-desktop
  // My case
  docker run -d -v ~/github/fiberPCB/kicad/fiberPCB:/gerbers -v ~/github/fiberPCB/flatcam:/projects -it --name flatcam -p 5901:5901 queeno/ubuntu-desktop
  ```
  Connect VNC to vnc://localhost:5901, launch xterm then run these commands.
  ```
  apt-get update
  apt-get -y install git sudo wget
  //git clone https://bitbucket.org/jpcgt/flatcam <- latest one has different file structure
  wget https://bitbucket.org/jpcgt/flatcam/downloads/FlatCAM-8.5.zip
  unzip FlatCAM-8.5.zip
  cd FlatCAM-8.5
  sh setup_ubuntu.sh
  python FlatCAM.py
  ```
* [EZCAD](https://www.litlaser.com/ezcad), laser controller
* Fiber Laser
* Laminator
* UV illuminator
* Dry film
  * I first thought that Kapton film can replace it but that would be wrong.
* [FR-4](https://en.wikipedia.org/wiki/FR-4)

My case in Tokyo Japan :
| Item                | Price         | Shipping     | Comment |
| ------------------- |:-------------:| ------------:| ------------:|
| [Fiber Laser](https://www.aliexpress.com/item/32974751052.html?spm=a2g0s.9042311.0.0.65f44c4dIleBKp&fbclid=IwAR10NMvGiH47895B0QpRRJNL5SNHvLvtUy33UhqqUZfuPdR8BVw_eg-WCHc)         | $1,837.44     | $249.81 | 20W JPT 200x200mm DHL8-16days |
| [Laminator](https://www.lami-corporation.co.jp/archives/products/leon13dx/)           | $10.64        | $11.12       | Got $1800 worth one as junk. Replaced blown fuse:wink: |
| [UV illuminator](https://www.amazon.co.jp/gp/product/B07HFRDK3V/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1&fbclid=IwAR2NO4W7daOl4TgFSwwDDsZGD15Jek28WylPpzhUsRBBjHX5G8EQiuQLUwU)      | $4.73         | $0           | I will line them up for larger PCB |
| [Dry film](https://www.amazon.co.jp/gp/product/B01NCS88LU/ref=ppx_yo_dt_b_asin_title_o05_s01?ie=UTF8&psc=1&fbclid=IwAR3ORckfPM1z7tKVWN8LTQ-CgsBqjpBLfcwR8V2A0jhZy2ZhwNkz0N1GbfY)          | $19.15        | $0           | VANTIYAUS Zp00088(5m x 30cm) |
| [FR-4](https://www.sengoku.co.jp/mod/sgk_cart/detail.php?code=EEHD-4BPE)                | $1.64         | $0           | 1.6t x 75 x 100mm |
| Total               | $1873.6       | $260.93      |  $2395.46 include shippings |

## How to choose fiber laser
 * Stronger/Wider is not always better

## How to choose laminator
 * List confirmed to support 1.6mm thickness

## Detailed steps to make fiberPCB by KiCAD
 1. Design PCB as usual
   ![Step1](https://raw.githubusercontent.com/hisashin/fiberPCB/main/images/step1_design_pcb_kicad_test01.png)
 2. Export Gerber Files
   - In Pcbnew, Select \[File > Plot\] -> Check F.Cu, F.Paste, F.Mask and Edge.Cuts -> Click \[Plot\]
   ![Step2](https://raw.githubusercontent.com/hisashin/fiberPCB/main/images/step2_export_gerber_kicad.png.png)
   - Click \[Generate Drill Files...\] -> Click \[Generate Drill File\]
   ![Step2](https://raw.githubusercontent.com/hisashin/fiberPCB/main/images/step2_export_drl.png)
 3. Convert Gerber for CAM
   - Click \[File > Open Gerbers\] and select all gerbers exported at prior step.
   ![Step2](https://raw.githubusercontent.com/hisashin/fiberPCB/main/images/step3_open_gerbers.png)
 4. Convert CAM for EZCAD
 5. Cut patterns
 6. Print solder mask
 7. Open pads
 8. Cut holes and contor

## Detailed steps to make fiberPCB by EAGLE

// TODO
