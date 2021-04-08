# Responsive images
How (not) to use srcset and sizes. 

## version history
* **2021-04-08** Initial commit. Needs more work.

## Introduction
Using two new attributes (srcset="" and sizes=""), modern browsers can download and present specific images depending on the current screen width.

## Browser support
<img width="1367" alt="grafik" src="https://user-images.githubusercontent.com/68318893/114036064-07430280-9880-11eb-841c-2e94ddd6d654.png">
**Source:** https://caniuse.com/?search=srcset

95% of all browsers can more or less make use srcset

## srcset Usage 
The browser has no knowlege about the dimensions of an image before it downloaded it from its source.

The srcset attribute offers the browser a list of images and also tells it what width each one is supposed to have.

Depending on the current screen width and the DPR (Device Pixel Ratio), the browser will pick one of theses images and download it. All other pictures are ignored.

**Important** Depending on the DPR of a device, different images will be loaded at the same screen width.

If the screen size is later changed (orientation change, windows resize), it will reconsider its decision and download another image that fits the curent environment.

**2do** Check what happens if this image cannot be downloaded

### Device Pixel Ratio (DPR)
DPR is a measure of how many pixels a screen will fit into a CSS pixel (in one direction). The exact number depends on the screen:

#### Examples for DPR on different devices
* my old Thinkpad Laptop has a DPR of 1, 
* my apple iMacs 2017 has a DPR of 2, 
* my Google Nexus phone has a DPR of 3.5.

### Example 1:
**Notes** This image has no default (src is empty).The scrset attribute lists 4 different images.

```
<img 
     src=""
     srcset="uploads/2736/bilder/srcset/1200x576.png 1200w,
             uploads/2736/bilder/srcset/992x576.png   992w,
             uploads/2736/bilder/srcset/576x576.png   768w,
             uploads/2736/bilder/srcset/576x576.png   576w"
     alt="srcset Test"
>
```

For this example the screen width on all devices is reduced to 412px. 


| Device | Thinkpad L520 Laptop | iMac (Retina 5K, 2017) | Google Nexus 2 |
|--------|-----------------------|------------------------|----------------|
| DPR | 1.0 | 2.0 | 3.5|
| Screen width | 412px | 412px | 412px |
| DPR relative width | 412px | 816px | 1442px |
| Result | ![DPR 1.0](https://user-images.githubusercontent.com/68318893/114030528-d1e7e600-987a-11eb-907f-5734adde0b09.jpeg) | ![DPR 2.0](https://user-images.githubusercontent.com/68318893/114030534-d2807c80-987a-11eb-887b-9f415771bc9e.jpeg) | ![DPR 3.5](https://user-images.githubusercontent.com/68318893/114030537-d3191300-987a-11eb-8b82-012c0251c978.jpeg) |
| Notes | 576x576.png is wide enought to cover the area | Image 576x576.png and 576x576.png are to small, but image 992x576.png covers the area. | Image 1200x576.png is the largest image available. Its too small, but we can't be picky here. |

**Learned:** Initial image loaded corresponds to current screensize. If I have 992 or more px. The one loaded is 1200px wide. 

# Bookmarks

## Further reading
* https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images
* https://salferrarello.com/responsive-images-srcset/
* https://blog.kulturbanause.de/2014/09/responsive-images-srcset-sizes-adaptive/
* https://css-tricks.com/responsive-images-youre-just-changing-resolutions-use-srcset/
* https://cloudfour.com/thinks/responsive-images-101-definitions/
* https://tomroth.com.au/dpr/
* http://adaptive-images.com/
* https://blog.assistancy.be/blog/reponsive-images-bootstrap-wordpress

## tools
https://www.mydevice.io/
