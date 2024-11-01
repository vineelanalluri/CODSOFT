# To-Do List Application in Python

class ToDoList:
    def __init__(self):
        self.tasks = []  # Initialize an empty list to store tasks

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})
        print(f"Task '{task}' added.")

    def view_tasks(self):
        if not self.tasks:
            print("No tasks in your to-do list.")
            return
        for i, task in enumerate(self.tasks, start=1):
            status = "✓" if task["completed"] else "✗"
            print(f"{i}. {task['task']} [{status}]")

    def update_task(self, task_number, new_task):
        if 0 < task_number <= len(self.tasks):
            self.tasks[task_number - 1]["task"] = new_task
            print(f"Task {task_number} updated to '{new_task}'.")
        else:
            print("Invalid task number.")

    def mark_task_completed(self, task_number):
        if 0 < task_number <= len(self.tasks):
            self.tasks[task_number - 1]["completed"] = True
            print(f"Task {task_number} marked as completed.")
        else:
            print("Invalid task number.")

    def delete_task(self, task_number):
        if 0 < task_number <= len(self.tasks):
            removed_task = self.tasks.pop(task_number - 1)
            print(f"Task '{removed_task['task']}' deleted.")
        else:
            print("Invalid task number.")

# Main function to interact with the To-Do List
def main():
    todo_list = ToDoList()

    while True:
        print("\n--- To-Do List Menu ---")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Update Task")
        print("4. Mark Task as Completed")
        print("5. Delete Task")
        print("6. Exit")

        choice = input("Choose an option: ")

        if choice == "1":
            task = input("Enter the task: ")
            todo_list.add_task(task)

        elif choice == "2":
            todo_list.view_tasks()

        elif choice == "3":
            task_number = int(input("Enter task number to update: "))
            new_task = input("Enter the new task: ")
            todo_list.update_task(task_number, new_task)

        elif choice == "4":
            task_number = int(input("Enter task number to mark as completed: "))
            todo_list.mark_task_completed(task_number)

        elif choice == "5":
            task_number = int(input("Enter task number to delete: "))
            todo_list.delete_task(task_number)

        elif choice == "6":
            print("Exiting To-Do List Application.")
            break

        else:
            print("Invalid choice. Please select a valid option.")

if __name__ == "__main__":
    main()


# Simple Calculator with Basic Arithmetic Operations

def add(x, y):
    return x + y

def subtract(x, y):
    return x - y

def multiply(x, y):
    return x * y

def divide(x, y):
    if y == 0:
        return "Error! Division by zero."
    return x / y

def calculator():
    print("Select Operation:")
    print("1. Add")
    print("2. Subtract")
    print("3. Multiply")
    print("4. Divide")
    
    while True:
        try:
            choice = input("Enter choice (1/2/3/4): ")

            if choice not in ['1', '2', '3', '4']:
                print("Invalid input. Please enter a number between 1 and 4.")
                continue

            num1 = float(input("Enter first number: "))
            num2 = float(input("Enter second number: "))

            if choice == '1':
                print(f"Result: {num1} + {num2} = {add(num1, num2)}")
            elif choice == '2':
                print(f"Result: {num1} - {num2} = {subtract(num1, num2)}")
            elif choice == '3':
                print(f"Result: {num1} * {num2} = {multiply(num1, num2)}")
            elif choice == '4':
                print(f"Result: {num1} / {num2} = {divide(num1, num2)}")
            
            next_calc = input("Do you want to perform another calculation? (yes/no): ")
            if next_calc.lower() != 'yes':
                print("Exiting the calculator. Goodbye!")
                break
        except ValueError:
            print("Invalid input! Please enter numeric values.")

if __name__ == "__main__":
    calculator()
# Password Generator

import random
import string
def generate_password(length):
    # Define character set for the password
    characters = string.ascii_letters + string.digits + string.punctuation
    # Generate a random password using the specified length
    password = ''.join(random.choice(characters) for i in range(length))
    return password

# Prompt the user for the desired password length
length = int(input("Enter the desired password length: "))
# Generate and display the password
password = generate_password(length)
print("Generated Password:", password)
