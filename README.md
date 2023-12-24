# Harris-Corner-Detection
Harris Corner Detection
import cv2
import numpy as np

def harris_corner_detection(image_path):
    image = cv2.imread(image_path)
    gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    gray = np.float32(gray)
    dst = cv2.cornerHarris(gray, 2, 3, 0.04)

    # Threshold for an optimal value, it may vary depending on the image
    image[dst > 0.01 * dst.max()] = [0, 0, 255]

    cv2.imshow('Harris Corner Detection', image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

# Example usage
image_path = 'path/to/your/image.jpg'
harris_corner_detection(image_path)
