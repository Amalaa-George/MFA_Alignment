# Montreal Forced Aligner Assignment

This project demonstrates **forced alignment** of speech audio with text transcriptions using the **Montreal Forced Aligner (MFA)** toolkit and visualization in **Praat**.  
It aligns each word and phoneme in a spoken utterance to its corresponding time interval in the waveform.
---
Repository Structure:
MFA_Alignment/
|---README.md
|---run_alignment.txt   #Contains all MFA commands used
|
|---dataset
|       F2BJRLP1.lab
|       F2BJRLP1.wav
|       F2BJRLP2.lab
|       F2BJRLP2.wav
|       F2BJRLP3.lab
|       F2BJRLP3.wav
|       ISLE_SESS0131_BLOCKD02_01_sprt1.lab
|       ISLE_SESS0131_BLOCKD02_01_sprt1.wav
|       ISLE_SESS0131_BLOCKD02_02_sprt1.lab
|       ISLE_SESS0131_BLOCKD02_02_sprt1.wav
|       ISLE_SESS0131_BLOCKD02_03_sprt1.lab
|       ISLE_SESS0131_BLOCKD02_03_sprt1.wav
|
|---output
|       alignment_analysis.csv
|       F2BJRLP1.TextGrid
|       F2BJRLP2.TextGrid
|       F2BJRLP3.TextGrid
|       ISLE_SESS0131_BLOCKD02_01_sprt1.TextGrid
|       ISLE_SESS0131_BLOCKD02_02_sprt1.TextGrid
|       ISLE_SESS0131_BLOCKD02_03_sprt1.TextGrid
|
|---Screenshots
        praat_alignment1.png
        praat_alignment2.png

##  1. Objective

The goal of this assignment is to:
- Install and configure Montreal Forced Aligner (MFA)
- Align audio (`.wav`) files with their corresponding text transcriptions (`.lab`)
- Visualize phoneme and word boundaries in Praat
- Analyze the alignment quality and report observations

---

##  2. System Requirements

| Requirement | Version / Tool |
|--------------|----------------|
| Operating System | Windows 10 / 11 (64-bit) |
| Environment Manager | Miniconda (Python 3.10+) |
| Alignment Toolkit | Montreal Forced Aligner 3.x |
| Visualization Tool | Praat 6.4.46 |

---

##  3. Installation and Setup

### Step 1: Install Miniconda
Download and install **Miniconda (Python 3.10+)** from  
[https://docs.conda.io/en/latest/miniconda.html](https://docs.conda.io/en/latest/miniconda.html)


---

### Step 2: Create a new environment and install MFA
Open **Anaconda Prompt (Miniconda3)** and run:

```bash
conda create -n aligner -c conda-forge montreal-forced-aligner
conda activate aligner

---
### Step 3: Download resources (dictionary & acoustic model)
mfa model download dictionary english_us_arpa
mfa model download acoustic english_us_arpa

These download the American English pronunciation dictionary and the acoustic model required for alignment.

---
### 4. Dataset Preparation
Organize your dataset as follows:

dataset/
 ├── file1.wav
 ├── file1.lab
 ├── file2.wav
 ├── file2.lab

🔹 Each .lab file must have the same name as its corresponding .wav file.

----
### 5. Validation
Validate your dataset to ensure that all audio and transcription files are correctly matched:
mfa validate dataset english_us_arpa english_us_arpa

----
### 6. Running Alignment
mfa align dataset english_us_arpa english_us_arpa output

This will produce time-aligned .TextGrid files inside the output/ folder.

---
### 7. Visualization in Praat

After alignment:
Download and extract Praat (64-bit)
https://www.fon.hum.uva.nl/praat/
Open Praat.exe
Load a .wav and its corresponding .TextGrid:
Open > Read from file... → select file1.wav
Open > Read from file... → select file1.TextGrid
Select both in the Objects list → click View & Edit
You will see:
Waveform (top)
Word tier (middle)
Phone tier (bottom)
Example visualization:
![Alignment Visualization](Screenshots/praat_alignment1.png)
