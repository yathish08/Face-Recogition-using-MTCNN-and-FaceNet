# Face Recognition using MTCNN and FaceNet

This script performs real-time face detection and recognition using the MTCNN face detector and the FaceNet model. It captures video from the default webcam, detects faces, generates embeddings, and compares them to a database of known faces for recognition.

## Overview

### Initialization
- The script initializes the MTCNN face detector and the FaceNet model.
- It loads known face embeddings from `known_faces.npy` if the file exists.

### Webcam Capture
- The script opens the default webcam for video capture.

### Face Detection
- In each frame, MTCNN detects faces and returns their bounding boxes.

### Face Embedding Generation
- For each detected face:
  - The face region of interest (ROI) is extracted from the frame.
  - The ROI is resized to 160x160 pixels (required by FaceNet).
  - The ROI is converted to a PyTorch tensor and normalized.
  - The FaceNet model generates a 128-dimensional embedding for the face.

### Face Recognition
- The `recognize_face` function compares the generated embedding to the stored embeddings in `known_faces.npy` using cosine distance.
- If the minimum distance is below a specified threshold, the function returns the associated name.

### Display
- Bounding boxes are drawn around detected faces, and recognized names (if found) are displayed on the frame.

### Loop
- The script continues processing frames until the user presses the 'q' key.

## Installation and Usage

### Clone the Repository (Optional)
- If you're using Git, clone the repository. Otherwise, create a directory and place the Python script (`face_recognition.py`) inside.

### Prepare Known Faces
1. Place images of the people you want to recognize in a directory. Clear, frontal views of faces are recommended.
2. Run the script once, providing the path to an image as an argument or by modifying the `image_path` variable. The script will generate the embedding and save it to `known_faces.npy`.
3. Repeat for each person you want to add, changing `image_path` each time. The script will load existing embeddings, add the new one, and save the updated file. The name associated with the embedding is derived from the image filename.

### Steps to Run
1. **Prepare Known Faces**: Follow the steps in the "Installation and Usage" section to create the `known_faces.npy` file.
2. **Run the Script**:
   ```bash
   python face_recognition.py

   ## Webcam Interaction
- The webcam feed will be displayed in real-time.
- Faces will be detected and recognized as they appear in the feed.
- Press the 'q' key to exit the application.

## Future Enhancements
- **Real-time Performance Optimization**: Explore techniques to speed up the recognition process, especially for a large number of known faces (e.g., k-d trees).
- **GUI**: Develop a graphical user interface for easier interaction and improved user experience.


## Contributions
Contributions are welcome! Please submit pull requests or open issues for bug reports or feature requests.

## License
This project is distributed under the **Apache License 2.0**. See the [LICENSE](LICENSE) file for more details.
