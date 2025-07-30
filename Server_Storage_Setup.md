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
![HR Partition](images/hr_partition.png)
![Accounts Partition](images/accountsdb.png)
![IT Partition](images/it_storage.png)

# The final disk management storage allocated:
![Final Volume List](images/final_volume_list.png)

