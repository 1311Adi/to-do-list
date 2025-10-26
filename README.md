FILENAME = "tasks.txt"
def load_tasks():
    try:
        with open(FILENAME, 'r') as file:
            tasks = [line.strip() for line in file.readlines()]
    except FileNotFoundError:
            tasks = []
    return tasks
def save_tasks(tasks):
     with open(FILENAME,'w')as file:
          for task in tasks:
               file.write(task + "\n")
def view_tasks(tasks):
     print("--- To do list ---")
     if not tasks:
          print("To do list is empty!")
     else:
          for i, task in enumerate(tasks,1):
               print(f"{i}. {task}")
          print("---------------------\n")
def add_task(tasks):
     task = input("Enter the new task: ")
     tasks.append(task)
     save_tasks(tasks)
     print(f"Task '{task}' added successfully!")
def delete_task(tasks):
     view_tasks(tasks)
     try:
          task_num = int(input("Enter the numer of tasks to delete: "))
          if 1 <= task_num <= len(tasks):
               removed_task = tasks.pop(task_num - 1)
               save_tasks(tasks)
               print(f"Task '{removed_task}' has been deleted!")
          else:
               print("INVALID TASK NUMBER")
     except ValueError:
          print("Invalid input. Please enter a number!")
tasks = load_tasks()
while True:
     print("To-Do list Menu:")
     print("1. View tasks")
     print("2. Add task")
     print("3. Delete task")
     print("4. Exit")
     choice = input("Enter ypur choice (1 to 4): ")
     if choice == '1':
          view_tasks(tasks)
     elif choice == '2':
          add_task(tasks)
     elif choice == '3':
          delete_task(tasks)
     elif choice == '4':
          print("Exiting!")
          break
     else:
          print("Invalid choice!")
