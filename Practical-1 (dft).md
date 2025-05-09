Practical-1 (dft)
BSP PRACTICAL 1

clc; 
clear all; 
Fs = 1000; % sampling frequency 1 kHz 
t = 0 : 1/Fs : 0.296; % time scale 
f = 200; % Hz, embedded dominant frequency 
x = cos(2*pi*f*t) + randn(size(t)); % time series 
plot(t,x), axis('tight'), grid('on'), title('Time series'), figure 
nfft = 512; % next larger power of 2 
y = fft(x,nfft); % Fast Fourier Transform 
y = abs(y.^2); % raw power spectrum density 
y = y(1:1+nfft/2); % half-spectrum 
[v,k] = max(y); % find maximum 
fprintf('Maximum value is: %f\n', v);
f_scale = (0:nfft/2)* Fs/nfft; % frequency scale 
plot(f_scale, y),axis('tight'),grid('on'),title('Dominant Frequency') 
f_est = f_scale(k); % dominant frequency estimate 
fprintf('Dominant freq.: true %f Hz, Estima
 
