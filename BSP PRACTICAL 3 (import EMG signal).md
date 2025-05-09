BSP PRACTICAL 3 (import EMG signal)
CODE
clc;
clear all;
close all;
fid = fopen('emg_healthy.txt','r');
emg = fscanf(fid,'%f');
fclose(fid);
fs=1000;
Y=fft(emg);
N=length(Y);
f=linspace(0,fs,N);
Y(1)=0;
[~,idx]=max(abs(Y));
freq=f(idx);
fprintf('Dominant frequency:%f Hz\n', freq)
