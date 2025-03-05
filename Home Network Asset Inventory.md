
# Home Network Asset Inventory

## Step 2: Identify Assets  
Below is an updated list of devices connected to the home network, including additional possessions.

| Asset                 | Network Access     | Owner        | Location       | Notes | Sensitivity |
|-----------------------|------------------|-------------|---------------|-------|-------------|
| Smart TV             | Frequent         | Yudi        | Living Room   | Connects via Wi-Fi, used for streaming services | Internal-only |
| Personal Laptop      | Always           | Yudi        | Bedroom       | Stores personal documents and financial records | Confidential |
| Smart Thermostat    | Occasional       | Shared      | Hallway       | Controls home temperature remotely, IoT security risk | Internal-only |
| External Hard Drive  | Rare (Only via laptop) | Yudi | Bedroom  | Stores all personal and work project files | Confidential |
| Company Tablet       | Frequent         | Employer    | Home Office   | Work device, requires secure access | Restricted |
| Personal Printer     | Rare (Only via USB) | Yudi | Home Office | Not connected to Wi-Fi, manual connection required | Internal-only |
| Smart Doorbell (Camera) | Frequent | Yudi | Entrance | Monitors home entry, video stored in the cloud | Confidential |
| Smart Light Bulbs (x2) | Frequent | Yudi | Various Rooms | Controlled via Google Nest Hub, part of smart home system | Internal-only |
| Google Nest Hub      | Frequent         | Yudi        | Living Room   | Acts as a smart home assistant, voice-controlled | Internal-only |

---

## Step 3 & 4: Characteristics and Network Access Details  

### **Smart TV**  
- **Network Access:** Frequently connected via Wi-Fi.  
- **Owner:** Yudi.  
- **Location:** Living Room.  
- **Notes:**  
  - Primarily used for entertainment.  
  - Could be compromised if not updated regularly.  

### **Personal Laptop**  
- **Network Access:** Always connected via Wi-Fi.  
- **Owner:** Yudi.  
- **Location:** Bedroom.  
- **Notes:**  
  - Stores sensitive personal documents and financial records.  
  - Requires strong authentication and encryption.  

### **Smart Thermostat**  
- **Network Access:** Occasionally connects via Wi-Fi.  
- **Owner:** Shared.  
- **Location:** Hallway.  
- **Notes:**  
  - Can be controlled remotely.  
  - Could be exploited for unauthorized home access.  

### **External Hard Drive**  
- **Network Access:** Not directly connected to the network.  
- **Owner:** Yudi.  
- **Location:** Bedroom.  
- **Notes:**  
  - Stores critical work projects and personal data.  
  - Should be encrypted and backed up securely.  

### **Company Tablet**  
- **Network Access:** Frequently connected via Wi-Fi.  
- **Owner:** Employer.  
- **Location:** Home Office.  
- **Notes:**  
  - Used for work, contains sensitive corporate data.  
  - Requires VPN and security policies from the company.  

### **Personal Printer**  
- **Network Access:** Not connected to Wi-Fi, manual USB connection only.  
- **Owner:** Yudi.  
- **Location:** Home Office.  
- **Notes:**  
  - Minimal security risk.  
  - Only connected when needed.  

### **Smart Doorbell (Camera)**  
- **Network Access:** Always connected via Wi-Fi.  
- **Owner:** Yudi.  
- **Location:** Entrance.  
- **Notes:**  
  - Stores video footage in the cloud.  
  - Could be exploited to access security footage.  

### **Google Smart Light Bulbs (x2)**  
- **Network Access:** Frequently connected via Google Nest Hub.  
- **Owner:** Yudi.  
- **Location:** Various rooms.  
- **Notes:**  
  - Low security risk.  
  - Could be used as an entry point for hacking if the smart home system is vulnerable.  

### **Google Nest Hub**  
- **Network Access:** Always connected via Wi-Fi.  
- **Owner:** Yudi.  
- **Location:** Living Room.  
- **Notes:**  
  - Acts as a smart home assistant, connected to multiple devices.  
  - Can be used for voice control, but requires strong authentication.  

---

## Step 5: Sensitivity Classification  

| Asset                 | Sensitivity Classification |
|-----------------------|--------------------------|
| Smart TV             | Internal-only |
| Personal Laptop      | Confidential |
| Smart Thermostat    | Internal-only |
| External Hard Drive  | Confidential |
| Company Tablet       | Restricted |
| Personal Printer     | Internal-only |
| Smart Doorbell (Camera) | Confidential |
| Google Smart Light Bulbs | Internal-only |
| Google Nest Hub      | Internal-only |

---

## **Final Thoughts**  
This asset inventory provides a comprehensive overview of devices connected to the home network. By classifying them based on their sensitivity, it ensures that security measures are prioritized appropriately.  

Key takeaways:  
- **Devices storing sensitive data (Laptop, Hard Drive, Company Tablet, Smart Doorbell) require strong security controls.**  
- **Smart home devices (Light Bulbs, Thermostat, Nest Hub) pose minimal risk but could be potential entry points for attackers.**  
- **Non-networked devices (Printer, Hard Drive) have lower risk but still require physical security considerations.**  

🚀 **Next Steps:** Ensure that high-risk devices have proper security controls like encryption, multi-factor authentication, and secure network configurations.
