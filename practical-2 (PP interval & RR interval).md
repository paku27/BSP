practical-2 (PP interval & RR interval)
BSP Practical 2

CODE:

h=60/72;
for a=0:h:2h
ECGdur=0:0.001:2.5;
Pint=0.11;
PRint=0.17;
STseg=0.10;
QTint=0.40;
QRSint=0.09;
pPeak=0.25;
rPeak=1.6;
qPek=.25*rPeak;
sPeak=.35*rPeak;
tPeak=0.3;

%genertion of p Wave
x=0:0.001:Pint;
y=pPeak*sin(x*pi/Pint)
plot (a+x,y);
grid on
hold on
xlabel('time(a)');
ylabel('voltage(mv');
title('ECG with 72bpm');

%genertion of pr segment
x=Pint:0.001:PRint;
plot(a+x,0);

%qrs Complex
q1=PRint+0.015;
r1=PRint+0.045;
s1=PRint+0.075;
s2=PRint+QRSint;
x=PRint:0.001:q1;
y=-26.667*x+4.53333;
plot(a+x,y)
x=q1:0.001:r1;
y=66.667*x-12.733;
plot(a+x,y)
x=r1:0.001:s1;
y=-72*x+17.08;
plot(a+x,y)
x=s1:0.001:s2;
y=37.333*x-9.706;
plot(a+x,y)
%st segment
t1=PRint+QRSint+STseg;
x=s2:0.0001:t1;
plot(a+x,0)
%Twave
t2=PRint+QTint;
x=t1:0.001:t2;
y=tPeak*sin((x-t1)*pi/(t2-t1));
plot(a+x,y)
x=t2:0.0001:h;
plot(a+x,0)
xlabel('time(s)');
ylabel('voltage(mV');
title('ECG wave');
end;

% Calculate R-R interval
RR_interval = r_locs (2) r_locs(1);
% Display intervals on the plot
text(mean([p_locs (1), p_locs (2)]), pPeak + 0.1, [num2str(PP_interval ), 's'], 'Color', 'b', 'FontSize', 12); text(mean([r_locs (1), r_locs (2)]), rPeak + 0.2, [num2str(RR_interval ), 's'], 'Color', 'r', 'FontSize', 12);
% Draw P-P interval line
plot([p_locs(1), p_locs (2)], [pPeak, pPeak], 'k-', 'LineWidth', 0.5);
% Draw R-R interval line
plot([r_locs(1), r_locs (2)], [rPeak, rPeak], 'k-', 'LineWidth', 0.5);
