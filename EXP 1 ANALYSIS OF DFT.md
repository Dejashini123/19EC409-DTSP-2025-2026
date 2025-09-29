# EXP 1 :  ANALYSIS OF DFT WITH AUDIO SIGNAL

# AIM: 

  To analyze audio signal by removing unwanted frequency. 

# APPARATUS REQUIRED: 
   
   PC installed with SCILAB/Python. 

# PROGRAM: 

// analyze audio signal
```from google.colab import files
uploaded = files.upload()
!pip install scipy matplotlib numpy
import numpy as np
import matplotlib.pyplot as plt
from scipy.io import wavfile
from scipy.fft import fft, fftfreq, ifft

# Step 1: Load the audio
fs, data = wavfile.read("dog bark sound.wav")  
if data.ndim > 1:   # if stereo, take one channel
    data = data[:,0]

# Step 2: Plot original waveform
plt.figure(figsize=(10,4))
plt.plot(data)
plt.title("Original Audio Signal")
plt.xlabel("Samples")
plt.ylabel("Amplitude")
plt.show()

# Step 3: Do FFT (DFT)
N = len(data)
yf = fft(data)
xf = fftfreq(N, 1/fs)

plt.figure(figsize=(10,4))
plt.plot(xf[:N//2], np.abs(yf[:N//2]))
plt.title("Frequency Spectrum")
plt.xlabel("Frequency (Hz)")
plt.ylabel("Magnitude")
plt.show()

# Step 4: Remove unwanted frequency (example: remove around 1000 Hz)
filtered = yf.copy()
low, high = 995, 1005   # frequency range to remove
filtered[(xf>low) & (xf<high)] = 0
filtered[(xf<-low) & (xf>-high)] = 0

# Step 5: Inverse FFT to reconstruct signal
cleaned = np.real(ifft(filtered))

# Step 6: Plot cleaned waveform
plt.figure(figsize=(10,4))
plt.plot(cleaned)
plt.title("Filtered Audio Signal")
plt.xlabel("Samples")
plt.ylabel("Amplitude")
plt.show()

# Step 7: Save filtered audio
wavfile.write("cleaned_audio.wav", fs, cleaned.astype(np.int16))
print("Filtered audio saved as cleaned_audio.wav")
```


# OUTPUT: 
<img width="658" height="287" alt="image" src="https://github.com/user-attachments/assets/80fce9fa-1ef5-4343-b699-92e49980deb1" />
<img width="631" height="296" alt="image" src="https://github.com/user-attachments/assets/a83f4432-27ab-41bd-9303-028e64aeb14d" />
<img width="658" height="304" alt="image" src="https://github.com/user-attachments/assets/adc19851-8cf4-46f3-8da1-61edfbf9997c" />

input audio: "C:\Users\91944\Downloads\dog-bark-sound-effect-322989 (1).mp3"
"C:\Users\91944\Downloads\dog bark sound.wav"



# RESULTS:The audio file has a sampling rate of 44100 Hz and contains 1428558 samples.
The waveform shows the variations in amplitude over time, representing the dog bark sound.

