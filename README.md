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

2. Accessing the pixel located in the fifth row and tenth column (5,10)

```python
image_arr[5][10]
```

3. Accessing the pixel located in the hundredth row and fourteenth column (100, 14)

```python
image_arr[100][14]
```

**OBS.<sub>1</sub>:** Note that the number of pixels depends on the image.

**OBS.<sub>2</sub>:** When we display a pixel, it's shown as a vector, as we can see below.

```python
[103  99  100]
```

Each vector position represents the red, green, and blue components, in that order.

## **References**

BATISTA, L. V. **Processamento digital de imagens**. 2022. 428 slides.

GONZALEZ, R. C.; WOODS, R. E.**Digital Image Processing**. 4. ed. New York: Pearson, 2018.
