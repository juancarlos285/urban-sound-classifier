## Urban Sound Classification Project

### Motivation
The motivation behind this project is to address the issue of noise pollution in urban settings. Noise pollution can have detrimental effects on human health, including hearing loss, sleep disturbances, increased stress levels, and impaired cognitive function. By developing a machine learning model capable of accurately classifying urban sounds, we can better understand and monitor noise pollution levels, ultimately working towards mitigating its adverse impacts on urban residents.

### Overview
This project aims to classify urban sounds using machine learning techniques. The dataset utilized is the UrbanSounds8K from Kaggle, containing various urban sound recordings across different categories. The classification task involves identifying the following classes: air conditioner, car horn, children playing, dog bark, drilling, engine idling, gun shot, jackhammer, siren, and street music.

### Dataset and Testing Methodology
The dataset comprises audio files obtained from urban environments, each labeled with one of the aforementioned classes. To ensure fair evaluation, a specific testing methodology is employed. The data is divided into 10 predetermined folds, and cross-validation is performed across these folds to obtain the mean accuracy. Reshuffling the data is avoided to prevent inflated scores that may not accurately reflect model performance.

### Features Extraction
Features are extracted from the audio files, categorized into three domains: time, frequency, and time-frequency. These features include:

**Time Domain:**
- Zero-crossing rate: The rate at which the audio waveform changes its sign. It provides insights into the noisiness of the signal.
- Tempo: The speed or pace of the audio signal, usually measured in beats per minute (BPM). It characterizes the rhythm of the sound.

**Frequency Domain:**
- RMS energy (Root Mean Square energy): It represents the overall energy level of the audio signal. It is calculated as the square root of the average of the squared values of the signal's amplitude.
- Spectral centroid: It indicates where the "center of mass" of the spectrum is located, providing information about the brightness of the sound.
- Spectral rolloff: It is the frequency below which a certain percentage (usually 85% or 95%) of the total spectral energy lies. It helps in distinguishing between harmonic and non-harmonic sounds.
- Spectral flatness: It measures the flatness or peakiness of a power spectrum. A value closer to 1 indicates a flat spectrum, while a value closer to 0 indicates a peaky spectrum.

**Time-Frequency Domain:**
- MFCCs (Mel-frequency cepstral coefficients): These coefficients represent the short-term power spectrum of a sound. They are widely used in speech and audio processing tasks due to their effectiveness in capturing spectral characteristics.
- Spectral flux: It measures the change in spectral content between consecutive frames of an audio signal, indicating the dynamics or spectral changes over time.
- Tempogram ratio: It captures rhythmic patterns in music by analyzing the tempo variations over time.
- Spectral contrast: It quantifies the difference in amplitude between peaks and valleys in the spectrum of an audio signal, providing information about spectral texture and timbre.

### Machine Learning Models Tested
Several machine learning models are tested for classification performance:

1. **Logistic Regression:**
   - Accuracy: ~66%
   - Parameters:
     - C regularization: 100
     - Model penalty: L2
     - Solver: LBFGS

2. **Convolutional Neural Network (CNN):**
   - Accuracy: ~39% (trained on 10 epochs per validation)
   - Approach: Due to varying audio file lengths, spectrograms used in CNN had different dimensions. Zero-padding was employed to address this issue.

3. **XGBoost:**
   - Accuracy: ~69%
   - Parameters:
     - Learning rate: 0.3
     - Max tree depth: 6
     - Estimators: 500

### Conclusion
This project served as an excellent exercise in implementing multiple machine learning models to tackle audio classification. Moving forward, further steps may involve extracting additional features to enhance model performance and continuing to utilize XGBoost, or exploring recurrent neural networks (RNNs) which may be more suitable for capturing the temporal characteristics of sounds. Additionally, for CNNs, exploring alternative techniques to address varying audio lengths in spectrograms may yield improved results.
