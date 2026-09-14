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
 </ol>
</div>
