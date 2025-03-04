# **Linux User Management Project**

## **Project Description | 项目描述**
As a security professional, managing user accounts and file ownership is crucial for system security. This project demonstrates how to use Linux commands to add, modify, and remove users while ensuring proper authorization and access control. The document outlines command usage and best practices for secure user management.

作为一名安全专业人士，管理用户账户和文件所有权对于系统安全致关重要。本项目展示如何使用 Linux 命令添加、修改和删除用户，并确保适当的授权和访问控制。文档概述了命令使用方式和安全的最佳实践。

---

## **1. Adding a New User | 添加新用户**
To add a new user named `researcher9`, use the following command:
添加用户 `researcher9`，使用以下命令：

```bash
sudo useradd researcher9
```

To assign `researcher9` to the primary group `research_team`, use:
将 `researcher9` 分配为主群组 `research_team`，使用：

```bash
sudo usermod -g research_team researcher9
```

---

## **2. Assigning File Ownership | 指定文件所有权**
The `project_r.txt` file, located in `/home/researcher2/projects`, needs to be assigned to `researcher9`. The following command changes the ownership:

`project_r.txt` 文件位于 `/home/researcher2/projects`，需要设置为 `researcher9` 的所有文件：

```bash
sudo chown researcher9 /home/researcher2/projects/project_r.txt
```

---

## **3. Adding the User to a Secondary Group | 添加用户到辅助群组**
Later, `researcher9` was assigned additional responsibilities in the `sales_team`. To add `researcher9` to the `sales_team` as a secondary group:

后来，`researcher9` 负责 `sales_team`的工作，需要将其添加到 `sales_team`为辅助群组：

```bash
sudo usermod -a -G sales_team researcher9
```

📌 **Note**: Always use `-a -G` to append to existing groups without removing previous ones.
📌 **注意**：使用 `-a -G`，避免覆盖用户已经属于的群组。

---

## **4. Deleting a User | 删除用户**
After a year, `researcher9` left the organization. To remove them from the system:

一年后，`researcher9` 离开公司，需要从系统中删除：

```bash
sudo userdel researcher9
```

To clean up any remaining empty groups after user deletion:
删除用户后，删除其名称相同的群组：

```bash
sudo groupdel researcher9
```

---

## **Summary | 摘要**
This project involved adding, modifying, and deleting user accounts while ensuring correct file ownership and group assignments. We followed best practices in user management and access control. Mastering these Linux commands is essential for maintaining system security and managing user access efficiently.

本项目包括添加、修改和删除用户账户，并确保正确的文件所有权和群组分配。
