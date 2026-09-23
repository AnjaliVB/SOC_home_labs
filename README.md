<image src="https://github.com/user-attachments/assets/134a3ee7-5675-408b-a5ac-4c34e2a96c64" width=80px height=80px align=left> <h1> Network Traffic Analysis with Wireshark</h1>

<div>
 <h3>What is Network Traffic Analysis?</h3>

<b> Network Traffic Analysis (NTA) </b> is the process of capturing, monitoring, and analyzing network communications to detect anomalies, security threats, and performance issues. It uses metadata, behavioral analytics, and machine learning rather than just inspecting every packet, enabling early threat detection even in encrypted traffic. 

<h3> Real-World Use Cases for Network Traffic Analysis </h3>
<ul>
 <li>Detecting Lateral Movement: Attackers who breach one endpoint often spread quietly. NTA identifies unusual east-west traffic between internal servers, revealing these movements.</li>
 <li>Spotting Data Exfiltration: Whether through unauthorized file transfers or hidden tunneling, NTA surfaces data leaving the network that shouldn’t.</li>
 <li>Exposing Command-and-Control Traffic: Communications with foreign rogue servers usually leave signatures of flow patterns even when encrypted.</li>
 <li>Performance and Optimization: Network traffic analysis enables the IT teams to identify the potential areas of congestion and underutilized assets and enhance the cost and user experience.</li>
</ul>

<h3>What Are Network Traffic Analysis Tools?</h3>
Network Traffic Analysis (NTA) tools monitor and analyze network traffic to identify unusual activity, security threats, and performance issues. They inspect data such as IP addresses, ports, protocols, traffic patterns, and connection behavior to provide visibility into what is happening across the network.

<h3>Why Network Traffic Analysis Tools Matter for Modern SOC Operations</h3>
For a modern Security Operations Center (SOC), NTA tools provide continuous network visibility and help security teams detect threats that may not be visible through endpoint or log-based monitoring alone. They support faster detection, investigation, and response by highlighting suspicious communication, abnormal traffic patterns, and potential attacks.

<h3>How Network Traffic Analysis Tools Work</h3>
NTA tools collect network data from sources such as packet captures, network taps, flow records, and sensors. They analyze this data using rules, signatures, behavioral analysis, and anomaly detection to identify suspicious activity. Alerts and network metadata are then presented to SOC analysts for investigation and correlation with other security data.

<h3></h3>
<b>Typical workflow:</b>

Network Traffic → Collection → Analysis → Detection → Alert → Investigation & Response

<h3>Common SOC Use Cases for Network Traffic Analysis Tools</h3>
<ul>
 <li>Threat Detection: Identify malware, command-and-control traffic, and suspicious connections.</li>
 <li>Network Anomaly Detection: Detect unusual traffic volumes, protocols, or communication patterns.</li>
 <li>Lateral Movement Detection: Identify suspicious connections between internal systems.</li>
 <li>Data Exfiltration: Detect unusual outbound traffic that may indicate data theft.</li>
 <li>Incident Investigation: Analyze historical network activity to understand the scope and timeline of an incident.</li>
 <li>Threat Hunting: Search network telemetry for indicators of compromise and suspicious behaviors.</li>
 <li>Asset Visibility: Discover communicating hosts, services, and network relationships.</li>
 <li>Security Monitoring: Provide additional network context for SIEM, EDR, and other SOC tools.</li>
</ul>

</div>

<div>
 <h1>Task: Analyze sample Network Traffic using Wireshark</h1>
 <h4>Description:
  <ol>
   <li>Analyze the sample network traffic using wireshark</li>
   <li>Search for any hidden malware or suspicious activity</li>
   <li>Investigate and gather IOCs</li>
   <li>Conclusion</li>
  </ol>
 </h4>
 <h1></h1>
 <b>Steps</b>
 <ol>
  
  <li> Open wireshark, open sample 2023-02-03.pcap file for investigation
  <br><br>
   <kbd height=80% width=80%> <img src="https://github.com/user-attachments/assets/881f74c6-e147-4d18-9f38-e3de369f5ffc"> </kbd>
  </li>
  
  <li>Investigating the HTTP traffic
  <br><br>
   <kbd height=80% width=80%> <img src="https://github.com/user-attachments/assets/98076556-11ae-45df-a077-31fcddaeb672"> </kbd>
  </li>
  
  <li>Follow the HTTP stream by right clicking the request/response
   <br>
   This screenshot clearly shows a <b>.dat file </b>.

   
   <kbd height=80% width=80%> <img src="https://github.com/user-attachments/assets/fae9fb56-2d55-4f4d-a873-3dd3d86dad5f" > </kbd>
   
   This will open the below conversation:

   
   <kbd height=80% width=80%> <img src="https://github.com/user-attachments/assets/79614c76-75ba-4650-9c0e-dcf8941b4960"> </kbd>

   
   <h4>*What is a DAT file?</h4>
   Computer programs create DAT files to store specific information or data. The information in the file is only relevant to the programme that created it, though almost any programme can create DAT files. DAT might look like an acronym, but the extension name is actually short for ‘data’ - so the name is more or less descriptive.
   </li>

   <li>
    Searching for MZ file signature (magic bytes) to find what it means.
    
   <kbd height=80% width=80% > <img src="https://github.com/user-attachments/assets/e8d1aade-e406-4774-8e29-b67be3025216"></kbd>
   </li>
   <li>To collect IOCs, go to statistics -> HTTP -> requests
    
   <kbd height=80% width=80% > <img src="https://github.com/user-attachments/assets/5f85a64e-342f-4d6e-847a-3aab5f62be54"></kbd>
   </li>

   <li>
    To save the .dat file, follow the steps: File -> Export Objects -> HTTP
    
   <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/4751638d-cc7c-4adb-9aa4-f85d0c74135a"></kbd>

   This will open the following dialog box:

   <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/903c7186-179f-478e-b6bc-b1ca0e326cf6" ></kbd>
   </li>

   <li>
   Reputation check of 86607.dat file on VirusTotal
    
   Create sha256 hash of 86607.dat by using the following command:
    
     sha256sum 86607.dat

   <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/fd5a6f77-83f1-4843-97e2-af2cefe80b3c" ></kbd>

   Enter the generated sha256 hash on VirusTotal to check its reputation

   <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/08de7946-9c4d-42cf-9343-b23581aa6add"></kbd>

   The reputation check resulted that the file is flagged as malicious by 54 vendors. Therefore, this is an IOC (Indicator Of Compromise) that this network has somewhere been targeted to attack the network.
   </li>

   <li>
    Second reputation check for the same file on MalwareBazaarDatabase

   Navigate to:
    https://bazaar.abuse.ch/browse/
    
   Type the below command in search bar:

    sha256:713207d9d9875ec88d2f3a53377bf8c2d620147a4199eb183c13a7e957056432

   Following is the o/p:
   
   <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/32c1006a-567b-42ef-a3cf-1362e8fb0dec" ></kbd>

   The output shows that the malware is "Quakbot".

   The below screenshots shows how many attacks were done by Quakbot and different hashes provided by different reporters that reported the malware.


  <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/e82c7d00-f21f-4125-8ac9-5b27c2e62482" ></kbd>
  
  <kbd height=80% width=80% ><img src="https://github.com/user-attachments/assets/a74510fb-0090-4fee-b27e-6bbb8b114864" ></kbd>
   </li>   
   
 </ol>

 <h4>Conclusion</h4>
 Based on these findings and all IOCs, it can be concluded that the network analyzed is compromised with Quakbot malware. The malware was sent by 128.254.207.55 (ip address) through http request, a file named 86607.dat to 10.0.0.149 (ip address). The receiver has accepted the request and has sent a response. This indicates that the receiver has downloaded the malware file via curl/7.83.1. 
 
 There are 2 possible scenarios that how the victim downloaded the malware-86607.dat file.
 
 <b>Scenario 1</b> : The attacker (128.254.207.55) previously gained initial access or Remote Code Execution (RCE) on 10.0.0.149 (eg. via a web vulnerability, phish, or exploit) and then executed a curl command on the victim machine.

 <b>Scenario 2</b>:The machine was infected via an initial access vector eg. a user opened a malicious macro-enabled document, executed a drive-by download, or ran a compromised installer and then the initial execution triggered a localized script eg. VBScript, PowerShell, or bash script that utilized curl and downloaded it.


 **Evidence Table:**
 
 **Network Traffic Evidence Analysis**

| Indicator | Packet Detail | Analysis / Security Significance |
| :--- | :--- | :--- |
| **Originating IP** | `10.0.0.149`  | Internal client host initiating the outbound network request. |
| **Destination IP** | `128.254.207.55` | External hosting, staging, or Command & Control (C2) server. |
| **User-Agent** | `curl/7.83.1` | Confirms execution via command-line tool or automated script rather than standard browser navigation. |
| **Request URI** | `GET /86607.dat` | Outbound request attempting to fetch a secondary stage file/payload. |
| **HTTP Response** | `200 OK` | Confirms the server successfully fulfilled the request and delivered the `.dat` file payload. |


**Investigation Tooling Summary**

* **Wireshark:** Used for deep packet inspection (DPI), extracting HTTP objects (`86607.dat`), and reconstructing TCP streams to identify protocol headers and payload data.
* **VirusTotal:** Used to query hashes (MD5/SHA256) of extracted payloads and cross-reference public IP addresses against multi-engine threat intelligence databases.
* **MalwareBazaar:** Used to cross-reference identified file hashes or signatures against known malware family samples for further dynamic/static sandbox analysis.
 
</div>
