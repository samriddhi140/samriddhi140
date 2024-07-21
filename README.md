- 👋 Hi, I’m @samriddhi140
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---from tkinter import *
from tkinter import messagebox
import pymysql

class EmployeeSystem:
    def __init__(self, root):
        self.root = root
        self.root.title("Employee Payroll Management System")
        self.root.geometry("1350x700+0+0")
        self.root.config(bg="white")

        title = Label(self.root, text="Employee Payroll Management System", font=("times new roman", 30, "bold"), bg="#262626", fg="white", anchor="w", padx=10).place(x=0, y=0, relwidth=1)

        # Variables
        self.var_emp_code = StringVar()
        self.var_designation = StringVar()
        self.var_name = StringVar()
        self.var_age = StringVar()
        self.var_gender = StringVar()
        self.var_email = StringVar()
        self.var_hired_location = StringVar()
        self.var_dob = StringVar()
        self.var_doj = StringVar()
        self.var_id_proof = StringVar()
        self.var_contact = StringVar()
        self.var_status = StringVar()
        self.var_experience = StringVar()
        self.var_address = StringVar()

        self.var_month = StringVar()
        self.var_year = StringVar()
        self.var_salary = StringVar()
        self.var_total_days = StringVar()
        self.var_absent = StringVar()
        self.var_medical = StringVar()
        self.var_pf = StringVar()
        self.var_conveince = StringVar()
        self.var_net_salary = StringVar()

        self.create_widgets()

        # Check database connection on startup
        self.check_connection()

    def create_widgets(self):
        # Frame 1: Employee Details
        Frame1 = Frame(self.root, bd=3, relief=RIDGE, bg="white")
        Frame1.place(x=10, y=70, width=750, height=620)
        title2 = Label(Frame1, text="Employee Details", font=("times new roman", 20), bg="lightgray", fg="black", anchor="w", padx=10).place(x=0, y=0, relwidth=1)

        lbl_code = Label(Frame1, text="Employee code", font=("times new roman", 15), bg="white", fg="black").place(x=10, y=70)
        txt_code = Entry(Frame1, font=("times new roman", 15), textvariable=self.var_emp_code, bg="light yellow", fg="black").place(x=220, y=74, width=200)
        btn_search = Button(Frame1, text="Search", font=("times new roman", 20), bg="light blue", fg="black").place(x=440, y=72, height=30)

        # ... [Other labels and entry fields for employee details as shown in your code] ...

        # Frame 2: Salary Details
        Frame2 = Frame(self.root, bd=3, relief=RIDGE, bg="white")
        Frame2.place(x=770, y=70, width=580, height=300)
        title3 = Label(Frame2, text="Employee Salary Details", font=("times new roman", 20), bg="lightgray", fg="black", anchor="w", padx=10).place(x=0, y=0, relwidth=1)

        lbl_month = Label(Frame2, text="Month", font=("times new roman", 16), bg="white", fg="black").place(x=10, y=60)
        txt_month = Entry(Frame2, font=("times new roman", 15), textvariable=self.var_month, bg="light yellow", fg="black").place(x=70, y=62, width=80)
        lbl_year = Label(Frame2, text="Year", font=("times new roman", 16), bg="white", fg="black").place(x=180, y=60)
        txt_year = Entry(Frame2, font=("times new roman", 15), textvariable=self.var_year, bg="light yellow", fg="black").place(x=247, y=62, width=100)
        lbl_salary = Label(Frame2, text="Salary", font=("times new roman", 16), bg="white", fg="black").place(x=310, y=60)
        txt_salary = Entry(Frame2, font=("times new roman", 15), textvariable=self.var_salary, bg="light yellow", fg="black").place(x=390, y=62, width=100)

        # ... [Other labels and entry fields for salary details as shown in your code] ...

        btn_calculate = Button(Frame2, text="Calculate", command=self.calculate, font=("times new roman", 20), bg="Red", fg="white").place(x=70, y=240, height=30, width=120)
        btn_save = Button(Frame2, text="Save", command=self.add, font=("times new roman", 20), bg="green", fg="white").place(x=220, y=240, height=30, width=120)
        btn_clear = Button(Frame2, text="Clear", font=("times new roman", 20), bg="gray", fg="black").place(x=360, y=240, height=30, width=120)

        # Frame 3: Calculator and Salary Receipt
        Frame3 = Frame(self.root, bd=3, relief=RIDGE, bg="white")
        Frame3.place(x=770, y=380, width=580, height=310)

        # Calculator Frame
        self.create_calculator(Frame3)

        # Salary Receipt Frame
        self.create_salary_receipt(Frame3)

    def create_calculator(self, parent):
        self.var_txt = StringVar()
        self.Var_operator = ''

        def btn_click(num):
            self.Var_operator = self.Var_operator + str(num)
            self.var_txt.set(self.Var_operator)

        def result():
            res = str(eval(self.Var_operator))
            self.var_txt.set(res)
            self.Var_operator = ''

        def clear_cal():
            self.var_txt.set('')
            self.Var_operator = ''

        Cal_Frame = Frame(parent, bg="white", bd=2, relief=RIDGE)
        Cal_Frame.place(x=1, y=1, width=280, height=300)
        txt_Result = Entry(Cal_Frame, bg="lightyellow", textvariable=self.var_txt, font=("times new roman", 20, "bold"), justify=RIGHT).place(x=0, y=0, relwidth=0.9, height=90)

        # ... [Calculator buttons as shown in your code] ...

    def create_salary_receipt(self, parent):
        Sal_Frame = Frame(parent, bg="white", bd=2, relief=RIDGE)
        Sal_Frame.place(x=251, y=2, width=241, height=300)
        title_Salary = Label(Sal_Frame, text="SALARY RECEIPT", font=("times new roman", 17), bg="lightgray", fg="black", anchor="w", padx=10).place(x=0, y=0, relwidth=1)

        Sal_Frame2 = Frame(Sal_Frame, bg="white", bd=2, relief=RIDGE)
        Sal_Frame2.place(x=0, y=30, relwidth=1, height=230)

        sample = '''\t Company Name, XYZ\n\tAddress: XYZ, Floor 4
-----------------------------
Employee ID\t\t: 
Salary Of\t\t: Mon-YYYY
Generated On\t\t: DD-MM-YYYY
------------------------------
Total Days\t\t: XX
Total Present\t\t: XX
Total Absent\t\t:  XX
Convenience\t\t: Rs. XX
Medical\t\t: Rs. XX
PF\t\t: Rs. XX
Gross Payment\t\t: Rs. XX
Net Salary\t\t: Rs. XX
------------------------------
This is a computer-generated slip, no signature required.
        '''

        scroll_Y = Scrollbar(Sal_Frame2, orient=VERTICAL)
        scroll_Y.pack(fill=Y, side=RIGHT)

        self.txt_salary_receipt = Text(Sal_Frame2, font=("times new roman", 12), bg="lightgray", yscrollcommand=scroll_Y.set)
        self.txt_salary_receipt.pack(fill=BOTH, expand=1)
        scroll_Y.config(command=self.txt_salary_receipt.yview)
        self.txt_salary_receipt.insert(END, sample)
        btn_print = Button(Sal_Frame, text="PRINT", font=("times new roman", 17), bg="lightblue", fg="black").place(x=100, y=262, height=30, width=120)

    def calculate(self):
        if not self.var_emp_code.get() or not self.var_year.get() or not self.var_salary.get() or not self.var_total_days.get():
            messagebox.showerror('Error', 'All fields are required')
        else:
            try:
                per_day = float(self.var_salary.get()) / int(self.var_total_days.get())
                work_days = int(self.var_total_days.get()) - int(self.var_absent.get())
                sal_ = per_day * work_days
                deduct = float(self.var_medical.get()) + float(self.var_pf.get())
                addition = float(self.var_conveince.get())
                net_sal = sal_ - deduct + addition
                self.var_net_salary.set(f'{net_sal:.2f}')
                self.txt_salary_receipt.delete('1.0', END)
                self.txt_salary_receipt.insert(END, self.generate_salary_receipt(net_sal))
            except Exception as ex:
                messagebox.showerror('Error', str(ex))

    def generate_salary_receipt(self, net_salary):
        return f'''\tCompany Name, XYZ\n\tAddress: XYZ, Floor 4
-----------------------------
Employee ID\t\t: {self.var_emp_code.get()}
Salary Of\t\t: {self.var_month.get()}-{self.var_year.get()}
Generated On\t\t: DD-MM-YYYY
------------------------------
Total Days\t\t: {self.var_total_days.get()}
Total Present\t\t: {int(self.var_total_days.get()) - int(self.var_absent.get())}
Total Absent\t\t: {self.var_absent.get()}
Convenience\t\t: Rs. {self.var_conveince.get()}
Medical\t\t: Rs. {self.var_medical.get()}
PF\t\t: Rs. {self.var_pf.get()}
Gross Payment\t\t: Rs. {self.var_salary.get()}
Net Salary\t\t: Rs. {net_salary:.2f}
------------------------------
This is a computer-generated slip, no signature required.
        '''

    def check_connection(self):
        try:
            con = pymysql.connect(host='localhost', user='root', password='password', db='emplolyee2')
            cur = con.cursor()
            cur.execute("SELECT * FROM emp_salary")
            con.close()
        except Exception as ex:
            messagebox.showerror('Error', f'Error due to : {str(ex)}')

    def add(self):
        try:
            con = pymysql.connect(host='localhost', user='root', password='password', db='emplolyee2')
            cur = con.cursor()
            cur.execute("INSERT INTO emp_salary (emp_code, emp_designation, emp_name, emp_age, emp_gender, emp_email, emp_hiredLocation, emp_dob, emp_doj, emp_idproof, emp_contact, emp_status, emp_experience, emp_address, emp_month, emp_year, emp_salary, emp_total_days, emp_absent, emp_medical, emp_pf, emp_conveince, emp_net_salary) VALUES (%s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s, %s)", (
                self.var_emp_code.get(),
                self.var_designation.get(),
                self.var_name.get(),
                self.var_age.get(),
                self.var_gender.get(),
                self.var_email.get(),
                self.var_hired_location.get(),
                self.var_dob.get(),
                self.var_doj.get(),
                self.var_id_proof.get(),
                self.var_contact.get(),
                self.var_status.get(),
                self.var_experience.get(),
                self.var_address.get(),
                self.var_month.get(),
                self.var_year.get(),
                self.var_salary.get(),
                self.var_total_days.get(),
                self.var_absent.get(),
                self.var_medical.get(),
                self.var_pf.get(),
                self.var_conveince.get(),
                self.var_net_salary.get()
            ))
            con.commit()
            con.close()
            messagebox.showinfo('Success', 'Record added successfully')
        except Exception as ex:
            messagebox.showerror('Error', f'Error due to : {str(ex)}')

if __name__ == "__main__":
    root = Tk()
    obj = EmployeeSystem(root)
    root.mainloop()

samriddhi140/samriddhi140 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
