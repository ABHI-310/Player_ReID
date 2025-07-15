**README.md**

# Player Re-Identification Assignment

## Overview

This project tackles the challenge of player re-identification across different camera views in a football match setting. It aims to ensure consistent player identity even as players move between the broadcast and tacticam footage.

## Folder Structure

```
.
├── botsort_broadcast/         # BoT-SORT tracking results on broadcast video
├── botsort_tacticam/          # BoT-SORT tracking results on tacticam video
├── Output/                    # Extracted player crops from both cameras
├── Embeddings/                # Saved embeddings for each tracklet
├── TrackletEmbeddings/        # Optionally used during experimentation
├── Visual_Matches/            # (Empty) Placeholder for visual verification
├── extract_tracklets.ipynb    # Tracking + crop extraction
├── extract_embeddings.ipynb   # Embedding extraction from cropped images
├── appearance_script.ipynb    # Final matching using appearance features
├── matches.csv                # Final matching result between broadcast and tacticam
├── broadcast.mp4 / .avi       # Broadcast video
├── tacticam.mp4 / .avi        # Tacticam video
├── README.md                  # This file
├── requirements.txt           # Python dependencies
```

## Setup Instructions

1. **Install dependencies:**

```bash
pip install -r requirements.txt
```

2. **Run the following notebooks in order:**

   * `extract_tracklets.ipynb`: Uses BoT-SORT labels + videos to extract player crops
   * `extract_embeddings.ipynb`: Uses Torchreid (ResNet-50) to extract embeddings
   * `appearance_script.ipynb`: Matches players across cameras using cosine similarity

3. **Output:**

   * Player crops saved in `Output/`
   * Embeddings saved in `Embeddings/`
   * Final matches in `matches.csv`

## Notes

* Due to lack of GPU, heavier models like TransReID were not used.
* Torchreid was installed manually due to a deprecation warning.
* Preprocessing, cropping, and matching were all optimised for correctness and reproducibility.

## Known Limitations

* A few cropped images contained background noise due to detection inaccuracy.
* Visual\_Matches folder remains unused due to incorrect results during visualization.

## Note on Hardware Availability

During the assignment, I faced certain limitations due to lack of access to high-end hardware (specifically GPU support), which influenced my choice of models and methods. However, this constraint was temporary — I’ll be switching to a new mac with significantly better capabilities by next week.

With this upgrade, I’ll be fully equipped to work efficiently and independently throughout the internship, including handling more comput-intensive models and experiments without interruption.

---

**requirements.txt**

```
torch==2.0.1
opencv-python
tqdm
numpy
pillow
torchreid
torchvision
```
