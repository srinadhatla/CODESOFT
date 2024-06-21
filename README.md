# CODESOFT
                                                              TASK 1
                                                            TO-DO LIST
                                                            
A To-Do List application is a useful project that helps users manage and organize their tasks efficiently. This project aims to create a command-line or GUI-based application using Python, allowing users to create, update, and track their to-do lists

Python program for TO-DO LIST:

# Importing the necessary modules
import json
from datetime import datetime

# Function to load tasks from a JSON file
def load_tasks():
    try:
        with open('tasks.json', 'r') as file:
            tasks = json.load(file)
    except FileNotFoundError:
        tasks = []
    return tasks

# Function to save tasks to a JSON file
def save_tasks(tasks):
    with open('tasks.json', 'w') as file:
        json.dump(tasks, file, indent=4)

# Function to display tasks
def display_tasks(tasks):
    if not tasks:
        print("No tasks found!")
    else:
        print("Tasks:")
        for i, task in enumerate(tasks, start=1):
            print(f"{i}. {task['title']} - {task['description']} - {task['due_date']} - {'Done' if task['done'] else 'Pending'}")

# Function to add a new task
def add_task(tasks):
    title = input("Enter task title: ")
    description = input("Enter task description: ")
    due_date = input("Enter due date (YYYY-MM-DD): ")
    new_task = {
        'title': title,
        'description': description,
        'due_date': due_date,
        'done': False
    }
    tasks.append(new_task)
    save_tasks(tasks)
    print("Task added successfully!")

# Function to mark a task as done
def mark_task_done(tasks):
    display_tasks(tasks)
    task_index = int(input("Enter task number to mark as done: ")) - 1
    tasks[task_index]['done'] = True
    save_tasks(tasks)
    print("Task marked as done!")

# Main function to run the application
def main():
    tasks = load_tasks()

    while True:
        print("\n===== To-Do List Menu =====")
        print("1. Display Tasks")
        print("2. Add New Task")
        print("3. Mark Task as Done")
        print("4. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            display_tasks(tasks)
        elif choice == '2':
            add_task(tasks)
        elif choice == '3':
            mark_task_done(tasks)
        elif choice == '4':
            print("Exiting program...")
            break
        else:
            print("Invalid choice. Please enter a number from 1 to 4.")

if __name__ == "__main__":
    main()

How to Use:
1.	Run the Script: Save this code to a file (e.g., todo_app.py) and run it using Python (python todo_app.py).
2.	Menu Options:
o	Display Tasks: Shows all tasks with their details.
o	Add New Task: Lets you add a new task with a title, description, and due date.
o	Mark Task as Done: Marks a task as completed.
o	Exit: Quits the application.



                                                                TASK 2
                                                             CALCULATOR
Design a simple calculator with basic arithmetic operations. Prompt the user to input two numbers and an operation choice. Perform the calculation and display the result.

Python program for CALCULATOR:


# Function to add two numbers
def add(x, y):
    return x + y

# Function to subtract two numbers
def subtract(x, y):
    return x - y

# Function to multiply two numbers
def multiply(x, y):
    return x * y

# Function to divide two numbers
def divide(x, y):
    if y == 0:
        return "Error! Division by zero."
    else:
        return x / y

# Function to perform modulus operation
def modulus(x, y):
    if y == 0:
        return "Error! Modulus by zero."
    else:
        return x % y

# Main function to run the calculator
def main():
    print("Welcome to Simple Calculator")

    while True:
        # Display operation menu
        print("\nOperations:")
        print("1. Addition")
        print("2. Subtraction")
        print("3. Multiplication")
        print("4. Division")
        print("5. Modulus")
        print("6. Exit")

        choice = input("Enter your choice (1-6): ")

        if choice in ('1', '2', '3', '4', '5'):
            # Input two numbers
            num1 = float(input("Enter first number: "))
            num2 = float(input("Enter second number: "))

            if choice == '1':
                print(f"{num1} + {num2} = {add(num1, num2)}")
            elif choice == '2':
                print(f"{num1} - {num2} = {subtract(num1, num2)}")
            elif choice == '3':
                print(f"{num1} * {num2} = {multiply(num1, num2)}")
            elif choice == '4':
                print(f"{num1} / {num2} = {divide(num1, num2)}")
            elif choice == '5':
                print(f"{num1} % {num2} = {modulus(num1, num2)}")
        elif choice == '6':
            print("Exiting the calculator. Goodbye!")
            break
        else:
            print("Invalid input! Please choose a valid operation (1-6).")

if __name__ == "__main__":
    main()


How to Use:
1.	Run the Script: Save this code to a file (e.g., calculator.py) and execute it using Python (python calculator.py).
2.	Calculator Operations:
o	Addition: Adds two numbers.
o	Subtraction: Subtracts the second number from the first.
o	Multiplication: Multiplies two numbers.
o	Division: Divides the first number by the second (handles division by zero).
o	Modulus: Computes the remainder of the first number divided by the second (handles modulus by zero).
o	Exit: Quits the calculator program.
 

                                                                TASK 3
                                                           PASSWORD GENERATOR
A password generator is a useful tool that generates strong and random passwords for users. This project aims to create a password generator application using Python, allowing users to specify the length and complexity of the password. 
User Input: Prompt the user to specify the desired length of the password. 
Generate Password: Use a combination of random characters to generate a password of the specified length. 
Display the Password: Print the generated password on the screen.
Python program for PASSWORD GENERATOR:
Copy code
import random
import string

def generate_password(length):
    # Define the character sets to generate the password
    characters = string.ascii_letters + string.digits + string.punctuation
    
    # Generate the password
    password = ''.join(random.choice(characters) for _ in range(length))
    
    return password

def main():
    print("Welcome to Password Generator")
    
    while True:
        try:
            # Prompt user for password length
            length = int(input("Enter the desired length of the password (at least 6 characters): "))
            
            if length < 6:
                print("Password length should be at least 6 characters.")
                continue
            
            # Generate the password
            password = generate_password(length)
            
            # Display the generated password
            print(f"Generated Password: {password}")
            
            # Ask user if they want to generate another password
            while True:
                another = input("Generate another password? (yes/no): ").strip().lower()
                if another == 'yes':
                    break
                elif another == 'no':
                    print("Exiting Password Generator. Goodbye!")
                    return
                else:
                    print("Invalid input! Please enter 'yes' or 'no'.")
        
        except ValueError:
            print("Invalid input! Please enter a valid integer for password length.")

if __name__ == "__main__":
    main()
How to Use:
1.	Run the Script: Save this code to a file (e.g., password_generator.py) and execute it using Python (python password_generator.py).
2.	Generate Password:
o	Enter the desired length of the password when prompted (must be at least 6 characters).
o	The program will generate a random password consisting of uppercase letters, lowercase letters, digits, and punctuation characters.
o	The generated password will be displayed on the screen.
o	You can choose to generate another password or exit the program.


