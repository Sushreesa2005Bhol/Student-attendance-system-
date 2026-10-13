# Student-attendance-system-

students = set()
attendance = {}

def register_students():
    n = int(input("Enter number of students: "))

    for i in range(n):
        name = input("Enter student name: ").strip()
        if name:
            students.add(name)

    print("Students registered!")

def mark_attendance():
    attendance.clear()

    for name in sorted(students):
        status = input(name + " (P/A): ").upper()

        if status == "P":
            attendance[name] = "Present"
        else:
            attendance[name] = "Absent"

    print("Attendance marked!")

def show_summary():
    if not attendance:
        print("Mark attendance first!")
        return

    for name, status in attendance.items():
        print(name, "-", status)

    present = sum(1 for s in attendance.values()
                  if s == "Present")
    absent = len(attendance) - present

    print("Present:", present)
    print("Absent:", absent)

while True:
    print("\n1. Register Students")
    print("2. Mark Attendance")
    print("3. Attendance Summary")
    print("4. Exit")

    choice = input("Enter choice: ")

    if choice == "1":
        register_students()
    elif choice == "2":
        mark_attendance()
    elif choice == "3":
        show_summary()
    elif choice == "4":
        break
    else:
        print("Invalid choice!")
        
