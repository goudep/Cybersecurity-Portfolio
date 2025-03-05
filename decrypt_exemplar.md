# **Exemplar: Decrypt an Encrypted Message | 示例：解密加密消息**  

## **Activity Overview | 活动概述**  
Previously, you learned about cryptography and how encryption and decryption can be used to secure information online.  
你之前学习了密码学，以及如何使用加密和解密来保护在线信息。  

You were also introduced to the Caesar cipher, one of the earliest cryptographic algorithms used to protect people’s privacy.  
你还学习了凯撒密码（Caesar cipher），这是最早用于保护隐私的加密算法之一。  

As a security analyst, it’s important that you understand the role of encryption to secure data online and that you’re familiar with the right security controls to do so.  
作为安全分析师，理解加密在保护在线数据中的作用，并熟悉正确的安全控制措施至关重要。  

In this lab activity, you’ll be guided through some basic cryptographic activities using Linux commands to decrypt files and reveal hidden messages.  
在本实验活动中，你将使用 Linux 命令进行一些基本的密码学操作，以解密文件并揭示隐藏的信息。  

---  

## **Scenario | 场景**  
In this scenario, all of the files in your home directory have been encrypted. You’ll need to use Linux commands to break the Caesar cipher and decrypt the files so that you can read the hidden messages they contain.  
在此场景中，你的 home 目录中的所有文件都已加密。你需要使用 Linux 命令破解凯撒密码并解密文件，以读取其中包含的隐藏消息。  

### **Steps to complete this task | 任务完成步骤**  
1. Explore the contents of the home directory and read the contents of a file.  
   **浏览 home 目录的内容并读取文件内容。**  
2. Find a hidden file and decrypt the Caesar cipher it contains.  
   **找到一个隐藏文件并解密其中的凯撒密码。**  
3. Decrypt the encrypted data file to recover your data and reveal the hidden message.  
   **解密加密的数据文件，以恢复数据并揭示隐藏的信息。**  

---  

## **Task 1: Read the contents of a file | 任务 1：读取文件内容**  
### **Step 1: List files in the home directory | 步骤 1：列出 home 目录中的文件**  
Run the following command:  
```bash
ls /home/analyst
```
Expected output:  
```bash
Q1.encrypted  README.txt caesar
```
### **Step 2: Read the README.txt file | 步骤 2：读取 README.txt 文件**  
Run the following command:  
```bash
cat README.txt
```
Expected output:  
```bash
Hello,
All of your data has been encrypted. To recover your data, you will need to solve a cipher. To get started, look for a hidden file in the caesar subdirectory.
```
This indicates that a hidden file is located in the **caesar** directory.  
**这表明在 `caesar` 目录中有一个隐藏文件。**  

---  

## **Task 2: Find a hidden file | 任务 2：找到隐藏文件**  
### **Step 1: Change to the caesar subdirectory | 步骤 1：切换到 caesar 子目录**  
Run the following command:  
```bash
cd caesar
```  
### **Step 2: List all files, including hidden files | 步骤 2：列出所有文件，包括隐藏文件**  
Run the following command:  
```bash
ls -a
```
Expected output:  
```bash
.  ..  .leftShift3
```
Hidden files in Linux start with a period (`.`).  
**在 Linux 中，隐藏文件以 `.` 开头。**  

### **Step 3: Read the hidden file | 步骤 3：读取隐藏文件**  
Run the following command:  
```bash
cat .leftShift3
```
The message appears scrambled because it is encrypted using a **Caesar cipher**.  
**消息是加密的，需要解密凯撒密码。**  

### **Step 4: Decrypt the Caesar cipher | 步骤 4：解密凯撒密码**  
Run the following command:  
```bash
cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
```
Expected output:  
```bash
In order to recover your files you will need to enter the following command:

openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```
Now that you have the decryption command, return to your home directory:  
```bash
cd ~
```  

---  

## **Task 3: Decrypt a file | 任务 3：解密文件**  
### **Step 1: Decrypt the encrypted file | 步骤 1：解密加密文件**  
Run the command provided in the previous step:  
```bash
openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
```
This command:  
- Uses **AES-256-CBC** to decrypt the file.  
- **`-pbkdf2`** adds extra security.  
- **`-d`** indicates decryption mode.  
- **`-in` and `-out`** specify input and output files.  
- **`-k ettubrute`** provides the decryption key.  

### **Step 2: List the decrypted file | 步骤 2：列出解密后的文件**  
Run the following command:  
```bash
ls
```
Expected output:  
```bash
Q1.encrypted  README.txt  caesar  Q1.recovered
```
### **Step 3: Read the decrypted file | 步骤 3：读取解密文件**  
Run the following command:  
```bash
cat Q1.recovered
```

---  

## **Summary | 总结**  
✅ **You successfully decrypted the hidden message!**  
✅ **你已成功解密隐藏的消息！**  

This exercise demonstrated:  
- How to **navigate directories** and **list files** in Linux.  
- How to **find and decrypt a hidden file** encrypted with a **Caesar cipher**.  
- How to **use OpenSSL to decrypt an encrypted file** using **AES-256-CBC**.  

本次练习演示了：  
- 如何在 Linux 中**浏览目录并列出文件**。  
- 如何**找到并解密**使用**凯撒密码**加密的隐藏文件。  
- 如何使用 **OpenSSL** 进行 **AES-256-CBC** 解密。  

🚀 **Well done! Now you understand the basics of cryptographic decryption in Linux!**  
🚀 **干得好！现在你掌握了 Linux 中基本的密码学解密方法！**  
