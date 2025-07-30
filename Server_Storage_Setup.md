# 💻 Mini Project: Server Storage Setup for Departmental Drives

## 🎯 Objective
Create separate partitions for three departments — HR, Accounts, and IT — on Windows Server 2022 Core.

## 📋 Partition Setup

| Department | Drive Letter | Volume Label | Size |
|------------|--------------|--------------|------|
| HR         | H:           | HR_Data      | 5 GB |
| Accounts   | A:           | AccountsDB   | 10 GB |
| IT         | I:           | IT_Storage   | 8 GB |

## 🛠️ Commands Used

```cmd
diskpart
select disk 0

create partition primary size=5120
format fs=ntfs label=HR_Data quick
assign letter=H

create partition primary size=10240
format fs=ntfs label=AccountsDB quick
assign letter=A

create partition primary size=8192
format fs=ntfs label=IT_Storage quick
assign letter=I

list volume
exit

'''

<img width="960" height="1020" alt="image" src="https://github.com/user-attachments/assets/cb0230ea-af99-4af9-870b-fa7c0003b73b" />

<img width="960" height="1020" alt="image" src="https://github.com/user-attachments/assets/ca548986-c916-4dfb-b1b5-053d041fca5f" />

<img width="960" height="1020" alt="image" src="https://github.com/user-attachments/assets/55592def-594c-4a38-8571-f485b7eb3b19" />


#  The project was successfully completed

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/fdc5ad96-1d4f-4f9f-a0f0-c1100aca621b" />

