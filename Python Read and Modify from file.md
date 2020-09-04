##Programmer: Dylan Ackerley - Program 7


name = input("Please enter your name: ")
whatfile = (input("Please enter your file name: "))
try:
    infile = open(whatfile,"r") #opens our list of the users answers. We'll want to compare this to correct_answers at some point in time

    correct_answers = ['A', 'C', 'A', 'A', 'D', 'B', 'C', 'A', 'C', 'B', 'A', 'D', 'C', 'A', 'D', 'C', 'B', 'B', 'D', 'A']
    users_answers = [] #This list is just as long as correct_answers


    line=infile.readline()
    while line !="":
        answers = line.strip()
        users_answers.append(answers)
        line=infile.readline()


    correct_amount = []
    incorrect_amount = []
    for x in range (20):
        if users_answers[x] == correct_answers[x]:
            correct_amount.append(x)
        elif users_answers[x] != correct_answers[x]:
            incorrect_amount.append(x)

    print("\n\n\nName of Examinee:", name)

    correct_number = (len(correct_amount))
    if correct_number >= 15:
        print("Congratulations, you passed the exam!")

    else:
        print("Sorry, you did not pass the exam this time")

    score = (correct_number % len(correct_answers))
    print("Score: {0}%".format(score * 5))
    #print("Score: {0}%".format(correct_number*5)) #can use multipliers in format arguments. - Alternative way, better way to do it.
    print("Number correct: {0}".format(len(correct_amount))) #can use len() method in format arguments.
    print("Number incorrect: {0}".format(len(incorrect_amount)))






    print("Questions missed: ", end="")

    for elem in incorrect_amount:
        if elem == incorrect_amount[len(incorrect_amount)-1]:  #if elem equals anything other than the last element, do the else statement. Once it equals the last element, do the if statement.
            print(elem)                                        #does else statement everytime except last time
        else:
            print (elem,end =",")

    print(input("\n\n\nEnter any key to exit... "))

except Exception as err:
    print(input("\nError, read source code. Enter any key to exit... "))




