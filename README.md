<a name="top"></a>

<p align="center"> 
  <a href="https://www.linkedin.com/in/clarence-fong" target="_blank">
    <img width="50" height="50" alt="LinkedIn" src="https://github.com/user-attachments/assets/7ab6e12b-ca8a-4aa6-8f10-79ba89d485b5" />
  </a>
  <a href="mailto:abc1230940@gmail.com">
    <img width="50" height="50" alt="Gmail" src="https://github.com/user-attachments/assets/4e0491ce-239c-413c-b433-74a5ff48f231" />
  </a>
  <a href="https://www.instagram.com/cyberbrexel?igsh=MXNxeWJid2VxZWxxaw%3D%3D&utm_source=qr" target="_blank">
    <img width="50" height="50" alt="Instagram Old" src="https://github.com/user-attachments/assets/62e4672b-d424-4489-a204-c301040905a3" />
  </a>
  <a href="https://discordapp.com/users/cyberbrexel" target="_blank">
    <img width="50" height="50" alt="Discord" src="https://github.com/user-attachments/assets/f76173ca-fad3-4390-bca1-5c2305bc748e" />
  </a>
  <a href="https://www.reddit.com/user/abc1230940/" target="_blank">
    <img width="50" height="50" alt="Reddit" src="https://github.com/user-attachments/assets/6e9bd985-dfa3-4349-b966-4cf49362bd61" />
  </a>
</p> <br>


<h2 align="center"> CyberDefenders Write-up - 3CX Supply Chain </h2>
<h2 id="scenario"> Scenario </h2>
<p> A large multinational corporation heavily relies on the 3CX software for phone communication, making it a critical component of their business operations. After a recent update to the 3CX Desktop App, antivirus alerts flag sporadic instances of the software being wiped from some workstations while others remain unaffected. Dismissing this as a false positive, the IT team overlooks the alerts, only to notice degraded performance and strange network traffic to unknown servers. Employees report issues with the 3CX app, and the IT security team identifies unusual communication patterns linked to recent software updates. </p>
<p> As the threat intelligence analyst, it's your responsibility to examine this possible supply chain attack. Your objectives are to uncover how the attackers compromised the 3CX app, identify the potential threat actor involved, and assess the overall extent of the incident. </p>
<p align="right">(<a href="#top">Back to Top</a>)</p>


<h2 id="tools-used"> Tools Used </h2>
<ol>
  <li> <a href="https://www.virustotal.com/"> VirusTotal </a> </li>
  <li> <a href="https://attack.mitre.org/"> MITRE ATT&CK </a> </li>
  <li> msiinfo.exe from <a href="https://learn.microsoft.com/en-us/windows/apps/windows-sdk/downloads"> Windows SDK </a> </li>
  <li> msiexec </li>
  <li> sigcheck64.exe from <a href="https://learn.microsoft.com/en-us/sysinternals/downloads/sysinternals-suite"> Sysinternals Suite </li>
</ol>
<p align="right">(<a href="#top">Back to Top</a>)</p>


<h2 id="questions"> Questions </h2>
<p> <strong> 1. Understanding the scope of the attack and identifying which versions exhibit malicious behavior is crucial for making informed decisions if these compromised versions are present in the organization. How many versions of 3CX running on Windows have been flagged as malware? </strong> </p>
<p> I googled the related websites using the keywords "3CX windows malware" and found an article <a href="https://blogs.vmware.com/security/2023/03/investigating-3cx-desktop-application-attacks-what-you-need-to-know.html"> Investigating 3CX Desktop Application Attacks: What You Need to Know </a>from VMWare. </p>
<img width="1058" height="180" alt="Screenshot 2026-07-03 184348" src="https://github.com/user-attachments/assets/6f9e8c27-02dc-44f1-b387-7da92aa8a5f9" />
<p> According to the article we knew that the affected 3CX desktop app versions were 18.12.407 and 18.12.416 for Windows, confirmed by 3CX. Therefore, the answer was <strong>2</strong>.</p>
<br>
<p> <strong> 2. Determining the age of the malware can help assess the extent of the compromise and track the evolution of malware families and variants. What's the UTC creation time of the .msi malware? </strong> </p>
<p> I uploaded 3CXDesktopApp-18.12.416.msi to VirusTotal and navigated to Details section and looked at the History. </p>
<img width="507" height="187" alt="Screenshot 2026-07-03 184916" src="https://github.com/user-attachments/assets/e017b341-8510-4eb7-8ddd-e6ae994d6550" />
<p> The creation Time of the malware was <strong>2023-03-13 06:33</strong>. </p>
<br>
<p> <strong> 3. Executable files (.exe) are frequently used as primary or secondary malware payloads, while dynamic link libraries (.dll) often load malicious code or enhance malware functionality. Analyzing files deposited by the Microsoft Software Installer (.msi) is crucial for identifying malicious files and investigating their full potential. Which malicious DLLs were dropped by the .msi file? </strong></p>
<p align="right">(<a href="#top">Back to Top</a>)</p>


<h2 id="reference"> Reference </h2>
<p> <a href="https://cyberdefenders.org/blueteam-ctf-challenges/achievements/abc1230940/3cx-supply-chain/"> CyberDefenders - 3CX Supply Chain Lab </a> </p>
<p> <a href="https://blogs.vmware.com/security/2023/03/investigating-3cx-desktop-application-attacks-what-you-need-to-know.html"> VMWare - Investigating 3CX Desktop Application Attacks: What You Need to Know </a> </p>
<p> <a href="https://www.virustotal.com/gui/file/59e1edf4d82fae4978e97512b0331b7eb21dd4b838b850ba46794d9c7a2c0983/detection"> Static Analysis report of 3CXDesktopApp-18.12.416.msi from VirusTotal </p>
<p align="right">(<a href="#top">Back to Top</a>)</p>
