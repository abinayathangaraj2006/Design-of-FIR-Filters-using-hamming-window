# Design-of-FIR-Filters-using-hamming-window

# DESIGN OF LOW PASS FIR DIGITAL FILTER 

# AIM: 
          
  To generate design of high pass FIR digital filter using SCILAB 

# APPARATUS REQUIRED: 

  PC Installed with SCILAB 

# PROGRAM
clc;
clear;
close;

// Low Pass FIR Filter using Hamming Window
N = 31;              // Filter length
fc = 0.3;            // Normalized cutoff frequency (fc = Fcutoff / (Fs/2))
n = 0:N-1;
alpha = (N-1)/2;

// Hamming window
w = 0.54 - 0.46*cos(2*%pi*n/(N-1));

// Ideal Low Pass Filter Impulse Response
hd = zeros(1, N);
for i = 1:N
    if (i-1) == alpha then
        hd(i) = 2*fc;
    else
        hd(i) = sin(2*%pi*fc*(i-1-alpha)) / (%pi*(i-1-alpha));
    end
end

// Multiply by window
h = hd .* w;

// Frequency Response
[H, f] = frmag(h, 512);

// Plot
figure;
subplot(2,1,1);
plot(f, 20*log10(abs(H)));
xlabel('Normalized Frequency');
ylabel('Magnitude (dB)');
title('LOW PASS FIR FILTER (Hamming Window)');

subplot(2,1,2);
plot(f, atan(imag(H), real(H)));
xlabel('Normalized Frequency');
ylabel('Phase (radians)');
title('Phase Response');


# OUTPUT
<img width="799" height="388" alt="Screenshot 2025-11-17 160307" src="https://github.com/user-attachments/assets/b5bcabd0-2900-4328-98c6-6bd8edfc1338" />

<img width="858" height="423" alt="Screenshot 2025-11-17 160318" src="https://github.com/user-attachments/assets/2d9dd3e9-9851-4e8e-8579-6f6c43645b42" />
<img width="550" height="672" alt="Screenshot 2025-11-17 160327" src="https://github.com/user-attachments/assets/2bdcdb04-aaa9-405c-ae71-34613bd1f021" />


# RESULT
design of lowpass filter using hamming window
