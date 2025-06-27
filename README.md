# Data-Augmentation
Code for manuscript titled:

**Innovative** **Data** **Augmentation** **Strategy** **for** **Deep** **Learning** **on** **Biological** **Datasets** **with** **Limited** **Gene** **Representations**


# Overview
In the current study, a novel and highly effective data augmentation strategy was introduced that addresses the challenges posed by small genomic datasets. This approach enables deep learning applications for omics and other related biological datasets when limited sequence data is available. The method expands the datasets (without introducing noise or overfitting) while preserving the biological integrity of the sequences and ensuring comprehensive coverage of the original sequences. The flexibility of this user-friendly approach, combined with its ability to generate biologically relevant data, makes it applicable to a wide range of biological data repositories. By enabling high-performance deep learning models to capture subtle, biologically relevant patterns in small datasets, the current approach offered a significant advancement in the field of biological data analysis. Another key advantage of the current introduced approach is its user-friendliness, as all its parameters, such as the overlapping length and the length of the generated sequences, can be easily modified. This flexibility makes the method applicable not only to gene or regulatory sequences but also to genomic sequences. As illustrated in the Figure below for ease of understanding, a graphical flowchart summarizes the data augmentation strategy designed to overcome the challenges of limited sequence availability in omics and related biological datasets, thereby facilitating more effective deep learning applications.

![Flowchart](https://github.com/user-attachments/assets/56939990-8065-429c-ac3e-6bbf3fe4fe4d)
![Uploading Flowchart.jpeg…]()


In addition, a k-mer-based data augmentation strategy also offered a robust solution for enhancing unsupervised data analysis, enabling the identification of unknown gene functions, uncovering co-functional genes and proteins, and advancing systems biology for the small datasets. 

The current introduced innovative approaches enable the applicability of deep learning and machine learning to omics datasets with limited data availability. This provides new opportunities for researchers working with underrepresented biological data.

# Authors

This section will be completed later.


# Requirements and Installation

All analyses were conducted using the free version of Google Colaboratory (Google Colab), an online platform that offers cloud-based access to a shared computing environment. Alternatively, analyses can be performed on other online platforms such as Kaggle or in offline Python-based environments. All necessary dependencies and packages are specified in the code and can be easily installed.

# Availability of the code

The code for the various sections of this study is available in the file titled **"S 3_main scripts.ipynb."**. To facilitate ease of use and understanding, important sections have been annotated with comments highlighting areas that may require modification. This file includes code for different parts of the analysis, including:
 
 Code for applying data augmentation for deep learning model inputs


 Training the CNN-LSTM hybrid model


 Code for applying data augmentation strategy for unsupervised analysis


 Code for applying data augmentation strategy for unsupervised analysis


 Additional utilities and helper functions


These annotations and modular sections are intended to help users quickly identify and adapt relevant parts of the code for their own applications.

# The flexibility of these user-friendly approaches

The current user-friendly augmentation process is highly adaptable, enabling researchers to easily modify key parameters such as the length of the subsequences, the degree of overlap, and the total number of generated subsequences, providing flexibility across different types of omics datasets. 

# An example of easily adjusting based on the specific characteristics of different datasets

Here, consider the example “Applying data augmentation to deep learning model inputs” and refer to the corresponding code, then for adjusting the length of the subsequences, modify the **k=40**, for adjusting the degree of overlap, change the **min_overlap=5** and **max_overlap=20** in below part and other related parts.

def generate_sequences_with_variable_overlap_and_common_bases(seq, k=40, min_overlap=5, max_overlap=20): 

    
# Citations
If you use these data augmentation approaches in your research, please cite our paper:

This section will be completed later.

# Contact for providing more details
For more information or assistance with using or running the codes employed in this study, please feel free to contact us at the following email addresses:
This section will be completed later.
