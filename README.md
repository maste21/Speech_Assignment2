# Speech Understanding Assignment - 2

## Overview

This project implements a complete speech processing pipeline for handling code-switched (English-Hindi) lecture audio and converting it into Tamil (Low Resource Language).

The system includes:

* Speech-to-Text (STT)
* Language Identification (LID)
* IPA conversion
* Translation to Tamil
* Prosody alignment using DTW
* Anti-spoofing detection
* Adversarial robustness (FGSM)

---

## Folder Structure

```
├── pipeline.ipynb              # Main implementation
├── Report.pdf                 # Final report
├── original_segment.wav       # Input audio
├── clean_audio.wav            # Preprocessed audio
├── student_voice_ref.wav      # 60 sec voice sample
├── final_output.txt           # Translated Tamil text
```

---

## Requirements

Install dependencies:

```
pip install torch librosa numpy matplotlib scikit-learn noisereduce epitran resemblyzer
```

---

## Methodology

### 1. Preprocessing

* Noise reduction using spectral subtraction
* Audio normalized to 22.05 kHz

### 2. Speech-to-Text

* Whisper model used
* Logit bias applied for domain-specific words

### 3. Language Identification

* LFCC features used
* Feedforward neural network classifier

### 4. Translation

* Custom English–Tamil dictionary (~50+ words)
* Unknown words retained

### 5. Voice Processing

* Speaker embedding using Resemblyzer
* DTW for prosody alignment

### 6. Anti-Spoofing

* LFCC-based classifier
* Evaluated using EER

### 7. Adversarial Testing

* FGSM attack applied
* Accuracy degradation analyzed

---

## Results

| Metric        | Value |
| ------------- | ----- |
| WER (English) | ~18%  |
| WER (Hindi)   | ~30%  |
| LID F1-score  | ~0.78 |
| EER           | ~35%  |

---

## Limitations

* Limited translation dictionary
* No full TTS implementation
* Proxy labels used for LID

---

## Conclusion

The system demonstrates a functional pipeline for code-switched speech processing. While performance can be improved with better datasets and models, the implementation satisfies core objectives of the assignment.

---
