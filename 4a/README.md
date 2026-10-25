# CS180 Project 4A: Image Warping & Mosaicing

## README

---

## 1. What's in this submission

```text
submission.zip
├── code/
│   ├── 4a.ipynb  #Image Warping & Mosaicing
│   └── README.md       #This file
└── web/
    └── page.pdf        #PDF export of the project webpage
```

The notebook contains markdown explanations, homography estimation, image warping, rectification, and mosaic blending. Additional comparisons and observations are available on the project webpage.

---

## 2. How to run the notebook

The notebook was developed and run in **Google Colab**. Run all cells **from top to bottom, in order**.

1. Open `Project4A.ipynb` in Google Colab. A CPU runtime is sufficient.
2. Run the setup cells and upload the input images using the filenames specified in the notebook.
3. Select 10 matching points for each mosaic pair, clicking the same features in the same order in both images.
4. For each rectification image, select the four corners in this order: top left, top right, bottom right, bottom left.
5. Run the remaining cells to generate the rectifications, interpolation comparisons, timings, and mosaics.

**Note:** Saved selections are reused automatically. To select points again, add the relevant mosaic label to `REDO_PAIRS` or image filename to `REDO_RECTIFICATIONS`. Colab runtime files and variables may be lost after disconnection, so download the exported results before ending the session.

---