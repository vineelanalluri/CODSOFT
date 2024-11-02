#Task 1  To-Do List Application in Python

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


# Task 2 :Simple Calculator with Basic Arithmetic Operations

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
# Task 3 : Password Generator

import random
import string
def generate_password(length):
    # Define character set for the password
    characters = string.ascii_letters + string.digits + string.punctuation
    # Generate a random password using the specified length
    password = ''.join(random.choice(characters) for i in range(length))
    return password
length = int(input("Enter the desired password length: "))
password = generate_password(length)
print("Generated Password:", password)

# Task 4 : Rock -Paper Scissorrs Game
import random
choices = ["rock", "paper", "scissors"]
user_score = 0
computer_score = 0

def determine_winner(user_choice, computer_choice):
    if user_choice == computer_choice:
        return "It's a tie!"
    elif (user_choice == "rock" and computer_choice == "scissors") or \
         (user_choice == "scissors" and computer_choice == "paper") or \
         (user_choice == "paper" and computer_choice == "rock"):
        return "You win!"
    else:
        return "Computer wins
while True
    user_choice = input("Enter rock, paper, or scissors (or 'quit' to stop playing): ").lower()
    if user_choice == 'quit':
        break
    if user_choice not in choices:
        print("Invalid choice. Please try again.")
        continue
    computer_choice = random.choice(choices)
    print(f"Computer chose: {computer_choice}")
    result = determine_winner(user_choice, computer_choice)
    print(result)
    if result == "You win!":
        user_score += 1
    elif result == "Computer wins!":
        computer_score += 1
    print(f"Scores - You: {user_score}, Computer: {computer_score}")
    play_again = input("Do you want to play again? (yes/no): ").lower()
    if play_again != "yes":
        break

print("Thanks for playing!")
print(f"Final Scores - You: {user_score}, Computer: {computer_score}")

#Task 5 : Contact book
class ContactBook:
    def __init__(self):
        self.contacts = {}
    def add_contact(self, name, phone, email, address):
        self.contacts[name] = {
            'phone': phone,
            'email': email,
            'address': address
        }
        print(f"Contact {name} added successfully.")
    def view_contacts(self):
        if not self.contacts:
            print("Contact list is empty.")
        else:
            for name, details in self.contacts.items():
                print(f"Name: {name}, Phone: {details['phone']}")

    def search_contact(self, search_term):
        results = {name: details for name, details in self.contacts.items() 
                   if search_term.lower() in name.lower() or search_term in details['phone']}
        if not results:
            print("No contacts found.")
        else:
            for name, details in results.items():
                print(f"Name: {name}, Phone: {details['phone']}, Email: {details['email']}, Address: {details['address']}")

    def update_contact(self, name, phone=None, email=None, address=None):
        if name in self.contacts:
            if phone:
                self.contacts[name]['phone'] = phone
            if email:
                self.contacts[name]['email'] = email
            if address:
                self.contacts[name]['address'] = address
            print(f"Contact {name} updated successfully.")
        else:
            print("Contact not found.")

    def delete_contact(self, name):
        if name in self.contacts:
            del self.contacts[name]
            print(f"Contact {name} deleted successfully.")
        else:
            print("Contact not found.")

def main():
    contact_book = ContactBook()

    while True:
        print("\n1. Add Contact\n2. View Contacts\n3. Search Contact\n4. Update Contact\n5. Delete Contact\n6. Exit")
        choice = input("Choose an option: ")

        if choice == '1':
            name = input("Enter name: ")
            phone = input("Enter phone number: ")
            email = input("Enter email: ")
            address = input("Enter address: ")
            contact_book.add_contact(name, phone, email, address)
        
        elif choice == '2':
            contact_book.view_contacts()
        
        elif choice == '3':
            search_term = input("Enter name or phone number to search: ")
            contact_book.search_contact(search_term)
        
        elif choice == '4':
            name = input("Enter the name of the contact to update: ")
            phone = input("Enter new phone number (or press Enter to skip): ")
            email = input("Enter new email (or press Enter to skip): ")
            address = input("Enter new address (or press Enter to skip): ")
            contact_book.update_contact(name, phone or None, email or None, address or None)
        
        elif choice == '5':
            name = input("Enter the name of the contact to delete: ")
            contact_book.delete_contact(name)
        
        elif choice == '6':
            print("Exiting Contact Book.")
            break
        
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()

