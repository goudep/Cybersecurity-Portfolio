# Linux File Permissions Management Project

## **Project Description | 项目描述**
As a security professional, managing file permissions is crucial to maintaining system security. This project demonstrates the use of Linux commands to examine and modify file permissions following the Principle of Least Privilege. The document outlines command usage, permission analysis, and modifications needed to secure files and directories.

作为一名安全专业人士，管理文件权限对于系统安全至关重要。本项目展示了如何使用 Linux 命令检查和修改文件权限，并遵循最小权限原则。本文档概述了命令使用方式、权限分析及所需的安全修改措施。

---

## **1. Checking File and Directory Permissions | 检查文件和目录权限**

To list file permissions, including hidden files, use the command:
查看包括隐藏文件在内的文件权限，使用以下命令：

```bash
ls -la /home/research_team/projects
```

This command outputs permission details in a 10-character string format.
该命令以 10 字符串格式输出文件权限详情。

---

## **2. Interpreting File Permission String | 解析文件权限字符串**
Example output:
示例输出：

```bash
-rw-rw----  1 researcher2 hr 2048 Mar 3 12:00 bonuses.txt
```

Explanation:
说明：
- `-rw-rw----` → Regular file with read/write permissions for owner and group, but no access for others.
- `researcher2` → File owner.
- `hr` → Group owner.

---

## **3. Modifying File Permissions | 修改文件权限**
The company policy does not allow others to have write access. Use the following command to revoke write permissions for others:

公司规定不允许其他用户具有写权限，因此使用以下命令取消其权限：

```bash
chmod o-w bonuses.txt
```

---

## **4. Changing Hidden File Permissions | 修改隐藏文件权限**
The `.project_x.txt` file should not have write permissions for anyone but should be readable by the owner and group:

`.project_x.txt` 文件不应具有任何写权限，但用户和组应能读取该文件：

```bash
chmod u=r,g=r,o= .project_x.txt
```

---

## **5. Restricting Access to Directories | 限制目录访问权限**
Only `researcher2` should access the `drafts` directory:

仅 `researcher2` 应被允许访问 `drafts` 目录：

```bash
chmod 700 /home/research_team/drafts
```

---

## **Summary | 摘要**
This project involved checking and modifying file permissions using Linux commands. We ensured compliance with the **Principle of Least Privilege**, revoked unnecessary write permissions, and secured sensitive files and directories. Mastering these Linux commands is essential for cybersecurity professionals to maintain system security.

本项目涉及使用 Linux 命令检查和修改文件权限。我们确保遵循 **最小权限原则**，移除不必要的写权限，并安全管理机密文件和目录。熟练掌握这些 Linux 命令对系统安全专业人士至关重要。
