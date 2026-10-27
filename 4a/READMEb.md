# CS180 Project 4B: Feature Matching for Autostitching

## README

---

## 1. What's in this submission

```text
submission.zip
├── code/
│   ├── 4b.ipynb        # Part B: Feature Matching for Autostitching
│   └── README.md      # This file
└── web/
    └── page.pdf       # PDF export of the project webpage, including Parts A and B
```

The Part B notebook contains Harris corner detection, Adaptive Non-Maximal Suppression (ANMS), normalized feature descriptor extraction, feature matching, and four-point RANSAC homography estimation. It reuses the image warping and feathered blending functions from Part A to generate three automatic mosaics.

The project webpage includes corner detection comparisons with and without ANMS, sample descriptors, matched features, RANSAC results, and side-by-side comparisons of manually and automatically stitched mosaics. The Part A content is also included.

---

## 2. How to run the notebook

The notebook was developed and run in **Google Colab**. Run all cells **from top to bottom, in order**.

1. Open `4b.ipynb` in Google Colab. A CPU runtime is sufficient.

2. Run the setup cell and upload the six original photographs using these filenames:
   - `mosaic1_left.jpg` and `mosaic1_right.jpg`
   - `mosaic2_left.jpg` and `mosaic2_right.jpg`
   - `mosaic3_left.jpg` and `mosaic3_right.jpg`

3. In the same upload step, include the three final feathered mosaics from Part A:
   - `mosaic1_final.png`
   - `mosaic2_final.png`
   - `mosaic3_final.png`

   Use the final feathered results, not the `_overwrite.png` baselines.

4. Run the remaining cells to detect corners, apply ANMS, extract descriptors, match features, estimate homographies using RANSAC, and generate the automatic mosaics and manual-versus-automatic comparisons. **No manual point selection is required for Part B.**

5. Run the final export cell to create `cs180_proj4b_results.zip`. Download this archive from Colab's Files panel and save the executed notebook separately.

**Note:** The submitted run used the six working images exported from Part A, named `mosaic1_left_working.png`, `mosaic1_right_working.png`, and similarly for mosaics 2 and 3. These can be uploaded instead of the original JPGs, together with the same three final manual mosaics. The notebook supports both options, with JPGs taking priority if both are present.


---