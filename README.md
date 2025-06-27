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

The example for "Applying data augmentation for deep learning model inputs"

from Bio import SeqIO

def has_15_consecutive_common(seq1, seq2):
    """
    Check if two sequences have at least 15 consecutive nucleotides in common.
    """
    for i in range(len(seq1) - 14):  # Check for windows of 15 nucleotides
        if seq1[i:i+15] in seq2:
            return True
    return False

def generate_sequences_with_variable_overlap_and_common_bases(seq, k=40, min_overlap=5, max_overlap=20): 
    """
    Generate all possible k-mers (subsequences) of length `k` (40 nucleotides) from the sequence with:
    1. Overlaps of varying lengths (5-20 nucleotides).
    2. Sequences that share at least 15 consecutive nucleotides with a previously extracted sequence.
    """
    valid_sequences = set()  # Use a set to ensure uniqueness

    # 1. Generate subsequences with varying overlaps (5 to 20 nucleotides)
    for overlap in range(min_overlap, max_overlap + 1):
        # Left overlap
        for i in range(0, len(seq) - k + 1, k - overlap):
            sub_seq = str(seq[i:i + k])
            valid_sequences.add(sub_seq)
        # Right overlap
        for i in range(overlap, len(seq) - k + 1, k - overlap):
            sub_seq = str(seq[i:i + k])
            valid_sequences.add(sub_seq)
        # Both sides overlap
        for i in range(overlap // 2, len(seq) - k + 1, k - overlap):
            sub_seq = str(seq[i:i + k])
            valid_sequences.add(sub_seq)

    # 2. Generate subsequences with at least 15 consecutive nucleotides in common
    for i in range(len(seq) - k + 1):
        sub_seq = str(seq[i:i + k])
        if not valid_sequences:  # If no sequences yet, add the first one
            valid_sequences.add(sub_seq)
        else:
            # Check if the current subsequence has 15 consecutive nucleotides in common with any previously added one
            if any(has_15_consecutive_common(existing_seq, sub_seq) for existing_seq in valid_sequences):
                valid_sequences.add(sub_seq)

    return list(valid_sequences)

def process_fasta_for_nn(input_fasta, output_file, k=40, min_overlap=5, max_overlap=20):
    """
    Process each sequence in the input FASTA file to generate subsequences with:
    1. Variable overlaps of 5-20 nucleotides.
    2. Sequences sharing at least 15 consecutive nucleotides with previous sequences.
    Ensure that all subsequences are exactly 40 nucleotides long.
    """
    with open(output_file, 'w') as output_handle:
        for record in SeqIO.parse(input_fasta, "fasta"):
            # Generate subsequences with variable overlap and common bases
            overlap_sequences = generate_sequences_with_variable_overlap_and_common_bases(record.seq, k, min_overlap, max_overlap)

            # Combine all sequences and ensure uniqueness by using a set
            all_sequences = set(overlap_sequences)

            label = record.id.split('_')[0]  # Extract label from the header (e.g., "trnR1" from ">trnR1_seq_1")
            for sub_seq in all_sequences:
                output_handle.write(f"{sub_seq}, {label}\n")

Example usage
input_fasta = "/content/drive/MyDrive/C.... /chloroplast_300 bp up.fasta"
output_file = "/content/drive/MyDrive/...../chloroplast_300N_40N_5to20_overlap.csv"
process_fasta_for_nn(input_fasta, output_file)



# Citations
If you use these data augmentation approaches in your research, please cite our paper:
This section will be completed later.

# Contact for providing more details
This section will be completed later.
