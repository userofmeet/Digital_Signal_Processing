# DFT using inbuilt function
``` scilab
x=[1 2 3 4];
y=fft(x);
plot(abs(y));
plot2d3(abs(y));
title(’dft’);
xlabel(’time’);
ylabel(’amplitude’);
```

# Spectrum of exponential function
```scilab
//Spectrum of the exponential function
clc;
close;
clear;
fs=1; //sampling rate
n=0:1/fs:10 //10s duration (Increasing the value and observe spectrum)
x=exp(-n);
plot2d3(x)
//x1=[x, zeros(1,100)]; //zero padding for better spectrum resolution
y=fft(x1);
plot2d3(abs(fftshift(y)))
```

# Circular shift to x by 2 
``` scilab

clc;
clear;
close;
// Define original signal
x = [1 2 3 4];
// Plot original signal
subplot(311);
plot2d3(1:length(x), x, style=2);
title(’Original Signal’);
xlabel(’Index’);
ylabel(’Amplitude’);
// Perform manual circular shift by 2 positions
n = length(x);
shift_amount = 2;
x_shifted = [x(n-shift_amount+1:n) x(1:n-shift_amount)]; // Manual circu
subplot(312);
plot2d3(1:length(x_shifted), x_shifted, style=5);
title(’Circularly Shifted Signal’);
xlabel(’Index’);
ylabel(’Amplitude’);
// Compute DFT of circularly shifted signal
y = fft(x_shifted);
subplot(313);
plot2d3(1:length(y), abs(y), style=3);
title(’DFT Magnitude Spectrum’);
xlabel(’Frequency Index’);
ylabel(’Magnitude’);
```

# IDFT using inbuilt function
``` scilab
clc;
close;
clear;
fs=1; //sampling rate
n=0:1/fs:10 //10s duration (Increasing the value and observe spectrum)
x=exp(-n);
subplot(311)
plot2d3(x)
title(’Original Signal’);
xlabel(’Index’);
ylabel(’Amplitude’);
x1=[x, zeros(1,100)]; //zero padding for better spectrum resolution
y=fft(x1);
subplot(312)
plot2d3(abs(fftshift(y)))
title(’FFT of x(t)’);
xlabel(’Index’);
ylabel(’Amplitude’);
z=ifft(y);
subplot(313)
plot2d3(z)
title(’Inverse FFT of X(k)’);
xlabel(’Index’);
ylabel(’Amplitude’);
```

