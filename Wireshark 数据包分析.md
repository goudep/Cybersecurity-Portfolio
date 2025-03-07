# 

## 1. 概述（Activity Overview）
作为安全分析师，需要分析网络流量，以了解发送和接收的数据类型。

### **Wireshark 作用：**
- 捕获网络数据包（Packet Capture, P-cap）。
- 过滤和分析数据流量。
- 识别可疑行为，协助安全调查。

## 2. **实验场景（Scenario）**
分析某用户访问网站时的网络数据包，目标：
- 识别源 IP 和目标 IP。
- 观察使用的网络协议。
- 分析传输的数据类型。

## 3. **任务 1：使用 Wireshark 浏览数据（Explore Data with Wireshark）**

### **步骤：**
1. 打开 Wireshark，加载 `.pcap` 文件。
2. 查看数据包属性：
   - `No.`：数据包索引号。
   - `Time`：时间戳。
   - `Source`：源 IP 地址。
   - `Destination`：目标 IP 地址。
   - `Protocol`：使用的协议（TCP, UDP, ICMP）。
   - `Length`：数据包大小。
   - `Info`：数据包摘要信息。
3. 识别 **Echo (ping) request** 数据包。
   - **ICMP** 协议用于 Ping 请求。

## 4. **任务 2：应用基本过滤器（Apply Basic Wireshark Filter）**

### **步骤：**
1. 过滤特定 IP 地址的数据包：
   ```
   ip.addr == 142.250.1.139
   ```
2. 仅显示源 IP 地址匹配的数据包：
   ```
   ip.src == 142.250.1.139
   ```
3. 仅显示目标 IP 地址匹配的数据包：
   ```
   ip.dst == 142.250.1.139
   ```

## 5. **任务 3：筛选特定网络流量（Use Filters to Select Packets）**

### **基于 MAC 地址筛选：**
```
eth.addr == 42:01:ac:15:e0:02
```

### **基于 DNS 过滤流量（UDP 端口 53）：**
```
udp.port == 53
```

- 解析 DNS 查询，例如 `opensource.google.com`。
- 提取 DNS 服务器返回的 **IP 地址（142.250.1.139）**。

## 6. **任务 4：分析 TCP 流量（Use Filters to Explore TCP Packets）**

### **筛选 TCP 端口 80（HTTP 访问）：**
```
tcp.port == 80
```

### **查找特定文本数据（curl 请求）：**
```
tcp contains "curl"
```

## 7. **Wireshark 数据分析能揭示的信息（Key Takeaways）**

### **1. 识别异常通信模式**
Wireshark 可以帮助安全分析师检测以下异常：
- **异常 IP 地址通信**：某些 IP 地址不应出现在特定网络中。
- **非正常时间流量**：凌晨 3 点大量数据传输可能表明数据泄露。
- **大量失败登录尝试**：可能是暴力破解攻击。

### **2. 监测恶意软件行为**
- **DNS 隧道（DNS Tunneling）**：攻击者通过 DNS 查询传输数据。
- **异常端口使用**：例如，HTTP（80） 应该使用端口 80，但攻击者可能使用端口 8088 进行 C2 通信。

### **3. 典型异常实例（Security Incident Examples）**

| **异常行为** | **分析方式** | **可能的攻击类型** |
|-------------|-------------|----------------|
| 大量 DNS 查询（UDP 53） | `udp.port == 53` | DNS 数据隧道攻击 |
| 访问可疑 IP 地址 | `ip.addr == 192.168.1.100` | C2（指挥控制服务器）|
| 非工作时间大量流量 | `tcp.port == 443` | 数据泄露（Data Exfiltration）|
| HTTP 请求中包含 `curl` | `tcp contains "curl"` | Web 服务器探测 |
| 同一 IP 短时间多次登录失败 | `ip.src == x.x.x.x` | 暴力破解攻击 |

## 8. **结论（Conclusion）**

Wireshark 是安全分析师的重要工具，能够帮助分析数据包并发现异常模式。

通过本次实验，掌握：
- **如何捕获和分析数据包**
- **如何应用过滤器筛选流量**
- **如何发现潜在的安全威胁**



