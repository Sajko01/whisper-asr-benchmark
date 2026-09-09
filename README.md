# Whisper vs Faster-Whisper: ASR Benchmark

An experimental evaluation of **Whisper** and **Faster-Whisper** for Automatic Speech Recognition (ASR), with a focus on inference speed, memory consumption, transcription accuracy, model size, multilingual performance, and robustness to background noise.

The project evaluates different Whisper configurations under CPU-based execution and analyzes the trade-offs between recognition quality and computational efficiency.

## Key Results

The experiments demonstrated several performance differences between the original Whisper implementation and Faster-Whisper:

* Up to **1.96× faster inference** with Faster-Whisper on shorter audio samples
* Approximately **73% lower memory consumption**
* Evaluation of transcription accuracy using **Word Error Rate (WER)**
* Comparison of multiple Whisper model sizes
* Evaluation on both **English and Serbian speech**
* Robustness testing under different types and levels of background noise
* Analysis of the relationship between audio duration and processing time

Example benchmark results for the `base` model:

| Audio Duration | Whisper | Faster-Whisper | Speedup |
| -------------- | ------: | -------------: | ------: |
| 11.06 s        |  2.35 s |         1.20 s |   1.96× |
| 24.89 s        |  2.50 s |         1.58 s |   1.58× |
| 66.65 s        |  6.53 s |         4.90 s |   1.33× |

Memory consumption observed during the experiment:

| System         | Memory Usage |
| -------------- | -----------: |
| Whisper        |    422.80 MB |
| Faster-Whisper |    113.64 MB |

In this experimental setup, Faster-Whisper reduced memory consumption by approximately **73%**.

## Technologies

The project was developed using **Python** and Jupyter Notebook.

Main technologies and libraries:

* Python
* Jupyter Notebook
* OpenAI Whisper
* Faster-Whisper
* CTranslate2
* JiWER
* NumPy
* Pandas
* Matplotlib

## Project Overview

Whisper is a general-purpose speech recognition model capable of multilingual speech recognition, translation, and language identification.

Faster-Whisper is an optimized implementation of Whisper based on **CTranslate2**, designed to improve inference efficiency and reduce computational requirements.

The main objective of this project was to experimentally investigate the differences between the two implementations and evaluate whether Faster-Whisper can provide better computational performance while maintaining useful transcription quality.

The experiments focus on four main areas:

1. Whisper vs Faster-Whisper performance
2. Different Whisper model sizes
3. Multilingual speech recognition
4. Robustness to background noise

## Experiments

### 1. Whisper vs Faster-Whisper

The first experiment compares the original Whisper implementation with Faster-Whisper.

The evaluation focuses on:

* inference time
* memory consumption
* transcription output
* Word Error Rate (WER)

Audio samples of different durations were used to investigate how processing time changes as the input becomes longer.

The experiments were executed on CPU, with Faster-Whisper using INT8 computation where applicable.

### 2. Model Size Comparison

Multiple Whisper model sizes were evaluated:

* `tiny`
* `base`
* `small`
* `medium`

The purpose of this experiment was to analyze the trade-off between computational requirements and transcription quality.

Smaller models generally require fewer computational resources and provide faster inference, while larger models can provide better recognition performance at the cost of increased processing time and memory consumption.

### 3. Multilingual Speech Recognition

The project also evaluates Whisper on speech from different languages.

The experiments include:

* English speech
* Serbian speech

This experiment demonstrates the multilingual capabilities of Whisper and allows the behavior of the models to be compared across languages.

### 4. Noise Robustness

Additional experiments were performed to investigate the robustness of speech recognition under noisy conditions.

Two types of artificial background noise were evaluated:

* white noise
* pink noise

Different Signal-to-Noise Ratio (SNR) configurations were used to simulate varying levels of acoustic degradation.

Transcription quality was evaluated using **Word Error Rate (WER)**.

Example WER results from the noise experiments:

| Noise Condition    |    WER |
| ------------------ | -----: |
| Clean audio        |  3.70% |
| White noise, 0 dB  |  0.00% |
| White noise, -5 dB |  7.41% |
| Pink noise, -5 dB  | 11.11% |

These results are specific to the audio samples used in this experiment and should not be interpreted as general benchmark results for Whisper.

## Evaluation Metrics

### Inference Time

Inference time measures how long the model requires to process an audio sample.

It is used to compare the computational performance of Whisper and Faster-Whisper.

### Speedup

Speedup is calculated as:

```text
Speedup = Whisper execution time / Faster-Whisper execution time
```

A value greater than `1.0` indicates that Faster-Whisper completed the transcription faster.

### Memory Consumption

Memory usage was measured during model execution to compare the resource requirements of the two implementations.

This is particularly relevant when ASR models are deployed on systems with limited hardware resources.

### Word Error Rate

Word Error Rate (WER) is used to evaluate transcription accuracy.

WER is based on the number of substitutions, deletions, and insertions required to transform the predicted transcription into the reference transcription.

```text
WER = (Substitutions + Deletions + Insertions) / Number of reference words
```

Lower WER values indicate better transcription accuracy.

## Repository Structure

```text
AudioASR/
│
├── reprodukcija5.ipynb
├── doprinos1.ipynb
├── doprinos2.ipynb
├── doprinos3.ipynb
│
├── audio/
│   └── audio samples used in experiments
│
├── rezultati/
│   ├── experimental results
│   ├── CSV files
│   └── generated figures
│
└── README.md
```

The repository structure may be further reorganized as the project is extended.

## Installation

Clone the repository:

```bash
git clone https://github.com/Sajko01/AudioASR.git
cd AudioASR
```

It is recommended to create a virtual environment before installing the dependencies.

### Windows

```bash
python -m venv .venv
.venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the required Python packages:

```bash
pip install faster-whisper
pip install ctranslate2
pip install openai-whisper
pip install jiwer
pip install pandas
pip install matplotlib
pip install numpy
pip install jupyter
pip install psutil
```

Alternatively, if a `requirements.txt` file is available:

```bash
pip install -r requirements.txt
```

## Running the Project

Start Jupyter Notebook:

```bash
jupyter notebook
```

Open and execute the experimental notebooks:

```text
reprodukcija5.ipynb
doprinos1.ipynb
doprinos2.ipynb
doprinos3.ipynb
```

For each notebook, run all cells in order:

```text
Kernel → Restart & Run All
```

Depending on the experiment, the notebooks generate:

* benchmark tables
* execution-time measurements
* memory measurements
* WER results
* plots and visualizations
* CSV files containing experimental results

## Reproducing the Results

To reproduce the experiments:

1. Install all required dependencies.
2. Make sure the required audio samples are available.
3. Start Jupyter Notebook.
4. Open the desired experimental notebook.
5. Restart the kernel.
6. Run all cells sequentially.
7. Compare the generated results with the provided experimental results.

Execution times can vary depending on CPU performance, available memory, operating system, library versions, and other hardware/software characteristics.

## Main Contributions

In addition to reproducing the basic Whisper/Faster-Whisper comparison, the project introduces several additional experimental analyses:

* benchmarking different Whisper model sizes
* comparing English and Serbian speech recognition
* evaluating robustness under white noise
* evaluating robustness under pink noise
* testing different SNR levels
* measuring Word Error Rate
* comparing inference time
* measuring memory consumption
* analyzing performance across different audio durations
* evaluating CPU-based INT8 Faster-Whisper inference

These experiments provide a broader view of the practical trade-offs involved when selecting a Whisper configuration for speech recognition applications.

## Conclusions

The experiments show that Faster-Whisper can significantly reduce computational requirements compared with the original Whisper implementation.

In the tested CPU environment, Faster-Whisper achieved faster inference and substantially lower memory consumption. The results also demonstrate that model size, audio duration, language, and background noise can affect ASR performance.

The project highlights an important practical trade-off in speech recognition systems:

> selecting an ASR model is not only about maximizing transcription accuracy, but also about balancing accuracy, inference speed, memory consumption, and robustness.

This makes optimized implementations such as Faster-Whisper particularly interesting for practical deployment scenarios where computational resources are limited.

## Future Work

Possible extensions of the project include:

* evaluation on larger speech datasets
* GPU benchmarking
* additional languages
* additional noise types and SNR levels
* real-world noisy recordings
* statistical evaluation across larger test sets
* automatic selection of the optimal Whisper configuration
* domain-specific evaluation and adaptation
* real-time speech recognition experiments

## Author

**Aleksandar Jovanović**

MSc student in Artificial Intelligence and Machine Learning
Faculty of Electronic Engineering, University of Niš
