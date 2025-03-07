# **Task Report: Updating a File Through a **

## **Project Description**
As a security professional at a healthcare company, part of my role involves managing access to restricted patient records. Access to these records is controlled through an allow list of authorized IP addresses stored in `allow_list.txt`. To maintain security, a separate remove list identifies IPs that should be removed from the allow list.

This project involves creating a Python algorithm that reads the allow list, identifies and removes IP addresses found in the remove list, and updates the file accordingly. This automation enhances security by ensuring that only authorized personnel have access.

---

## **Step 1: Open the Allow List File**
### **Python Code:**
```python
import_file = "allow_list.txt"

# Open the allow list file in read mode
with open(import_file, "r") as file:
    ip_addresses = file.read()
```
### **Explanation:**
- `open(import_file, "r")` opens the file in read mode.
- The `with` statement ensures that the file is closed automatically after reading.
- `.read()` converts the file contents into a string, making it easier to process.

---

## **Step 2: Convert File Contents into a List**
### **Python Code:**
```python
ip_addresses = ip_addresses.split()  # Convert string into a list
```
### **Explanation:**
- `.split()` separates the string at each whitespace, converting it into a list of IP addresses.
- This allows for easy iteration and removal of specific IPs.

---

## **Step 3: Iterate Through the Remove List**
### **Python Code:**
```python
remove_list = ["192.168.1.10", "10.0.0.5"]  # Example IPs to remove

for ip in remove_list:
    if ip in ip_addresses:
        ip_addresses.remove(ip)  # Remove the IP if it exists in the allow list
```
### **Explanation:**
- The `for` loop iterates through the remove list.
- The `if` condition checks whether the IP exists in `ip_addresses`.
- `.remove(ip)` deletes the identified IP from the allow list.
- This approach works because `ip_addresses` does not contain duplicates.

---

## **Step 4: Update the File with the Revised Allow List**
### **Python Code:**
```python
updated_ips = "\n".join(ip_addresses)  # Convert list back to a string

# Write the updated list back to the file
with open(import_file, "w") as file:
    file.write(updated_ips)
```
### **Explanation:**
- `.join("\n")` ensures that each IP appears on a new line in the file.
- The file is reopened in write mode (`"w"`), which clears existing content.
- `.write(updated_ips)` writes the updated list of IPs to the file.

---

## **Summary**
This Python algorithm automates the process of maintaining a secure allow list for restricted network access. The main steps include:
1. **Reading the allow list file** using `open()` and `.read()`.
2. **Converting the contents into a list** using `.split()`.
3. **Iterating through the remove list** and removing matching IPs using `.remove()`.
4. **Updating the allow list file** by converting the modified list back to a string and writing it back.

By implementing this algorithm, the security team can efficiently manage user access without manual intervention, ensuring that unauthorized IP addresses are promptly removed from the allow list.

This project demonstrates a fundamental security automation technique that is essential in cybersecurity operations.

