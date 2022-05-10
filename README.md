# hokya
Write a program apply smoothing and sharpening filters on grayscale ad color image 
clc;
clear all;
a=imread("D:\download\babu.jpeg"); 
a=double(a);
[row col k]=size(a); 
while(1)
    rc=input('mask'); 
    remain=modulo(rc,2);
    if remain ==0
        disp('enter odd value'); 
        continue;
    else
        break;
    end
end
z=(rc+1)/2; 
n=rc*rc; 
for v=1:1:rc
    for w=1:1:rc msk(v,w)=1/n;
    end
end
a1=a;
for d=1:1:k
    for x=z:1:row-z+1 
        for y=z:1:col-z+1
            for i=1:1:rc 
                for j=1:1:rc
                    a1(x,y,d)= a1(x,y,d)+msk(i,j)*a(x-z+i,y-z+j,d);
                end
            end
        end
    end
 end
subplot(2,2,1);
imshow(uint8(a)); 
title('original image'); 
subplot(2,2,2); 
imshow(uint8(a1)); 
title('image filtered lowpass'); 
x = a1 -a;
subplot(2,2,3);
imshow(uint8(x));

Pract 1 d) Program to perform image averaging (image addition) for noise reduction
clc; clear all;
subplot(2,2,1);
i=imread('C:\Program Files\scilab-6.0.2\IPCV\images\cameraman.tif'); i=double(i);
imshow(uint8(i)); title('original image') k = floor(i*256)/64;
subplot(2,2,2); imshow(uint8(k)); title('quantization 64') k = floor(i*255)/32;
subplot(2,2,3); imshow(uint8(k)); title('quantization 32') k = floor(i*255)/32;
subplot(2,2,4); imshow(uint8(k)); title('quantization 16') k = floor(i*255)/16;

) Program to study the effects of varying the number of intensity levels in a digital image

clc; clear all; figure(1)
/// checker board
subplot(3,3,1);
i=imread('C:\Program Files\scilab-6.0.2\IPCV\images\peppers.png'); imshow(i);
title('original image'); subplot(3,3,2); j=imresize(i,0.8); imshow(j);
title('resized image 0.8');
subplot(3,3,3); j=imresize(i,0.7); imshow(j);
title('resized image 0.7');
subplot(3,3,4); j=imresize(i,0.6); imshow(j);
title('resized image 0.6');
subplot(3,3,5); j=imresize(i,0.1); imshow(j);
title('resized image 0.1');


Program to study the effects of reducing the spatial resolution of a digital image

clc; clear all;
Img=imread('C:\Program Files\scilab-6.0.2\IPCV\images\lena.png');
 subplot (2,2,1),imshow(Img),title('Og image 512*512'); 
Samp=zeros(256);
for i=1:1:512
 for j=1:1:512
if modulo(i,2)==0 m=i/2;
if modulo(j,2)==0 n=j/2;
Samp(i-m,j-n)=Img(i,j);
 else
n=0;
end
       else
m=0;
end 
end
end 
SampI+mg256=mat2gray(Samp);
subplot(2,2,2),imshow(SampImg256),title('Sampled.Img512*512') Samp=zeros(128)
for i=1:1:512 
for j=1:1:512
if modulo(i,4)==0 m=i/4*3;
if modulo(j,4)==0 n=j/4*3;
Samp(i-m,j-n)=Img(i,j);
 else
n=0;
end
 else
m=0;
end 
end
end

SampImg128=mat2gray(Samp);

 subplot(2,2,3),imshow(SampImg128),title('Sampled.Img 128*128') Samp=zeros(64)
for i=1:1:512 
for j=1:1:512
if modulo(i,8)==0 m=i/8*7;
if modulo(j,8)==0 n=j/8*7;
Samp(i-m,j-n)=Img(i,j);
 else
n=0;
end
 else
m=0;
end
 end
end

SampImg64=mat2gray(Samp);
subplot(2,2,4), imshow(SampImg128), title('Sampled Image 64 x 64');
Samp = zeros(32); for i=1:1:512
for j = 1 : 1 : 512
if modulo(i,16)==0 m= i/16*4;
if modulo(j,16)==0 n=j/16*4;
Samp(i-m,j-n) = Img(i,j);
 else
n=0;
end
 else
m=0;
end 
end
end


Program to calculate number of samples required for an image
clc; clear;
fm = input('input signal frequency');
 k = input('no. of cycles');
A = input('Enter amplitude signal');
 tm = 0:1 / (fm*fm) :k/fm;
x = A*cos(2* %pi *fm*tm); 
figure(1);
a = gca();
a.x_location = "origin"; 
a.y_location = "origin";
 plot(tm,x);
title('Original signal'); 
xlabel('Time'); 
ylabel('Amplitude');
 xgrid(1)fnyq = 2* fm;
fs = (3/4) * fnyq ;
 n = 0:1 / fs: k / fm;
x = A * cos(2 * %pi *fm * n); 
figure(2);
a = gca();
a.x_location = "origin"; 
a.y_location = "origin";
 plot(n,x);
title('under sampling signal'); 
xlabel('Time'); 
ylabel('Amplitude');
xgrid(1)
fnyq = 2* fm;
fo = (3/4) * fnyq ; 
o = 0:1 / fo : k / fm;
x = A * cos(2 * %pi *fm * o); 
figure(3);
a = gca();
a.x_location = "origin"; 
a.y_location = "origin";
 plot(o,x);
title('nyquist sampling');
 xlabel('Time'); 
ylabel('Amplitude'); 
xgrid(1)
fo = 10 * fnyq ;
o = 0:1 / fo : k / fm;
x = A * cos(2 * %pi *fm * o);
 figure(4);
a = gca();
a.x_location = "origin";
 a.y_location="origin"; plot2d3('gnn',o,x);
plot(o,x,'r');
title('over sampling signal');
 xlabel('Time');
ylabel('Amplitude'); 
xgrid(1)


Write a program to perform convolution and correlation

clc;
 x=[4,5,6;7,8,9]; 
h=[1;1;1];
y=conv2(x,h);
disp(y);
