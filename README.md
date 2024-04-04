import os

TODO_FILE = "todo_list.txt"

def load_tasks():
    tasks = []
    if os.path.exists(TODO_FILE):
        with open(TODO_FILE, "r") as file:
            tasks = [task.strip() for task in file.readlines()]
    return tasks

def save_tasks(tasks):
    with open(TODO_FILE, "w") as file:
        for task in tasks:
            file.write(task + "\n")

def add_task(task):
    tasks = load_tasks()
    tasks.append(task)
    save_tasks(tasks)
    print("Задача добавлена.")

def remove_task(task_index):
    tasks = load_tasks()
    if task_index < 1 or task_index > len(tasks):
        print("Неверный номер задачи.")
        return
    removed_task = tasks.pop(task_index - 1)
    save_tasks(tasks)
    print(f"Задача '{removed_task}' удалена.")

def show_tasks():
    tasks = load_tasks()
    if not tasks:
        print("Список задач пуст.")
    else:
        print("Список задач:")
        for index, task in enumerate(tasks, start=1):
            print(f"{index}. {task}")

while True:
    print("\nМеню:")
    print("1. Добавить задачу")
    print("2. Удалить задачу")
    print("3. Показать все задачи")
    print("4. Выйти")
    
    choice = input("Выберите действие: ")

    if choice == "1":
        task = input("Введите новую задачу: ")
        add_task(task)
    elif choice == "2":
        task_index = int(input("Введите номер задачи для удаления: "))
        remove_task(task_index)
    elif choice == "3":
        show_tasks()
    elif choice == "4":
        break
    else:
        print("Неверный ввод. Попробуйте снова.")
