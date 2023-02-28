# Digital Image Processing

All the information presented here was gathered by me through my studies in the Digital Image Processing class teached by Professor Leonardo Vidal Batista, bibliographic research carried out and personal practices.

## **Introduction**

A grayscale image is a two-dimensional function **f(x,y)**, where **x** and **y** are spatial coordinates and **f** is a gray level of the image at that point. However, if **x**, **y** and **f** are finite and discrete values, then the image is called a digital image. Thus, a digital image is composed of a finite number of elements called **picture elements** (pixel).

The pixel is based on the RGB color model, where a color is formed by combining R (red),G (green) and B (blue) components with integer values ranging from 0 to 255. Thus, a pixel is a vector that has both components.

Therefore, image processing consists of techniques where their input and output are images, enabling the application of noise reduction, contrast enhancement, image subtraction and other processing for human and computational interpretation, for aesthetic purposes, storage and transmission.

## **Dependencies and Development Environment**

All techniques presented here were implemented in *Google Collaboratory* using the Python programming language and the following dependencies:

- PIL (Python Imaging Library)
- Matplotlib
- Numpy
- OS

## **Implementation of Techniques**

Initially, it's important to understand how to load and display an image, as well as how to access a pixel using dependencies.

First, it's important to know which image formats are accepted by the PIL library, so to check this we run the following command:

```python
features.pilinfo()
```
 
Now, to make programming practice easier, let's move our workspace inside the images folder, as follows:

```python
os.chdir("/content/Drive/MyDrive/@DIP/Images")
```

We'll then load and store an image via the following statement:

```python
image = Image.open("fruits.jpg")
```

Now, it's important to know how to display an image to check what's happening when you apply any technique. So, to display an image just run the command below.

```python
plt.imshow(image)
```

Finally, let's get to know how to access any pixel of an image easily. However, it's first necessary to convert an image to a Numpy Array, but this is done extremely easily, as we can see below.

```python
image_arr = np.array(image)
```

So, to explain how to access any pixel, we'll give three examples.

1. Accessing the first pixel (0,0):

```python
image_arr[0][0]
```

2. Accessing the pixel located in the fifth row and tenth column (5,10):

```python
image_arr[5][10]
```

3. Accessing the pixel located in the hundredth row and fourteenth column (100, 14):

```python
image_arr[100][14]
```

**OBS.<sub>1</sub>:** Note that the number of pixels depends on the image.

**OBS.<sub>2</sub>:** When we display a pixel, it's shown as a vector, as we can see below.

```python
[103  99  100]
```

Each vector position represents the red, green, and blue components, in that order.

### **Displaying Color Channels Individually**

To display a color channel without interference from another, we must redefine which ones shouldn't contribute by accessing the pixels, as explained, assigning them the value 0.

Then, consider the following image.

![reference image](https://user-images.githubusercontent.com/53544629/215173991-21749a5d-2a18-4d09-aa83-c97582c922c3.png)

So, to display the red color channel of this image, for example, we must redefine the green and blue color channels as follows.

```python
image_r[:,:,1] = 0
image_r[:,:,2] = 0
```

The result when displaying the image is shown below.

![red color channel](https://user-images.githubusercontent.com/53544629/215169226-85022461-ca19-40b7-856a-ee73d13be8e6.png)

 For the other channels, we do it in a similar way.
 
 **OBS.:** The complete code can be seen by [clicking here](https://github.com/ryann-arruda/digital-image-processing/blob/master/digital_image_processing.ipynb).
 
 ### **Conversion from RGB color space to YIQ color space**
 
The first TVs displayed images in black and white, however, when new TVs that displayed images in color began to be sold, it was important to offer compatibility with the old system so that people didn't have to change sets.

So researchers started studying how to encode RGB values into the TV signal. So they decided to add two chrominance (color information) components in addition to the luminance that already enabled black and white images on older systems.

In this sense, the National Television Standard Committee (NTSC) system defined the YIQ color space, where Y is the luminance and I, Q are the chrominances.

$$ Y = 0.299R + 0.587G + 0.114B $$

$$ I = 0.596R - 0.274G - 0.322B $$

$$ Q = 0.211R - 0.523G + 0.312B $$

Also, it's important to note that the YIQ color space is only used for transmission, not for display, so if you try to display a strange image will appear, as we can see below.

![trying_to_displaying_the_YIQ_image](https://user-images.githubusercontent.com/53544629/221473672-f61b6755-169e-43c7-947e-5f703893181f.png)

Thus, after receiving the transmitted image, it's necessary to convert it to the RGB color space to display it. 

$$ R = Y + 0.956I + 0.621Q $$

$$ G = Y - 0.272I - 0.647Q $$

$$ B = Y - 1.106I + 1.702Q $$

 **OBS.:** The complete code can be seen by [clicking here](https://github.com/ryann-arruda/digital-image-processing/blob/master/digital_image_processing.ipynb).

## **References**

BATISTA, L. V. **Processamento digital de imagens**. 2022. 428 slides.

GONZALEZ, R. C.; WOODS, R. E.**Digital Image Processing**. 4. ed. New York: Pearson, 2018.

GUNJAL, B.L.; MALI, S. N. Comparative Performance Analysis of DWT-SVD Based Color Image Watermarking Technique in YUV, RGB and YIQ Color Spaces. International Journal of Computer Theory and Engineering, \[S.I.\], v. 3, n. 6, p. 714-719, Dec. 2011.

IBRAHEEM, N. A. et al. Understanding Color Models: A Review. ARPN Journal of Science and Technology, \[S.I.\], v. 2, n. 3, p. 265-275, Apr. 2012.

TKALCIC, M.; TASIC, J. F. Colour spaces - perceptual, historical and applicational background. The IEEE Region 8 EUROCON 2003. Computer as a Tool, Ljubljana, v.1, p. 304-308, 2003.
