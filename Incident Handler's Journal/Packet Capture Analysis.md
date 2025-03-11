# **tcpdump 数据包捕获与分析**

## **1. 概述（Activity Overview）**

作为安全分析师，掌握 **tcpdump** 捕获和过滤网络流量的能力至关重要。本实验将指导你如何在 **Linux 环境** 下使用 tcpdump 进行数据包捕获与分析。

### **实验目标：**
1. **识别网络接口**，确定可用于数据包捕获的接口。
2. **使用 tcpdump 监控实时网络流量**，筛选关键数据。
3. **捕获网络流量并保存为 P-cap 文件** 供后续分析。
4. **过滤捕获的数据包**，提取特定流量信息。

---

## **2. 任务 1：识别网络接口（Identify Network Interfaces）**

### **步骤 1：使用 ifconfig 确定可用网络接口**
```bash
sudo ifconfig
```
示例输出（部分）：
```bash
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1460
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:ac:11:00:02  txqueuelen 0  (Ethernet)
```
**eth0** 是主要的以太网接口，将用于数据包捕获。

### **步骤 2：使用 tcpdump 列出所有可用接口**
```bash
sudo tcpdump -D
```

---

## **3. 任务 2：使用 tcpdump 监控实时流量（Inspect Network Traffic）**

### **使用 tcpdump 监测 eth0 接口的流量**
```bash
sudo tcpdump -i eth0 -v -c5
```
**参数解析：**
- `-i eth0`：监听 eth0 网络接口。
- `-v`：提供详细信息。
- `-c5`：捕获 5 个数据包后停止。

示例输出：
```bash
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
10:57:33.427749 IP 172.17.0.2.5000 > nginx.internal.59788: Flags [P.], length 82
```

**解析：**
- **时间戳**（`10:57:33.427749`）
- **源 IP 和端口**（`172.17.0.2.5000`）
- **目标 IP 和端口**（`nginx.internal.59788`）
- **TCP 标志**（`Flags [P.]`，PUSH 数据包）

---

## **4. 任务 3：捕获并存储网络数据包（Capture Network Traffic）**

### **保存 TCP 80 端口数据包到 P-cap 文件**
```bash
sudo tcpdump -i eth0 -nn -c9 port 80 -w capture.pcap &
```
**参数解析：**
- `-nn`：禁用 IP 地址和端口的名称解析。
- `-c9`：捕获 9 个数据包。
- `port 80`：仅捕获 HTTP 流量。
- `-w capture.pcap`：将数据保存到 `capture.pcap` 文件。

**生成 HTTP 流量**（用于测试捕获）：
```bash
curl opensource.google.com
```

**验证数据是否捕获成功：**
```bash
ls -l capture.pcap
```

---

## **5. 任务 4：过滤捕获的数据包（Filter Captured Packet Data）**

### **从 P-cap 文件读取数据包信息**
```bash
sudo tcpdump -nn -r capture.pcap -v
```

### **过滤并显示完整的 TCP 负载（Hex + ASCII 格式）**
```bash
sudo tcpdump -nn -r capture.pcap -X
```
**解析：**
- `-X` 选项显示十六进制和 ASCII 格式的原始数据包内容。
- 适用于恶意软件分析或入侵检测。

---

## **6. 真实场景：检测异常流量（Real-World Abnormalities）**

### **场景：检测恶意扫描行为（Port Scanning）**

在实际环境中，黑客可能会对服务器进行端口扫描，以寻找开放的服务端口。

#### **检测端口扫描：**
```bash
sudo tcpdump -i eth0 'tcp and (dst port 22 or dst port 80 or dst port 443)'
```

**异常分析：**
- **短时间内来自同一 IP 的多个端口请求**（如 `22, 80, 443`）。
- **来源 IP 可疑**（例如从未知国家或非公司网络的流量）。
- **大量 SYN 数据包但无后续 ACK**（SYN Flood 攻击）。

#### **示例异常数据包：**
```bash
22:53:27.669101 IP 203.0.113.5.43567 > 192.168.1.10.22: Flags [S], seq 4197622953, win 65320
22:53:27.669422 IP 203.0.113.5.43568 > 192.168.1.10.80: Flags [S], seq 4197622954, win 65320
22:53:27.669533 IP 203.0.113.5.43569 > 192.168.1.10.443: Flags [S], seq 4197622955, win 65320
```

**分析：**
- **同一 IP `203.0.113.5` 短时间内扫描多个端口**。
- **所有数据包均为 SYN**（扫描行为）。
- **目标端口 22（SSH）、80（HTTP）、443（HTTPS）**，表明黑客可能在寻找弱点。

**应对措施：**
1. **阻止可疑 IP**
   ```bash
   sudo iptables -A INPUT -s 203.0.113.5 -j DROP
   ```
2. **设置 fail2ban 规则**，检测 SSH 端口扫描：
   ```bash
   sudo fail2ban-client set sshd bantime 3600
   ```

---

## **7. 关键要点总结（Key Takeaways）**
✅ **tcpdump 是强大的命令行网络分析工具，可实时监测和捕获流量。**  
✅ **通过 `-w` 选项，可保存数据包供后续分析。**  
✅ **使用 `-nn` 选项避免 DNS 解析，以提高隐私性和准确性。**  
✅ **结合 `-X` 选项，可分析数据包的 HEX 和 ASCII 内容。**  
✅ **在实际场景中，tcpdump 可用于检测端口扫描、DDoS、C2 通信等异常行为。**  

tags: [
  "tcpdump",
  "Network Traffic Analysis",
  "Packet Capture",
  "Cybersecurity",
  "Threat Detection",
  "Linux Networking",
  "Intrusion Detection"
]

categories: ["Cybersecurity", "Networking", "Threat Analysis", "Incident Response"]

