# **Parking Lot USB Exercise Report | 停车场 USB 设备安全分析报告**

## **Contents | USB 设备内容**
![这是图片]("C:\Users\yudim\Downloads\USB_Baiting.jpg" "USB_Baiting")

The USB drive contains a mix of **personal and work-related files**, including **family and pet photos, a new hire letter, an employee shift schedule, and budget documents**. Some of these documents may contain **personally identifiable information (PII)**, such as employee names, contact details, and financial data. Storing personal and work files together on a USB drive is a **security risk**, as it increases the likelihood of unauthorized access and data leakage.

USB 设备包含**个人和工作相关的文件**，例如**家庭和宠物照片、新员工录用信、员工班次安排表和预算文件**。其中一些文件可能包含**个人身份信息（PII）**，如员工姓名、联系方式和财务数据。将个人和工作文件存储在同一 USB 设备中是**安全风险**，因为这增加了**未经授权访问和数据泄露**的可能性。

---

## **Attacker Mindset | 攻击者视角分析**
An attacker could **exploit the contents of the USB drive** in multiple ways. For example, if the attacker gains access to **employee schedules**, they could target hospital staff through **social engineering attacks**. Additionally, if the new hire letter contains **employee credentials**, an attacker could attempt **phishing or impersonation** attacks. This USB drive could also be a **baiting attack**, intentionally left behind to trick an unsuspecting employee into **plugging it into a company workstation**, potentially **installing malware** on the hospital's network.

攻击者可以利用 USB 设备中的信息进行**多种攻击**。例如，如果攻击者获取了**员工班次安排**，他们可能会利用**社会工程攻击**针对医院员工。此外，如果新员工录用信包含**员工凭据**，攻击者可能会尝试**钓鱼攻击或身份冒充**。该 USB 设备还可能是一次**诱骗式攻击（Baiting Attack）**，故意被遗留在停车场，以引诱毫无戒心的员工将其插入公司计算机，从而在医院网络中**植入恶意软件**。

---

## **Risk Analysis | 风险分析**
USB baiting attacks can introduce **various forms of malware**, including **keyloggers, ransomware, or remote access trojans (RATs)**. If an infected USB were connected to a workstation, it could lead to **data breaches, network infiltration, or system compromise**. Sensitive files containing **PII and financial data** could be stolen and used for **identity theft, financial fraud, or corporate espionage**. 

USB 诱骗攻击可能会传播**各种恶意软件**，包括**键盘记录程序（Keylogger）、勒索软件（Ransomware）或远程访问木马（RAT）**。如果受感染的 USB 设备被连接到计算机，可能会导致**数据泄露、网络渗透或系统受控**。包含**个人身份信息（PII）和财务数据**的敏感文件可能被窃取，并被用于**身份盗窃、金融欺诈或商业间谍活动**。

### **Mitigation Strategies | 缓解策略**
To **mitigate these risks**, organizations should:
1. **Implement USB security policies**, including **blocking unauthorized USB devices** on company computers.
2. **Educate employees** about the dangers of plugging in unknown USB drives.
3. **Use virtualization software** to safely inspect external storage devices before allowing access.
4. **Enforce encryption and secure storage practices** to protect work-related data.

为了**降低这些风险**，企业应采取以下安全措施：
1. **实施 USB 设备安全策略**，包括**禁止在公司计算机上使用未经授权的 USB 设备**。
2. **对员工进行安全教育**，让他们了解插入未知 USB 设备的危险性。
3. **使用虚拟化软件**，在允许访问 USB 设备之前进行安全检查。
4. **执行数据加密和安全存储策略**，以保护工作相关数据。

By following these security controls, the hospital can reduce the risk of **USB-related cyber threats** and **protect sensitive information** from unauthorized access.

通过实施这些安全控制，医院可以降低**与 USB 相关的网络安全威胁**，并**防止敏感信息被未经授权的访问**。

---

