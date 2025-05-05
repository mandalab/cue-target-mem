# Cue vs. Target Word Memorability Analysis in Cued Recall

## Project Overview

This project investigates the nature of word memorability within a cued recall paradigm. It challenges the view of memorability as a purely intrinsic, stimulus-driven property by demonstrating its dependence on the functional role a word plays – either as a retrieval **cue** or as a **target** to be recalled. Using data derived from Cox et al. (2018), this analysis explores how different psycholinguistic properties predict memorability for cues versus targets and examines memorability differences across semantic categories.



## Dataset

The primary dataset used is based on the cued recall data from:
*   Cox, G. E., Hemmer, P., Aue, W. R., & Criss, A. H. (2018). Cue and Target Affect Influence Cued Recall. *Journal of Experimental Psychology: Learning, Memory, and Cognition, 44*(9), 1367–1379.

Word properties were compiled from various sources and merged with the memorability scores derived from the Cox et al. data. 

## Key data files involved:
*   `Cox Data Final.xlsx`: Combining entire test phase data across all cued recall sessions.
*   `Cox Data Mem Combined.xlsx`: Combining cue and target memorability scores across the 924 words.
*   `Cox_Word_Properties.xlsx`: The final output file containing words, their calculated properties, and memorability scores, used for regression. Generated from `Word_Properties_and_VIF.ipynb`.


## Code Structure & Files

*   **`Split_half_Cue_Mem_Cox.ipynb`**: Get cue memorability scores and perform Split Half Analysis to get CC correlation.
*   **`Split_half_Target_Mem_Cox.ipynb`**: Get target memorability scores and perform Split Half Analysis to get TT correlation.
*   **`CC_TT_CT.ipynb`**: Get cue and target memorability scores, get CT correlation and compare with CC and TT split half scores.


*   **`Word_Properties_and_VIF.ipynb`**:
    *   Loading data (`Cox Data Mem Combined.xlsx`).
    *   Computing word properties for the Cox dataset words using external datasets (`SUBTLEXusExcel2007.xlsx`, `BOI means.csv` etc. as described in the paper) and `nltk`.
    *   Merging and saving the final file as `Cox_Word_Properties.xlsx`.
    *   VIF analysis to obtain the final word properties to create Regression models(for both cues and targets).
*   **`Regression_stats.ipynb`**: Final regression table creation calculating all statistics. 


*   **`SVR_training.ipynb`**: To save the trained SVR cue and target models respectively.
*   **`LIWC_GI_file_gen.ipynb`**: 
    * Predicting word level and category level memorability scores on LIWC and GI words using the saved SVR models.
    * Saving the files.
*   **`Category_level_analysis.ipynb`**:
    * Loading the category level and word level files.
    * Performing dichotomy analyses and category vs individual word level correlational analyses.

  

## Requirements & Dependencies

*   Python 3.x
*   Pandas
*   NumPy
*   Matplotlib
*   Seaborn
*   SciPy (specifically `scipy.stats` for t-tests and percentile calculations)
*   Statsmodels (for OLS regression, VIF, ANOVA)
*   NLTK (Natural Language Toolkit)
    *   Requires downloading specific NLTK data packages: `punkt`, `wordnet`, `cmudict` (using `nltk.download()`)
*   adjustText (for non-overlapping text labels on plots)
*   openpyxl (or similar engine for reading Excel files with Pandas)
