# 🛠 1️⃣ Create User Groups in Active Directory
We’ll create 3 groups:
Managers
Employees
IT_Admin

Commands in Server Core:

## powershell

# Open Active Directory Users and Computers
```dsa.msc   (If GUI)

# OR PowerShell (Server Core)
```
New-ADGroup -Name "Managers" -GroupScope Global
New-ADGroup -Name "Employees" -GroupScope Global
New-ADGroup -Name "IT_Admin" -GroupScope Global

# 2️⃣ Create Test User Accounts
## powershell
'''
--> New-ADUser -Name "Manager1" -AccountPassword (ConvertTo-SecureString "Pass@123" -AsPlainText -Force) -Enabled $true
Add-ADGroupMember -Identity "Managers" -Members "Manager1"

--> New-ADUser -Name "Employee1" -AccountPassword (ConvertTo-SecureString "Pass@123" -AsPlainText -Force) -Enabled $true
Add-ADGroupMember -Identity "Employees" -Members "Employee1"

--> New-ADUser -Name "Admin1" -AccountPassword (ConvertTo-SecureString "Pass@123" -AsPlainText -Force) -Enabled $true
Add-ADGroupMember -Identity "IT_Admin" -Members "Admin1"

# 3️⃣ Create the Shared Folder
```
powershell
mkdir "D:\CompanyData"

# 4️⃣ Set Share Permissions
We allow Everyone for now, but control access using NTFS permissions later.
```
powershell
net share CompanyData="D:\CompanyData" /grant:Everyone,full

# 5️⃣ Set NTFS Permissions (More Secure)
```
powershell
# Give Managers Read/Write
icacls "D:\CompanyData" /grant "Managers:(OI)(CI)M"

# Give Employees Read-Only
icacls "D:\CompanyData" /grant "Employees:(OI)(CI)R"

# Give IT Admin Full Control
icacls "D:\CompanyData" /grant "IT_Admin:(OI)(CI)F"

Legend:
(OI) – Object Inherit (applies to files)
(CI) – Container Inherit (applies to folders)
R – Read
M – Modify
F – Full Control

# 6️⃣ Test the Setup
Log in as Manager1 → Try creating and editing files.
Log in as Employee1 → You should be able to open but not modify files.
Log in as Admin1 → Full control.

----> 📌 Project Task I complished

Project Name: Company File Server with Role-Based Access

# commands in windows powershell

<img width="1920" height="1020" alt="Screenshot 2025-08-03 043800" src="https://github.com/user-attachments/assets/92b49183-66ba-46e3-b495-1b1aab806ea4" />
<img width="1920" height="1020" alt="Screenshot 2025-08-03 043821" src="https://github.com/user-attachments/assets/aaa94f6f-b77d-48e6-845b-e1bb51fc800b" />

# commands in windows powershell run administartor

<img width="1468" height="1020" alt="Screenshot 2025-08-03 043958" src="https://github.com/user-attachments/assets/3c646883-1ee7-4ad3-99ac-17575dab3ea9" />
<img width="1468" height="1020" alt="Screenshot 2025-08-03 044011" src="https://github.com/user-attachments/assets/280e6073-2367-4135-8c87-a84d3ef6b7bb" />
<img width="1468" height="1020" alt="Screenshot 2025-08-03 044028" src="https://github.com/user-attachments/assets/c58b6eb0-558d-4e47-8e0c-4ea11de0f92e" />
<img width="1468" height="1020" alt="Screenshot 2025-08-03 044048" src="https://github.com/user-attachments/assets/73cfadc1-94dd-4175-96a9-bf81076bb55c" />
<img width="1468" height="1020" alt="Screenshot 2025-08-03 044111" src="https://github.com/user-attachments/assets/746e39ce-36ee-4aef-8802-93fa03877f98" />


