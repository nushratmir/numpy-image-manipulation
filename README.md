NumPy Image Lab

A from-scratch image manipulation toolkit built with NumPy. Every filter — grayscale, brightness, invert, and more — is implemented as raw array math, with no image-processing libraries doing the heavy lifting.

Why I built this

This is a deliberate learning project to consolidate my NumPy skills before moving deeper into the data science stack. The goal isn't to reinvent Pillow or OpenCV — it's to prove out the core insight that an image is just a NumPy array, and that most "filters" are simple operations on that array (slicing, broadcasting, boolean masking, axis reductions).

How it works

A color image loads as a 3D array of shape (height, width, 3) — the last axis holds the Red, Green, and Blue values (0–255) for each pixel. Once you see an image that way, the filters follow naturally:

Grayscale collapses the 3 color channels into 1
Brightness / contrast are arithmetic on the pixel values
Flip / crop are pure slicing
Invert is one operation across the whole array
Features
 Grayscale conversion
 Brightness adjustment
 Contrast adjustment
 Invert (negative)
 Horizontal / vertical flip
 Crop
 Blur (stretch goal)
Requirements
Python 3
NumPy
Pillow (only for reading/writing image files — all processing is NumPy)

Both come bundled with Anaconda.

Usage
python
import numpy as np
from PIL import Image
from operations import grayscale, adjust_brightness, invert

# Load an image as a NumPy array
arr = np.array(Image.open('sample_images/photo.jpg'))

# Apply a filter
gray = grayscale(arr)

# Save the result
Image.fromarray(gray).save('output.jpg')

See demo.ipynb for before/after examples of every filter.

Project structure
numpy-image-lab/
├── README.md
├── operations.py      # the image manipulation functions
├── demo.ipynb         # notebook showing before/after results
└── sample_images/     # test images
Notes

All processing is done in pure NumPy on purpose — in real-world work you'd typically reach for a dedicated library like OpenCV or Pillow's own filters. This project trades that convenience for a clearer understanding of what those libraries do under the hood.
