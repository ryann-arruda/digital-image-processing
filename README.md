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

So, to display the red color channel of an image, for example, we must redefine the green and blue color channels as follows.

```python
image_r[:,:,1] = 0
image_r[:,:,2] = 0
```

The result when displaying the image is shown below.

![red color channel](https://user-images.githubusercontent.com/53544629/215169226-85022461-ca19-40b7-856a-ee73d13be8e6.png)

 For the other channels, we do it in a similar way.
 
 **OBS.:** The complete code can be seen by [clicking here](https://github.com/ryann-arruda/digital-image-processing/blob/master/digital_image_processing.ipynb).

## **References**

BATISTA, L. V. **Processamento digital de imagens**. 2022. 428 slides.

GONZALEZ, R. C.; WOODS, R. E.**Digital Image Processing**. 4. ed. New York: Pearson, 2018.
