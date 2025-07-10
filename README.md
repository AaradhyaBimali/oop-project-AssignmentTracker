#include <iostream>
#include <vector>
#include <string>
#include <thread>
#include <chrono>
using namespace std;

// Assignment Class
class Assignment {
public:
    string title;
    string dueDate;

    Assignment(string t, string d) : title(t), dueDate(d) {}

    void display() {
        cout << "📚 " << title << " (Due: " << dueDate << ")\n";
    }
};

// Study Timer Function
void studyTimer(int minutes) {
    cout << "⏳ Starting " << minutes << "-minute study session...\n";
    for (int i = minutes; i > 0; --i) {
        cout << "⏱️ " << i << " minute(s) left...\n";
        this_thread::sleep_for(chrono::seconds(1)); // use 1 second per minute for demo
    }
    cout << "✅ Study session completed!\n";
}

// Dashboard display
void showDashboard() {
    cout << "\n🗓️ Daily Schedule:\n";
    cout << " - 6:00 AM : Wake Up\n";
    cout << " - 7:00 AM : Study\n";
    cout << " - 10:00 AM : Break\n";
    cout << " - 2:00 PM : Assignment Work\n";
    cout << " - 9:00 PM : Review Day\n";
}

int main() {
    vector<Assignment> assignments;
    int choice;

    while (true) {
        cout << "\n📘 STUDY APP MENU 📘\n";
        cout << "1. Add Assignment\n2. View Assignments\n3. Show Schedule\n4. Start Study Timer\n0. Exit\nChoose: ";
        cin >> choice;
        cin.ignore();

        if (choice == 1) {
            string title, due;
            cout << "Enter assignment title: ";
            getline(cin, title);
            cout << "Enter due date: ";
            getline(cin, due);
            assignments.emplace_back(title, due);
            cout << "✅ Assignment added!\n";
        }
        else if (choice == 2) {
            cout << "\n📋 Your Assignments:\n";
            for (auto& a : assignments) a.display();
        }
        else if (choice == 3) showDashboard();
        else if (choice == 4) {
            int mins;
            cout << "Enter study time (minutes): ";
            cin >> mins;
            studyTimer(mins);
        }
        else if (choice == 0) break;
        else cout << "❌ Invalid choice!\n";
    }

    return 0;
}


