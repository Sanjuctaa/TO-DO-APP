# TO-DO-APP

from tkinter import *

from tkinter import messagebox

#create funtion

task_list= []

    
#create main window

win=Tk()

win.geometry('500x450+500+200')

win.title("Sanjucta Sutadhar's App")

win.config(bg='#0077B6')

#create label

name_lab= Label(win,text='To Do List',bg='light blue',font=('Times','25'))

name_lab.pack(fill=BOTH)

    #create widgets (frame,Listbox, Scrollbar,Entry,Button)

    #entry_box

my_entry=Entry(win,font=('Times',18))

my_entry.pack(pady=40)

def newTask():

    task= my_entry.get()
    
    if task !="":
    
        lb.insert(END,task)
        
        my_entry.delete(0,"end")
        
    else:
    
        messagebox.showwarning("warning","please enter some task.")

def deleteTask():

    lb.delete(ANCHOR)



#button

but_frame= Frame(win)

but_frame.pack(pady=1)

add_button= Button(but_frame,text="Add Task",bg='#008631',font=('Times', "13"),fg='white',command= newTask)

add_button.pack(fill=BOTH, expand=True,side=LEFT)

del_button= Button(but_frame,text="Delete Task",bg='#FF6E00',font=('Times', "13"),fg='white',command=deleteTask)

del_button.pack(fill=BOTH, expand=True,side=RIGHT)

#listbox

frame= Frame(win)

frame.pack(pady=50)

lb=Listbox(frame,width=25,height=30,font=('Times',17),bd=0, fg='#464646', 
           highlightthickness=0,selectbackground='#a6a6a6',activestyle="none")
           
lb.pack(side=LEFT,fill= BOTH)


for item in task_list:

    lb.insert(END,item)          

sb= Scrollbar(frame)

sb.pack(side=RIGHT, fill=BOTH)

lb.config(yscrollcommand=sb.set)

sb.config(command=lb.yview)

win.mainloop()
