# ⚽ Player Re-Identification Assignment

## 🧠 Objective

This project addresses the challenge of player re-identification across multiple camera feeds — specifically broadcast and tacticam footage from a football match. The goal is to assign consistent IDs to players, even as they move between camera views or exit the frame.

---

## 📂 Folder Structure
├── botsort_broadcast/ # BoT-SORT output on broadcast video
├── botsort_tacticam/ # BoT-SORT output on tacticam video
├── Output/ # Cropped player images (per tracklet)
├── Embeddings/ # ResNet50 feature vectors for each crop
├── TrackletEmbeddings/ # (Optional) Experimental stage results
├── Visual_Matches/ # (Unused) For visual re-ID verification
├── extract_tracklets.ipynb # Crop extraction based on BoT-SORT + video
├── extract_embeddings.ipynb # Feature extraction using Torchreid
├── appearance_script.ipynb # Re-ID: Appearance-based matching (cosine sim)
├── matches.csv # Final match results (broadcast ↔ tacticam)
├── broadcast.mp4 / .avi # Broadcast camera footage
├── tacticam.mp4 / .avi # Tacticam footage
├── README.md # You're here
├── requirements.txt # All dependencies

Run the pipeline notebooks sequentially:

extract_tracklets.ipynb
→ Parses BoT-SORT labels & extracts player crops from both videos.

extract_embeddings.ipynb
→ Uses Torchreid + ResNet-50 to extract appearance embeddings.

appearance_script.ipynb
→ Matches players across views using cosine similarity.

Key Outputs:

Crops saved in Output/

Embeddings in Embeddings/

Final re-ID results in matches.csv

📌 Key Notes
Lightweight models were chosen (e.g., ResNet-50 via Torchreid) due to hardware constraints, ensuring the pipeline remains efficient and reproducible.

Torchreid was manually installed due to a pip deprecation warning.

The Visual_Matches directory was set up for visual inspection but left unused due to inaccurate early-stage overlay results.

❗ Known Limitations
Some cropped images include partial background or occlusion due to imperfect detection bounding boxes.

The visual inspection phase remains incomplete; re-ID is evaluated only via embeddings and cosine similarity.

💻 On Hardware Availability
This project was implemented without access to a dedicated GPU, influencing the selection of lightweight, CPU-friendly architectures. However, this was a temporary limitation — I’ll be switching to a MacBook Pro with enhanced compute capacity (M-series + SSD) next week.

As we advance, I’ll be fully equipped to handle deep re-ID models (e.g., TransReID, ViT) and more compute-intensive experimentation for deployment-grade pipelines.

✅ Requirements
torch==2.0.1
torchvision
torchreid
opencv-python
tqdm
numpy
pillow

👀 Final Remark
This solution prioritises correctness, reproducibility, and modularity, making it straightforward to extend or upgrade individual components (e.g., switching feature extractor models or integrating tracklet stitching).
