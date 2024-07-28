def display_tasks(tasks):
    if not tasks:
        print("No tasks to display.")
        return

    for idx, (task, completed) in enumerate(tasks, start=1):
        status = "Completed" if completed else "Not Completed"
        print(f"{idx}. {task} - {status}")

def add_task(tasks):
    task = input("Enter the task: ")
    tasks.append((task, False))
    print("Task added.")

def mark_task_completed(tasks):
    display_tasks(tasks)
    try:
        task_num = int(input("Enter the task number to mark as completed: "))
        if 1 <= task_num <= len(tasks):
            task, _ = tasks[task_num - 1]
            tasks[task_num - 1] = (task, True)
            print("Task marked as completed.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def remove_task(tasks):
    display_tasks(tasks)
    try:
        task_num = int(input("Enter the task number to remove: "))
        if 1 <= task_num <= len(tasks):
            tasks.pop(task_num - 1)
            print("Task removed.")
        else:
            print("Invalid task number.")
    except ValueError:
        print("Invalid input. Please enter a number.")

def main():
    tasks = []
    while True:
        print("\nTask Manager")
        print("1. Display to-do list")
        print("2. Add a Task")
        print("3. Mark a task as Completed")
        print("4. Remove a task")
        print("5. Exit")
        
        choice = input("Choose an option: ")
        
        if choice == '1':
            display_tasks(tasks)
        elif choice == '2':
            add_task(tasks)
        elif choice == '3':
            mark_task_completed(tasks)
        elif choice == '4':
            remove_task(tasks)
        elif choice == '5':
            print("Exiting Task Manager.")
            break
        else:
            print("Invalid choice. Please choose a valid option.")

if __name__ == "__main__":
    main()
