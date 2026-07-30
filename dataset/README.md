# Dataset — Pepper Healthy vs Bacterial Spot

## Source

**Kaggle:** [Plant Disease Detection](https://www.kaggle.com/datasets/karagwaanntreasure/plant-disease-detection)
by **Karagwaan Ntreasure**

## Brief Description

The dataset is a subset of the PlantVillage collection containing leaf images for
multiple plant species and disease categories. For this project only the **bell pepper**
class is used, selecting two condition folders: `Pepper__bell___healthy` and
`Pepper__bell___Bacterial_spot`. All other plant types and disease categories are
excluded. Images are provided as flat class folders with no pre-made splits; the
notebook builds a stratified **70 / 15 / 15** train / val / test split at runtime using
a fixed seed (42). All images are resized to **224 × 224** pixels during loading. For
full details on collection method and licensing refer to the dataset page linked above.

## Structure (after runtime split)

```
pepper_split/
├── train/
│   ├── Healthy/
│   └── Bacterial_Spot/
├── val/
│   ├── Healthy/
│   └── Bacterial_Spot/
└── test/
    ├── Healthy/
    └── Bacterial_Spot/
```