# python.coding-notes
#____________________________first.py_____________________________________
num=int(input("Enter A number from 0 to 999:   "))
if num<0 or num>999:
    print ("Invalide entry")
elif num<10: 
    print ("One digit number")
elif num<100 :
    print ("Two digit number")
else:       
    print ("Triple digit number")
#____________________________calculator.py_____________________________________
    num1 = float(input("Enter first number: "))
op = input("Enter operation (+, -, *, /): ")
num2 = float(input("Enter second number: "))
if op == "+":
    result = num1 + num2
elif op == "-":
    result = num1 - num2
elif op == "*":
    result = num1 * num2
elif op == "/":
    if num2 != 0:
        result = num1 / num2
    else:
        result = "Error! Division by zero."
#____________________________datatype.py_____________________________________
x=2
y=True
z="3.5"
str=3.5
list=[1,2,3,5,'a','g']
tuples=(1,2,3,5,'a','g')
dict={'a':1,'b':2,'c':3,'d':4,'e':5}
print(x,y,z,str)
print(list)
print(tuples)
print(dict)
print(type(x))
print(type(y))
print(type(z))
print(type(str))
print(type(list))
print(type(tuples))
print(type(dict))
print(dict.keys())
print(dict.values())  
r=10/2
print(r)
h=4.5/2.25
print(h)
c=4.5/1
print(c)
w=5/2.3
print(w)
#____________________________function.py_____________________________________
def sum(a,b,d):                   #parameter=a,b,d
    c=a+b*d
    return c
print(sum(5,6,7))                     #argument=5,6,7
print(sum(56,63,87))
print(sum(-5,-35,56))
print(sum(22,7,67))

def greet():
    print("hello how how are you")
greet ()
greet ()
greet ()
greet ()

def calculate(a,b):
    r=a+b,a-b,a*b,a/b
    return r
print(calculate(2,4))
#____________________________homework.py_____________________________________
def hello():
    print("Hello, World!")
hello()
...............................................................................................
def  square(n):
    m=n*n
    return m
print(square(3))
...............................................................................................
def  is_even(n):
    m=n%2==0
    return m
print(is_even(6))
...............................................................................................
def add_numbers(a,b):                   
     c=a+b
     return c
print(add_numbers(5,6))
...............................................................................................
def greet(name="Guest"):
    print("Hello", name)
greet("Bhavyansh")
...............................................................................................
def factorial(n):
    a = 1
    for i in range(2, n+1):
        a*= i
    return a  
print(factorial(3))
...............................................................................................
def reverse_string(s):
    return s[::-1]
print(reverse_string("12345678"))
...............................................................................................
def is_palindrome(s):
    s = s.lower()   
    return  s[::-1]
print(is_palindrome("bhavyansh"))        
...............................................................................................
def calculator(a, b, operation):
    if operation =="+":
        return a + b
    elif operation =="-":
        return a - b
    elif operation =="*":
        return a * b
    elif operation =="/":
        return a / b if b != 0 else "Error: Division by zero"
    else:
        return "Invalid operation"
print(calculator(4,3,"*"))
...............................................................................................
def find_max(numbers):
    return max(numbers)
print(find_max([1,2,3,4,5,6,7,8,4,64,65,3466]))
...............................................................................................
def count_vowels(s):
    vowels="aeiouAEIOU"
    return sum(1 for char in s if char in vowels)
print(count_vowels("Bhavyansh jain"))
...............................................................................................
def get_even_list(lst):
    return [num for num in lst if num%2!=0]
print(get_even_list([1,2,3,4,5,6,7,8]))
...............................................................................................
##fibonacci =0,1,1,2,3,5,8,13,21,34,55,89,144
def fibo(n):
    seq=[0,1]
    while len(seq)<n:
        seq.append(seq[-1]+seq[-2])
    return seq[:n]
print (fibo(20))
...............................................................................................
def prime_numbers(limit):
    prime=[]
    for num in range(2,limit+1):
        isprime=True 
        for i in range(2,int(num*0.5)+1):
            if num % i==0:
                isprime=False
                break
        if isprime:
            prime.append(num)
    return prime
print(prime_numbers(100))
..............................................................................................
def word_frequency(text):
    letters=text.lower()
    frequency={}
    for letter in letters:
        frequency[letter]=frequency.get(letter,0)+1
    return frequency
print(word_frequency("Hello hello Hello world World world"))
#________________________________________advence calculatof.py_______________________________________________
import ast
import operator as op
# Allowed operators
BIN_OPS = {
    ast.Add: op.add,
    ast.Sub: op.sub,
    ast.Mult: op.mul,
    ast.Div: op.truediv,
    ast.FloorDiv: op.floordiv,
    ast.Mod: op.mod,
    ast.Pow: op.pow,
}
UNARY_OPS = {
    ast.UAdd: op.pos,
    ast.USub: op.neg,
}
def _eval(node):
    if isinstance(node, ast.Expression):
        return _eval(node.body)
    if isinstance(node, ast.Constant):  # Numbers
        if isinstance(node.value, (int, float)):
            return node.value
        raise TypeError("Only numbers are allowed.")
    if hasattr(ast, "Num") and isinstance(node, ast.Num):  # For older Python
        return node.n
    if isinstance(node, ast.BinOp):  # Binary ops
        left = _eval(node.left)
        right = _eval(node.right)
        op_type = type(node.op)
        if op_type in BIN_OPS:
            return BIN_OPS[op_type](left, right)
        raise TypeError(f"Unsupported operator: {op_type}")
    if isinstance(node, ast.UnaryOp):  # Unary ops (+, -)
        operand = _eval(node.operand)
        op_type = type(node.op)
        if op_type in UNARY_OPS:
            return UNARY_OPS[op_type](operand)
        raise TypeError(f"Unsupported unary operator: {op_type}")
    raise TypeError(f"Unsupported expression: {type(node)}")
def calculate(expr):
    expr = expr.replace("^", "**")  # Allow ^ for power
    tree = ast.parse(expr, mode='eval')
    return _eval(tree)
def calculator():
    print("===== Calculator App =====")
    print("Enter any expression (e.g., 10 + 20 * 3 - 5 / 2)")
    print("Supported ops: +, -, *, /, //, %, **, ^ (power), parentheses ()")
    print("Type 'exit' to quit.\n")
    while True:
        expr = input(">>> ")
        if expr.lower() in ["exit", "quit", "q"]:
            print("Goodbye!")
            break
        try:
            result = calculate(expr)
            print("Result:", result)
        except Exception as e:
            print("Error:", e)
# Run the calculator
if __name__ == "__main__":
    calculator()
    else:
    result = "Invalid operation."
#__________________________________________________loop.py____________________________________
a=int(input("Enter a number:"))
for i in range(1,11):
    print(f"{a}X{i}={a*i}")
.................................................................................................
num=int(input("Take any number lasses than"))
while num<=10:
    if num%2==0:
        print(num,"number is even")
    else:
        print(num,"number is odd")
    num+=1
print("Progrem is over")
.................................................................................................
num=int(input("Take any number :"))
if num%2==0:
     print(num,"number is even")
else:
    print(num,"number is odd")
.................................................................................................
num=1
for num in range(1,11):
    if num%2==0:
        print(num,"number is even")
    else:
        print(num,"number is odd")
    num+=1
print("Progrem is over")
.................................................................................................
jump statment
1 break:statement skips the rest of the loop and jump over to statement folloing the loop
2 continue: skips the rest of the after loop statemnt
.................................................................................................
a=b=c=0
for i in range (1,11):
    a=int(input("Enter a number"))
    b=int(input("Enter another a number"))
    if b==0:
        print("division by 0 error")
        continue
    else :
        c=a/b
        print("Quotient is equal to :",c)
print("program is over")
.................................................................................................
name="Bhavyansh jain"
print(type(name))
for n in name:
    print(n,'',end='')
.................................................................................................
#str= anything within inverted comma
string concadination
name1="Bhavyanh "
name2="Jain"
print(name1+name2)
.................................................................................................
member functioning (not in) (in)
name="bhavyansh"
print('he'not in"bhavyansh")
.................................................................................................
#string slicing
#forward
name="bhavyanshjain"
print(name[::-1])
print(name[6:])
print(name[:10])
print(name[:])
.................................................................................................
#string slicing
#backward
name="bhavyanshjain"
print(name[-6:-1])
print(name[-6:])
print(name[:-10])
print(name[:])
.................................................................................................
name="bhavyansh"
print(name.__len__())
.................................................................................................
name="bhavyansh"
print(name.capitalize())
.................................................................................................
name="BHAVYANSH"
print(name.lower())
.................................................................................................
name="&*"
print(name.isalnum())
.................................................................................................
list=[1,2,3,4,5,6,7,8]
print(list[3:6])
print(list[4:])
print(list[:7])
print(list[:])
#___________________________calculator.py_______________
def add(a, b):
    return a + b
def subtract(a, b):
    return a - b
def multiply(a, b):
    return a * b
def divide(a, b):
    if b == 0:
        return "Error! Division by zero."
    return a / b
def calculator():
    print("===== Calculator App =====")
    print("1. Use calculator")
    print("2. Exit")
    while True:
        choose = input("Enter choice (1 or 2): ")
        if choose == '2':
            print("Exiting Calculator. Goodbye!")
            break
        if choose == '1':
            num1 = float(input("Enter first number: "))
            print("1. Addition")
            print("2. Subtraction")
            print("3. Multiplication")
            print("4. Division")
            choice=(input("Operation from 1 to 4:"))
            num2 = float(input("Enter second number: "))
            if choice == '1':
                print("Result:", add(num1, num2))
            elif choice == '2':
                print("Result:", subtract(num1, num2))
            elif choice == '3':
                print("Result:", multiply(num1, num2))
            elif choice == '4':
                print("Result:", divide(num1, num2))
        else:
            print("Invalid choice! Please enter a number between 1-5.")
# Run the calculator
calculator()
#_____________________________________________







    
print("Result:", result)
