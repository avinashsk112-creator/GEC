# Fiction AI: Webisodes, Best Scenes & Social Reels Generator

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/avinashsk112-creator
/GEC/blob/main/BPNT.ipynb)

An automated offline media pipeline designed for broadcast fiction drama. It ingests master episodes, indexes dialogue via Faster-Whisper, detects physical scene cuts, isolates dramatic highlights, smart-crops to **9:16** and **1:1** using active-character torso tracking, normalizes audio to **-24 LKFS (EBU R128)**, and packages client-ready assets.

---

## Deliverables Generated per Episode

| Asset Type | Aspect Ratio | Target Duration | Specs / Processing |
| :--- | :--- | :--- | :--- |
| **Webisode Story Beats** | 16:9 | 60–90s per act | Master cut, dialogue anchors, EBU R128 (-24 LKFS) |
| **Best Scene** | 16:9 | 2–3 mins | Highest dialogue density, scene-cut snapped |
| **Reels (2 Units)** | 9:16 & 1:1 | 50–60s each | Active-speaker torso tracking, shot-locked smooth reframe |
| **Thumbnails** | 16:9 | 2 frames per clip | Climax & reaction frame captures |
| **Metadata** | N/A | Manifest | JSON timecode manifest + CSV cue sheet |

---

## How to Run (For Collaborators & Editors)

1. Click the **Open In Colab** badge above.
2. In the top menu, go to **Runtime** → **Change runtime type** and set the hardware accelerator to **T4 GPU** (or A100).
3. In the menu, click **Runtime** → **Run all** (or execute cells sequentially from Cell 1 to Cell 8).
4. At **Cell 8**, click the **Upload Episode Video** button and select your master video file (`.mp4`, `.mov`, `.mkv`).
5. Once processing finishes, run **Cell 9** to automatically download the packaged `episode_delivery_package.zip`.

---

## Output Structure

The exported `.zip` file extracts to the following directory layout:

```text
output_delivery/
├── metadata/
│   ├── delivery_manifest.json       # Machine-readable timecodes, categories & rationales
│   └── delivery_manifest.csv        # Standard broadcast cue sheet
├── clips/
│   ├── 1_Best_Scene_16x9.mp4        # 2–3 min continuous dramatic cut (-24 LKFS)
│   ├── 2_Reel_1x1.mp4               # 50–60s centered 1:1 square crop
│   ├── 2_Reel_9x16.mp4              # 50–60s active-speaker vertical 9:16 crop
│   └── 3_Webisode_Beat_16x9.mp4     # Narrative story beats for NLE assembly
└── thumbnails/
    ├── 1_Best_Scene_thumb1.jpg
    └── 1_Best_Scene_thumb2.jpg
