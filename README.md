# Getting started with fiberPCB, Fiber Laser DIY PCB

- [Why fiberPCB?](#why-fiberPCB?)
- [Useful References](#useful-references)
- [All required tools and expendables](#all-required-tools-and-expendables)
- [How to choose fiber laser](#how-to-choose-fiber-laser)
- [How to choose laminator](#how-to-choose-laminator)
- [Detailed steps to make fiberPCB](#detailed-steps-to-make-fiberPCB)

## Why fiberPCB?
* Chemical etching
  * Cheap but need skills for small pitches like 10 mil (0.25mm). Harmful to the environment.
* CNC milling
  * I had [USD2300 one designed for PCB millling](https://www.youtube.com/watch?v=cwREOBL9E-A) and noticed that required time and cares are proportionate to the complexity of the pattern.
  * You must replace end mills not to cut contor after cutting patterns. Or you have to replace it every 50 meter stroke. Machine with auto tool changer is expensive. [LPKF ProtoMat S104](https://www.youtube.com/watch?v=GRow5AqFxZA) is around USD30,000.
* Commercial PCB laser machine.
  * Ridiculously expensive. "Entry model" [LPKF Photolaser ST](https://www.youtube.com/watch?v=WMgXvRwbaLw) is over USD100,000.
  
## Useful References
* [Making fine pitch PCB prototypes with fiber laser](https://www.kurokesu.com/main/2021/01/07/making-fine-pitch-pcb-prototypes-with-fiber-laser/?fbclid=IwAR3_8MipkpVS9d9DjpUQ1I7AqjXdvbW7uQoy86yiT56GoPLZ7w0Zegjyjy0)
* [Youtubes](https://www.youtube.com/playlist?list=PLIcr1mnww28Doh5sBvfblVOn0Wxk1qtYr)
 
## All required tools and expendables
* Gerber Files (Free)
* Fiber Laser
* [EZCAD](https://www.litlaser.com/ezcad), laser controller software (Free)
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
| [UV illuminator](https://www.amazon.co.jp/gp/product/B07HFRDK3V/ref=ppx_yo_dt_b_asin_title_o02_s00?ie=UTF8&psc=1&fbclid=IwAR2NO4W7daOl4TgFSwwDDsZGD15Jek28WylPpzhUsRBBjHX5G8EQiuQLUwU)      | $4.73         | $0           | |
| [Dry film](https://www.amazon.co.jp/gp/product/B01NCS88LU/ref=ppx_yo_dt_b_asin_title_o05_s01?ie=UTF8&psc=1&fbclid=IwAR3ORckfPM1z7tKVWN8LTQ-CgsBqjpBLfcwR8V2A0jhZy2ZhwNkz0N1GbfY)          | $19.15        | $0           | VANTIYAUS Zp00088(5m x 30cm) |
| [FR-4](https://www.sengoku.co.jp/mod/sgk_cart/detail.php?code=EEHD-4BPE)                | $1.64         | $0           | 1.6t x 75 x 100mm |
| Total               | $1873.6       | $260.93      |  $2395.46 include shippings |

## How to choose fiber laser
 * Stronger/Wider is not always better

## How to choose laminator
 * List confirmed to support 1.6mm thickness

## Detailed steps to make fiberPCB
 * Export Gerber Files
 * Convert files for EZCAD
 * Cut patterns
 * Print solder mask
 * Open pads
 * Cut holes and contor



