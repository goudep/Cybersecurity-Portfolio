# **Phishing Alert Investigation Report | 网络钓鱼警报调查报告**

## **1. Scenario Overview | 场景概述**

As a Level-1 SOC analyst at a financial services company, you received a phishing alert regarding a suspicious file downloaded on an employee’s computer. After investigating the file's hash, it has been verified as malicious. Following the organization's security policy, you will complete the investigation and resolve the alert based on the phishing incident response playbook.

作为金融服务公司的一级 SOC 分析员，你收到了一条关于员工计算机下载可疑文件的网络钓鱼警报。在调查该文件的哈希值后，已确认其为恶意文件。根据公司的安全政策，你需要按照网络钓鱼事件响应手册完成调查并解决警报。

---

## **2. Alert Ticket Details | 警报工单详情**

| **Ticket ID** | **A-2703** |
|-------------|------------|
| **Alert Message | 警报信息** | Phishing attempt - possible malware download | 网络钓鱼尝试 - 可能下载了恶意软件 |
| **Severity | 严重性** | Medium | 中等 |
| **Status | 状态** | Investigating | 调查中 |
| **Known Malicious File Hash | 已知恶意文件哈希** | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` |
| **Sender Details | 发送者信息** | Def Communications `<76tguyhh6tgftrt7tg.su>` (`114.114.114.114`) |
| **Receiver Details | 接收者信息** | HR at Inergy `<hr@inergy.com>` (`176.157.125.93`) |
| **Email Subject | 邮件主题** | Re: Infrastructure Engineer role |
| **Email Attachment | 邮件附件** | `bfsvc.exe` (Password-protected: `paradise10789`) |

---

## **3. Incident Timeline | 事件时间线**

| **Time 时间** | **Event 事件** |
|----------|-----------|
| **1:11 PM** | Employee received a phishing email with an attachment. | 员工收到带有附件的网络钓鱼邮件。 |
| **1:13 PM** | Employee downloaded and opened the attachment. | 员工下载并打开了附件。 |
| **1:15 PM** | Unauthorized executable files were created on the system. | 未经授权的可执行文件在系统中被创建。 |
| **1:20 PM** | IDS detected the malicious activity and sent an alert. | 入侵检测系统（IDS）检测到恶意活动并发送警报。 |

---

## **4. Investigation and Findings | 调查结果**

### **4.1 Evaluating the Alert | 评估警报**

Using the **Phishing Incident Response Playbook**, we evaluated the following details:

- **Alert Severity:** Medium (May require escalation)
- **Sender Email & IP Mismatch:** The email address (`76tguyhh6tgftrt7tg.su`) does not match the sender’s supposed identity.
- **Message Content:** Contains grammatical errors and requests the recipient to open a password-protected attachment.
- **Attachment:** The attached file (`bfsvc.exe`) is an executable file, which is highly suspicious.
- **VirusTotal Results:** The SHA256 hash of the file is marked as malicious by multiple security vendors.

**Conclusion:** The phishing attempt is legitimate, and the alert should be escalated.

### **4.2 Indicators of Compromise (IoCs) Identified | 确定的入侵指标**

From the VirusTotal analysis, the following **Indicators of Compromise (IoCs)** were identified:

| **IoC Type 类型**  | **Details 详细信息** |
|------------|------------|
| **Hash Value | 哈希值** | `54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b` |
| **IP Address | IP 地址** | `185.220.101.42` (Malicious) |
| **Domain Name | 域名** | `hxxp://malware-distribution.com` (Flagged as phishing/malware site) |
| **Host Artifact | 主机工件** | Created file: `C:\Users\Public\svchost.exe` |
| **Tactics, Techniques, and Procedures (TTPs) | 攻击策略、技术与程序** | MITRE ATT&CK TTPs: Phishing (T1566), Execution via Scripting (T1059) |

---

## **5. Resolution and Next Steps | 解决方案与后续步骤**

### **5.1 Immediate Actions | 立即采取的行动**
1. **Escalate the incident to Level-2 SOC Analysts.**
   **将事件升级至二级 SOC 分析师。**
2. **Block the identified malicious IP (`185.220.101.42`) and domain (`hxxp://malware-distribution.com`).**
   **在网络防火墙中屏蔽恶意 IP 和域名。**
3. **Isolate the affected employee's device for further forensic analysis.**
   **隔离受感染的设备，以进行进一步的取证分析。**
4. **Remove the malicious file (`C:\Users\Public\svchost.exe`) and check for persistence mechanisms.**
   **删除恶意文件，并检查是否有持久化机制。**

### **5.2 Long-term Security Measures | 长期安全措施**
1. **Strengthen Email Filtering**: Implement stricter email security rules to block phishing attempts.
   **加强电子邮件过滤规则，以阻止网络钓鱼攻击。**
2. **Conduct Employee Awareness Training**: Educate employees on phishing threats and safe email practices.
   **对员工进行网络钓鱼安全培训，提高安全意识。**
3. **Enable Endpoint Detection and Response (EDR) Monitoring**: Ensure continuous monitoring of suspicious activities.
   **启用终端检测与响应（EDR）系统，实现持续监控。**

---

## **6. Final Ticket Update | 最终工单更新**

| **Ticket Status 工单状态** | **Escalated 已升级** |
|-----------------|-----------------|
| **Ticket Comments | 工单备注** | A phishing email containing a malicious attachment was detected and verified. VirusTotal analysis confirmed the file as malware, with associated IoCs including malicious IP, domain, and host artifacts. The alert has been escalated to Level-2 SOC analysts for further investigation. | 发现并确认了一封带有恶意附件的网络钓鱼邮件。VirusTotal 分析确认该文件为恶意软件，相关 IoCs 包括恶意 IP、域名及主机工件。已将警报升级至二级 SOC 分析师进行进一步调查。 |

---

**🔎 Report Generated By: [Your Name] | SOC Level 1 Analyst**  
**📅 Date: [YYYY-MM-DD]**

