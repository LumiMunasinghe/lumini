# lumini
import sys    #to access the variables and the function
count_progress=0
count_trailer=0
count_exclude=0
count_retriever=0
pass_credit=0
defer_credit=0
fail_credit=0
total=0
total_1=0
List =[]
option=''
x=''

s1= '****************'
print(f"{s1:>40}\n_____MAIN VERSION_____")
print()

while x.upper!='A' or x.upper!='B':
    x=input("If you are a student, press 'A' and if you are a staff member, press 'B':")
    def uppercase():
        global x
        x=x.upper() #convert x's value in to capital 
        return x
    uppercase()  #to return the x value to capital
    while x=='A' or x=='B':    
        pass
        print()
        if x=='A' or x=='B':
            pass
        else:
            continue
        while option!='y' or option!='q':       
            try:
                pass_credit=int(input('Enter your total PASS credits:'))
                if pass_credit <=120 and pass_credit%20==0:
                    defer_credit=int(input('Enter your total DEFER credits:')) 
                else:
                    print ('Out of range')
                    print()
                    continue

                if defer_credit<=120 and defer_credit%20==0:
                    fail_credit=int(input('Enter your total FAIL credits:')) 
                else:
                    print('out of range')
                    print ()
                    continue
                if fail_credit<=120 and fail_credit%20==0:
                    pass
                else:
                    print('out of range')
                    print ()
                    continue

                total=(fail_credit+defer_credit+pass_credit)
                if total==120 and total%20==0 :  
                    pass
                else:
                    print('Total incorrect')
                    print()
                    continue

            except ValueError:
                    print ('Integer requied')         
                    print()
                    continue
                           
            while total!=0:
                if (pass_credit==120)and (defer_credit==0)and (fail_credit==0):     
                    outcome = 'Progress'
                    print (outcome)                          
                    count_progress+=1
                    print()
                    break
                
                elif (pass_credit==100)and (defer_credit<=20)and (fail_credit<=20):  
                    outcome = 'Progress(module trailer)'
                    print (outcome)
                    count_trailer+=1
                    print()
                    break
                elif (pass_credit<=40)and (defer_credit<=40) and (fail_credit>=80):
                    outcome = 'Excluded'
                    print(outcome)
                    count_exclude+=1
                    print()
                    break
                else:
                    outcome = 'module retriever'
                    print(outcome)
                    count_retriever+=1
                    print()
                    break

            input_credits=(outcome,'-',pass_credit,defer_credit,fail_credit)
            List.append(input_credits) # add the outputs to the list
            
          
            if x=='A':
                s1= '****************'
                print(f'{s1:>40}')
                sys.exit() #exit in student version                            
                print()
            else:
                pass

            while x!='A':
                option=str(input("Would you like to enter another set of data? \nEnter 'y' for yes or 'q' to quit and view results: "))
                option=option.lower()
                if option=='y':
                    print()
                    break
                elif option=='q':
                    print()
                    break
                else:
                    print()     
                    continue  
    #HISTOGRAM         
            if option=='q':   # when the program quit
                print("-"*62)
                print ("Histrogram \nProgress",count_progress,":","*"*count_progress)
                print('Trailer',count_trailer,':','*'*count_trailer)
                print('Retriever',count_retriever,':','*'*count_retriever)
                print('Excluded',count_exclude,':','*'*count_exclude)
                total_1=(count_progress+count_trailer+count_retriever+count_exclude)
                print (total_1, 'outcomes in total')
                print("-"*62)
                
    #______________________________PART 2 - LIST_____________________________________________

                print ('*'*10,'List','*'*10)
                print()
                for i in List:
                    ii=str(i)[1:-1] #convers int. value to a string
                    ii=ii.replace ("'","")   #remove the " ' "
                    print(ii)
                    print()
            
                s1= '****************'
                print(f'{s1:>40}')
                
    #___________________________PART 3 - TEXT FILE___________________________________________
                
                with open ('lumininew.txt','w')as file: #create a new file
                    for d in List:
                        dd=str(d)[1:-1]
                        dd=dd.replace("'","")
                        file.write(str(dd )+ '\n') #print the list in line by line
                file.close()
            
                
                if x=='B':
                    sys.exit() #exit the all program
                    
                else:
                    pass
