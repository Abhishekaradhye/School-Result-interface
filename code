stud_info = {101: {'name':'Virat Kohli',
                     'subject':{'English': 93,
                                'Science': 90,
                                'Maths'  : 83}},
             102: {'name':'Rohit Sharma',
                     'subject':{'English': 85,
                                'Science': 87,
                                'Maths'  : 91}},
             103: {'name':'Shikhar Dhawan',
                     'subject':{'English': 84,
                                'Science': 92,
                                'Maths'  : 86}}}

teacher_info = {'MS Dhoni': {'id' : '07',
                             'password' : 'MSD'},
                'Rahul Dravid': {'id' : '19',
                                 'password' : 'RD'}}
all_perc = []

school_name = 'Ashvamedh Highschool'
zone = 'Teachers Console'
w = 60
max_retry = 3

#######  ERRORS ########
em_1 = 'ERROR : Invalid Choice Entered '
em_2 = 'ERROR : Max Retries Exceeded '
em_3 = 'ERROR : Invalid Roll Number Entered '
em_4 = 'ERROR : Invalid Name Entered '
em_5 = 'ERROR : Invalid Credentials Entered '
em_6 = 'ERROR : Invalid Marks Entered'

def header(msg=school_name):
    print(f"{'='*w}\n{msg.center(w)}\n{'='*w}")

def screen_one():
    valid_choices = ['1','2','3']
    header()
    print("1) Student Login \n2) Teacher Login \n3) Exit")
    ch = input('Please enter your choice here : ')
    for i in range(max_retry):
        if ch not in valid_choices :
            print(em_1)
        elif ch =='3':
            print('Do you want to exit ? (yes/no) : ')
            ch1 = input('Enter choice : ')
            if ch1.lower()=='yes':
                return ch
        else :
            return ch
    print(em_2)
    return False

def teacher_login(): 
    for i in range(max_retry):
        header(msg=zone)
        t_name = input('Please enter your name here : ')
        if t_name in teacher_info:
            t_id = input('Please enter your identity here : ')
            if t_id == teacher_info[t_name]['id']:
                t_paswd = input('Please enter your password here : ')
                if t_paswd == teacher_info[t_name]['password']:
                    return True
                else:
                    print(em_5)
            else:
                print(em_5)               
        else :
            print(em_4)
        
    print(em_2)
    return False

def get_result():
    header(msg=school_name)

    rno = int(input('Please enter the student roll number here : '))
    if rno in stud_info :

        print(f"name  :  {stud_info[rno]['name']} \nRoll Number  : {rno}")
        print('-'*w)
        print(f"English  :  {stud_info[rno]['subject']['English']} \nScience  :  {stud_info[rno]['subject']['Science']}\nMaths    :  {stud_info[rno]['subject']['Maths']}")
        print('-'*w)
        percentage = (stud_info[rno]['subject']['English'] + stud_info[rno]['subject']['Science'] + stud_info[rno]['subject']['Maths']) / len(stud_info[rno]['subject'])
        print(f"Percentage  : {percentage}")
        global all_perc
        all_perc.append(percentage)
        all_perc=list(set(all_perc))
        all_perc.sort(reverse=True)
        rank = all_perc.index(percentage)+1
        print(f"Rank  :  {rank}")
        
    else:
        print(em_3)

def search_roll_no():
    header(msg=zone)
    rno = int(input('Please enter the student roll number here : '))
    if rno in stud_info:
        print(stud_info[rno]['name'], ' '*5, rno )
        print('\n')
    else:
        print(em_3)

def get_new_roll_no():
    if stud_info:
        return max(stud_info) + 1
    else:
        return 101
    
def enter_stud_info():
    header(msg=zone)
    name = input("Please enter new student's name here : ")
    eng_mrk = int(input('Please enter the marks in English : '))
    if 0<eng_mrk<101:
        sci_mrk = int(input('Please enter the marks in Science : '))
        if 0<sci_mrk<101:
            math_mrk = int(input('Please enter the marks in Maths : '))
            rno = get_new_roll_no()
            global stud_info
            stud_info[rno]={'name' : name,
                            'subject':{'English' : eng_mrk,
                                       'Science' : sci_mrk,
                                       'Maths' : math_mrk}}
            print(f"New student information is created with roll number {rno} ")
        else:
            print(em_6)
    else:
        print(em_6)

def logged_in_teacher():
    while True:
        valid_choices = ['1','2','3','4']
        print('1) Get Result \n2) Search Roll Number \n3) Enter student Information \n4) Exit ')
        ch2 = input('Please enter your choice here : ')
        if ch2 not in valid_choices:
            print(em_1)
        elif ch2 =='4' :
            return ch2
        elif ch2 == '1':
            get_result()
        elif ch2 == '2':
            search_roll_no()
        elif ch2 == '3':
            enter_stud_info()
        else :
            return ch2
        
def main():
    while True:
        ch = screen_one()
        if ch =='1':
            get_result()
        elif ch == '2':
            ok = teacher_login()
            if ok:
                logged_in_teacher()              
            else:
                print(em_5)
        elif ch =='3':
            header('Thank You !!!')
            break
        else:
            break

main()
