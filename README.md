# Portfolio
print("Sender's Side : ")
n = int(input("Enter Size of the DataWord : "))
s = input("Enter DataWord : ")[::-1]
r = int(input("Enter Number of Redundant Bits : "))
parity = input("Enter Parity (1.Even/2.Odd) : ")
cw = [0]*(n+r+1)
p = 0
i = 0
j = 1
while i<n:
    if j==2**p:
        p+=1
    else:
        cw[j]=s[i]
        i+=1
    j+=1
i = 0
while i<r:
    c = 0
    for j in range(1,len(cw)):
        if j&(1<<i):
            if cw[j]=='1':
                c+=1
    if c%2==0:
        cw[2**i]='0'
    else:
        cw[2**i]='1'
    i+=1
print("Generated CodeWord using Hamming Code : ",*cw[1:])
print("Reciever's Side : ")
s = input("Enter Recieved codeword : ")
res=0
i = 0
while i<r:
    c = 0
    for j in range(len(s)):
        if((j+1)&(1<<i)):
            c+=1
    print(c)
    if c%2:
        res+=(1<<i)
    i+=1
print(res)
    
    
    
    
    
    

    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
