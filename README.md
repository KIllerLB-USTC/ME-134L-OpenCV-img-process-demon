# ME-134L-OpenCV-img-process-demon

Discussed:

# Binary image process principle
## How computer store images
![Pixel](https://www.researchgate.net/profile/Shihab-Shawkat/publication/328828460/figure/fig14/AS:694959833362438@1542702744693/Figure-216-A-8-bit-grayscale-image-pixel-value-ranges-between-0-black.jpg)

Figure 0: image is a matrix, value in the matrix are the depth
![BitDepthCompared](https://www.projectorcentral.com/images/articles/BitDepthComparedgrayscale-600.jpg)

Figure 1: Comparison of bit-depth gradations (note: illustration limited to 8-bits due to web limitations)

![bitdepthdef](https://www.projectorcentral.com/images/articles/Fig1-BitDepthValues-600.jpg)

Figure 2 : the bitdepth is defined by $2^{bit}$ 8bit -> $2^{8} =256$


![ProjectorCentral 10-bit HDR Grayscale Pattern](https://www.projectorcentral.com/images/articles/RGB-Explained-600.jpg)

Figure 3: how color image has the color, instead of one channel, commonly we use three channel for the images stroage(e.g. RGB), and the image is the overlapping of the three channel's grey scale

## Why binary img
Binary images are digital images that consist of pixels with only two possible values, typically represented as black and white. They have several important applications and advantages in image processing and computer vision:

### Key Characteristics

- Each pixel is represented by a single bit - either 0 (black) or 1 (white)[1][5].
- Binary images are the simplest type of digital images[4].
- They can be efficiently stored as bitmaps (packed arrays of bits)[5].

### Advantages

- **Simplicity**: Binary images are easy to process, store, and analyze due to their simple two-state nature[1][4].

- **Small File Size**: A 640x480 binary image requires only 37.5 KiB of storage, making them efficient for transmission and storage[5].

- **Computational Efficiency**: Processing binary images requires less computational time and resources[2].

- **Noise Immunity**: Binary signals are unambiguous, providing resistance to noise in image processing[6].

- **Perfect Replication**: Binary data can be copied flawlessly without degradation[6].

### Applications

Binary images are used in various fields and applications, including:

1. **Optical Character Recognition (OCR)**: For separating text from backgrounds[1][2].

2. **Industrial Automation**: 
   - Quality control and defect detection (e.g., in printed circuit boards)[4].
   - Object detection on assembly lines[1].

3. **Medical Imaging**: 
   - Segmentation in X-rays, MRIs, and other medical scans[1][2].
   - Enhancing specific features in medical images[1].

4. **Biometrics**: 
   - Fingerprint recognition[1][4].
   - Iris recognition[2].

5. **Computer Vision Tasks**:
   - Edge detection[3].
   - Pattern recognition[1].
   - Object detection and tracking[1][2].

6. **Document Analysis**: Enhancing clarity of handwritten or printed text[1].

7. **Barcode and QR Code Scanning**: Simplifying recognition processes[1].

8. **Machine Vision**: Identifying objects on production lines[1].

Binary images, despite their simplicity, play a crucial role in various image processing tasks and serve as a foundation for more complex computer vision applications.

Citations:

[1] https://cloudinary.com/glossary/binary-image

[2] https://www.geeksforgeeks.org/binary-image/

[3] https://homepages.inf.ed.ac.uk/rbf/CVonline/LOCAL_COPIES/OWENS/LECT2/node3.html

[4] https://cave.cs.columbia.edu/Statics/monographs/Binary%20Images%20FPCV-1-3.pdf

[5] https://en.wikipedia.org/wiki/Binary_image

[6] https://computerscience.chemeketa.edu/cs160Reader/Binary/Binary.html

[7] https://www.v7labs.com/blog/image-processing-guide

### Hands On OpenCV Binary process
![opencvlog](https://upload.wikimedia.org/wikipedia/commons/thumb/3/32/OpenCV_Logo_with_text_svg_version.svg/360px-OpenCV_Logo_with_text_svg_version.svg.png)

#### what is Opencv

**There is no doubt, opencv is the library make your computer could observe the real world**

OpenCV is a cross-platform library that provides a comprehensive set of tools and functions for image and video processing, analysis, and manipulation. It was originally developed by Intel in 1999 and is now maintained by a community of developers under the OpenCV Foundation.
OpenCV is extremely important in the field of computer vision and image processing. 
### key steps of Binary process 
1. original img
2. convert to grey 8 bit img $2^8$ (0-255)
3. Set threshold for binary img conversion,
    - method1:**cv2.THRESH_BINARY** pixel value < TH --> 0
    - method2:**cv2.THRESH_BINARY_INV** pixel value < TH --> 1
4. optional process: you can add the blur process before step2 via Gaussian Blur filter to denoise the low frequency noise

![]

### For binary:
- simple binary img:**cv2.threshold**
    - stastic threshold and manually tunning.
    - Analysis the image histogram get the threshold --> otsu's method
    [otsu wiki][https://www.wikiwand.com/en/articles/Otsu's_method]
- adaptive binary (kernel: gaussian or mean):**cv2.adaptiveThreshold**
    - Why adaptive: tunning the threshold dynamically.
    - Dive into details: The adaptiveMethod decides how the threshold value is calculated: **cv.ADAPTIVE_THRESH_MEAN_C**: The threshold value is the mean of the neighbourhood area minus the constant C.**cv.ADAPTIVE_THRESH_GAUSSIAN_C**: The threshold value is a gaussian-weighted sum of the neighbourhood values minus the constant C.
The blockSize determines the size of the neighbourhood area and C is a constant that is subtracted from the mean or weighted sum of the neighbourhood pixels.

#### Further reference:
[Opencv_documentation](https://docs.opencv.org/4.x/d7/d4d/tutorial_py_thresholding.html)

[Opencv_application](https://viso.ai/computer-vision/opencv/)

