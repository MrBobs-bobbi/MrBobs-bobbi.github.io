# CS180 Project 3 — Flow Models & Flow Matching from Scratch

## README

---

## 1. What's in this submission

```text
submission.zip
├── code/
│   ├── part_a.ipynb    # Part A: Exploring Flow Models
│   ├── part_b.ipynb    # Part B: Flow Matching from Scratch
│   └── README.md       # This file
└── web/
    └── page.pdf        # PDF export of the project webpage
```

Both notebooks contain markdown explanations, implementation details, and experimental results. Additional visualizations and observations are available on the project webpage.

---

## 2. How to run the notebooks

Both notebooks were developed and run in **Google Colab**. Open each notebook separately and run all cells **from top to bottom, in order**.

### Part A — Exploring Flow Models

1. Open `part_a.ipynb` in Google Colab.
2. Enable a GPU runtime.
3. Run the setup cells to install dependencies and load the pretrained PixNerd model.
4. Upload the required input images when prompted.
5. Run the remaining cells sequentially to generate the results.

### Part B — Flow Matching from Scratch

1. Open `part_b.ipynb` in Google Colab.
2. Select a **T4 GPU** runtime.
3. Run all cells sequentially. The notebook automatically downloads MNIST.
4. Allow the denoising and flow-matching models to finish training before running their sampling cells.

**Note:** Google Colab runtime files and variables may be lost after disconnection. If the runtime resets, rerun the notebook from the beginning.

---