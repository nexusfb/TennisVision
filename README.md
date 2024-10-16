# TennisVision

## Project Overview

This project aims to analyze tennis player performance using computer vision techniques. The system uses **OpenPose** for pose estimation, **SVM** for action recognition, and **DTW (Dynamic Time Warping)** to compare players' movements against professional players. This project was developed as part of the 'AI Lab: Computer Vision and NLP' course at La Sapienza University of Rome.

---

## Table of Contents
- [Introduction](#introduction)
- [Design](#design)
- [Implementation](#implementation)
- [Usage](#usage)
- [Technologies](#technologies)
- [Contributors](#contributors)

---

## Introduction

### Motivation

As tennis enthusiasts, we wanted to find a way to improve our game using technology. Tennis lessons can be expensive, dependent on various factors like weather, coach availability, and court time. Our solution is to use computer vision to analyze and improve tennis strokes.

### Goal

1. Use a single camera to analyze tennis movements.
2. Compare amateur shots to professional shots and provide a score based on how similar the movements are.

### Assumptions

- We focus on right-handed players.
- The camera view is from the back of the player.

---

## Design

### Pose Estimation

We use **OpenPose** to estimate the keypoints of a player's body. By focusing on each frame of a video sequence, OpenPose detects body parts as keypoints, allowing us to track movement accurately.

### Action Recognition

To classify strokes (Forehand, Backhand, Serve), we use **SVM** (Support Vector Machines). The player's body movements are tracked, and strokes are classified based on the relative position of the ball and player.

### Action Scoring

We compare a player's stroke to a professional player's stroke using **Dynamic Time Warping (DTW)**. DTW computes a similarity score by comparing time-series data of keypoints.

---

## Implementation

### Pose Estimation

We use OpenPose to detect body keypoints from the input video. A preprocessing function processes the video and organizes the output in terms of images, videos, and keypoints data.

### Action Recognition

Using labeled data, we train a **SVM** classifier to recognize strokes. The labeled frames are merged with keypoint data, and an SVM is trained to predict strokes on test data.

### Action Scoring

To score the strokes, we compute the DTW distance between the player's movements and a professional player's movements. Each keypoint gets a score, and the overall stroke score is an average of these keypoints' scores.

---

## Usage

1. **Setup**:
   Install required dependencies by running:
   ```bash
   pip install -r requirements.txt
   ```

## Running the Project

1. Place training videos in the `train` directory and test videos in the `test` directory.
2. Run the script to extract keypoints and classify actions.

### Scoring
Use the scoring function to compare movements with professional strokes.

---

## Technologies

- **OpenPose** for pose estimation.
- **Scikit-Learn** for SVM-based action recognition.
- **dtaidistance** for DTW (Dynamic Time Warping) comparison.

---

## Contributors

- **Federica Bruni** (1933963)
- **Maria Emilia Russo** (1966203)
