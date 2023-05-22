# Lab-Reports-ECE-4124
### Name: Md. Aarik Enam
### Roll: 1810020
### Exp No: 04
### Exp Name: Study of time delay of a signal and cross correlation of the given signal and the delayed signal
### Date of Submission:22/05/2023
#### Theory:
In the laboratory experiment, the focus is on examining the delay in timing of a signal and examining its cross-correlation with the original signal. Time delay refers to a shift in the signal's timing, while cross-correlation quantifies the similarity between two signals at various time lags. Through the manipulation of time delays and the calculation of cross-correlation, valuable information about signal alignment and similarity is obtained. This analysis holds significance in signal processing, communication systems, and applications related to pattern recognition.
#### Code:
```
clc
clear all
t=0:0.1:40
x1=(t>=0 & t<=10);
x2=(t>=10 & t<=15);
x3=(t>=15 & t<=25);
x4=(t>=25 & t<=40);
signal1 = 1*x1+0*x2-1*x3+0*x4;
subplot(3,1,1);
plot(t,signal1);
title('Main Signal');
delay = 5;
x5=(t>=0+delay & t<=10+delay);
x6=(t>=10+delay & t<=15+delay);
x7=(t>=15+delay & t<=25+delay);
x8=(t>=25+delay & t<=40+delay);
signal2 = 1*x5+0*x6-1*x7+0*x8;
subplot(3,1,2);
plot(t,signal2);
title('Delay Signal');
signal3 = xcorr(signal1,signal2);
subplot(3,1,3);
plot(signal3);
xlim([0 800]);
title('Cross-correlation of signals');
[~, max_index] = max(signal3);
delay_time =(length(signal1)-max_index);
disp('Delay Time: ');
disp(delay_time*0.1);
```
#### Output:
![HBK_04_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/ab08ad2c-8094-4a98-bcf7-03e2a70c56be)
#### Discussion:
In the laboratory experiment, our main objective was to examine the impact of time delay on the relationship between signals and their delayed versions through cross-correlation analysis. We closely monitored how various time delays affected the similarity between the original signal and its delayed counterparts. The results revealed a decline in cross-correlation as the time delay increased, indicating a decrease in alignment and similarity between the signals.
#### Conclusion:
The importance of aligning signals in terms of time and its influence on their similarity was demonstrated in the experiment. Through the examination of cross-correlation, we obtained a better understanding of how the time delay between signals relates to their correlation. This knowledge has practical implications in various fields including signal processing, communication systems, and pattern recognition, offering valuable insights for tasks like estimating time delays and synchronizing signals.
