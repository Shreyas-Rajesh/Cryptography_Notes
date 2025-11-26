The Python Imaging Library adds image processing capabilities to your Python interpreter. 

Import `PIL`  to use Pillow. 
And there are multiple modules that you can use to handle files

### Image module
`from PIL import Image`
Similar to file handle create a image handle by using `Image.open("location")`. Here we are going to use `img` as the handle.

1. `img.show()` - to show an image.
2. `img.save("File_name")` - to save an image
	This method can also be used to change the filetype. But note that the file type must be compatible (PNG has alpha channels but JPEG's don't).  
	- `image.save("File_Name", "JPEG")` -  to change file type
3. `img.mode()` - To show the mode of the image.
	- [Modes](https://pillow.readthedocs.io/en/stable/handbook/concepts.html) : Refer this page for different modes
4. `img.convert("Mode")` - To convert an image from one mode to another.
5. `img.size` - Returns a tuple containing the height and width of the image.
6. `img.format` - Returns the image file format.
7. `img.rotate(Value)` - To rotate an image by the specified angle, counter-clockwise.
8. `img.resize(size, resampling = 0)` - Returns the resize copy of the image
	- Interpolation happens during the resize process, due to which the quality of image changes whether it is being upscaled (resized to a higher dimension than original) or downscaled (resized to a lower Image then original)
9. `img.crop(left,upper,right,lower)` - To crop the image by reducing the number of pixels specified by the float value, from the respective position.

### ImageChops module
`from PIL import ImageChops as im`
1. `im.duplicate(image)` - Returns the duplicate of an image
2. `im.add(image1, image2, scale, offset)` - To add two images
	- Adds two images, dividing the result by scale and adding the offset. If omitted, scale defaults to 1.0, and offset to 0.0.
3. `im.subtract(image1, image2, scale, offset)` - To subtract images
	- Subtracts two images, dividing the result by scale and adding the offset. If omitted, scale defaults to 1.0, and offset to 0.0.
4. `im.subtract_modulo(image1, image2, scale, offset)` - Subtract two images, without clipping the result.
5. `im.darker(image1, image2)` - Compares the two images, pixel by pixel, and returns a new image containing the darker values.
6. `im.difference(image1,image2)` - Returns the absolute value of the pixel-by-pixel difference between the two images.
7. `im.logical_and(image1, image2)` - Logical AND between two images.
	- It requires both images to be in mode "1"
	- If you want to do this for other than mode "1", `im.multiply()` one image and a black and white mask
8. `im.multiply(image1, image2)` : Superimposes two images on top of each other.
	- If you multiply an image with a solid black image, the result is black. If you multiply with a solid white image, the image is unaffected.
9. `im.logical_or(image1, image2)` - Logical OR between two images.
10. `im.logical_xor(image1, image2)` - Logical XOR between two images.