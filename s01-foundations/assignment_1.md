# S01 Research Work

**Task A:** Malware types and real-world examples  
**Task B:** B1 (isolated VM) and B2 (`chmod` permissions)

## Task A: Malware types and examples

| Type | Definition in my own words | Named example + year | Who it targeted | How it spread or was installed | Primary impact |
|---|---|---|---|---|---|
| **Virus** | Code that inserts itself into a host document or program and runs when that infected host is opened; Melissa specifically used Word macros and infected the Word template. | Melissa (1999) [FBI](https://www.fbi.gov/history/cases-and-criminals/melissa-virus), [Microsoft](https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?Name=Virus%3AW97M%2FMelissa.A) | People and workplaces using Microsoft Word with Outlook. | An infected Word attachment ran a macro, then sent a copy of the infected document to the first 50 Outlook addresses. | Rapid mail multiplication overwhelmed business email systems. It also infected Word documents or templates. |
| **Worm** | Malware that can move to other machines without each person opening a new malicious document; Conficker copied itself through vulnerable Windows networking and shares. | Conficker.B (2008)  [Microsoft](https://www.microsoft.com/en-us/wdsi/threats/malware-encyclopedia-description?Name=Worm%3AWin32%2FConficker.B) | Unpatched Windows computers, including machines on office networks. | Exploited the Windows Server service flaw MS08-067, also tried weak administrator passwords on shares and used removable drives or AutoPlay. | Disabled security services and antivirus protections, making affected networks harder to defend and clean. |
| **Trojan** | A malicious program delivered through something the user is tricked into opening; Zeus hid its banking-theft purpose rather than copying itself like a worm. | Zeus/Zbot (seen from 2007) [NHS Digital](https://digital.nhs.uk/cyber-alerts/2017/cc-1138), [US DOJ](https://www.justice.gov/archives/opa/pr/us-leads-multi-national-action-against-gameover-zeus-botnet-and-cryptolocker-ransomware) | Windows users conducting online banking, including consumers and businesses. | Primarily spam-email lures and drive-by downloads from malicious or compromised sites. | Grabbed saved passwords and intercepted banking-site information, enabling fraudulent transfers. |
| **Ransomware** | Malware that denies access to data and demands payment; WannaCry also included a worm-like component that reached other unpatched Windows PCs. | WannaCry (2017) [CERT-EU](https://cert.europa.eu/publications/security-advisories/2017-012/), [UK NAO](https://www.nao.org.uk/reports/investigation-wannacry-cyber%20attack-and-the-nhs/) | Unpatched Windows systems worldwide; the NHS in England was one prominent affected organisation, **not a uniquely selected target**. | Used the EternalBlu SMB exploit against systems missing the MS17-010 patch, then moved through networks. | Encrypted files, demanded ransom, and interrupted NHS healthcare services and appointments. |
| **Spyware** | Software installed to observe a person secretly; Pegasus was designed to turn the phone itself into a surveillance device. | Pegasus (2016 attack attempt) [Citizen Lab](https://citizenlab.ca/research/million-dollar-dissident-iphone-zero-day-nso-group-uae/) | UAE human-rights defender Ahmed Mansoor was targeted; researchers confirmed the exploit on a test phone, not a successful infection of his phone. | SMS messages contained a malicious link; opening it on a vulnerable iPhone triggered a three-vulnerability exploit chain. | The tested payload could record calls and messages, activate microphone/camera surveillance, and track movements. |
| **Adware** | Software that manipulates browsing to earn advertising revenue, Fireball hijacked the browser rather than merely displaying a normal advertisement. | Fireball (2017) [Check Point Research](https://research.checkpoint.com/2017/fireball-chinese-malware-250-million-infection/) | Windows computer users, including machines in corporate networks. | Bundled with seemingly useful free programs, including installers associated with Deal Wifi and Mustang Browser. | Replaced homepage or search settings, redirected traffic, tracked users, and created a route for downloading further malware. |
| **Rootkit** | Software that changes what the operating system reveals, concealing files or processes so they are harder to detect and remove. | Sony BMG XCP rootkit (2005) [Mark Russinovich, Virus Bulletin](https://virusbulletin.com/virusbulletin/2005/12/inside-sony-s-rootkit) | Windows users who played affected Sony BMG music CDs. | The CD's autorun digital-rights-management installer installed a hidden system component after the user accepted its licence screen. | Hid files and registry entries from normal views, reduced user control, and created security concerns on affected PCs. |
| **Keylogger** | Malware that records the keys pressed inside real applications; the Agent Tesla campaign collected keystrokes alongside stored passwords and screenshots. | Agent Tesla (2023 campaign) [Fortinet](https://www.fortinet.com/blog/threat-research/agent-tesla-variant-spread-by-crafted-excel-document) | Windows users receiving a forged industrial purchase-order email. | A malicious Excel attachment exploited CVE-2017-11882/CVE-2018-0802 and downloaded the payload. | Captured typed input, saved browser, email credentials, and screen images, then sent stolen data via SMTP. |
| **Botnet agent** | A piece of malware that enrolls an infected device into an attacker-controlled network; Mirai made everyday internet-connected equipment into DDoS workers. | Mirai (2016) [FBI IC3](https://www.ic3.gov/PSA/2017/PSA171017), [CERT-In](https://www.cert-in.org.in/s2cMainServlet?VLCODE=CIAD-2016-0086&pageid=PUBVLNOTES02) | Internet-exposed routers, IP cameras and digital video recorders, often owned by people unaware of the infection. | Scanned IP addresses for exposed Telnet/SSH services and tried common/default credentials. | Turned compromised devices into remotely commanded bots used for large distributed denial-of-service attacks. |
| **Fileless / living-off-the-land** | An attack method that uses legitimate system tools to execute malicious code, making activity resemble administration; it does **not** mean no files ever touch disk. | Astaroth (2019 campaign) [Microsoft Security](https://www.microsoft.com/en-us/security/blog/2019/07/08/dismantling-a-fileless-campaign-microsoft-defender-atp-next-gen-protection-exposes-astaroth-attack/), [Bitdefender](https://www.bitdefender.com/en-au/blog/labs/astaroth-trojan-resurfaces-targets-brazil-through-fileless-campaign) | Windows users, especially in Brazil. | Phishing links led to LNK shortcuts, which abused **WMIC, Bitsadmin, Certutil and Regsvr32** before loading the stealer into a process. | Stole credentials, keystrokes and other data while blending execution into trusted Windows utilities. |
| **Logic bomb** | Destructive code planted in an existing system that remains quiet until a trigger condition occurs, rather than trying to infect other computers. | Omega Engineering “time bomb” (1996) [US DOJ](https://www.justice.gov/archive/criminal/cybercrime/press-releases/2002/lloydSent.htm), [US appellate record](https://law.justia.com/cases/federal/appellate-courts/F3/269/228/532823/) | Omega Engineering's manufacturing/design computer systems. | Allegedly planted by an insider on the company's central server before his departure; **it did not self-spread**. | Deleted approximately 1,200 design/production programs and caused millions of dollars in business losses. |
| **Bootkit** | Malware embedded in the early startup chain, where it can execute before the main operating system and survive ordinary disk cleanup; LoJax specifically infected UEFI firmware. | LoJax (2018) [ESET](https://blog.eset.ie/2018/09/28/lojax-first-uefi-rootkit-found-in-the-wild-courtesy-of-the-sednit-group/) | Several government organisations in the Balkans and Central/Eastern Europe. | Not a self-spreading worm: an attacker with system access wrote a malicious UEFI module into the machine's SPI flash. | Reinstalled malicious components during boot and could persist even after reinstalling Windows or replacing the disk. |

### Most dangerous type for a Pakistani SME

I consider ransomware the most dangerous type for a Pakistani small or medium-sized business because encrypting accounts, invoices, stock records or customer files can stop everyday work immediately. The [2017 WannaCry incident](https://www.nao.org.uk/reports/investigation-wannacry-cyber%20attack-and-the-nhs/) showed how an unpatched Windows environment can suffer disruption well beyond one computer, so a small company with limited IT support could face a business-wide outage. I would therefore prioritize tested offline backups and prompt security updates, consistent with [CISA's ransomware recovery guidance](https://www.cisa.gov/sites/default/files/publications/CISA_MS-ISAC_Ransomware%20Guide_S508C.pdf), because recovering operations matters more than relying on a ransom payment.

## Task B1 Evidence that my VM is isolated

![Kali commands for ip, route and a network scan](screenshots_assignment_1\taskb1.jpg)

I made the kali network adapter hostonly (switched from initial NAT) for isolation made metasploitable hostonly as well. The network scan at the end shows that the other host only machine can be discovered but the network is isolated from internet.

## Task B2 Three file-permission changes

These commands run in a disposable test directory. Keep the terminal visible for screenshots of the **initial state and the state after every change**.

### Creating file

![Creating file](screenshots_assignment_1\creating_file.jpg)

### Using `chmod u+x`

![chmod u+x to make file executeable](screenshots_assignment_1\chmod_u+x.jpg)

### Using `000`  remove all permissions for user, groups and others users

![using chmod 000](screenshots_assignment_1\chmod_000.jpg)

### Restoring read

![Restoring read](screenshots_assignment_1\restore_read.jpg)
