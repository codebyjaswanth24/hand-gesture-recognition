# hand-gesture-recognition
 It simulates gesture recognition by comparing predefined 2D array patterns representing basic gestures like "thumbs up," "palm," and "fist." The system uses a simple pixel-wise comparison function to identify the closest matching pattern and return the associated gesture label.
# --- Mock data and model implementation ---

# Fake image data: 2D lists simulating grayscale 3x3 images
gesture_data = {
    "thumbs_up": [[0, 0, 0], [1, 1, 1], [0, 0, 0]],
    "palm":      [[1, 1, 1], [1, 0, 1], [1, 1, 1]],
    "fist":      [[1, 1, 1], [1, 1, 1], [1, 1, 1]]
}

# "Trained" gesture patterns (simplified)
trained_patterns = {
    "thumbs_up": [[0, 0, 0], [1, 1, 1], [0, 0, 0]],
    "palm":      [[1, 1, 1], [1, 0, 1], [1, 1, 1]],
    "fist":      [[1, 1, 1], [1, 1, 1], [1, 1, 1]]
}

# Simple comparison function (measuring match)
def compare_images(img1, img2):
    score = 0
    for i in range(len(img1)):
        for j in range(len(img1[i])):
            if img1[i][j] == img2[i][j]:
                score += 1
    return score

# Inference: identify gesture from input image
def classify_gesture(input_image):
    best_score = -1
    best_label = "unknown"

    for label, pattern in trained_patterns.items():
        score = compare_images(input_image, pattern)
        if score > best_score:
            best_score = score
            best_label = label

    return best_label

# --- Example usage ---
input_image = [[0, 0, 0], [1, 1, 1], [0, 0, 0]]  # Should match "thumbs_up"
result = classify_gesture(input_image)
print("Detected gesture:", result)
