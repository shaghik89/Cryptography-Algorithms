import math
import matplotlib.pyplot as plt

class elliptic_curves:
    def __init__(self,a,b,p):
        self.a = a
        self.b = b
        self.p = p
               
    def prime_check(n):
            if n<=1:
                return False
            for i in range(2,int(math.sqrt(n))+1):
                if n%i!=0:
                    continue
                else:
                    return False
            return True
        
    def mod_inverse(n,p):
        if elliptic_curves.prime_check(p):
            for i in range(1,p):
                if (i*n)%p==1:
                    return i
        else:
            return str(p)+' is not prime.'
    
    def curve_plot(self):
        if elliptic_curves.prime_check(self.p) and (4*pow(self.a,3)+27*pow(self.b,2))%self.p!=0:
            C = []
            if elliptic_curves.prime_check(self.p):
                for i in range(1,self.p):
                    for j in range(1,self.p):
                        if (pow(i,2)-pow(j,3)-self.a*j-self.b)%self.p==0:
                            C.append((j,i))
            if len(C)!=0:
                plt.scatter(*zip(*C),s=10)
            
            plt.title(f'Points lying on elliptic curve with  $y^2$ = $x^3$ + {self.a}x +{self.b} over $F_{{p}}$( p = {self.p})')
            return C
        
        else:   
            return []
    
    def check_point(self,P):
        if elliptic_curves.prime_check(self.p) and (4*pow(self.a,3)+27*pow(self.b,2))%self.p!=0:
            if len(P[0])==1:
                x = int(P[0][0])%self.p
                if len(P[1])==1:
                    y = int(P[1][0])%self.p
                    if (x,y) in elliptic_curves.curve_plot(self):
                        return True
                    else:
                        return False
                else:
                    nu = int(P[1][0])%self.p
                    de = int(P[1][1])%self.p
                    if elliptic_curves.gcd(de,self.p)==1:
                        y = (nu*elliptic_curves.mod_inverse(de,self.p))%self.p
                        if (x,y) in elliptic_curves.curve_plot(self):
                            return True
                        else:
                            return False
                    else:
                        return False
            else:
                nu = int(P[0][0])%self.p
                de = int(P[0][1])%self.p
                if elliptic_curves.gcd(de,self.p)==1:
                    x = (nu*elliptic_curves.mod_inverse(de,self.p))%self.p
                    if len(P[1])==1:
                        y = int(P[1][0])%self.p
                        if (x,y) in elliptic_curves.curve_plot(self):
                            return True
                        else:
                            return False
                    else:
                        nu = int(P[1][0])%self.p
                        de = int(P[1][1])%self.p
                        if elliptic_curves.gcd(de,self.p)==1:
                            y = (nu*elliptic_curves.mod_inverse(de,self.p))%self.p
                            if (x,y) in elliptic_curves.curve_plot(self):
                                return True
                            else:
                                return False
                        else:
                            False
                else:
                    return False
        else:
            return False
               
if __name__=='__main__':
    a = int(input('Enter a - '))
    b = int(input('Enter b - '))
    p = int(input('Enter prime - '))
    obj = elliptic_curves(a,b,p)
    print('Points on elliptic curve - ',obj.curve_plot()+['§'])
    P = []
    for _ in range(2):    
        x = tuple(input().split('/'))
        P.append(x)
    print(obj.check_point(P))
    
