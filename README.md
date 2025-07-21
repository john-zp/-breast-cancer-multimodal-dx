# -breast-cancer-multimodal-dx

This repo contains the complete, reproducible code behind the study
“Multimodal Features Integration for Enhanced Breast Cancer Diagnosis Using Machine Learning.”
It integrates BI-RADS terminology, handcrafted ultrasound (US) image features, and 600 radiomic features (reduced to 31 PCs) to train and evaluate Logistic Regression, SVM and Random Forest models on 3 703 US images from 2 685 patients split 80 / 20 into train-validation sets 
.
The best combined-feature RF model reached AUC 0.85 / Accuracy 0.82 on the hold-out set

## Repository layout
| Folder / Notebook                                  | Purpose                                                                                                                         |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `01_*`                                             | **Image & ID alignment** – helper notebooks that associate BI-RADS reports and radiology images with unique patient IDs.        |
| `02_1 qfeature_id…`                                | Extracts **quantitative US features** (size, shape, texture).                                                                   |
| `03 Dataset Splitting.ipynb`                       | Stratified split into train / validation folds.                                                                                 |
| `04_* Qualitative Feature Model`                   | Builds **qualitative (BI-RADS terminology) models**: cross-validation, model selection, full-data training, calibration curves. |
| `05_* Quantitative Feature Model`                  | Same workflow for **quantitative US features**.                                                                                 |
| `06_* Omics Feature Model`                         | Radiomics pipeline: 837 initial features → 600 significant → 31 PCs via PCA .                                                   |
| `07_* Composite Model`                             | Fusion of qualitative + quantitative + radiomics (multimodal) with CV, full training & LR/RF variants.                          |
| `08_Cluster Model - Malignant_Final version.ipynb` | Optional clustering / visualization of malignant subtypes.                                                                      |

Tip: notebooks ending with “_Cross-validation” search hyper-parameters; those ending with “_Full data model” train on the entire training set and output calibration plots.



## Key dependencies
| Package         | Version used in study |
| --------------- | --------------------- |
| Python          | 3.8                   |
| scikit-learn    | 0.23.2                |
| PyRadiomics     | 3.0.1                 |
| pandas          | 1.1.4                 |
| seaborn (plots) | 0.11.0                |



## Citation
If you find this code useful, please cite:


@article{multimodalBC2025,\
  title   = {Multimodal Features Integration for Enhanced Breast Cancer Diagnosis Using Machine Learning},\
  author  = {Li Ma and Shengxin Pei and others},\
  journal = {Under Review},\
  year    = {2025}\
}


## License
Released under the MIT License – free for academic and commercial use; please credit the authors.

## Acknowledgements
This work was supported by the Chengdu Science & Technology Program (2022-YF05-01884-SN) and the Qinghai University Medical Faculty teaching reform project (qyjg202221)
