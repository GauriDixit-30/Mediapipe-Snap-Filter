# Mediapipe-Snap-Filter
🎭 Animated Snapchat-style Filters using MediaPipe
Bring your webcam to life with real-time animated filters like smoke effects and glowing eyes! This project uses MediaPipe’s Face Mesh and OpenCV to detect facial landmarks and intelligently apply dynamic filters based on expressions like mouth or eye movements.

✨ Features
🔍 Face Detection using MediaPipe

🎯 468-Point Facial Landmark Tracking (real-time)

👁️ Eye & Mouth Open Detection using geometric ratios

💨 Animated Smoke Filter when mouth is open

👀 Custom Eye Filters (e.g., left_eye.png, right_eye.png) on eye open

🖼️ Frame-by-Frame Overlaying using masking logic

⚡ Smooth Performance (~60+ FPS on modern machines)

🛠️ Setup
1. Install Dependencies


pip install opencv-python mediapipe matplotlib numpy

2. Media Folder Structure

Create a folder named media/ and add the following files:


media/
├── sample.jpg
├── sample2.jpg
├── sample3.jpg
├── left_eye.png
├── right_eye.png
└── smoke_animation.mp4

🔁 smoke_animation.mp4 should be a looping video with transparent background (if possible).

🧠 How It Works

📌 Core Functions

detectFacialLandmarks(image, face_mesh, display=True)

Converts image to RGB

Detects and draws face mesh (tessellation + contours)

Returns annotated image and detection results

getSize(image, face_landmarks, INDEXES)

Extracts a face part (like eye or lips)

Returns width, height, and landmark coordinates

isOpen(image, face_mesh_results, face_part, threshold, display=True)
Calculates the part’s height-to-face ratio

Returns whether a face part (like mouth/eyes) is OPEN or CLOSE

overlay(image, filter_img, face_landmarks, face_part, INDEXES, display=True)
Centers the overlay image on the face part

Resizes it (~2.5× of part height)

Applies transparency using masks

🎥 Real-Time Filter Application

The webcam is accessed with OpenCV’s VideoCapture. For each frame:

Flip for selfie-view

Detect facial landmarks

Check if eyes/mouth are open

Overlay:

Smoke if mouth is open

Eye filters if eyes are open

Display with FPS counter

▶️ Usage
Run the script:

python your_script.py

Press ESC to quit the real-time window
