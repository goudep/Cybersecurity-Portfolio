# **Exploring  | 使用 Suricata 探索签名**

## **1. Overview | 概述**
Previously, we explored packet analysis and the structure of intrusion detection system (IDS) signatures in Suricata. This document provides a step-by-step guide to using Suricata for custom rule creation, alert generation, and log analysis.

在之前的学习中，我们探讨了数据包分析以及 Suricata 入侵检测系统（IDS）签名的基本语法。本文件提供了一份详细的指南，介绍如何使用 Suricata 创建自定义规则、触发警报并分析日志。

---

## **2. Scenario | 场景**
As a security analyst, your task is to monitor traffic on your employer's network using Suricata. This involves:
1. Exploring **custom rules** in Suricata.
2. Running Suricata with a custom rule to trigger alerts and analyzing log outputs.
3. Examining log files such as **fast.log** and **eve.json** for further insights.

作为一名安全分析师，你的任务是使用 Suricata 监控公司网络流量，具体包括：
1. **研究 Suricata 的自定义规则**。
2. **运行 Suricata 以触发警报，并分析日志输出**。
3. **检查 fast.log 和 eve.json 日志文件，以深入了解警报详情**。

---

## **3. Files Used in This Lab | 本实验使用的文件**
| **File文件** | **Description 描述** |
|-----------|-------------|
| `sample.pcap` | A packet capture file containing example network traffic for testing Suricata rules. 一个包含示例网络流量的数据包捕获文件，用于测试 Suricata 规则。 |
| `custom.rules` | A file containing custom rules that define which traffic should be monitored and alerted on. 包含自定义规则的文件，定义需要监控和警报的流量。 |
| `fast.log` | Stores basic alert information such as source IP, destination IP, and protocol. 记录基本警报信息，如源 IP、目标 IP 和协议。 |
| `eve.json` | A detailed log file in JSON format, storing comprehensive event details for analysis.  详细记录事件的 JSON 格式日志文件，用于深入分析。 |

---

## **4. Step-by-Step Guide | 操作指南**

### **Task 1: Examine a Custom Rule | 任务 1：检查自定义规则**
1. Display the contents of the `custom.rules` file:
   ```bash
   cat custom.rules
   ```
   **Example Output | 示例输出:**
   ```plaintext
   alert http $HOME_NET any -> $EXTERNAL_NET any (msg:"GET on wire"; flow:established,to_server; content:"GET"; http_method; sid:12345; rev:3;)
   ```
2. **Rule Components | 规则组成**
   - **Action | 动作**: `alert` - Generates an alert when conditions are met.
   - **Header | 头部信息**: `http $HOME_NET any -> $EXTERNAL_NET any` - Targets HTTP traffic leaving the home network.
   - **Rule Options | 规则选项**:
     - `msg:"GET on wire"` - Alert message.
     - `flow:established,to_server` - Matches established TCP connections to the server.
     - `content:"GET"; http_method;` - Detects HTTP GET requests.
     - `sid:12345; rev:3;` - Assigns a unique ID and revision number.

### **Task 2: Trigger a Custom Rule | 任务 2：触发自定义规则**
1. Run Suricata with the custom rule and sample traffic:
   ```bash
   sudo suricata -r sample.pcap -S custom.rules -k none
   ```
2. **Command Breakdown | 命令解析**
   - `-r sample.pcap` - Uses the packet capture file as input.
   - `-S custom.rules` - Loads the custom rules file.
   - `-k none` - Disables checksum validation (not needed for offline packet analysis).

### **Task 3: Examine Logs | 任务 3：检查日志**
#### **3.1 Analyze fast.log | 分析 fast.log**
1. List log files:
   ```bash
   ls -l /var/log/suricata
   ```
2. Display alert log:
   ```bash
   cat /var/log/suricata/fast.log
   ```
   **Example Output  示例输出:**
   ```plaintext
   11/23/2022-12:38:34.624866 [**] [1:12345:3] GET on wire [**] {TCP} 172.21.224.2:49652 -> 142.250.1.139:80
   ```
   **What to look for? 关注信息**
   - **Timestamp  时间戳**: `11/23/2022-12:38:34.624866`
   - **Signature ID **: `[1:12345:3]`
   - **Message **: `GET on wire`
   - **Source & Destination 源和目标 IP**: `172.21.224.2 -> 142.250.1.139`

#### **3.2 Analyze eve.json 分析 eve.json**
1. Display JSON logs in a readable format:
   ```bash
   jq . /var/log/suricata/eve.json | less
   ```
2. Extract specific fields:
   ```bash
   jq -c "[.timestamp,.flow_id,.alert.signature,.proto,.dest_ip]" /var/log/suricata/eve.json
   ```
   **Example Output  示例输出:**
   ```json
   ["2022-11-23T12:38:34.624866+0000",14500150016149,"GET on wire","TCP","142.250.1.139"]
   ```
   **Key Insights 关注信息**
   - **Severity Level 严重性等级**: Look for `"severity": 3` or higher.
   - **Network Flow ID 网络流 ID**: Helps correlate related events.
   - **Destination IP 目标 IP**: Identifies potential attack targets.

---

## **5. Use Cases & Applications 使用场景 & 价值**
| **Scenario 场景** | **What to Analyze 重点分析内容** |
|------------|------------------|
| **Detecting Malicious HTTP Requests  监测恶意 HTTP 请求** | Check for **GET/POST patterns** in logs. |
| **Identifying Suspicious IPs  识别可疑 IP** | Monitor traffic from unusual **external IPs**. |
| **Investigating Data Exfiltration 数据泄露调查** | Look for **large outbound traffic flows**. |
| **Threat Hunting 威胁狩猎** | Analyze **eve.json** for repeated attack signatures. |

---

## **6. Summary | 关键总结**
✅ **Suricata detects network threats using rule-based signatures.**
✅ **Custom rules enhance detection capabilities and reduce false positives.**
✅ **fast.log provides quick insights, while eve.json enables deep forensic analysis.**
✅ **Using Suricata effectively helps security teams monitor, analyze, and respond to network threats.**

🚀 **Mastering Suricata will enhance your cybersecurity skills and help you detect and mitigate threats more efficiently!**

