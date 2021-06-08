# Twister
Class Fraction Python

What has to be done to print for example: 
r = fraction(13/15)
z = 1 + r
print(z) 
or 
print(-r)

My code now: 

def hcf(a,b):
  if a == 0:
    return b
  else:
    return hcf(b % a, a)

class fraction:

  def __init__(self, numerator, denominator):
    gcd = hcf(numerator,denominator)
    self.top = numerator // gcd
    self.bottom = denominator // gcd

  def __str__(self):
    if self.bottom == 1:
      return str(self.top)
    elif self.top > self.bottom:
      return str(self.top//self.bottom) + " " 
      + str(fraction(self.top % self.bottom, self.bottom))
    else: 
      return str(self.top) + "/" + str(self.bottom)

  def double(self):
    return fraction(2*self.top,self.bottom)

  def multiply_by(self, n):
    return fraction(n*self.top,self.bottom)

  def __add__(self,other):
    newtop = self.top * other.bottom + other.top * self.bottom
    newbottom = self.bottom * other.bottom
    return fraction(newtop,newbottom)

  def __sub__(self,other):
    newtop = self.top * other.bottom - other.top * self.bottom
    newbottom = self.bottom * other.bottom
    return fraction(newtop,newbottom)

  def __mul__(self,other):
    newtop = self.top * other.top
    newbottom = self.bottom * other.bottom
    return fraction(newtop,newbottom)

  def __truediv__(self,other):
    newtop = self.top * other.bottom
    newbottom = self.bottom * other.top 
    return fraction(newtop,newbottom)

  def __lt__(self,other):
    return(self.top*other.bottom < other.top*self.bottom)

  def __gt__(self,other):
    return(self.top*other.bottom > other.top*self.bottom)

  def __eq__(self,other):
    return(self.top*other.bottom == other.top*self.bottom)

  def __le__(self,other):
    return(self<other or self==other)

  def __ge__(self,other):
    return(self>other or self==other)
