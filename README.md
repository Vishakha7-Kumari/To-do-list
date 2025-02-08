# To-do-list
#include <iostream>
#include <vector>
#include <string>

using namespace std;

class TodoList {
private:
    vector<string> tasks;

public:
    // Function to add a task
    void addTask(const string& task) {
        tasks.push_back(task);
        cout << "Task added!" << endl;
    }

    // Function to view all tasks
    void viewTasks() {
        if (tasks.empty()) {
            cout << "No tasks available!" << endl;
            return;
        }
        cout << "\nYour To-Do List:" << endl;
        for (int i = 0; i < tasks.size(); ++i) {
            cout << i + 1 << ". " << tasks[i] << endl;
        }
    }

    // Function to delete a task
    void deleteTask(int index) {
        if (index < 1 || index > tasks.size()) {
            cout << "Invalid task number!" << endl;
        } else {
            tasks.erase(tasks.begin() + index - 1);
            cout << "Task deleted!" << endl;
        }
    }

    // Function to clear all tasks
    void clearAllTasks() {
        tasks.clear();
        cout << "All tasks cleared!" << endl;
    }
};

int main() {
    TodoList todoList;
    int choice;
    string task;

    do {
        cout << "\nTo-Do List Menu" << endl;
        cout << "1. Add Task" << endl;
        cout << "2. View Tasks" << endl;
        cout << "3. Delete Task" << endl;
        cout << "4. Clear All Tasks" << endl;
        cout << "5. Exit" << endl;
        cout << "Enter your choice: ";
        cin >> choice;
        cin.ignore();  // To ignore the newline character left in the buffer

        switch (choice) {
            case 1:
                cout << "Enter task: ";
                getline(cin, task);
                todoList.addTask(task);
                break;
            case 2:
                todoList.viewTasks();
                break;
            case 3:
                int taskNumber;
                cout << "Enter the task number to delete: ";
                cin >> taskNumber;
                todoList.deleteTask(taskNumber);
                break;
            case 4:
                todoList.clearAllTasks();
                break;
            case 5:
                cout << "Goodbye!" << endl;
                break;
            default:
                cout << "Invalid choice! Please try again." << endl;
        }
    } while (choice != 5);

    return 0;
}
