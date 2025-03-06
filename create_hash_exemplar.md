# **Exemplar: Create Hash Values | 示例：创建哈希值**  

## **Activity Overview | 活动概述**  
As a security analyst, you’ll need to implement security controls to protect organizations against a range of threats.  
作为安全分析师，你需要实施安全控制措施，以保护组织免受各种威胁。  

That’s where hashing comes in. Previously, you learned that a hash function is an algorithm that produces a code that can’t be decrypted.  
这就是哈希（Hashing）的作用。你之前学习过，哈希函数是一种生成**不可逆代码**的算法。  

Hash functions are used to uniquely identify the contents of a file so that you can check whether it has been modified.  
哈希函数用于**唯一标识文件内容**，以便检查文件是否被篡改。  

For example, a malicious program may mimic an original program. If one code line is different from the original program, it produces a different hash value.  
例如，一个恶意程序可能伪装成原始程序。如果代码有任何改动，它会生成一个不同的哈希值。  

Many tools are available to compare hashes for various scenarios. But for a security analyst, it’s important to know how to manually compare hashes.  
虽然有许多工具可以比较哈希值，但作为安全分析师，你需要掌握**手动比较哈希值**的方法。  

---  

## **Scenario | 场景**  
In this scenario, you need to investigate whether two files are identical or different.  
在此场景中，你需要检查两个文件是否相同或存在差异。  

### **Steps to complete this task | 任务完成步骤**  
1. Display the contents of two files and generate hashes for each.  
   **显示两个文件的内容，并生成各自的哈希值。**  
2. Examine the hashes and compare them.  
   **检查哈希值，并比较它们的不同。**  

---  

## **Task 1: Generate Hashes for Files | 任务 1：生成文件的哈希值**  
### **Step 1: List files in the home directory | 步骤 1：列出 home 目录中的文件**  
Run the following command:  
```bash
ls
```
Expected output:  
```bash
file1.txt  file2.txt
```

### **Step 2: Display the file contents | 步骤 2：显示文件内容**  
Run the following commands:  
```bash
cat file1.txt
cat file2.txt
```
Expected output:  
```bash
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
X5O!P%@AP[4\PZX54(P^)7CC)7}$EICAR-STANDARD-ANTIVIRUS-TEST-FILE!$H+H*
```

**Do the contents of the two files appear identical? | 这两个文件的内容是否相同？**  
✅ **Yes, they appear identical. | 是的，它们看起来相同。**  

### **Step 3: Generate Hashes | 步骤 3：生成哈希值**  
Run the following commands:  
```bash
sha256sum file1.txt
sha256sum file2.txt
```
Expected output:  
```bash
131f95c51cc819465fa1797f6ccacf9d494aaaff46fa3eac73ae63ffbdfd8267  file1.txt
2558ba9a4cad1e69804ce03aa2a029526179a91a5e38cb723320e83af9ca017b  file2.txt
```

**Do both files produce the same hash value? | 这两个文件的哈希值是否相同？**  
❌ **No, the hashes are different, indicating that the files are different. | 不，哈希值不同，说明文件内容存在差异。**  

---  

## **Task 2: Compare Hashes | 任务 2：比较哈希值**  
### **Step 1: Store Hashes in Separate Files | 步骤 1：将哈希值存入文件**  
Run the following commands:  
```bash
sha256sum file1.txt >> file1hash
sha256sum file2.txt >> file2hash
```

### **Step 2: Display the Hashes | 步骤 2：显示存储的哈希值**  
Run the following commands:  
```bash
cat file1hash
cat file2hash
```

### **Step 3: Use cmp to Compare the Files | 步骤 3：使用 cmp 命令比较哈希文件**  
Run the following command:  
```bash
cmp file1hash file2hash
```
Expected output:  
```bash
file1hash file2hash differ: char1, line 1
```

**Based on the hash values, are file1.txt and file2.txt different? | 根据哈希值，file1.txt 和 file2.txt 是否不同？**  
✅ **Yes, the hash values are different, which confirms that the files are not identical. | 是的，哈希值不同，确认文件内容不同。**  

---  

## **Summary | 总结**  
✅ **You successfully created and compared hash values! | 你已成功创建并比较了哈希值！**  

This exercise demonstrated:  
- How to **generate hash values using sha256sum**.  
- How to **compare file contents using hash functions**.  
- How to **use cmp to check file differences**.  

本次练习演示了：  
- 如何使用 `sha256sum` **生成哈希值**。  
- 如何使用**哈希函数比较文件内容**。  
- 如何使用 `cmp` **检查文件差异**。  

🚀 **Now you understand how to create and analyze hash values in Linux! | 现在你掌握了在 Linux 中创建和分析哈希值的方法！**  
