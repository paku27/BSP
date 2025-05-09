Practical 6 (import EMG signal , determine frequency pectrum or power spectrum )
clc; 
close all; 
clear all; 
% Import the CSV file correctly
problem11_1 = readtable('/MATLAB Drive/BSP/EMG-data.csv');  
% Extract time and EMG signal data
t = problem11_1.time; 
y1 = problem11_1.channel1; 
% Find the length of the data per second
N = length(y1);
ls = size(y1); % Size of y1
f = 1/N; % Sampling rate or frequency
fs = 3000; 
T = 1/fs; % Period between each sample
t1 = (0 : N-1) * T; % Time vector
Nyquist = fs / 2; 
% Plot EMG Signal
figure;
subplot(3,1,1), plot(t, y1, 'b'); 
title('EMG signal'); 
xlabel('time (sec)'); 
ylabel('Amplitude (V)'); 
grid on; 
% Compute Power Spectrum
Y = abs(fft(y1)); 
Y(1) = []; 
power = abs(Y(1:N/2)).^2; 
nyquist = 1 / (2 * 0.001); 
freq = (1:N/2) / (N/2) * nyquist; 
% Plot Power Spectrum
subplot(212), plot(freq, power), grid on;
xlabel('Sample number (in Frequency)') 
ylabel('Power spectrum'); 
title({'Single-sided Power Spectrum' ... 
 ' (Frequency shown on a log scale)'}); 
axis tight;
 
