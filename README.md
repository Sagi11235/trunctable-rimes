# trunctable-primes
import math
def is_prime(n):
    if n==1:
        return 'False'
    for i in range(1,math.floor(math.sqrt(n))):
        if n%(i+1)==0:
            return 'False'
    return 'True'

def truncatable(n):
    k=0
    num=n
    for i in range(len(str(n))):
       k=num%10
       if k==0:
            return 'False'
       num=(num-k)/10
    num=0
    r=0
    l=0
    if is_prime(n)=='False':
        return 'False'
    num=n
    while num>0:
        num=math.floor(num/10)
        if is_prime(num)=='False':
            r=0
            break
    if num==0:
        r=1
    num=n
    while num>0:
        num=num%(10**(len(str(num))-1))
        if is_prime(num)=='False':
            l=0
            break
    if num==0:
        l=1
    if l==1 and r==1:
        return 'both'
    elif r==1:
        return 'Right'
    elif l==1:
        return 'Left'
    return 'False'
       
print(truncatable(6043))
