# Lab-Reports-ECE-4124
## Name: Md. Aarik Enam
## Roll: 1810020
## Date of Submission:19/08/2023

### Exp No: 01
### Exp Name: Study of Convolution of Two Signals using MATLAB
#### Theory:
The study of convolution involves understanding how two signals interact and combine to create a new signal. Convolution is a fundamental concept in signal processing and mathematics that finds applications in various fields, including signal analysis, image processing, and engineering.Studying the convolution of two signals is pivotal in understanding how signals interact and create new signals based on their characteristics. This concept has broad applications in various fields and provides insights into system behavior and signal processing operations.
#### Code:
```
x = [ 1 2 3 4]; 
h = [ 4 4 3 2]; 
m=length(x); 
l=length(h); 
X=[x,zeros(1,l)]; 
H=[h,zeros(1,m)]; 
z=[]; 
for i=1:m 
g=h.*x(i); 
z=[z;g]; 
end 
[r c] = size(z); 
k = r+c; 
t =2; 
Y =[]; 
cd =0; 
while(t<=k) 
for i=1:r 
for j=1:c 
if((i+j)==t) 
cd = cd+ z(i,j); 
end 
end 
end 
t = t+1; 
Y = [Y cd]; 
cd =0; 
end 
subplot(3,1,1); 
stem(x); 
xlabel('n'); 
ylabel('x'); 
title('1st Signal'); 
subplot(3,1,2); 
stem(h); 
xlabel('n'); 
ylabel('h'); 
title('2nd Signal'); 
subplot(3,1,3); 
stem(Y); 
xlabel('n'); 
ylabel('Y'); 
title('Convoluted Signal');
```
#### Output:
![Experiment-1_page3_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/08080f60-0ff7-4052-bf68-27968b33a4ec)
#### Discussion & Conclusion:
In this instance, we performed convolution between two signals manually, without employing the conv() function. To validate the accuracy of our manual computation, we also utilized the conv() function and compared the results. Remarkably, the outcomes from both approaches were found to be identical, confirming the successful execution of the convolution process.
### Exp No: 02
### Exp Name:  Study of Circular Convolution, Plotting of Figures, Summation, Subtraction and Particular Shapes of Two Signals Using MATLAB
#### Theory:
The study encompassed several key aspects of signal processing using MATLAB, including circular convolution, graph plotting, summation, subtraction, and the analysis of specific signal shapes. Notably, circular convolution was thoroughly examined through manual calculations, avoiding the utilization of built-in functions. MATLAB's capabilities were harnessed to generate graphical representations of various figures. Additionally, the study involved performing summation and subtraction operations on pairs of signals to explore their effects. Lastly, the MATLAB platform was utilized to investigate and visualize particular signal shapes exhibited by the signals under consideration.
#### Code:
##### Problem-01:
```
x = input('Enter the first signal: '); 
subplot(3, 1, 1);
stem(x);
h = input('Enter the second signal: '); 
subplot(3, 1, 2);
stem(h);

N = length(x); 
M = length(h);

if N > M
h = [h zeros(1,N-M)];
else
x = [x zeros(1,M-N)];
end

y = zeros(1, N); 
for n = 1:N
for m = 1:N
k = mod(n - m, N) + 1; 
y(n) = y(n) + x(m) * h(k);
end 
end

disp('Circular Convolution Output: '); 
disp(y);
subplot(3, 1, 3); 
stem(y);
```
##### Problem-02:
```
n1 = [0, 0, 0, 2, 2, 2, 1, 1, 1, 0, 2] 
subplot(4, 1, 1);
stem(n1);
title('1st signal'); 
xlabel('Index');
ylabel('Value'); 

n2 = [2, 2, 0, 1, 1, 1, 0, 0, 0, 0, 3] 
subplot(4, 1, 2);
stem(n2);
title('2nd signal'); 
xlabel('Index');
ylabel('Value'); 

n3=n1+n2; 
subplot(4, 1, 3); 
stem(n3);
title('Summation'); 
xlabel('Index'); 
ylabel('Value');

n4=n1-n2; 
subplot(4, 1, 4); 
stem(n4);
title('Subtraction'); 
xlabel('Index');
ylabel('Value');
```
##### Problem-03:
```
x=[0 0 1 1 1 1 0 0]; 
t=0:1:7;
subplot(2,1,1); 
plot(t,x);

y=[0 1 1 2 2 1 1 0]; 
t=0:1:7;
subplot(2,1,2); 
plot(t,y);
```
#### Output:
##### Problem-01:
![Experiment-2_page4_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/7c4873e5-6358-4204-8486-852917420803)
![Experiment-2_page5_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/9de636f5-ef15-4f7f-9e08-b7c3f1a472bf)

##### Problem-02:
![Experiment-2_page5_image2](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/84f5e697-a321-44dd-91a2-625ff56753a1)

##### Problem-03:
![Experiment-2_page6_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/d79877b9-48ef-4ac6-83f1-12365640dc07)

#### Discussion & Conclusion:
Circular convolution of a pair of signals was executed manually, circumventing the use of any pre-existing functions. Subsequently, a built-in function was employed to validate the consistency of the previously computed output. Remarkably, the outcomes from both approaches were found to be identical. Furthermore, the study involved the plotting of two signals, their summation, and subtraction, along with an exploration of specific signal shapes exhibited by them.
It was done successfully.
### Exp No: 03
### Exp Name: Study of Auto-correlation & Cross-correlation Using MATLAB
#### Theory:
Auto-correlation and cross-correlation are statistical measures used to quantify the similarity or relationship between different instances of a signal or between two different signals.

Auto-correlation:
Auto-correlation measures the similarity between a signal and a time-shifted version of itself. It gives us an idea of how much a signal's values at different time points correlate with each other. In other words, it tells us how well a signal matches with a delayed copy of itself.

Cross-correlation:
Cross-correlation measures the similarity between two different signals as one of them is shifted over time. It gives us insight into how well two signals match with each other when they are displaced by a certain amount.

In both auto-correlation and cross-correlation:
Positive values indicate that the signals are positively correlated (similar patterns).
Negative values indicate that the signals are negatively correlated (opposite patterns).
Values near zero indicate little to no correlation between the signals.

#### Code:
##### Auto-Correlation:
```
x=input('Enter your sequence:'); 
h=fliplr(x);
a=length(x); 
b=length(h); 
n=a+b-1; 
y=zeros(1,n); 
l=1:n;
for i=0:n 
for j=0:n
if((i-j+1)>0 && (i-j+1)<=b && (j+1)<=a) 
y(i+1)=y(i+1)+x(j+1).*h(i-j+1);
end 
end 
end
b=xcorr(x,x)
disp(y)
subplot(4,1,1) 
stem(x)
xlabel('n'); 
ylabel('x[n]'); 
title('Sequence1');
subplot(4,1,2) 
stem(h)
xlabel('n'); 
ylabel('h[n]'); 
title('Sequence2');
subplot(4,1,3); 
stem(l,y) 
xlabel('n'); 
ylabel('y[n]'); 
title('Result');
subplot(4,1,4); 
stem(b) 
xlabel('n'); 
ylabel('y[n]');
title('Result using built-in function');
```
##### Cross-Correlation:
```
x = input('Enter the 1st signal sequence:'); 
h = input('Enter the 2nd signal sequence: '); 
z=fliplr(h);
a=length(x); 
b=length(z); 
n=a+b-1; 
y=zeros(1,n); 
l=1:n;
for i=0:n 
for j=0:n
if((i-j+1)>0 && (i-j+1)<=b && (j+1)<=a) 
y(i+1)=y(i+1)+x(j+1).*z(i-j+1);
end 
end
end
b=xcorr(x,h)
disp(y)
subplot(4, 1, 1); 
stem(x);
xlabel('n');
ylabel('x[n]'); 
title('1st Sequence');
subplot(4, 1, 2); 
stem(h);
xlabel('n');
ylabel('z[n]'); 
title('2nd Sequence');
subplot(4, 1, 3); 
stem(l,y); 
xlabel('n'); 
ylabel('y[n]'); 
title('Result'); 
subplot(4, 1, 4);
stem(b); 
xlabel('n'); 
ylabel('b[n]');
title('Result using built-in function');
```
#### Output:
##### Auto-Correlation:
![Experiment-3_page4_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/87dfa3c1-baa6-4290-89ba-b6fe69981b76)
![Experiment-3_page5_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/9041d705-c886-4c45-a2d6-3ec7b9014b42)
##### Cross-Correlation:
![Experiment-3_page5_image2](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/e604ecc6-8fb1-4f65-bd99-61e592e69b7f)
![Experiment-3_page6_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/2d4b9329-0cd2-428e-9319-6c9a1b2e0e85)

#### Discussion & Conclusion:
Auto-correlation of a single signal and cross-correlation between two distinct signals were conducted through manual computations, avoiding the use of any pre-existing functions. A comparison was made between these manual results and the outcomes generated using a built-in function. Remarkably, the findings from both approaches were found to be consistent. MATLAB was employed to graphically represent the signals, their auto-correlation, and cross-correlation, both for the manual calculations and those based on the built-in function.
The experiment was carried out successfully.
### Exp No: 04
### Exp Name: Study of time delay of a signal and cross correlation of the given signal and the delayed signal
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


### Exp No: 05
### Exp Name: Study of Causal, Anti-causal, Non-causal Signals, Their Respective Poles & Zeros on the Z-plane.
#### Theory:
The study of signals and systems in the context of the Z-plane involves analyzing their properties such as causality and the locations of poles and zeros.

Causal Signal: A signal is considered causal if its value at any given time depends only on its past values and not on its future values. Mathematically, a discrete-time signal x[n] is causal if x[n] = 0 for n < 0.
Anti-Causal Signal: An anti-causal signal is the opposite of a causal signal. It depends only on future values and not on past values. A discrete-time signal x[n] is anti-causal if x[n] = 0 for n ≥ 0.
Non-Causal Signal: A non-causal signal doesn't satisfy the causality condition, meaning it has non-zero values both in the past and future. Non-causal signals are not typically encountered in physical systems and often arise due to theoretical considerations or mathematical manipulation.

Poles: In the context of the Z-transform, poles are the values of the variable 'z' for which the denominator of the Z-transform becomes zero. Poles determine the stability and behavior of a system. In terms of the Z-plane, poles are points that affect the convergence and behavior of the system.
Zeros: Zeros are the values of the variable 'z' for which the numerator of the Z-transform becomes zero. Zeros indicate where the system output becomes zero. Similar to poles, zeros also influence the behavior of a system.

Analyzing poles and zeros in the Z-plane is crucial for understanding the behavior and characteristics of discrete-time signals and systems, as they directly influence properties like stability, transient response, and frequency response.

#### Code:
##### Causal Signal:
```
x=[3 1 2 4]
b=0;
n=length(x);
y=sym('z');
for i=1:n
b=b+x(i)*y^(1-i);
end
display(b)
z=[];
p=[0]
zplane(z,p)
```
##### Anti-Causal Signal:
```
x=[3 1 2 4]
b=0;
n=length(x);
y=sym('z');
for i=1:n
b=b+x(i)*y^(i-1);
end
display(b)
z=[];
p=[]
zplane(z,p)
```
##### Non-Causal Signal:
```
x=[3 1 2 4]
c=input('Enter the Index: ');
disp(c);
b=0;
n=length(x);
y=sym('z');
for i=0:n-1
if i>=c-1
b=b+x(i+1)*y^(c-i-1);
else
b=b+x(i+1)/y^(i-c+1);
end
end
display(b)
z=[];
p=[0]
zplane(z,p)
```
#### Output:
##### Causal Signal:
![Experiment-5_page4_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/4d35e616-a374-4fd2-8ca8-f079fa3de903)
![Experiment-5_page4_image2](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/031da275-9fcd-409e-9fff-a9b2fb2b5755)

##### Anti-Causal Signal:
![Experiment-5_page5_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/834fda04-c548-42fa-b657-14c5dd180324)
![Experiment-5_page5_image2](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/81333c3f-41fd-43d7-98fb-a36599988f06)

##### Non-Causal Signal:
![Experiment-5_page6_image](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/49190121-1478-4fb3-9daa-240086a0166e)
![Experiment-5_page6_image2](https://github.com/Dragorrik/Lab-Reports-ECE-4124/assets/86437161/66d48c33-c4c3-4414-9791-f2d0027ccc8b)

#### Discussion & Conclusion:
This experiment has provided us with insights into causal, anti-causal, and non-causal signals, along with their corresponding poles and zeros. A causal signal is represented by a sequence with values only for nonnegative time instances or indices. Applying the Z-transform to a causal signal typically yields a rational function that is valid within a region of convergence (ROC) encompassing the unit circle.
Conversely, an anti-causal signal is described by a sequence having values exclusively for negative time instances or indices. When the Z-transform is applied to an anti-causal signal, it typically results in a rational function with an ROC that covers the area outside the unit circle.
Lastly, a non-causal signal pertains to a sequence with nonzero values for both positive and negative time instances or indices. Despite being able to compute the Z-transform for a non-causal signal, the resultant expression might not be a rational function. In this case, the ROC may take the form of a ring or annulus within the Z-plane.

The experiment was carried out successfully.


