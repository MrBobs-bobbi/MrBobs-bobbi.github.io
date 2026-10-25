# CS180 Project 2 — Fun with Filters and Frequencies

## README

---

## 1. What's in this submission

```
submission.zip
├─ code/
│  ├─ main.ipynb        # the full project notebook (rename before zipping —
│  │                       course submission format requires main.ipynb or main.py)
│  └─ README.md          # this file
└─ web/
   └─ page.pdf           # PDF export of the project webpage
```

The notebook contains informal, journal-style markdown notes inserted throughout,
explaining what each section does and why specific parameter choices (thresholds,
sigmas, alphas) were made.

---

## 2. How to run this notebook

Built and run in Google Colab. It is organized as a single linear notebook: **run all
cells top to bottom, in order.** Do not skip cells or run them out of order — many
later cells depend on variables/functions defined earlier (`low_pass`, `high_pass`,
`hybrid_image`, `gaussian_stack`, `laplacian_stack`, and `multires_blend` are each
defined once and reused across multiple later sections).

### Required file uploads

The notebook pauses and prompts for these via Colab's file picker at the relevant
cell — have them ready before running.

**Part 1.1 / 1.2 / 1.3**
- One photo of yourself (any common format: jpg/png). Converted to grayscale
  automatically by the notebook.
- *(No upload needed for the cameraman image — fetched automatically via
  `skimage.data.camera()`.)*

**Part 2.1 — Unsharp Masking**
- `taj.jpg` (the Taj Mahal image provided by the course)
- A second image of your own choice (visible fine detail/texture works best)
- A third image (used here to test the technique on an AI-generated/edited image)

**Part 2.2 — Hybrid Images**
- `DerekPicture.jpg` and `nutmeg.jpg` (official course-provided sample images), plus
  `align_image_code.py` (official alignment starter code — used unmodified except for
  `get_points`; see Section 3)
- Two of your own image pairs (4 images total) for your own hybrid results

**Part 2.3 / 2.4 — Stacks and Blending**
- `apple.jpeg` and `orange.jpeg` (official course-provided sample images, from
  `spline.zip`)
- Two of your own image pairs: one for a straight-seam blend, one for an
  irregular-mask blend

> Uploaded files persist only for the current Colab runtime session. If the runtime
> disconnects or restarts, all uploads **and** previously-run cell outputs/variables
> are lost — the entire notebook must be re-run from the top, including re-uploading
> every file above, in order.

---

## 3. Important: why `get_points` is patched in the hybrid image section

The official `align_image_code.py` starter uses `plt.ginput()` to let the user click
two corresponding points on each image for alignment (e.g. both eyes). This requires
an interactive matplotlib backend with a real, clickable window — it does **not**
work in Google Colab, whose inline plotting backend cannot register mouse clicks on a
displayed plot. Running the starter code as-is in Colab causes the cell to hang
indefinitely, waiting for clicks that can never register.

**Workaround used:** rather than modifying any of the actual alignment math in
`align_image_code.py`, only the point-*collection* step was replaced. Each image pair
is first displayed with a coordinate grid overlay (`show_with_grid`), used to
manually estimate the (x, y) pixel coordinates of two matching landmark points
(typically both eyes) by eye. These coordinates are hardcoded into a small function
monkey-patched onto `align_image_code.get_points`:

```python
def get_points_manual(im1, im2):
    p1 = (x1, y1)
    p2 = (x2, y2)
    p3 = (x3, y3)
    p4 = (x4, y4)
    return (p1, p2, p3, p4)

align_image_code.get_points = get_points_manual
```

Every other function in `align_image_code.py` — `recenter`, `align_image_centers`,
`rescale_images`, `rotate_im1`, `match_img_size`, `align_images` — is used completely
unmodified from the original starter file. This patch only changes **how** the four
alignment points are obtained (typed coordinates instead of mouse clicks); it does
not change any of the alignment computation itself.

If re-running this notebook with different image pairs, the coordinates in each
`get_points_manual`-style function must be updated to match the new images — they
are specific to the exact photos used in this submission and will not produce
correct alignment on different images.

---
