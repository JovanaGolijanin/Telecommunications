clc;clear;close all;
M=16;%modulation order
bb=log2(M);%bits per symbol
N=4000;%input bits size
x=randi([0,1],1,N);%random input bits
yy=[];
for i=1:4:length (x)
	if x(i)==0 && x(i+1)==0 && x(i+2)==1 && x(i+3)==0
		y=-3+1j*3;
	elseif x(i)==0 && x(i+1)==1 && x(i+2)==1 && x(i+3)==0
		y=-1+1j*3;
	elseif x(i)==0 && x(i+1)==0 && x(i+2)==1 && x(i+3)==1
		y=-3+1j*1;
	elseif x(i)==0 && x(i+1)==1 && x(i+2)==1 && x(i+3)==1
		y=-1+1j*1;
	elseif x(i)==1 && x(i+1)==1 && x(i+2)==1 && x(i+3)==0
		y=1+1j*3;
	elseif x(i)==1 && x(i+1)==0 && x(i+2)==1 && x(i+3)==0
		y=3+1j*3;
	elseif x(i)==1 && x(i+1)==1 && x(i+2)==1 && x(i+3)==1
		y=1+1j*1;
	elseif x(i)==1 && x(i+1)==0 && x(i+2)==1 && x(i+3)==1
		y=3+1j*1;
	elseif x(i)==0 && x(i+1)==0 && x(i+2)==0 && x(i+3)==1
		y=-3-1j*1;
	elseif x(i)==0 && x(i+1)==1 && x(i+2)==0 && x(i+3)==1
		y=-1-1j*1;
	elseif x(i)==0 && x(i+1)==0 && x(i+2)==0 && x(i+3)==0
		y=-3-1j*3;
	elseif x(i)==0 && x(i+1)==1 && x(i+2)==0 && x(i+3)==0
		y=-1-1j*3;
	elseif x(i)==1 && x(i+1)==1 && x(i+2)==0 && x(i+3)==1
		y=1-1j*1;
	elseif x(i)==1 && x(i+1)==0 && x(i+2)==0 && x(i+3)==1
		y=3-1j*1;
	elseif x(i)==1 && x(i+1)==1 && x(i+2)==0 && x(i+3)==0
		y=1-1j*3;
	elseif x(i)==1 && x(i+1)==0 && x(i+2)==0 && x(i+3)==0
		y=3-1j*3;
	end
yy=[yy y];
end
scatterplot(yy)

EbN0dB=10;
EbN0=10^(EbN0dB/10);
n=(1/sqrt(2))*[randn(1,length(yy))+sqrt(-1)*randn(1,length(yy))];
sigma=sqrt(1/((log2(M))*EbN0));
r=yy+sigma*n;
scatterplot(r)