Practical 5  (import EMG signal calculate AVR value to EMG signal)


code:-
clc; 
close all; 
clear all; 
%problem 11.1
%%import the data in the fil\tsclient\E\BIOM480A3\Hw5\p11_1.xls'e and plot the signal
problem11_1 = load('C:\Users\admin\Downloads\b2\b2\emg_healthy.txt'); 
t = problem11_1(:, 1); 
y1 = problem11_1(:, 2); 
N = length(y1);% find the length of the data per second
ls = size(y1); %% size
f = 1/N;% find the sampling rate or frequency
fs = 3000; 
T = 1/fs % period between each sample
t1 = (0 : N-1) *T;%t = (0:1:length(y1)-1)/fs; % sampling period
Nyquist = fs/2; figure; 
subplot (3,1,1), plot(t,y1,'b'); 
title ('EMG signal of single muscle 40 month old patient '); 
xlabel ('time (sec)'); 
ylabel ('Amplitute (V)'); 
grid on; 
Y= abs(fft(y1)); Y(1) = []; 
power = abs(Y(1:N/2)).^2; 
nyquist = 1/(2*0.001); freq = (1:N/2)/(N/2)*nyquist; 
subplot(212), plot(freq,power), grid on xlabel('Sample number (in Frequency)') 
ylabel('Power spectrumen'); 
title({'Single-sided Power spectrum' ... 
 ' (Frequency in shown on a log scale)'}); 
axis tight
%%% RMS of the signal
rms_y1 = sqrt(mean(y1.^2)); 
msgbox(strcat('RMS of EMG signal is = ',mat2str(rms_y1), '')); 
rms_emg = rms (y1); 
%%%%%AVR of the signal
 arv_y1 = abs(mean(y1)); 
 msgbox(strcat('ARV of EMG signal is = ',mat2str(arv_y1), ''));
 
