Results and simulated data examples of ICA2, CMML3

### 1. `Real_data_results/`

This directory contains the predicted cell type proportion matrices from Cell2location, CARD, and SpatialDWLS for the seven real sequencing-based datasets described in Supplementary Table S1 of the paper.
Each subdirectory corresponds to a specific dataset:
*   `Slideseq_mop`: Mouse Primary Motor Cortex (MOP) using Slide-seq.
*   `StereoSeq`: Mouse Brain using Stereo-seq.
*   `VisiumLymphNode`: Human Lymph Node using 10x Visium.
*   `VisiumMsBrain`: Mouse Brain using 10x Visium.
*   `Visium_mop`: Mouse Primary Motor Cortex (MOP) using 10x Visium.
*   `Visium_tumor`: Mouse MCA205 Tumor using 10x Visium.
*   `Zebrafish_ST5`: Zebrafish Embryo using 10x Visium.

Within each dataset folder, you will find:
*   `CARD_proportions.csv`: Predicted proportions from CARD.
*   `DWLS_proportions.csv`: Predicted proportions from SpatialDWLS.
*   `cell2loc_proportions.csv`: Predicted proportions from Cell2location.
    *(Note: Some datasets might not have results for all three methods due to computational constraints or method applicability, as detailed in the main paper.)*

These results were used to generate metrics presented in Figure 1b of the main paper.

### 2. `Simulation_examples/`

This directory contains example input data used for generating and running deconvolution on simulated MERFISH datasets, particularly for the spot resolution experiments (related to main paper Figure 2a, 2b and Supplementary Figure S1c, S2).
*   `cell_type_gt_07.csv`: Ground truth cell type proportions for the simulated spots from MERFISH slice 07.
*   `for_R/`: Subdirectories containing input files (e.g., spatial expression matrices, cell type annotations) formatted for R-based tools (CARD, SpatialDWLS) for MERFISH slice 07 at different simulated resolutions (e.g., `resolution_0.1_merfish7_con`, `resolution_0.25_merfish7_con`).
*   `resolution_*.h5ad`: AnnData files (`.h5ad`) containing the simulated spatial transcriptomics data for MERFISH slice 07 at various resolutions (e.g., `resolution_0.1_merfish7_con.h5ad`, `resolution_0.25_merfish7_con.h5ad`). These are typically used as input for Python-based tools like Cell2location.
*   `sc_level_Merfish_07.h5ad`: The raw single-cell resolution MERFISH data for slice 07, used as the basis for simulation and as the reference scRNA-seq data for deconvolution.

The simulation process involved binning cells from `sc_level_Merfish_07.h5ad` to create spots of varying resolutions, as described in the "Data Preparation" section of the paper.

### 3. `Simulation_results/`

This directory contains the deconvolution results (predicted cell type proportions and/or aggregated metrics) for the simulated datasets.

*   **`Merfish_multi_slices_results/`**: Contains deconvolution outputs for simulated MERFISH data generated from 6 independent MERFISH mouse brain slices (07-12 from Allen Inst. ABC Atlas) at a 0.25 spot resolution. This corresponds to results shown in Figure 1c and Supplementary Figure S1a.
    *   `benchmark_pipeline_output_SimMerfish`: Aggregated performance metrics across these slices.
    *   `resolution_0.25_Zhuang-ABCA-1.0XX`: Folders containing per-slice deconvolution results (e.g., proportion matrices).

*   **`resolution_results/`**: Contains deconvolution outputs for simulated MERFISH data (slice 07) across nine varying spot resolutions (from 0.1 to 0.5). These results are visualized in main paper Figure 2a, 2b and Supplementary Figure S1c, S2.
    *   `CARD_resolution_X.X.csv`: Predicted proportions from CARD at resolution X.X.
    *   `DWLS_resolution_X.X.csv`: Predicted proportions from SpatialDWLS at resolution X.X.
    *   `cell2loc_resolution_X.X.csv`: Predicted proportions from Cell2location at resolution X.X.


*   **`simulation_seqFish/`**: Contains deconvolution outputs for simulated seqFISH+ data, focusing on performance with varying gene numbers (3k, 6k, 10k genes) and across replicates. These results are visualized in main paper Figure 1d and Supplementary Figure S1b.
    *   `benchmark_output_repX`: Aggregated performance metrics for replicate X.
    *   `for_R/`: Input files for R-based tools for the seqFISH+ simulations.
    *   `result_repX/` or `results_repX/`: Folders containing raw deconvolution output proportion matrices for replicate X.
    *   `sc_seqfish.h5ad`: The single-cell reference data used for seqFISH+ simulations.
    *   `seqFISH+_XXXXXgenes.h5ad`: The simulated spatial data with a specific number of genes.


## How to Use

The data in this repository is primarily intended for:
*   Reproducing the figures and quantitative results presented in the associated paper.
*   Serving as a benchmark dataset for future deconvolution method development.
*   Providing examples of input and output formats for spatial deconvolution tasks.

To regenerate the results or apply the benchmarking pipeline to new data, please refer to the code repository: [https://github.com/AnonymityICAuser/CMML3_ICA2_code](https://github.com/AnonymityICAuser/CMML3_ICA2_code).

## Raw datasets

For the raw datasets and their related link, please check the Supplementary Material Table S1,S2. 