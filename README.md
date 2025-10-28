## 🧠 Project Overview

This project focuses on **video-based upper-body exercise analysis** using **MediaPipe pose estimation**.
The goal is to extract joint motion parameters — such as **angles, displacement, velocity, acceleration, and jerk** — and analyze them to detect **fatigue, incorrect form, or injury risk**.

Since the dataset was externally sourced, the workflow involved **working backwards** from available videos to derive all possible measurable parameters.
The system pipeline includes pose estimation, kinematic feature extraction, signal filtering (FFT & Butterworth), repetition segmentation, and theoretical fatigue analysis.

Dataset: https://www.kaggle.com/datasets/hasyimabdillah/workoutfitness-video?resource=download-directory
Project Gdrive: https://drive.google.com/drive/folders/13d3gKZofFpBBctATwcOjMID9xfDYEImu?usp=sharing

---

## ⚙️ Project Workflow & Weekly Progress

### 🗓️ **27 June – Project Registration**

* Course and project registration initiated.

---

### 🗓️ **10 July – First Meeting**

* Discussed project title and direction.
* Dataset not self-collected → focus on extracting max possible parameters from available videos.
* Decided to use **MediaPipe** for joint tracking (shoulder, elbow, wrist).
* Aim: analyze **unloaded vs loaded upper-body exercises** for fatigue and form deviation.
* Identified initial parameters: **elbow angles**, ~32–33 metrics (jerk, displacement, velocity, acceleration).
* Planned visualization through **plots** and comparison between exercises.

---

### 🗓️ **30 July – Zeroth Review**

* Feedback: algorithm and model architecture not clearly specified yet.
* Action: formalize workflow and define processing pipeline.

---

### 🗓️ **31 July – Implementation Progress**

* Extracted all **33 parameters** from MediaPipe.
* Initial attempt at displacement, velocity, and acceleration — results inconsistent, required rework.

---

### 🗓️ **1 August – Weekly Review 3**

* Introduced **Taylor series / five-point derivative** for velocity and acceleration calculation.
* Verified units and scaling consistency.

---

### 🗓️ **8 August – Weekly Review 4**

**Enhancements:**

* Extended to **five exercises**: push-up, pull-up, bicep curl, shoulder press, bench press.
* Added **shoulder angle** (hip–shoulder–elbow) along with elbow angle.
* Generated **joint-angle plots** for left and right sides separately (to detect asymmetry/injury).
* Implemented **Displacement → Velocity → Acceleration** chain with X–Y trajectory plots.
* Verified formulas (diff, cumsum, trig functions like cos & arccos).

**Clarifications:**

* Observed jerks in velocity-time plots → caused by frame-level noise.
* Planned smoothing via **filters** to handle noise amplification in derivatives.

---

### 🗓️ **15 August – Leave**

---

### 🗓️ **22 August – CAT 1 Review**

* Interim review on progress and analysis direction.

---

### 🗓️ **29 August – Weekly Review 5**

* Addressed **multi-axis joint movement** (especially shoulders).
* Identified which axes dominate using **variance / PCA**.
* Recorded multiple videos per exercise for consistency.
* Replaced direct Mediapipe displacement values with **5-point numerical formula** (fixed zero-crossing bug in velocity).
* Added **3D trajectory plots** and **stick diagrams** for movement visualization.
* Defined **start/end reference points** for motion comparison.

---

### 🗓️ **5 September – Leave**

---

### 🗓️ **12 September – Weekly Review 6**

* Standardized one reference video for testing pipeline.
* Worked on **landmark jumping / overlap** issue → tested visibility thresholds and magnitude-based filtering.
* Designed **video inclusion criteria** using stability metrics.

---

### 🗓️ **17 September – Review 1**

* Finalized project timeline and task division.
* Clarified final objective and measurable deliverables.

---

### 🗓️ **26 September – Weekly Review 7**

* Changed X-axis representation to **time (seconds)** instead of frame count.
* Verified video frame rate for accurate time scaling.
* Implemented **FFT and Butterworth low-pass filter** to smooth signals.
* Began work on **rep segmentation** logic.

---

### 🗓️ **3 October – Review Cancelled**

---

### 🗓️ **10 October – CAT 2 Review**

* Presented progress on filtering and rep segmentation.

---

### 🗓️ **17 October – Weekly Review 8**

* Organized data into **two Excel files** per video:

  1. Raw extracted parameters (angles, coordinates).
  2. Processed data (displacement, velocity, acceleration).
* Rechecked velocity computation — resolved similarity issue between displacement and velocity.
* Used **angle range** and **velocity thresholds** to quantify repetitions.
* Finalized **rep segmentation rule:** start/end defined by frames where velocity > 5% of its peak.
* Corrected earlier FFT implementation — used appropriate **cut-off frequency (≈5 Hz)** based on PSD analysis.
* Added **PSD graphs** to confirm energy distribution across frequencies.
* Decided to conclude with **theoretical model analysis** using extracted features (fatigue / form classification).


want me to also add a **“📁 Repository Structure”** section after this (like showing folders `/data`, `/scripts`, `/plots`, `/models`, etc.) so your README looks fully professional?
