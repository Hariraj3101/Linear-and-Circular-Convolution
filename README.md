# EXP 1 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```scilab
clc;
clear;
x = [1 2 3 4];
h = [1 -1];
lx = length(x);
lh = length(h);
ly= lx+lh-1
y = zeros(1, ly);
for n = 1:ly
    for k = 1:lx
        if (n - k + 1 >= 1) & (n - k + 1 <= lh) then
            y(n) = y(n) + x(k) * h(n - k + 1);
        end
    end
end
disp("First Sequence x(n)=",x)
disp("Second Sequence x(n)=",h)
disp("Linear Convolution y(x):",y);

clf;
subplot(3,1,1);
plot2d3(0:lx-1,x)
xlabel("n");ylabel("x(n)")
title("First sequence")

subplot(3,1,2);
plot2d3(0:lh-1,h)
xlabel("n");ylabel("h(n)")
title("Second sequence")

subplot(3,1,3);
plot2d3(0:ly-1,y)
xlabel("n");ylabel("y(n)")
title("Output sequence")

```

## PROGRAM (Circular Convolution): 
```scilab
clc;
clear;

x = [1 2 3 4];
h = [1 -1];

lx = length(x);
lh = length(h);

// Length of circular convolution
N = max(lx,lh);

// Zero padding
x = [x zeros(1,N-lx)];
h = [h zeros(1,N-lh)];

y = zeros(1,N);

// Circular convolution
for n = 1:N
    for k = 1:N
        index = pmodulo(n-k, N) + 1;
        y(n) = y(n) + x(k) * h(index);
    end
end

disp("First Sequence x(n)=",x)
disp("Second Sequence h(n)=",h)
disp("Circular Convolution y(n)=",y)

// Plotting
clf;

subplot(3,1,1);
plot2d3(0:N-1,x)
xlabel("n");ylabel("x(n)")
title("First sequence")

subplot(3,1,2);
plot2d3(0:N-1,h)
xlabel("n");ylabel("h(n)")
title("Second sequence")

subplot(3,1,3);
plot2d3(0:N-1,y)
xlabel("n");ylabel("y(n)")
title("Circular Convolution Output")

```
## OUTPUT (Linear Convolution): 
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/864d60fb-9d4e-4478-abda-919b8f6fa77c" />


## OUTPUT (Circular Convolution): 
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/395b85db-c42f-45ce-a30f-1cba20866acf" />

## RESULT: 
Thus the Linear convolution and Circular convolution for two given sequence is obtained.
