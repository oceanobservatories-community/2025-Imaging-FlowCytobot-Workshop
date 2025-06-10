# 2025 OOIFB Imaging FlowCytobot Workshop

This repository demonstrates how to train and evaluate deep learning models on a high-performance JupyterHub server equipped with an NVIDIA L40S GPU. The server has direct access to Imaging FlowCytobot (IFCB) data from the NSF-funded [Ocean Observatories Initiative (OOI)](https://oceanobservatories.org/), making it an ideal environment for experimenting with marine plankton image classification.

---

## Repository Structure

```
.
├── deep_features/       # Saved deep feature vectors from ViT models
├── figures/             # Visualizations of clustered features and model results
├── notebooks/           # Jupyter notebooks for training, testing, and clustering
├── test-images/         # Example IFCB images for inference or testing

```

---

## Notebook Demonstrations

### `miniPhytoCNN-train.ipynb`
This notebook trains a phytoplankton image classifier using both a simple CNN and a transfer learning approach with ResNet18. It walks through downloading and visualizing a labeled dataset, followed by setting up data loaders and running training for multiple epochs. The notebook includes code to visualize class distributions and sample images, making it a useful tool for demonstrating model training on IFCB data in a GPU-enabled environment.

<table>
  <tr>
    <td><img src="/figures/class_image_mosaic.png" width="400"/></td>
    <td><img src="/figures/ConfusionMatrix_resnet18.png" width="400"/></td>
  </tr>
</table>
⸻

### `miniPhytoCNN-test.ipynb`

This notebook demonstrates how to use the trained miniPhytoCNN model on images requested directly from the IFCB dashboard. It loads model weights and classifies individual images downloaded from the dashboard.

⸻

### `miniPhytoCNN-inference-roi.ipynb`

This notebook uses the [`pyIFCB`](https://github.com/joefutrelle/pyifcb/tree/master) to directly run inference on images collected in `.roi` files mounted on the OOI/ JupyterHub server/ Predictions are saved alongside ROI indices to facilitate downstream analysis. It’s intended for use on new data streams not included in the training set.

⸻

### `miniPhytoCNN-cluster-roi.ipynb`

This notebook extracts [deep features](https://deepai.org/machine-learning-glossary-and-terms/deep-features) from IFCB .roi images using a trained model, then performs unsupervised clustering (KMeans, HDBSCAN). It visualizes clusters using t-SNE and generates mosaic plots for visual inspection of intra-cluster consistency. Feature arrays are saved for future use.

<table>
  <tr>
    <td><img src="/figures/ifcb_cluster_mosaic-HDBSCAN.png" width="400"/></td>
    <td><img src="/figures/ifcb_cluster-HDBSCAN.png" width="400"/></td>
  </tr>
</table>

⸻

### `ooi-ifcb-cleanvision.ipynb`

This notebook uses [`CleanVision`](https://cleanvision.readthedocs.io/en/latest/tutorials/tutorial.html) to automatically detect and flag low-quality or anomalous images in IFCB datasets. It outputs a quality report and visualizations of flagged samples. The tool helps curate cleaner training data for improved model performance.


---

## Acknowledgments

Data courtesy of the [Ocean Observatories Initiative](https://oceanobservatories.org/). This project is supported by NSF OOI.