# DTMF signal for Mobile no.
``` scilab
clc;
close;
clear;
row_f1=[700 770 850 941]; // Row Frequency
colum_f1=[1220 1350 1490]; // Column Frequency
fs=8000; // Sampling Frequency
N=1:4000; // Total No. of Sample
mobile=[9 9 9 8 7 6 0 4 6 5]; // Mobile Number
temp=[]; // Array that Contain total signal for each Digit
figure;
for i=1:length(mobile)
select mobile(i)
case 1
row_f=1;
colum_f=1;
case 2
row_f=1;
colum_f=2;
case 3
row_f=1;
colum_f=3;
case 4
row_f=2;
colum_f=1;
case 5
row_f=2;
colum_f=2;
case 6
row_f=2;
colum_f=3;
case 7
row_f=3;
colum_f=1;
case 8
row_f=3;
colum_f=2;
case 9
row_f=3;
colum_f=3;
case 0
row_f=4;
colum_f=2;
else
row_f=4;
colum_f=1;
end
y=sin(2*3.14*(row_f1(row_f)/fs)*N)+sin(2*3.14*(colum_f1(colum_f)/fs)*N);
temp=[temp y zeros(1,4000)]; // Append the Signal + zeros After each Numb
end
plot(temp);
sound(temp,fs);
wavwrite(temp, fs, ’C:\Users\user1/sound.wav’)
```

# Decoding number from DTMF signal
``` scilab
clc
clear
[thissound, fs]=wavread(’C:\Users\user1\sound.wav’);
L=length(thissound);
Y=fft(thissound);
L=length(Y)
f=(0:L-1)*(fs/L);
magnitude = abs(Y)
plot(f, magnitude)
```

# Echo generation
``` scilab
b = [1 zeros(1,7999) 0.5]; // numerator coefficient correspond to 1 sec d
a = [1]; //denominator coefficient
[x,Fs] = wavread(’C:\Users\djain/e.wav’) //read speech file
Y =filter(b,a,x); //pass speech file through filter
wavwrite( Y,’ringecho1.wav’) // generate another file with delay
```

# Low pass filtering 
``` scilab
N = 4;Rp = 5;Rs = 80;
Wn = .15;
[x, Fs] = wavread(’e.wav’);
[B,A] = ellip(N,Rp,Rs,Wn);
yl= filter(B,A,x);
sound(yl,44100)
wavwrite(yl,44100,’lpf.wav’)
```

# High pass filtering
``` scilab
N = 4;
Rp = 5;
Rs = 80;
Wn = 0.15;
[x, Fs] = audioread(’e.wav’);
[B, A] = ellip(N, Rp, Rs, Wn, ’high’);
yh = filter(B, A, x);
sound(yh, Fs);
audiowrite(’hpf.wav’, yh, Fs);
```

#  ECG signal generation
```scilab
//Generation of ECG signals.
clc;
clear all;
close all;
cycle=zeros(1,500);
y=[1 2 3 4 5 6 7 8 9 10 9 8 7 6 5 4 3 2 1 0]/4;
t=[0:1:40]; //% Local time axis
a=(.05*(t-20).*(t-20)-20)/50; //Parabolic recovery segment
cycle(1:61)=2*[y a]; // Place pulse in 1sec. cycle
cyc=filter([1 1 1 1 1], [1], cycle);// % Smooth the corners
x=[cyc cyc cyc cyc cyc]; //..% Repetition used for 5 cycle of trace
[idum, nsize]=size(x);
t=[0:1:nsize-1]/500 ; //% Sampling frequency 500Hz
plot(t,x);
xlabel(’Time(sec)’);
ylabel(’Amplitude’);
title(’ECG signal’)
```

# Noisy ECG
``` scilab
clc
clear
close;
cycle = zeros(1, 500);
y = [01 2 3 4 5 6 7 8 9 10 9 8 7 6 5 4 3 2 1 0] / 4;
t = 0:1:40;
a = (.05 * (t - 20) .* (t - 20) - 20) / 50;
cycle(1:61) = 2 * [y a];
cyc = filter([1 1 1 1 1], [1], cycle);
x = [cyc, cyc, cyc, cyc, cyc];
noise = (rand(1, length(x)) - 0.5); // Generate random noise
noisy_ecg = x + noise;
nsize = length(noisy_ecg);
t = (0:nsize-1) / 500;
plot(t, noisy_ecg);
xlabel("Time (sec)");
ylabel("Amplitude");
title("Noisy ECG Signal");
xtitle("Noisy ECG Signal");
```

# Moving average filter
``` scilab
x=[0 0 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0]
y(1)=0
y(2)=0
for n=1:16
y(n+2)= x(n+2)+0.166*x(n+1)+0.166*x(n)
end
disp(y)
plot(y)
```
