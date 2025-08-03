# 🛠 1️⃣ Create User Groups in Active Directory
We’ll create 3 groups:
Managers
Employees
IT_Admin

Commands in Server Core:

## powershell

# Open Active Directory Users and Computers
dsa.msc  # (If GUI)
# OR PowerShell (Server Core)
New-ADGroup -Name "Managers" -GroupScope Global
New-ADGroup -Name "Employees" -GroupScope Global
New-ADGroup -Name "IT_Admin" -GroupScope Global

# 2️⃣ Create Test User Accounts
## powershell

--> New-ADUser -Name "Manager1" -AccountPassword (ConvertTo-SecureString "Pass@123" -AsPlainText -Force) -Enabled $true
Add-ADGroupMember -Identity "Managers" -Members "Manager1"

--> New-ADUser -Name "Employee1" -AccountPassword (ConvertTo-SecureString "Pass@123" -AsPlainText -Force) -Enabled $true
Add-ADGroupMember -Identity "Employees" -Members "Employee1"

--> New-ADUser -Name "Admin1" -AccountPassword (ConvertTo-SecureString "Pass@123" -AsPlainText -Force) -Enabled $true
Add-ADGroupMember -Identity "IT_Admin" -Members "Admin1"

# 3️⃣ Create the Shared Folder
powershell
mkdir "D:\CompanyData"

# 4️⃣ Set Share Permissions
We allow Everyone for now, but control access using NTFS permissions later.

powershell
net share CompanyData="D:\CompanyData" /grant:Everyone,full

# 5️⃣ Set NTFS Permissions (More Secure)
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

----> 📌 Project Task for You
Project Name: Company File Server with Role-Based Access

# commands in windows powershell

"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 043800.png"
"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 043821.png"

# commands in windows powershell run administartor

"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 043958.png"
"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 044011.png"
"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 044028.png"
"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 044048.png"
"C:\Users\Administrator\Pictures\Screenshots\Screenshot 2025-08-03 044111.png"
