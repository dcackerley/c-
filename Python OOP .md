#November - 28
#The following is known as Object Oriented Programming (OOP)
#Classes/Objects
#Making an object out of a class
#class - blueprint of an object (think of a wow instance, and how every instance has premodeled renderings)
#instance of a class = "object"
#each new window of a chrome browser is a new instance / new object - tabbing out would "lose" the instance in some cases
#instances can have different data, like different ads, but the functional(format?) would be the same for each instance
#the browser page loads an instance of the browser class
#instances are located in ram
#objects are held in ram
#an instance is an object
#classes which can be instantiated, are held on the hard drive.
#classes can contain functions/methods/strings
#dictionaries are objects, something that can be worked on
#class theClassName: <-- creates a custom class
#def/class are keywords


#=====================================
##class  MyClass:                         #This is just a blue print, we have not instantiated it yet. Calling the class creates an instance, this is is instantiating.
##    prname = "Dylan Ackerley"
##                                        #custom class names need to be capitalized.
##    def greet(self,gr):                 #by default, self is in the creation of a function. 
##                                        #in function calls, we don't use self as an argument
##                                        #When defining a function, we have to refer to a positional value. (self) will references itself in the function
##                                        #def SquareIt(self,num): <-- does not work for some reason
##                                        #return num + "enter a number to be squared: "
##                  
##        return gr + "World!"            #a class is created
##
##                                        #These elements only exist in this class. We can't use anything in this class until we invoke the class, instantiating an instance.
##
###=====================================
##
##c1 = MyClass()                          #instantiates the "MyClass()" class. Pretty much creates the MyClass() object, the first instance of MyClass() is here.
##
##print (c1.prname)                       #c1 is an instance, prname is unique to the class. Only way to access prname is to instantiate the class, then work on prname
##
##g = input("Enter greeting")
##
##greeting = c1.greet(g)
##
##print(greeting)
##
##c2 = MyClass()                          #2nd instance of the MyClass instance. This is instantiating
##
##print(c2.prname)

#====================================

##import random
##
##class Coin:                             #These created functions are called methods
##    def __init__(self):                 #__init__ is the initializing function. The following will be an the initial attribute of self.sideup         
##        self.sideup = "Heads"
##    def toss(self):                     #We have to use self in classes, but not in the call function.       
##        if random.randint(0,1)==0:      #randint
##            self.sideup = "Heads"
##        else:
##            self.sideup = "Tails"
##
##    def get_sideup(self):
##        return self.sideup
##                                        #These are just the functions we're going to use later

##coin1 = Coin()                          #1st instance of Coin
##print(coin1.sideup)                     #Calls the initial value of coin1, which in the Coin() function is self.sideup = "Heads"
##coin1.toss()
##print(coin1.sideup)                     #uses "toss" function to change the initializez value (which is self.sideup = "Heads")



#=====================================
#December 5th

import coin #We're importing the Coin class from the "coin.py" module (file)
import math

def showpr(money):
    return money.get_prname()


coin1 = coin.Coin()                       #initializes 3 instances of coin/instantiates 3 coin instances                  
coin2 = coin.Coin()                       #these are 3 coin objects
coin3 = coin.Coin()

coin1.toss()
print(coin1.get_sideup())

coin2.toss()
print (coin2.get_sideup())

coin3.toss()
print(coin3.get_sideup())

print(coin1.get_prname())

programmer = input("Enter a programmer name: ")

coin1.set_prname(programmer)              #Sets _prname to whatever the programmer input
print(coin1.get_prname())


print("The name entered is: ", showpr(coin1))



#getter method's are also known as accessor method's - have return method's
#setter method's are also known as mutator  method's - have assignment operator's such as the = operato

#Function call - can use class objects as arguments in defining a function
#can pass a coin instance as an argument
#"Coin object has no .getprname"
#class.objectAttribute


#=============================================================================================


#list1 will be 3 coin objects

list1 = [coin1, coin2, coin3] #An array structure with a list of objects. This is a list of 3 instantiations of the coin class.
#print("Coin 1 in list 1",showpr(list1[0])) #<coin.Coin object at 0x0000000002EEA2E8> <---hexadecimal number, shows objects location in RAM memory. Will be different
token1 = list1[1]
print("Coin1", showpr(token1))
print("Coin1", showpr(list1[1]))

#Can cast data types such as objects into other types of data
