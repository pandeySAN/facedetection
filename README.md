# facedetection
import cv2 as cv
import tkinter as tk
from tkinter import filedialog

# Create a Tkinter window
root = tk.Tk()
root.withdraw()

# Open a file dialog to allow the user to select an image file
file_path = filedialog.askopenfilename(filetypes=[('Image files', '*.jpg *.jpeg *.png')])

# Load the image from file
img = cv.imread(file_path)

# Convert the image from BGR to RGB format
img_rgb = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# Load the Haar cascade file
haar_cascade = cv.CascadeClassifier(r'C:\Users\victus\OneDrive\Desktop\SHIVA\venv\.vscode\project\harcascade.xml')

faces_rect = haar_cascade.detectMultiScale(img_rgb, scaleFactor=1.1, minNeighbors=3)
print(f'Number of faces found = {len(faces_rect)}')
# Display the image
cv.imshow("person", img_rgb)
cv.waitKey(0)
