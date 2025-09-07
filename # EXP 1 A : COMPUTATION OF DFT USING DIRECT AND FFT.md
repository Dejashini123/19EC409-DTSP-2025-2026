# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 

# To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
// DISCRETE FOURIER TRANSFORM 
clc;
clear;

x = [1 2 3 4];   // input signal
N = length(x);
n = 0:N-1;

// --- Direct DFT (Formula Method) ---
X_dft = zeros(1, N);
for k = 0:N-1
    for m = 0:N-1
        X_dft(k+1) = X_dft(k+1) + x(m+1)*exp(-%i*2*%pi*k*m/N);
    end
end

// --- FFT (Built-in Function) ---
X_fft = fft(x, -1);

// --- Plots ---
subplot(3,1,1);
plot(n, x);
title("Input Signal");

subplot(3,1,2);
plot(n, abs(X_dft));
title("DFT Magnitude (Direct Method)");

subplot(3,1,3);
plot(n, abs(X_fft));
title("FFT Magnitude (Built-in)");

# OUTPUT: 
<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/29426bde-7665-40f7-b847-83048f529c23" />



# RESULT: The DFT of the given sequence using Direct method and FFT method are obtained.
Both methods give the same output spectrum, hence verified.
