# **Access Control Investigation Report | 访问控制调查报告**  

## **Scenario | 场景描述**  
You’re the first cybersecurity professional hired by a growing business. Recently, a deposit was made from the business to an unknown bank account. The finance manager denied making a mistake, and fortunately, the payment was stopped in time. The business owner has asked you to investigate the incident and recommend measures to prevent future occurrences.  
作为该公司首位网络安全专业人员，你被要求调查一起可疑的资金转账事件，并提出改进建议，以防止类似事件再次发生。  

Your investigation includes:  
1. **Reviewing the access log** to identify information about the user involved.  
2. **Identifying access control issues** that allowed the incident to occur.  
3. **Recommending security mitigations** to strengthen access control.  
你的调查包括：  
1. **查看访问日志** 以获取涉及用户的信息。  
2. **找出访问控制漏洞**，分析导致此次事件发生的原因。  
3. **提出改进建议**，加强访问控制，防止未来类似事件发生。  

---  

## **Step 1: Review the Event Log | 查看事件日志**  
**Findings | 调查发现**  
- **User involved**: `Legal\Administrator`  
- **Event timestamp**: `10/03/2023, 8:29:57 AM`  
- **Device used**: `Up2-NoGud`  
- **IP Address**: `152.207.255.255`  
- **Event Description**: Payroll transaction attempted to `FAUX_BANK`.  

📌 **Notes | 备注**  
1. The transaction was initiated using an `Administrator` account, which typically has high-level access.  
2. The login was made from `Up2-NoGud`, a potentially unauthorized or unmanaged computer.  

---  

## **Step 2: Identify Access Control Issues | 访问控制问题分析**  
**Findings | 问题发现**  
1. **Excessive Privileges**: The `Administrator` account had access to payroll transactions, which should be restricted.  
2. **Weak Device Management**: The transaction originated from a computer (`Up2-NoGud`) that may not belong to the finance team.  
3. **Lack of Activity Monitoring**: The payroll event wasn't flagged until after the transaction was processed.  

📌 **Access Control Issues | 访问控制漏洞**  
1. **The Administrator account had excessive permissions** beyond its intended function.  
2. **No restrictions on device usage**, allowing unauthorized computers to initiate financial transactions.  

---  

## **Step 3: Recommendations for Mitigation | 访问控制改进建议**  
### ✅ **1. Implement Role-Based Access Control (RBAC) | 采用基于角色的访问控制（RBAC）**  
- Restrict payroll access to authorized personnel only (e.g., finance department).  
- Limit **Administrator** account access to system-level functions, not financial transactions.  

### ✅ **2. Enforce Device Whitelisting | 启用设备白名单管理**  
- Allow payroll transactions **only from authorized company devices**.  
- Implement **endpoint security software** to monitor device compliance.  

### ✅ **3. Enable Real-Time Access Monitoring | 启用实时访问监控**  
- Set up **automated alerts** for suspicious login attempts or unusual transactions.  
- Require **MFA (Multi-Factor Authentication)** for payroll-related activities.  

### ✅ **4. Conduct Regular Access Audits | 定期进行访问权限审查**  
- Review all **Administrator account activities** weekly.  
- Disable inactive or unnecessary privileged accounts.  

---  

## **Conclusion | 结论**  
By implementing **RBAC, device whitelisting, real-time monitoring, and periodic audits**, the business can significantly reduce the likelihood of unauthorized payroll transactions. These security measures ensure that only the right personnel, using authorized devices, can perform financial operations.  

📌 **Key Takeaways | 关键要点**  
✅ **Restrict high-level account permissions** to prevent unauthorized access.  
✅ **Monitor login activities** to detect anomalies in real time.  
✅ **Strengthen device security** by enforcing whitelisting policies.  
✅ **Conduct regular audits** to ensure security policies remain effective.  

🚀 **Taking these steps will help enhance the company’s security posture and prevent future financial security incidents.**  
