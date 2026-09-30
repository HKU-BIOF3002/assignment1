# BIOF3002 - Assignment 1

**Due date:** October 18th, 2026 (Sunday) 23:59

**Marks:** 20 (submitted assignment) + 5 (in class MCQ quiz on assignment) [Total: 25% of course assessment]

## Submission instructions

The state of the main branch of your GitHub repository at the time of the Due Date will be considered the final submitted version of your assignment. If you make further commits to the repository after the due date, a late penalty of -10% (-2 marks) per day will apply.

You **MUST** also submit the link to your assignment's GitHub repository on Moodle by the Due Date. 

Submission of the answers as a PDF, together with the script(s) in a single zipped file on Moodle, is also acceptable in lieu of providing a link to your assignment's GitHub repository. However, this submission method will result in a 1-mark deduction.

In the case where **BOTH** a GitHub repository AND a zipped file is submitted on Moodle, the GitHub repository will be treated as the Final Submission.

## Introduction

During weeks 2 and 3 in this course, you generated long-read DNA sequencing data from one of the two unknown cell lines during the practicals. You have also started to learn how to use a high-performance computer (HPC) to analyse these datasets. This Assignment aims to assess your ability to analyse long-read DNA sequencing data, make quality control and biological interpretations from this data, and organise data analysis scripts. Course contents covered up to week 5 should provide you with sufficient background knowledge to complete the assignment. However, most questions will require you to independently explore tool options beyond what was discussed in the lectures - this is a fundamental skill of a bioinformatician and there is no restriction on the use of AI assistance on the assignment.

## The data

Information on how to access the CPOS HPC (hpcf3) is available from the Lecture Notes in Week 4. The data that were generated are located on the server in:

`/home/groups/biof3002/2026/fastq`

The samples are labelled from barcode01 to barcode24, along with the letter A or B corresponding to the cell line. For this assignment, you should use the sample that you prepared in the laboratory practical session as indicated by the sample+barcode number to answer Q1-5. If you feel that your sample has insufficient data, you may choose another sample+barcode combination to answer the question but remember to state the correct sample+barcode combination that you have used for the assignment. For Q6, you can use any or all of the samples to answer the question.

Note that this is an *Individual Assessment* and you must submit your own work independent of your laboratory partner.

## Instructions

-  Do not clone or fork this repository directly. Follow these steps to create your own copy:

      1. Sign into your GitHub account if you haven't already.
      2. **Create your repository:** Click the **"Use this template"** button at the top right of this page and select **"Create a new repository"**.
      3. **Configure settings:** 
         * Set the Repository name (e.g., `assignment-1-yourname`).
         * Choose **Private** (so other students cannot copy your work).
         * Click **"Create repository from template"**.
      4. **Clone to CPOS HPCF3:** Go to your newly created repository page, click the **Code** button, copy the URL. Navigate to an appropriate directory under your home folder and run this in the terminal:
         ```bash
         git clone <YOUR-NEW-REPOSITORY-URL>
         ```
-   Below are a set of questions that you will have to address using your dataset. Some questions may require the generation of figures (using *R* or *Python*) or additional justification of your response.

-   As each of you will be analysing a different file, it is expected that each of you will have different answers for most questions. Marks will be allocated based on the dataset you analysed.

-   The answers should be numbered and saved in this README.md file on GitHub.

-   Provide the code (in Bash, another programming language or both) that is used to generate the answer for relevant questions that require computation to answer. This may be submitted as a single script or separate scripts for each question. Put these scripts directly in your GitHub repository for this assignment.

-   It is essential to annotate your scripts clearly and concisely so that they are easy to understand. Apart from functionality, marks will also be allocated for the efficiency and readability of your scripts.

-   **Submit your work:** When you have finished your assignment, you must commit and push your completed README.md (with answers) and scripts to the main branch of your GitHub repository.

-   Remember to submit the link to your GitHub repository on the Moodle assignment page.

## Use of Generative AI

-   There is *no* restriction on the use of generative AI, such as GitHub Co-Pilot, to help you with the code to answer the questions.

-   However, the in-class quiz (Wed 21st Oct) will assess your understanding of the code used to answer the questions, so it is imperative that you have an understanding of what your code is doing.

## Paths to useful files on the CPOS HPC server

-   ***Long read sequencing data:*** `/home/groups/biof3002/2026/fastq/`

-   ***Reference genome:*** `/home/groups/biof3002/ref/reference_genome/hg38/hg38.fa`

-   ***Target regions for Q4:*** `/home/groups/biof3002/ref/targets/targets.hg38.bed`

-   ***Candidate variants for Q6:*** `/home/groups/biof3002/ref/cell_line_variants/`

## Questions

0.  Which sample and barcode are you using for Q1-Q5? **(0 marks)**

1.  How long is the longest read in your sample? **(2 marks)**

2.  Align your sample to the human reference genome (hg38). What percentage of the total number of sequenced reads could be mapped? **(2 marks)**

    *(Tips: Note the definition of primary, secondary, and supplementary mapped reads discussed in the lecture.)*

3.  Compare the read length distribution between the primary mapped and unmapped reads. Make a box plot to compare their read length distribution. Is the difference significant? **(3 marks)**
   
4.  There is a file called `targets.hg38.bed` in `/home/groups/biof3002/ref/targets/`. This file contains the coordinates from exons of selected genes from the human genome (hg38) in BED format. How many exons have read coverage in your sample? **(3 marks)**

5.  Provide an IGV screenshot showing reads from your sample overlapping a gene with read coverage **(1 mark)**

    (*Tips: use the analysis from Q4 to help you find a gene with coverage. Don't worry if the coverage is low)*.

6.  A researcher has previously identified variants (base substitutions) in 11 cell lines (A549, LOVO, HCT116, etc). These variants are provided in `/home/groups/biof3002/ref/cell_line_variants` in BED format (i.e. the genomic positions where there are variants are listed for each cell line). Samples A and B are two distinct cell lines chosen from this group of 11. Identify which cell line Sample A and Sample B are most likely to correspond to, and briefly explain how you reached your conclusion. **(9 marks)**

    (*Tips: There are different ways to answer this question, but we suggest using samtools mpileup. You can read about the pileup format <https://en.wikipedia.org/wiki/Pileup_format> and use awk or a simple script to parse the results. You may use any or all of the samples generated by the class if you find the data in your own barcode inadequate*.)
