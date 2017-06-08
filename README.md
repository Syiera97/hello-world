import sys
import datetime
import time

#Important data
username = ["admin","admin1","admin2"]
counterA = 0
counterC = 0
counterB = 0 + counterC
menuinput = ["1","2","3"]
boolean = ["n", "y"]
costA = 300
costB = 200
invoice = 0
expirationdate = datetime.date.today() + datetime.timedelta(days=140)
    

#Define function
def counterCC():
    global counterCC
    if counterC == 0:
        return("Unoccupied")
    elif counterC == 1:
        return("Occupied")
def xcommand():
    global xcommand
    print("Invalid command.")
def mainmenu():
    global mainmenu
    mainmenu = input("What would you like to do? \n 1 - Check apartment status \n 2 - Register a new student \n 3 - Exit \n Type here: ")
def studentregistered():
    print("Student has been registered!")
    
#Start of the program
print("Welcome to the apartment registration")
while True:
    #If the user types an incorrect login, an error message will be displayed
    #If the user types in a correct login, they will proceed to password
        user_login = input("Type 'B' anytime to go back. Please enter your username: ")
        if user_login not in username:
            print ("Your username is invalid")
            continue
        while True:
            user_pass = input("Please enter your password: ")
    #If the user types in a correct password, they will proceed to menu
    #If the user types in an incorrect password, they will be returned to 'please enter password'
    #If the user types in B, it will go back to 'username'
            if user_pass == "B":
                break
            elif user_pass != "admin123":
                print("Invalid password")
                continue
            elif user_pass == "admin123":
                print("\n"+"Welcome back," + user_login + "!" + "\n")
    #Main menu
            while True:
                mainmenu = input("What would you like to do? \n 1 - Check apartment status \n 2 - Register a new student \n 3 - Exit \n Type here: ")
                #main menu exit
                if mainmenu == "3":
                    print ("Goodbye!")
                    sys.exit()
                elif mainmenu not in menuinput:
                    xcommand()
                    continue
                #This checks the apartment status
                elif mainmenu == "1":
                     print("\n"+"Apartment A: " + str(counterA) + " \nApartment B: " + str(counterB) + " \nApartment B Master bedroom: " + str(counterCC()) + "\n")
                     continue
                #Start of menu for apartment registration
                while True:
                    if mainmenu == "2":
                        register = input("\n"+"'B' to return. Which apartment are you registering for? \n 1 - Type A \n 2 - Type B \n 3 - Check the type of apartment \n Type here: ")
                        if register == "B":
                            break
                        #Error message
                        elif register not in menuinput:
                            xcommand()
                            continue
                        #Prints out the types of rooms
                        elif register == "3":
                            print("Type A - 2 bedrooms and equipped with kitchen and laundry facilities. The monthly rental for the rooms in this apartment type is RM300 \nType B - 3 bedrooms includes one master bedroom with attached bathroom but does not have kitchen and laundry facilities. The monthly rental for the rooms in this apartment type is RM200 and students staying in the master bedroom will be paying an additional 40%")
                            continue
                        
                            
                    #Test for apartment full or not
                            if counterA == 2 and counterB == 3:
                                print("Sorry! Both apartments are currently full!")
                                break
                            if counterA == 2:
                                print ("Sorry! Type A is currently full! Perhaps you would like Type B?")
                                continue
                            if counterB == 3:
                                print ("Sorry! Type B is currently full! Perhaps you would like Type A?")
                            
                                newstudentB = input("Is the student new? y/n: ")
                                if newstudentB not in boolean:
                                    xcommand()
                                    continue
                                newstudentMB = input("Would you like the master bedroom? y/n: ")
                                if counterC == 1:
                                    print("Sorry! Master bedroom is currently occupied!")
                                if newstudentMB not in boolean:
                                    xcommand()
                                    continue
                        ##DO NOT TOUCH ANYTHING FRM HERE ONWARDS
                        #New student A
                        if register == "1":
                                newstudentA = input("Is the student new? y/n: ")
                                if newstudentA not in boolean:
                                    xcommand()
                                    continue
                                if newstudentA == "y":
                                    invoice = invoice + 300 + 100
                                    print("Your current total is: RM" + str(invoice))
                                    confirmNA = input("Are you sure you would like to register this? y/n: ")
                                    if confirmNA not in boolean:
                                        xcommand()
                                        continue
                                    if confirmNA == "n":
                                        invoice = invoice-400
                                        break
                                        break
                                        break
                                    if confirmNA == "y":
                                        print("The current amount of students in Type A are: " + str(counterA) + " Your expiry date is on: " + str(expirationdate))
                                        counterA = counterA + 1
                                    paymentNA = input("Are you done with your transaction? y/n: ")
                                    if paymentNA not in boolean:
                                        xcommand()
                                        continue
                                    if paymentNA == "y":
                                        print("Your total is: RM" + str(invoice))
                                        print("Goodbye!")
                                        sys.exit()
                                #Old student A
                                if newstudentA == "n":
                                    invoice = invoice + 300
                                    counterA = counterA + 1
                                    print("Your current total is: RM" + str(invoice))
                                    confirmOA =input("Are you sure you would like to register this? y/n: ")
                                    if confirmOA == "n":
                                        invoice = invoice-300
                                        break
                                        break
                                        
                                    elif confirmOA == "y":
                                        print("The current amount of students in Type A are: " + str(counterA) + " Your expiry date is on: " + str(expirationdate))
                                        counterA = counterA + 1
                                        paymentOA = input("Are you done with your transaction? y/n: ")
                                        if paymentOA == "y":
                                            print("Your total is: RM" + str(invoice))
                                            print("Goodbye!")
                                            sys.exit()
                                        if paymentOA == "n":
                                            break
                                            break
                                    
                        if register == "2":
                            #Start of room B
                            newstudentB = input("Is the student new? y/n: ")
                            if newstudentB not in boolean:
                                xcommand()
                                continue
                            newstudentMB = input("Would you like the master bedroom? y/n: ")
                            if counterC == 1:
                                print("Sorry! The Master bedroom is currently occupied!")
                                continue
                            elif newstudentMB not in boolean:
                                xcommand()
                                continue
                            #NEW STUDENT AND MASTER BEDROOM
                            if newstudentB == "y" and newstudentMB == "y":
                                invoice = invoice + costB*0.4 + 100 + 200
                                print("Your current total is: RM" + str(invoice))
                                confirmNMB = input("Are you sure you would like to register this? y/n: ")
                                if confirmNMB not in boolean:
                                    xcommand()
                                elif confirmNMB == "n":
                                    invoice = invoice - (costB*0.4 + 100 + 200)
                                    break
                                elif confirmNMB == "y":
                                    print("The current amount of students in Type B are: " + str(counterB) + " Your expiry date is on: " + str(expirationdate))
                                    counterB = counterB + 1
                                    paymentNMB = input("Are you done with your transaction? y/n: ")
                                    if paymentNMB not in boolean:
                                        xcommand()
                                        continue
                                    elif paymentNMB == "y":
                                        print("Your total is: RM" + str(invoice))
                                        print("Goodbye!")
                                        sys.exit()
                                    elif paymentNMB == "n":
                                        break
                                #OLD STUDENT NOT MASTERBED
                            elif newstudentB == "n" and newstudentMB == "n":
                                invoice = invoice + 200
                                print("Your current total is: RM" + str(invoice))
                                confirmOB = input("Are you sure you would like to register this? y/n: ")
                                if confirmOB not in boolean:
                                    xcommand()
                                elif confirmOB == "n":
                                    invoice = invoice - 200
                                    break
                                elif confirmOB == "y":
                                    print("The current amount of students in Type B are: " + str(counterB) + " Your expiry date is on: " + str(expirationdate))
                                    counterB = counterB + 1
                                    paymentOB = input("Are you done with your transaction? y/n: ")
                                    if paymentOB not in boolean:
                                        xcommand()
                                        continue
                                    elif paymentOB == "y":
                                        print("Your total is: RM" + str(invoice))
                                        print("Goodbye!")
                                        sys.exit()
                                    elif paymentOB == "n":
                                        break
                                #NEW STUDENT, NOT MASTERBEDROOM
                            elif newstudentB == "y" and newstudentMB == "n":
                                invoice = invoice +  200 + 100
                                print("Your current total is: RM" + str(invoice))
                                confirmNB = input("Are you sure you would like to register this? y/n: ")
                                if confirmNB not in boolean:
                                    xcommand()
                                elif confirmNB == "n":
                                    invoice = invoice - 200 - 100
                                    break
                                elif confirmNB == "y":
                                    print("The current amount of students in Type B are: " + str(counterB) + " Your expiry date is on: " + str(expirationdate))
                                    counterB = counterB + 1
                                    paymentNB = input("Are you done with your transaction? y/n: ")
                                    if paymentNB not in boolean:
                                        xcommand()
                                        continue
                                    elif paymentNB == "y":
                                        print("Your total is: RM" + str(invoice))
                                        print("Goodbye!")
                                        sys.exit()
                                    elif paymentNB == "n":
                                        break

                                    #OLD STUDENT, MASTERBEDROOM
                            elif newstudentB == "n" and newstudentMB == "y":
                                invoice = invoice + costB*0.4 + 200
                                print("Your current total is: RM" + str(invoice))
                                confirmOMB = input("Are you sure you would like to register this? y/n: ")
                                if confirmOMB not in boolean:
                                    xcommand()
                                elif confirmOMB == "n":
                                    invoice = invoice - costB*0.4 - 200
                                    break
                                elif confirmOMB == "y":
                                    print("The current amount of students in Type B are: " + str(counterB) + " Your expiry date is on: " + str(expirationdate))
                                    counterB = counterB + 1
                                    paymentOMB = input("Are you done with your transaction? y/n: ")
                                    if paymentOMB not in boolean:
                                        xcommand()
                                        continue
                                    elif paymentNB == "y":
                                        print("Your total is: RM" + str(invoice))
                                        print("Goodbye!")
                                        sys.exit()
                                    elif paymentNB == "n":
                                        break
                                    
                            
                                        
                            
                        
            

