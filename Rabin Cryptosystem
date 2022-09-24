# -*- coding: utf-8 -*-
"""
Created on Thu Sep 22 14:32:08 2022

@author: Shaghik
"""

import math

class Rabin:

    symbols = ' abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ^°1!2"3§4$5%6&7/8(9)0=?\}][{+*#,;.:-_<>|/'
    
    @staticmethod
    #Coversion of string to integer
    def str2int(s):
        n = 0
        for i in range(len(s)):
            n+=Rabin.symbols.index(s[i])*int(math.pow(len(Rabin.symbols),i))
        return n
    
    @staticmethod
    #Conversion of integer to string
    def int2str(n):
        for i in range(n):
            if int(math.pow(len(Rabin.symbols),i)) >= n:
                m = i
                break
        b = n
        a = ''
        for i in range(m+1):
            x = b%len(Rabin.symbols)
            a+= Rabin.symbols[x]
            b = b-x
            b = int(b/len(Rabin.symbols))
        return a
    
    @staticmethod
    # Function check for prime numbers    
    def prime_check(n):
        if n<=1:
            return False
        for i in range(2,int(math.sqrt(n))+1):
            if n%i!=0:
                continue
            else:
                return False
                break
        return True
    
    @staticmethod
    #Computes modular inverse
    def mod_inverse(n,p):
        for i in range (1,p):
            if (i*n)%p ==1:
                return i
            else:
                continue
    
    @staticmethod
    # Computing factors of a Rabin-modulus type number
    def Rabin_key_pairs(n):
        for i in range(3,int(math.sqrt(n)),4):
            if n%i==0:
                return n,(i,int(n/i))
            else:
                continue
    
    @staticmethod
    # Message Encryption
    def encrypt(n,msg):
        M = Rabin.str2int(msg)
        if Rabin.prime_check(Rabin.Rabin_key_pairs(n)[1][0]) and Rabin.prime_check(Rabin.Rabin_key_pairs(n)[1][1]):
            enc = pow(M,2,n)
            return Rabin.int2str(enc)
    
    @staticmethod
    # Message Decryption
    def decrypt(n,c):
        p,q = Rabin.Rabin_key_pairs(n)[1][0], Rabin.Rabin_key_pairs(n)[1][1]
        C = Rabin.str2int(c)
        cp, cq = pow(C,int((p+1)/4),n), pow(C,int((q+1)/4),n)
        m1,m2 = (Rabin.mod_inverse(q,p)*q*cp + Rabin.mod_inverse(p,q)*p*cq)%n, (Rabin.mod_inverse(q,p)*q*cp - Rabin.mod_inverse(p,q)*p*cq)%n
        return Rabin.int2str(m1), Rabin.int2str(n-m1), Rabin.int2str(m2), Rabin.int2str(n-m2) 
    
if __name__=='__main__':
    x = int(input('Enter Rabin modulus : '))
    m = input('Message : ')
    obj = Rabin()
    enc = obj.encrypt(x,m)
    print(enc) 
    dec = obj.decrypt(x,enc)
    print(dec)
