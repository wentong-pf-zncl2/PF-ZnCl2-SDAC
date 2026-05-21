# MATLAB Analysis Documentation

## Requirements

* MATLAB R2024a
* Image Processing Toolbox (required for dendrite analysis)

l=imread('F:\\New Folder (2)\\6a99dea8cf890cf424b65bbcb3705888.png');
whos;
T=rgb2gray(l);
J=imadjust(T,\[0.1,0.15],\[0.1,1]);
level=graythresh(J);
BW=imbinarize(J,level);
S=numel(BW);
s=sum(sum(BW));
ratio=s/S;
figure;
subplot(221),imshow(l);xlabel('(a)Color picture');
subplot(222),imshow(T);xlabel('(b)Grayscale image');
subplot(223),imshow(J);xlabel('(c)Adjust grayscale image');
subplot(224),imshow(BW);xlabe('(d)Binary image');

