# EXP 2 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
````
 clc;  
clear; 
x = [1 1 2 1]; 
 
h = [1 2 3 4]; 
 
m = length(x);
n = length(h);
a=0:1:m-1; 
b=0:1:n-1; 
 
subplot(3,1,1);  
plot2d3(a,x); 
xlabel('Time');
ylabel('Amplitude'); 
title('Graphical Representation of Input Signal X');

subplot(3,1,2); 
plot2d3(b,h);  
xlabel('Time'); 
ylabel('Amplitude');  
title('Graphical Representation of Impulse Signal h');
for i = 1: n+m-1 
conv_sum = 0; 
 
for j = 1:i 
 
if (((i-j+1) <= n)&(j <=m)) 
 
conv_sum = conv_sum + x(j)*h(i-j+1); 
 
end; 
 
y(i) = conv_sum; 
 
end;
 
end; 
disp(y,'Convolution Sum using Direct Formula Method = ')
subplot(3,1,3); 
plot2d3(y)  
title('Graphical Representation of output Signal y'); 
````

## PROGRAM (Circular Convolution): 

````
clc;
clear;

// Input sequences
x = [1 2 2 1];
h = [1 2 3 1];

// Length for circular convolution (take max length)
N = max(length(x), length(h));

// Zero padding if needed
x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

disp("Zero-padded input:");
disp(x);
disp("Zero-padded impulse:");
disp(h);

// ---- Circular convolution using modulo ----
y = zeros(1, N);

for n = 1:N
    for k = 1:N
        j = pmodulo(n-k, N) + 1;   // pmodulo avoids negative indices
        y(n) = y(n) + x(k) * h(j);
    end
end

disp("Circular convolution result:");
disp(y);

// ---- Plot results ----
subplot(3,1,1);
plot2d3(0:N-1, x);
title("Input sequence x[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,2);
plot2d3(0:N-1, h);
title("Impulse response h[n]");
xlabel("n"); ylabel("Amplitude");

subplot(3,1,3);
plot2d3(0:N-1, y);
title("Circular Convolution y[n]");
xlabel("n"); ylabel("Amplitude");
````
## OUTPUT (Linear Convolution): 
<img width="1920" height="1080" alt="486721453-30333b0f-b62c-4dda-a7a1-92f315615d88" src="https://github.com/user-attachments/assets/375b25b7-b4a2-4803-b45f-c08263c15a57" />

<img width="1920" height="1080" alt="486721549-db1bbf01-bd35-4bd8-b3c2-9882ea321b62" src="https://github.com/user-attachments/assets/590dfed8-266d-422c-bb82-060ca45cca1a" />


## OUTPUT (Circular Convolution): 
<img width="1920" height="1080" alt="486722175-0c677f15-74d5-4cdd-bcb0-60c21a16ada7" src="https://github.com/user-attachments/assets/56df8002-fb89-41b3-bd3b-b469f0be2bbd" />
<img width="1920" height="1080" alt="486722417-9c2e4b35-9705-4940-bd30-7304cad83aac" src="https://github.com/user-attachments/assets/100a4cd0-c64a-4518-b257-2952f51be2ed" />


## RESULT: 
Linear and Circular Convolution are successfully executed in scilab
