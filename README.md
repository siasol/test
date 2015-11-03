# test
def multiples():
    i = 1
    sum = 0
    while i < 1000:
        if i % 3 == 0 or i % 5 == 0:
            sum = sum + i
        i += 1
    return sum
  
        
print multiples()    

-------------
def pythagorean(sum=1000):
    for a in range(1,sum):
        for b in range(a+1,sum):
            c = sum - a - b
            if a*a + b*b == c*c:
                print a,b,c
        
  
pythagorean() 
----------------
def bill():
    names = []
    prices = []
    qtys = []
    rate = 0.0
    while True:
         name = raw_input("Item Name (or CHK for checkout) :")
         if name == "CHK":
             break
         names.append(name)
         tmp1 = raw_input("Price :")
         prices.append(float(tmp1))
         tmp2 = raw_input("Quantity :")
         qtys.append(int(tmp2))
         
    
    rate = raw_input("Tax Rate (0.XX) :")
    i= 0
    print "Names" "\t" "Price" "\t" "Qty" "\t" "\t" "Totals"
    total = 0.0
    while i < len(names):
        total = float(prices[i])*int(qtys[i])
        print names[i] + "\t", "%.2f" % round(prices[i],2), "\t", qtys[i], "\t" "\t", "%.2f" % round(total,2)
        total += float(prices[i])*int(qtys[i])
        i +=1  
    
    tax_rate = total * float(rate)
    grd_total = tax_rate + total
    print "--------------------------------------------------"
    print "Sub Total" + "\t" "\t" "\t" , "%.2f" % total
    print "Tax Rate" + "\t" "\t" "\t", "%.2f" % tax_rate
    print "Total"  + "\t" "\t" "\t" "\t",   "%.2f" % grd_total



bill()
--------------
def search(string,c):
    for ch in string:
        if ch == c:
            return True
        


def encrypt(string,offset):
    l = list(map(chr, range(97, 123))) 
    i=0
    encrp = ""
    while i < len(l):
        if search(string,l[i]):
            encrp += l[i+offset]
        i +=1
         
    return encrp          
        
          
    
    

def decrypt(string, offset):    
    l = list(map(chr, range(97, 123))) 
    i=0
    encrp = ""
    while i < len(l):
        if search(string,l[i]):
            encrp += l[i-offset]
        i +=1
         
    return encrp          
 
    

              
st = "abc"    
st1 = "def"      
print encrypt(st,3)
print decrypt(st1,3)
-------------------------
import numpy
import matplotlib.pyplot as plt


def loaddata(filename):
      
      import csv

      reader = csv.reader(open(filename, 'r'))

      data = []
	
      for r in reader:
	data.append( (r[5],r[20],r[10]))
			
      return data
      

def dat2array(datalist):
      n = len(datalist[0])
      m = len(datalist)
      arr = numpy.zeros([m,n])
      i=1
      while i<m:
          j =0 
          while j<n:
             arr[i][j]=float(datalist[i][j])
             j +=1 
                   
             
          i +=1
      
      return arr
       
def split(arr,condition):
    m= len(arr)
    n= len(arr[0])
    x = 0
    y = 0
    while x<m:
        if arr[x][0]>condition:
            y +=1
        x +=1
    array = numpy.zeros([y,n])
    i=0
    j=0
    while i<m:
        l=0
        if arr[i][0]>condition:
            while l<n:
                array[j][l]=arr[i][l]
                l +=1
            j +=1
        i +=1
    return array
      

def scatter(col1,col2,vol,c):
    plt.scatter(col1,col2,s=vol,color=c)
    plt.xlabel("At Bats")
    plt.ylabel("OBP")
    plt.show()
       
            
alist = loaddata("C:/al.csv")
#print al[1]
nlist = loaddata("C:/nl.csv")
al = dat2array(alist)
nl = dat2array(nlist)
#print al[:,0]
al1=split(al,100)
nl1=split(nl,100)
#print al1
scatter(al1[:,0],al1[:,1],al1[:,2],'b')
scatter(nl1[:,0],nl1[:,1],nl1[:,2],'r')
-------------------------------------------------
mport csv
     

def load(filename):
    f = open(filename) 
    text = []
    while True:
       line = f.read()
       line = line.replace("[","")
       line = line.replace("]","")
       line = line.replace("{","")
       line = line.replace("}","")
       line = line.replace(";"," ") 
       line += line
       text = line.strip().split()
       resultFile = open("output.csv",'wb')
       wr = csv.writer(resultFile)
       wr.writerow(text)
       
          
       if len(line) == 0: 
           break
       
    f.close()
    resultFile.close() 




load("C:/leafs.dmbfmt")
--------------------------------------------------------------
def isPalindrome(line):
    l = line.replace(".","").replace("!","").replace(" ","").lower().strip()
    word = list(l)
    rev_word = word[::-1]
    if word == rev_word:
        print     line, " " "is Palindrome"
    else:
        print     line,"is not palindrome"
    


def load(filename):
    f = open(filename) 
    while True:
       line = f.readline()
       isPalindrome(line)       
       if len(line) == 0: 
           break
       
    f.close() 
          
    
print load("C:/palindrome.txt")

---------------------------------------------------------------
from scipy.special import gamma as Gamma
import numpy
from pylab import *


def loaddata(filename):
      
      import csv

      reader = csv.reader(open(filename, 'r'))

      data = []
	
      for r in reader:
	data.append( (r[0],r[1],r[2]))
			
      return data
      



def dat2array(datalist):
      n = len(datalist[0])
      m = len(datalist)
      arr = numpy.zeros([m,n])
      i=1
      while i<m:
          j =0 
          while j<n:
             arr[i][j]=float(datalist[i][j])
             j +=1 
                   
             
          i +=1
      
      return arr
      


def f1(x):
    return Gamma(x)

l = loaddata("C:/gP.csv")
arr = dat2array(l)
print arr[:,1]


x = linspace(-5, 5, 512)
y1 = f1(x)
gca().set_autoscale_on(False)

# Matlab-style syntax:
plot(x, y1)
plot(arr[:,1],'o', ms=6)

xlabel('x')
ylabel('y')
# legend(r'$\Gamma(x)$')
axis([-5, 5, -10, 10])
grid(False)

show()
---------------------------------------------
import urllib
import csv

import matplotlib.pyplot as plt
import numpy as np

   

base_url = "http://ichart.finance.yahoo.com/table.csv?s="

def make_url(ticker_symbol):
    return base_url + ticker_symbol

output_path = "C:"		#folder location? YOU WILL NEED TO CHANGE THIS!!
def make_filename(ticker_symbol, directory="S&P"):
    return output_path + "/" + directory + "/" + ticker_symbol + ".csv"

def pull_historical_data(ticker_symbol, directory="S&P"):
    try:
        urllib.urlretrieve(make_url(ticker_symbol), make_filename(ticker_symbol, directory))
    except urllib.ContentTooShortError as e:
        outfile = open(make_filename(ticker_symbol, directory), "w")
        outfile.write(e.content)
        outfile.close()




def loaddata(filename):
      
      import csv

      reader = csv.reader(open(filename, 'r'))

      data = []
	
      for r in reader:
	data.append( (r[0],r[1],r[2],r[3]))
			
      return data
      

def dat2array(datalist):
      n = len(datalist[0])
      m = len(datalist)
      arr = np.zeros([m,n])
      i=1
      while i<m:
          j =1 
          while j<n:
             arr[i-1][j]=float(datalist[i][j])
             j +=1 
                   
             
          i +=1
      
      return arr

def split(l):
    l1 = []
    i = 1
    while i < 100:
        l1.append(l[i][0])
        i +=1
    return l1
        
pull_historical_data("MSFT")
l = loaddata("C:/S&P/MSFT.csv")
arr = dat2array(l)
l1 = split(l)
x = np.arange(100)
print x
print type(l1[0])
print l1
fig = plt.figure(figsize=(14,10))
ax = fig.add_subplot(111)
ax.plot(arr[:,0], color='Blue', linestyle ='dashed')
ax.plot(arr[:,1], color='red', linestyle='dotted', linewidth='5')
ax.plot(arr[:,2], color='green', linestyle='', marker='^')
plt.xticks(x,l1, rotation= 45)
plt.show()
