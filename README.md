# Power-System-Y-Bus-Matrix-Creation
The purpose of this code is to create a Y-bus matrix for a power system based on user input. The Y-bus matrix represents the admittance or impedance values between different buses in the power system. The code allows the user to choose between impedance or admittance calculation.


Here is the code:

clear all; clc;
n= input('Enter the number of buses '); fprintf('Enter your choice')
p= input ('1. impedance, 2. admittance'); if (p==1)
for q= 1:n
    for r=q+1:n
fprintf('Enter the impedance value between %d-%d',q,r); z(q,r)=input(':');
if (z(q,r)==0)
y(q,r)=0; else
y(q,r)=inv(z(q,r)); end
y(r,q)= y(q,r);
    end
end
elseif (p==2) for a= 1:n for b=a+1:n
fprintf('Enter the admittance value between %d-%d',a,b); y(a,b)=input(':');
y(b,a)= y(a,b); end
    end
else
fprintf('enter the correct choice'); end
ybus=zeros(n,n); for a =1:n
for b=1:n if (a==b)
for c = 1:n
ybus(a,a)= ybus(a,a)+ y(a,c); end
else
ybus(a,b)=-y(b,a); end
end
end
ybus



Explanation:
clear all; clc;: These commands clear the workspace and command window, respectively. They ensure a clean workspace before running the code.

n = input('Enter the number of buses ');: This line prompts the user to enter the number of buses and assigns the input value to the variable n.

fprintf('Enter your choice'): This line prints the message "Enter your choice" to the command window.

p = input('1. impedance, 2. admittance');: This line prompts the user to enter their choice of either impedance or admittance and assigns the input value to the variable p.

if (p == 1): This is an if statement that checks if the value of p is equal to 1. If it is, the code proceeds with the impedance calculation.

for q = 1:n: This is a for loop that iterates from 1 to the value of n. It represents the index of the first bus.

for r = q+1:n: This is another nested for loop that iterates from q+1 to the value of n. It represents the index of the second bus, ensuring that only the upper triangular part of the matrix is populated.

fprintf('Enter the impedance value between %d-%d', q, r);: This line prints the message "Enter the impedance value between x-y" to the command window, where x and y are the values of q and r, respectively.

z(q, r) = input(':');: This line prompts the user to enter the impedance value between the q-th and r-th buses and assigns the input value to the matrix element z(q, r).

if (z(q, r) == 0): This is an if statement that checks if the impedance value is equal to zero.

y(q, r) = 0;: If the impedance value is zero, it assigns zero to the corresponding element in the matrix y.

else: If the impedance value is non-zero.

y(q, r) = inv(z(q, r));: It calculates the inverse of the impedance value using the inv() function and assigns it to the corresponding element in the matrix y.

y(r, q) = y(q, r);: Since the matrix y is symmetric, the element at position (r, q) is set equal to the element at position (q, r).

elseif (p == 2): This is an elseif statement that checks if the value of p is equal to 2. If it is, the code proceeds with the admittance calculation.

for a = 1:n: This is a for loop that iterates from 1 to the value of n. It represents the index of the first bus.

for b = a+1:n: This is another nested for loop that iterates from a+1 to the value of n. It represents the index of the second bus, ensuring that only the upper triangular part of the matrix is populated.

fprintf('Enter the admittance value between %d-%d', a, b);: This line prints the message "Enter the admittance value between x-y" to the command window, where x and y are the values of a and b, respectively.

`y(a, b) = input
