# BIOF3002 - Assignment 1

**Due date:** October 31st, 2025 (Friday) 23:59

**Marks:** 25 (25% of total assessment)

## Submission instructions

The state of the main branch your GitHub reposotry at the time of the Due Date will be considered the final submitted version of your assignment. If you make further commits to the repository after the due date, a late penalty of -10% (-2.5 marks) per day will apply.

You may also submit your assignment on Moodle with the answers as a PDF and the script(s) in a single zipped file by the Due Date.

## Introduction

During weeks 2 and 3 in this course, you generated long-read DNA sequencing data from two unknown cell lines during the practicals. In recent weeks, you have also started to learn how to use a high-performance computer (HPC) to analyse these datasets. This Assignment aims to assess your ability to analyse long-read DNA sequencing data, make quality control and biological interpretations from this data, and organise data analysis scripts. All course contents covered up to week 5 are sufficient to complete the assignment. However, most questions will require you to self-explore the tools beyond what was discussed in the lectures.

## The data

Information on how to access the CPOS HPC is available from the Lecture Notes in Week 4. The data that were generated are located on the server in:

`/home/groups/biof3002/Data/fastq`

The samples are labelled from barcode01 to barcode20, along with letter A or B corresponding to the cell line. For this assignment, you will use the sample that you prepared in the laboratory practical session as indicated by the barcode number to answer Q1-5. For Q6, you can use any or all of the samples to answer the question.

Note that this is an [Individual Assessment,]{.underline} and you must submit your own work independent of your laboratory partner.

## Instructions

-   You are to clone this assignment to your account on the CPOS HPC server using the GitHub classroom invitation link provided on the Moodle assignment page.

-   Below is a set of questions that you will have to address using your dataset. Some questions may require the generation of figures (using *R* or *Python*) or additional justification of your response.

-   As each of you will be analysing a different file, it is expected that each of you will have different answers for most questions. Marks will be allocated based on the dataset you analysed. [**Make sure you specify which dataset you analysed**]{.underline}.

-   The answers should be numbered and saved in this README.md file on GitHub.

-   Provide the code (in bash or other programming language or both) that is used to generate the answer for relevant questions that require computation to answer. This may be submitted as a single script or separate scripts for each question. Put these scripts directly in your GitHub root repository for this assignment.

-   It is essential to annotate your scripts clearly and concisely so that they are easy to understand. Apart from functionality, marks will also be allocated for the efficiency and readability of your scripts.

-   When you have finished your assignment, you must commit and push your completed README.md (with answers) and scripts to the main branch your GitHub repository.

-   You may also submit your assignment on Moodle with the answers in a PDF and the script(s) in a single zipped file.

## Use of Generative AI

-   There is [no]{.underline} restriction on the use of generative AI, such as GitHub Co-Pilot, to help you with the code to answer the questions.

-   However, its use must be declared with a brief description of how it was used. This can be added to the comments section of the relevant code for each question. Or you may separately describe your answer in the README.md document.

## Paths to useful files on the CPOS HPC server

-   ***Long read sequencing data:*** `/home/groups/biof3002/Data/fastq/`

-   ***Reference genome:*** `/home/groups/biof3002/week5/ref/reference_genome/hg38/hg38.fa`

-   ***Target regions for Q4:*** `/home/groups/biof3002/week5/ref/targets/targets.hg38.bed`

-   ***Candidate variants for Q6:*** `/home/groups/biof3002/week5/ref/cell_line_variants/`

## Questions

1.  How long is the longest read in your sample? **(2 marks)**

    *(Tips: It is best to use awk and other bash commands for this)*

2.  Align your sample to the human reference genome (hg38). What % of reads could be mapped? **(2 marks)**

    *(Tips: Note the definition of primary, secondary, and supplementary mapped reads discussed in the lecture.)*

3.  Compare the read length distribution between the primary mapped and unmapped reads. Make a box plot to compare their read length distribution. Is the difference significant? **(4 marks)**

    (*Tips: use samtools view and FLAGS (-F or -f) to help you extract primary mapped and unmapped read lengths. You will need to read up about samtools FLAGS and can use this website to generate the appropriate ones <https://broadinstitute.github.io/picard/explain-flags.html>*)

4.  There is a file called `targets.hg38.bed` in `/home/groups/biof3002/week5/ref/targets/`. This file contains the coordinates of exons of selected genes from the human genome (hg38) in BED format. How many exons have read coverage in your sample? **(3 marks)**

    (*Tips: use samtools bedcov and then awk. You will need to understand the output of bedcov*)

5.  Provide an IGV screenshot showing your sample overlapping a gene with read coverage **(2 mark)**

    (*Tips: use the analysis from Q4 to help you find a gene)*.

6.  A researcher has previously identified variants in 10 cell lines (A549, LOVO, HCT116, etc). These variants are provided in the cell_line_variants folder in the GitHub repository (also in `/home/groups/biof3002/week5/ref/cell_line_variants`). Sample A and B are one of these 10 cell lines. Identify which cell line samples A and B are most likely to be and briefly explain how you reached this conclusion. **(12 marks)**

    (*Tips: There are different ways to answer this question, but we suggest using samtools mpileup. You can read about the pileup format <https://en.wikipedia.org/wiki/Pileup_format> and use awk or a simple script to parse the results. You may use any or all of the samples generated by the class if you find the data in your own barcode inadequate*.)
