print("HOSPITAL APPOINTMENT SYSTEM")
name = input("Enter patient name: ")

requested = ["Cardiology", "Neurology", "Cardiology"]
available = ["Cardiology", "Neurology", "Dermatology", "Pediatrics"]
visited = ["Dermatology"]
preferred_doctors = ["Dr. Khan", "Dr. Sharma"]
available_doctors = ["Dr. Sharma", "Dr. Reddy"]
emergency = ["Cardiology", "Emergency"]

req = set(requested)
avail = set(available)
visit = set(visited)
emer = set(emergency)

common = req & avail
unavailable = req - avail

previous = req & visit
urgent = req & emer
duplicates = []
for d in requested:
    if requested.count(d) > 1 and d not in duplicates:
        duplicates.append(d)
if urgent:
    recommended = list(urgent)[0]
elif common:
    recommended = list(common)[0]
else:
    recommended = "No department available"
if common:
    status = "Appointment can be booked"
else:
    status = "Appointment cannot be booked"
doctors = set(preferred_doctors) & set(available_doctors)
first_department = requested[0]       
first_two = requested[:2]             

requested.append("ENT")              
requested.remove("ENT")
all_departments = req | avail
if "Cardiology" in avail:
    cardiology = "Available"
else:
    cardiology = "Not Available"

print("\n----- FINAL APPOINTMENT REPORT -----")
print("Patient Name:", name)
print("Requested Departments:", requested)
print("Available Departments:", common)
print("Unavailable Departments:", unavailable)
print("Duplicate Requests:", duplicates)
print("Previously Visited:", previous)
print("Emergency Departments:", urgent)
print("Recommended Department:", recommended)
print("Available Preferred Doctors:", doctors)
print("Cardiology:", cardiology)
print("Appointment Status:", status)


