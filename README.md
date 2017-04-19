# dubaimetro
This python project enables a user or a passenger to purchase or recharge their Nol cards in an easier manner, in other terms the process becomes more “User-Friendly”. Each time you travel, tap your card at the card reader on the fare gates and it will automatically deduct the correct fare. It’s Easy!
import random
import os
import pickle
station=['Etisalat','Al Qusais','Airport Free Zone','Al Nahda','Stadium','Al Qiyadah','Abu
Hail','Abu Bakr Seddiq','Salahuddin','Union Square','Baniyas Square','Palm Deira','Al Ras','Al
Ghubaiba','Al Fahidi','Burjuman','Oud Metha','Healthcare City','Jaddaf','Creek']
class passenger:
 def __init__(self):
 self.name=''
 self.email=''
 self.c_no=''
 self.c_bal=0
 self.c_type=''
 self.mobile=''

 def store_data(self):
 self.name=raw_input('Enter Your Name- ')
 self.mobile=raw_input('Enter Your Mobile- ')
 self.c_no=self.name+self.mobile

 def display(self):
 print
 print '-------------------------Details-------------------------'
 print 'Name :',self.name
 print 'Mobile :',self.mobile
 print 'Email :',self.email
 print 'Card Number :',self.c_no
 print 'Card Balance :',self.c_bal
def disp_pass(email):
 f1=open("passenger.dat","rb")
 s=passenger()
 try:
 while True:
 s= pickle.load(f1)
 if s.email==email:
 s.display()
 except EOFError:
 f1.close()

def Cards():
 print
 print '-----------------------------------Nol Cards-----------------------------------'
 print '1)Gold Card'
 print '2)Blue Card'
 print '3)Silver Card'
 ch=input('Enter Your Choice- ')

 if ch==1:
 print "You Have Decided To Purchase A Gold Nol Card"
 a=raw_input("Do You Have The Required Documents? (Y/N)- ")
 if (a.upper()=='Y'):
 print"Please deposit 75 Dhs In The Machine..."
 print
 print"Processing...."
 print""
 print 'Your Card Has Been Created'
 print
 print 'Your Initial Amount Is Dhs 20'
 return (['Gold Card',20])

 else:
 print"Sorry,Try Again Later!"
 return ([-1])

 elif ch==2:
 print"You have decided to buy a blue card"
 b=input("What is Your Age?- ")
 if (b<=20 or b>=70):
 print '----------------------------Occupation----------------------------'
 print '1.Student\n2.Retired Employee\n3.Resident\n4.Physically Impaired\n5.None Of
The Above'
 c=input("What do you do in Dubai?(Choice Number)- ")
 if(c==1 or c==2 or c==3 or c==4):
 print"Congratulations!You Are Eligible For The Blue Card!"
 print"Please deposit a sum of 80 Dhs"
 print
 print"Processing...."
 print
 print 'Your Card Has Been Created'
 print
 print 'Your Initial Amount Is Dhs 20'
 return (['Blue Card',20])
 elif c==5:
 print "You are not eligible for the card,please purchase a gold or silver card"
 return([-1])
 else:
 print 'Wrong Choice'
 return ([-1])
 else:
 print "You are not eligible for the card,please purchase a gold or silver card"
 return ([-1])

 elif ch==3:
 print"You have decided to purchase a silver card!"
 print"Please deposit a sum of 20 Dhs at the billing machine"
 print
 print"Processing...."
 print""
 print 'Your Card Has Been Created'
 print
 f=raw_input("Have you recieved your card?(y/n)- ")
 if(f.upper()=='Y'):
 print 'Your Initial Amount Is Dhs 20'
 return (['Silver Card',20])

 else:
 print "Please contact the supervisor and inform him of this defect..."
 return ([-1])
 else:
 return ([-1])

def UpdateCard(card,bal):
 if (card=='Gold Card'):
 print
 print"You have a gold card..."
 print
 print 'Your Current Balance Is',bal
 print"You wish to add money..."
 k=input("Enter the amount you wish to add (>0)- ")
 print"You wish to add ",k,"Dhs!"
 bal=bal+k
 print"Your new balance is ",bal
 return (bal)

 elif (card=='Silver Card'):
 print
 print"You have a Silver card..."
 print
 print 'Your Current Balance Is',bal
 print"You wish to add money..."
 k=input("Enter the amount you wish to add (>0)- ")
 print"You wish to add ",k,"Dhs!"
 bal=bal+k
 print"Your new balance is ",bal
 return(bal)

 elif (card=='Blue Card'):
 print
 print"You have a Blue card..."
 print
 print 'Your Current Balance Is',bal
 print"You wish to add money..."
 k=input("Enter the amount you wish to add(>0)- ")
 print"You wish to add ",k,"Dhs!"
 bal=bal+k
 print"Your new balance is ",bal
 return (bal)

def chk_bal(email):
 f1=open("passenger.dat","rb")
 s=passenger()
 try:
 while True:
 s= pickle.load(f1)
 if s.email==email:
 print
 print 'You Have A',s.c_type
 print 'Your Balance Is',s.c_bal
 print
 except EOFError:
 f1.close()

def farecalc():
 stations=[]
 for j in station:
 stations=stations+[j.lower()]
 print '----------------------------Stations----------------------------'
 j=1
 for i in station:
 print str(j)+')'+i
 j=j+1
 print
 z1=['etisalat','al qusais','airport free zone','al nahda','stadium']
 z2=['al qiyadah','abu hail','abu bakr seddiq','salahuddin','union square']
 z3=['baniyas square','palm deira','al ras','al ghubaiba','al fahidi','burjuman']
 z4=['oud metha','healthcare city','jaddaf','creek']
 s=input('Enter Starting Station Number(<20)- ')
 start=stations[s-1]
 e=input('Enter Ending StationNumber(<20)- ')
 end=stations[e-1]
 print 'Your Starting Station Is',station[s-1]
 print 'Your Ending Station Is',station[e-1]
 print
 if (start in stations) and (end in stations):
 if (start==end) or (end==start):
 return(0.0)
 elif ((start in z1) and (end in z1)) or ((start in z2) and (end in z2)) or ((start in z3) and (end in
z3)) or ((start in z4) and (end in z4)) or ((start in z3) and (end in z4)) or ((start in z4) and (end in
z3)):
 return (4.0)
 elif ((start in z1) and (end in z2)) or ((start in z2) and (end in z1)) or ((start in z2) and (end in
z3)) or ((start in z3) and (end in z2)):
 return (5.0)
 elif ((start in z1) and (end in z3)) or ((start in z3) and (end in z1)) or ((start in z2) and (end in
z4)) or ((start in z4) and (end in z2)):
 return (6.0)
 elif ((start in z1) and (end in z4)) or ((start in z4) and (end in z1)):
 return (7.0)
 else:
 return (-1.0)
 else:
 print 'Starting/Ending Station Is Invalid'
 return (-1.0)
def update(email):
 f1=open("passenger.dat","rb")
 f2=open("newfile.dat","wb")
 s=passenger()
 try:
 while True:
 s= pickle.load(f1)
 if s.email==email:
 update=UpdateCard(s.c_type,s.c_bal)
 s.c_bal=update
 pickle.dump(s,f2)
 else:
 pickle.dump(s,f2)

 except EOFError:
 f1.close()
 f2.close()
 os.remove("passenger.dat")
 os.rename("newfile.dat","passenger.dat")
def calc(email):
 fare=farecalc()
 f1=open("passenger.dat","rb")
 f2=open("newfile.dat","wb")
 s=passenger()
 if fare!=-1:
 try:
 while True:
 s= pickle.load(f1)
 if s.email==email:
 if s.c_type=='Gold Card':
 fare=fare+(0.5*fare)
 print 'Your Fare Is',fare
 if s.c_bal>=fare:
 print
 print 'You Are Using Gold Card'
 print
 print 'You Have The Required Amount'
 print
 print 'Processing.......'
 print
 s.c_bal=s.c_bal-fare
 print 'Your New Balance Is',(s.c_bal)
 pickle.dump(s,f2)
 else:
 print 'You Do Not Have The Required Amount'
 pickle.dump(s,f2)

 elif s.c_type=='Silver Card':
 print 'Your Fare Is',fare
 if s.c_bal>=fare:
 print
 print 'You Are Using Siver Card'
 print
 print 'You Have The Required Amount'
 print
 print 'Processing.......'
 print
 s.c_bal=s.c_bal-fare
 print 'Your New Balance Is',(s.c_bal)
 pickle.dump(s,f2)
 else:
 print 'You Do Not Have The Required Amount'
 pickle.dump(s,f2)
 elif s.c_type=='Blue Card':
 print 'Your Fare Is',fare
 if s.c_bal>=fare:
 fare=fare-(0.75*fare)
 print
 print 'You Are Using Blue Card'
 print
 print 'You Have The Required Amount'
 print
 print 'Processing.......'
 print
 s.c_bal=s.c_bal-fare
 print 'Your New Balance Is',(s.c_bal)
 pickle.dump(s,f2)
 else:
 print 'You Do Not Have The Required Amount'
 pickle.dump(s,f2)
 else:
 pickle.dump(s,f2)
 else:
 pickle.dump(s,f2)

 except EOFError:
 f1.close()
 f2.close()
 os.remove("passenger.dat")
 os.rename("newfile.dat","passenger.dat")

def chk_mail(email):
 f=open("passenger.dat","rb")
 stat=0
 x=0
 try:
 while True:
 p= pickle.load(f)
 if p.email==email:
 x=1
 except EOFError:
 f.close()
 if x==1:
 return(-1)
 else:
 return(1)

def main():

 while True:
 print
 print "-------------------------------! Welcome To Dubai Metro !-------------------------------"
 print '1.Purchase Nol Card'
 print '2.Access MetroHub'
 print '3.Display/View Stations'
 print '4.Exit'
 print
 choice=input("Enter your choice: ")

 if choice==1:
 email=raw_input('Enter Your Email Id- ')
 
 if chk_mail(email)==1:
 print
 print 'Your Email Id Is Valid'
 f=open("passenger.dat","ab")
 p=passenger()
 c=Cards()
 if c[0]!=-1:
 p.store_data()
 p.email=email
 p.c_type=c[0]
 p.c_bal=c[1]
 pickle.dump(p,f)
 f.close()
 else:
 print
 print 'Your Email Id Is Invalid'
 elif (choice==2):
 email=raw_input('Enter Your Email Id- ')
 f=open("passenger.dat","rb")
 stat=0
 try:
 while True:
 p= pickle.load(f)
 if p.email==email:
 print
 print 'You Have Successfully Tagged In '
 print
 stat=1
 except EOFError:
 f.close()

 if stat==1:
 ch=0
 while ch!=-1:
 print '-------------------Traveller Options-------------------'
 print '1.Check Balance'
 print '2.Update Amount'
 print '3.Tag In'
 print '4.Passenger Details'
 print '5.Exit To Menu'
 print
 ch=input('Enter Your Choice- ')
 if ch==1:
 chk_bal(email)
 elif ch==2:
 update(email)
 elif ch==3:
 calc(email)
 elif ch==4:
 disp_pass(email)
 elif ch==5:
 ch=-1
 else:
 print 'Wrong Choice'
 else:
 print
 print 'Email Id Not Found'
 print

 elif (choice==3):
 print '----------------------------Stations----------------------------'
 j=1
 for i in station:
 print str(j)+')'+i
 j=j+1

 elif (choice==4):
 exit()
main()
