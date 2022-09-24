# -*- coding: utf-8 -*-
"""
Created on Sun Sep 18 13:28:04 2022

@author: Shaghik
"""
import math

class RSA:

    symbols = ' abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ^°1!2"3§4$5%6&7/8(9)0=?\}][{+*#,;.:-_<>|/'
    
    @staticmethod
    #Coversion of string to integer
    def str2int(s):
        n = 0
        for i in range(len(s)):
            n+=RSA.symbols.index(s[i])*int(math.pow(len(RSA.symbols),i))
        return n
    
    @staticmethod
    #Conversion of integer to string
    def int2str(n):
        for i in range(n):
            if int(math.pow(len(RSA.symbols),i)) > n:
                m = i
                break
        b = n
        a = ''
        for i in range(m+1):
            x = b%len(RSA.symbols)
            a+= RSA.symbols[x]
            b = b-x
            b = int(b/len(RSA.symbols))
        return a
    
    @staticmethod
    #Computing greatest common divisor
    def gcd(a,b):
            if a == 0 or b==0:
                if a + b == 0:
                    return 'GCD does not exist'
                else:
                    return a + b
            else:
                return RSA.gcd(b%a,a)
    
    @staticmethod
    #Euler Totient function    
    def euler_phi(n):  
        count = 0
        for i in range(1,n+1):
            if RSA.gcd(i,n)==1:
                count = count + 1
        return count
     
    @staticmethod
    # Function check for prime numbers    
    def prime_check(n):
        if n<=1:
            return False
        for i in range(2,int(math.sqrt(n))+1):
            if RSA.gcd(n,i)==1:
                continue
            else:
                return False
                break
        return True
    
    @staticmethod
    # Modular inverse of a number
    def mod_inverse (n,p):
        for i in range (1,p):
            if (i*n)%p ==1:
                return i
            else:
                continue
    
    @staticmethod
    # Checks whether an integer is RSA modulus           
    def RSA_modulus(n):
        for i in range(2,int(math.sqrt(n))):
            if RSA.prime_check(i) and RSA.prime_check(int(n/i)):
                return True
            else:
                continue
        return False
    
    @staticmethod
    #Generates a public-private key pair
    def RSA_key_pairs(n):
        if RSA.RSA_modulus(n):
            for i in range(2,RSA.euler_phi(n)):
                if RSA.gcd(i,RSA.euler_phi(n))==1:
                    e = i
                    break 
            return (n,e) , (n,RSA.mod_inverse(e,RSA.euler_phi(n)))
    
    @staticmethod
    # Message Encryption
    def encrypt(n,msg):
        M = RSA.str2int(msg)
        enc = pow(M,RSA.RSA_key_pairs(n)[0][1],n)
        return RSA.int2str(enc)
    
    @staticmethod
    # Message Decryption
    def decrypt(n,c):
        C = RSA.str2int(c)
        dec = pow(C,RSA.mod_inverse(RSA.RSA_key_pairs(n)[0][1],RSA.euler_phi(n)),n)
        return RSA.int2str(dec)
    
if __name__=='__main__':
    x = int(input('Enter RSA modulus : '))
    obj = RSA()
    enc = obj.encrypt(x,'Hi')
    print(enc)
    dec = obj.decrypt(x,enc)
    print(dec)
