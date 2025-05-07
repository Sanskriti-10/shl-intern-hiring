# shl-intern-hiring

 1. Libraries Used and Why
Library	Purpose	Why It’s Used
pandas, numpy	Data manipulation	To handle and transform data from .csv files and manage feature arrays.
librosa	Audio processing	Industry-standard Python library to extract meaningful features from .wav audio files.
soundfile	Audio reading	Backend used by librosa to load .wav files accurately.
sklearn.ensemble.GradientBoostingRegressor	Machine learning model	A powerful and interpretable tree-based regression model that handles non-linear relationships well.
sklearn.metrics.mean_squared_error	(Optional) Evaluation metric	Measures how close predictions are to actual values.
tqdm	Progress visualization	Adds a progress bar to long loops (like extracting features for all audio files), improving user experience.

 2. Audio Features Extracted and Why
The notebook uses feature engineering — manually extracting key characteristics from audio signals using librosa.

Feature	Explanation	Why It Helps
Duration	Length of the audio clip	Longer or shorter answers might relate to grammar usage (fluency).
Zero Crossing Rate (ZCR)	How frequently the audio waveform crosses the zero line	Indicates noisiness or articulation, possibly correlating with clarity.
Root Mean Square Energy (RMSE)	Loudness of the signal	Higher energy may imply more confident and fluent speech.
Spectral Centroid	“Center of mass” of the sound spectrum	Helps differentiate between different types of sounds (e.g., harsh vs. soft speech).
Spectral Bandwidth	Range of frequencies present	Indicates tonal range and variation in speech.
Spectral Rolloff	Frequency below which a large portion of the spectrum lies	Captures shape of the audio signal — potentially linked to articulation.
MFCCs (1st and 2nd)	Mel-frequency cepstral coefficients, summarizing audio shape in human-like hearing scale	Common in speech and emotion detection, helps characterize speaker style.


 3. Model Used: Gradient Boosting Regressor
Why Gradient Boosting?
Handles small tabular datasets well

Good performance without deep learning

Captures complex relationships between features and target

Less prone to overfitting than plain decision trees

No need for heavy GPU or long training times

This model is a good baseline when you're working with structured, hand-crafted features like these.
 4. Training and Prediction
What’s Done:
Loops through each training .wav file

Extracts audio features

Trains the Gradient Boosting Regressor on this data

Applies the same extraction on test audio

Predicts grammar scores using the trained model

This workflow creates a pipeline from raw audio → features → model → predictions.
