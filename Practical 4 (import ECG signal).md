Practical 4 (import ECG signal)
t = linspace(0, 1, 500); % Time Vector    
EEG = rand(10, 500)*0.005; % Simulate EEG (mV)    
ofst = [1:size(EEG,1)]*0.005 + 0.001; % ‘Offset’ Vector   
EEGp = bsxfun(@plus, EEG', ofst)'; % Add ‘Offset’ To Each Row    
figure(1)    
plot(t, EEGp) % Plot EEG    
axis([xlim 0 0.055]) % Set Axis Limits    
ChC = regexp(sprintf('Ch-%02d ', [1:size(EEG,1)]), ' ', 'split'); % Y-Tick Labels    
yt = ofst+0.0025; % Y-Yick Positions   
set(gca, 'YTick',yt, 'YTickLabel',ChC(1:end-1))

