# Signal Generation
``` scilab
%IMPULSE SIGNAL
t1=-5:5
x1=[zeros(1,5) 1 zeros(1,5)]
subplot(131)
plot2d3(t1,x1)

%UNIT STEP SIGNAL
x2=[zeros(1,5),1,ones(1,5)]
subplot(132)
plot2d3(t1,x2)

%RAMP SIGNAL
t2=0:5
x3=t2
subplot(133)
plot2d3(t2,x3)
```

# To separate odd and even parts of a signal
``` scilab
x=[1 2 3 4 4 2 1]
N=-3:3
x1=mtlb_fliplr(x)
xe=(x1+x)/2
xo=(x-x1)/2
subplot(221)
plot2d3(N,x)
subplot(222)
plot2d3(N,x1)
subplot(223)
plot2d3(N,xe)
subplot(224)
plot2d3(N,xo)
```

# Energy of a signal
``` scilab
x=[1,2,1,1,0,0,0,0]
y=length(x)
E=0
for i=1:y
E=E+(x(i)*x(i))
end
disp(E)
```

# Interpolation 
``` scilab
input_signal = [8, 6, 4, 7, 8, -2, 4, 2]
signal_length = length(input_signal)
linear_interp_signal = []
for i = 1:signal_length-1
start_value = input_signal(i)
end_value = input_signal(i+1)
linear_interp_signal = [linear_interp_signal, start_value]
interp_value = start_value + (end_value - start_value) / 2
linear_interp_signal = [linear_interp_signal, interp_value]
end
linear_interp_signal = [linear_interp_signal, input_signal(signal_length)
zero_interp_signal = []
for i = 1:signal_length-1
zero_interp_signal = [zero_interp_signal, input_signal(i), 0]
end
zero_interp_signal = [zero_interp_signal, input_signal(signal_length)]
step_interp_signal = []
for i = 1:signal_length-1
step_interp_signal = [step_interp_signal, input_signal(i), input_sign
end
step_interp_signal = [step_interp_signal, input_signal(signal_length)]
time_input_signal = 0:signal_length-1
time_linear_interp = 0:length(linear_interp_signal)-1
time_zero_interp = 0:length(zero_interp_signal)-1
time_step_interp = 0:length(step_interp_signal)-1
scf(0)
subplot(2, 2, 1)
plot(time_input_signal, input_signal, ’b-’, ’LineWidth’, 2)
title(’Original Signal’)
xlabel(’Time’)
ylabel(’Amplitude’)
grid on
subplot(2, 2, 2)
plot(time_zero_interp, zero_interp_signal, ’g-’, ’LineWidth’, 2)
subplot(2, 2, 3)
plot(time_step_interp, step_interp_signal, ’m-’, ’LineWidth’, 2)
subplot(2, 2, 4)
plot(time_linear_interp, linear_interp_signal, ’r-’, ’LineWidth’, 2)
```

# Discrete exponential, sine, and random and performing decimation on signals
```
// Discrete Exponential Signal
n = 0:20
a = -1
x_exp = exp(a * n)
subplot(3,1,1)
plot2d3(n, x_exp)
title(’Discrete Exponential Signal’)
xlabel(’n’)
ylabel(’{exp}(n)’)
f = 0.1
x_sin = sin(2 * %pi * f * n)
subplot(3,1,2)
plot2d3(n, x_sin)
title(’Discrete Sine Wave’)
xlabel(’n’)
ylabel(’x_{sin}(n)’)

// Discrete Random Signal
x_rand = 2 * rand(1, length(n)) - 1
// Plot Random Signal
subplot(3,1,3)
plot2d3(n, x_rand)
title(’Discrete Random Signal’)
xlabel(’n’)
ylabel(’x_{rand}(n)’)

// Decimation factor
D = 2
x_sin_decimated = x_sin(1:D:$)
scf()
plot2d3(0:length(x_sin_decimated)-1, x_sin_decimated)
title(’Decimated Sine Wave by Factor D=2’)
xlabel(’n’)
ylabel(’x_{sin-dec}(n)’)
```


# Sine waves with 50 Hz, 75 Hz and100 Hz and Addition of both for 0.1 sec
``` Scilab
fs = 1000
t = 0:1/fs:0.1
f1 = 50
f2 = 75
f3 = 100
y1 = sin(2 * %pi * f1 * t)
y2 = sin(2 * %pi * f2 * t)
y3 = sin(2 * %pi * f3 * t)
y_sum = y1 + y2 + y3
scf(0)
subplot(2, 1, 1)
plot(t, y1, ’r’, t, y2, ’g’, t, y3, ’b’)
xlabel(’Time (s)’)
ylabel(’Amplitude’)
legend([’50 Hz’, ’75 Hz’, ’100 Hz’])
title(’Individual Sine Waves’)
subplot(2, 1, 2)
plot(t, y_sum, ’k’)
xlabel(’Time (s)’)
ylabel(’Amplitude’)
title(’Sum of the Sine Waves’)
```

# rect(n/2N) for N=5
``` Scilab
N = 5;
n = -2*N:2*N;
rect_func = zeros(n);
for i = 1:length(n)
if abs(n(i)) < N then
rect_func(i) = 1;
else
rect_func(i) = 0;
end
end
plot(n, rect_func, ’-o’);
xlabel(’n’);
ylabel(’rect(n/2N)’);
title(’Rectangular Function rect(n/2N) for N = 5’);
grid(1);
```
