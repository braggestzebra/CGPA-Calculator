#include <iostream>
#include <string>
#include <unordered_map>
#include <vector>
using namespace std;

int main() {
    int numSubjects;
    cout << "Welcome to the CGPA calculator!" << endl;
    cout << "Enter the number of subjects: ";
    cin >> numSubjects;

    if (numSubjects <= 0) {
        cout << "Invalid number of subjects! Exiting program." << endl;
        return 1;
    }

    double totalGPA = 0.0;
    int totalSubjects = 0;

    // To store subject names and corresponding grades
    vector<pair<string, string>> subjectGrades;

    unordered_map<string, double> gradeToGPA = {
        {"A+", 4.0}, {"A", 3.7}, {"A-", 3.5},
        {"B+", 3.3}, {"B", 3.0}, {"B-", 2.7},
        {"C+", 2.5}, {"C", 2.0}, {"C-", 1.7},
        {"D+", 1.5}, {"D", 1.0}, {"D-", 0.7},
        {"F", 0.0}
    };

    for (int i = 1; i <= numSubjects; i++) {
        string subjectName, hgrade, alGrade;
        int totalMarks, obtainedMarks;
        double percent, GPA = 0.0;

        cout << "\nEnter the name of subject " << i << ": ";
        cin >> ws; // to clear any leftover newline character
        getline(cin, subjectName);

        cout << "Do you have the alphabet grade? (Yes/No): ";
        cin >> hgrade;

        // Normalize input for consistent Yes/No responses
        for (char &c : hgrade) c = tolower(c);

        if (hgrade == "yes" || hgrade == "y") {
            while (true) {
                cout << "Enter the letter grade (e.g., A+, A, A-, B+... etc.): ";
                cin >> alGrade;

                // Normalize grade input
                for (char &c : alGrade) c = toupper(c);

                if (gradeToGPA.find(alGrade) != gradeToGPA.end()) {
                    GPA = gradeToGPA[alGrade];
                    cout << "Your GPA based on the grade " << alGrade << " is: " << GPA << endl;
                    subjectGrades.push_back({subjectName, alGrade}); // Store subject and grade
                    break;  // Exit the loop when a valid grade is entered
                } else {
                    cout << "Invalid grade entered! Please try again." << endl;
                }
            }

        } else if (hgrade == "no" || hgrade == "n") {
            cout << "Enter total marks for the subject: ";
            cin >> totalMarks;
            cout << "Enter obtained marks: ";
            cin >> obtainedMarks;

            if (totalMarks <= 0) {
                cout << "Invalid total marks! Skipping this subject." << endl;
                continue;
            }

            percent = (static_cast<double>(obtainedMarks) / totalMarks) * 100;

            // Convert percentage to GPA
            if (percent >= 95) { GPA = 4.0; alGrade = "A+"; }
            else if (percent >= 90) { GPA = 3.7; alGrade = "A"; }
            else if (percent >= 85) { GPA = 3.5; alGrade = "A-"; }
            else if (percent >= 80) { GPA = 3.3; alGrade = "B+"; }
            else if (percent >= 75) { GPA = 3.0; alGrade = "B"; }
            else if (percent >= 70) { GPA = 2.7; alGrade = "B-"; }
            else if (percent >= 65) { GPA = 2.5; alGrade = "C+"; }
            else if (percent >= 60) { GPA = 2.0; alGrade = "C"; }
            else if (percent >= 55) { GPA = 1.7; alGrade = "C-"; }
            else if (percent >= 50) { GPA = 1.5; alGrade = "D+"; }
            else if (percent >= 45) { GPA = 1.0; alGrade = "D"; }
            else if (percent >= 40) { GPA = 0.7; alGrade = "D-"; }
            else { GPA = 0.0; alGrade = "F"; }

            cout << "You scored " << percent << "%, which corresponds to grade " << alGrade
                 << " and GPA " << GPA << "." << endl;
            subjectGrades.push_back({subjectName, alGrade}); // Store subject and grade
        } else {
            cout << "Invalid input! Please answer with 'Yes' or 'No'. Skipping this subject." << endl;
            continue;
        }

        totalGPA += GPA;
        totalSubjects++;
    }

    if (totalSubjects > 0) {
        double CGPA = totalGPA / totalSubjects;
        cout << "\nYour **Cumulative GPA (CGPA)** for the semester is: " << CGPA << endl;

        cout << "\nSubject-wise grades:" << endl;
        for (const auto &subjectGrade : subjectGrades) {
            cout << "- " << subjectGrade.first << ": " << subjectGrade.second << endl;
        }

        if (CGPA >= 3.75) {
            cout << "!!!!!! Congratulations !!!!!! You are on the Dean's List!" << endl;
        } else if (CGPA <= 1.9) {
            cout << "Academic suspension warning!" << endl;
            cout << "Make sure to improve your CGPA next semester." << endl;
        }
    } else {
        cout << "\nNo valid subjects entered. CGPA cannot be calculated." << endl;
    }

    return 0;
}
