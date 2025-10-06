# EXP 1(C) : Analysis of audio signal for noise removal

# AIM: 

# To analyse an audio signal and remove noise

# APPARATUS REQUIRED:  
PC installed with SCILAB. 

# PROGRAM: 
```
# Step 1: Upload the audio file
from google.colab import files
uploaded = files.upload()   # Upload your audio file (example: dog_bark.wav)

# Step 2: Install required libraries
!pip install scipy matplotlib numpy

# Step 3: Import libraries
import numpy as np
import matplotlib.pyplot as plt
from scipy.io import wavfile
from scipy.fft import fft, fftfreq, ifft

# Step 4: Read the audio file
fs, data = wavfile.read("dog bark sound.wav")   # change name if different
if data.ndim > 1:   # if stereo, select one channel
    data = data[:, 0]

# Step 5: Plot original audio waveform
plt.figure(figsize=(10,4))
plt.plot(data)
plt.title("Original Audio Signal")
plt.xlabel("Samples")
plt.ylabel("Amplitude")
plt.show()

# Step 6: Perform DFT using FFT
N = len(data)
yf = fft(data)
xf = fftfreq(N, 1/fs)

# Step 7: Plot frequency spectrum
plt.figure(figsize=(10,4))
plt.plot(xf[:N//2], np.abs(yf[:N//2]))
plt.title("Frequency Spectrum of Original Signal")
plt.xlabel("Frequency (Hz)")
plt.ylabel("Magnitude")
plt.show()

# Step 8: Remove unwanted frequency range (noise)
# Example: removing noise around 1000 Hz
filtered = yf.copy()
low, high = 995, 1005
filtered[(xf > low) & (xf < high)] = 0
filtered[(xf < -low) & (xf > -high)] = 0

# Step 9: Reconstruct cleaned signal using Inverse FFT
cleaned = np.real(ifft(filtered))

# Step 10: Plot filtered audio waveform
plt.figure(figsize=(10,4))
plt.plot(cleaned)
plt.title("Filtered Audio Signal (After Noise Removal)")
plt.xlabel("Samples")
plt.ylabel("Amplitude")
plt.show()

# Step 11: Save filtered audio
wavfile.write("cleaned_audio.wav", fs, cleaned.astype(np.int16))
print("Filtered audio saved as cleaned_audio.wav")

# Step 12: Download the filtered audio
from google.colab import files
files.download("cleaned_audio.wav")

```
OUTPUT:




// DISCRETE FOURIER TRANSFORM 

# RESULT: 
