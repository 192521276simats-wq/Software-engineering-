# Scrum Management System

product_backlog = [
    {"id": 1, "task": "User Login", "priority": 1, "status": "Pending"},
    {"id": 2, "task": "Doctor Registration", "priority": 2, "status": "Pending"},
    {"id": 3, "task": "Appointment Booking", "priority": 3, "status": "Pending"},
    {"id": 4, "task": "Video Consultation", "priority": 4, "status": "Pending"},
    {"id": 5, "task": "Online Payment", "priority": 5, "status": "Pending"}
]

sprint_backlog = []

def display_backlog():
    print("\n========== PRODUCT BACKLOG ==========")
    for task in product_backlog:
        print(f"ID: {task['id']} | Task: {task['task']} | Priority: {task['priority']} | Status: {task['status']}")

def create_sprint():
    sprint_backlog.clear()
    print("\nCreating Sprint...")
    for task in product_backlog:
        if task["status"] == "Pending" and len(sprint_backlog) < 3:
            sprint_backlog.append(task)
    print("Sprint created successfully.")

def display_sprint():
    print("\n========== SPRINT BACKLOG ==========")
    for task in sprint_backlog:
        print(f"ID: {task['id']} | Task: {task['task']} | Status: {task['status']}")

def complete_task():
    task_id = int(input("Enter Task ID to mark as Completed: "))
    found = False

    for task in sprint_backlog:
        if task["id"] == task_id:
            task["status"] = "Completed"
            found = True
            print("Task completed successfully.")

    if not found:
        print("Task not found in Sprint.")

def retrospective():
    print("\n========== SPRINT RETROSPECTIVE ==========")
    completed = 0
    pending = 0

    for task in sprint_backlog:
        if task["status"] == "Completed":
            completed += 1
        else:
            pending += 1

    print("Completed Tasks :", completed)
    print("Pending Tasks   :", pending)

    print("\nSuggestions:")
    print("- Improve backlog refinement.")
    print("- Avoid changing requirements during sprint.")
    print("- Increase communication among team members.")
    print("- Conduct daily stand-up meetings.")

while True:
    print("\n====== SCRUM MANAGEMENT SYSTEM ======")
    print("1. View Product Backlog")
    print("2. Create Sprint")
    print("3. View Sprint Backlog")
    print("4. Complete Task")
    print("5. Sprint Retrospective")
    print("6. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        display_backlog()

    elif choice == "2":
        create_sprint()

    elif choice == "3":
        display_sprint()

    elif choice == "4":
        complete_task()

    elif choice == "5":
        retrospective()

    elif choice == "6":
        print("Project Completed Successfully.")
        break

    else:
        print("Invalid Choice. Please try again.")
