---
layout: post
title: "Understanding Zero-Day Vulnerabilities"
date: 2024-08-28
---

### Attackers Exploit Critical Atlassian Confluence Flaw for Cryptojacking

Novel attack vectors leverage the CVE-2023-22527 RCE flaw discovered in January, which is still under active attack, to turn targeted cloud environments into cryptomining networks.
Threat actors continue to exploit a critical remote code execution (RCE) Atlassian bug discovered in January, with new attack vectors that turn targeted cloud environments into cryptomining networks.
Trend Micro has uncovered two separate attacks that use the flaw — tracked as CVE-2023-22527 in the Confluence Data Center and Confluence Server — in cryptojacking attacks that drain network resources. The server is for enterprise-level deployments of Atlassian Confluence, a collaboration and documentation platform designed for teams and organizations to create, share, and collaborate on content.

When discovered, the bug received a 10 out of 10 on the Common Vulnerability Scoring System (CVSS), so researchers knew out of the gate that it had great potential for exploit in attacks ranging from ransomware to cyber espionage. Now, cryptojacking can be added to that list, eight months after the flaw's discovery and subsequent patching by Atlassian, according to a blog post published on Aug. 28 by Trend Micro.

"The attacks involve threat actors that employ methods such as the deployment of shell scripts and XMRig miners, targeting of SSH endpoints, killing competing cryptomining processes, and maintaining persistence via cron jobs," Abdelrahman Esmail, senior engineer of threat research for Trend Micro, wrote in the post.
Trend Micro also discovered thousands of other attempts to exploit max-critical CVE-2023-22527 over the past few months, and thus recommended that those using the server who haven't yet patched their environments should do so as quickly as possible.


### uNew Attack Vectors for CVE-2023-22527
By abusing CVE-2023-22527, an unauthenticated attacker can achieve template injection, essentially enabling RCE on the affected instance.
Trend Micro discovered three threat actors using the bug for cryptojacking attacks. However, only two different attack vectors are described in the post. The first one exploited the flaw in the public-facing a Confluence Server application for initial access to the environment. Attackers then executed the XMRig miner via an ELF file payload, hijacking system resources in the process.
The second attack vector is much more complicated. It used a shell script to execute miner activity through a shell file over Secure Shell (SSH) for all accessible endpoints in the customer environment, according to Trend Micro. The attackers downloaded the shell file and ran it with bash from memory, then killed all known cryptomining processes and any process being run from */tmp/* directories. Then, they deleted all cron jobs, adding a new one that runs every five minutes to check for command-and-control (C2) server communications.
To avoid detection, the attackers also uninstalled security services such as Alibaba Cloud Shield, while blocking the Alibaba Cloud Shield IP address. Before the cryptojacking began later in the attack process, the attacker also turned off other security tools present on the system.
Meanwhile, the adversaries identified the current machine's IP address and gathered data on all possible users, IP addresses, and keys, using the information to target other remote systems via SSH to execute further cryptomining activities, Esmail explained in the post. Once this is done, the attacker launched automated attacks on the targeted other hosts via SSH, and then maintained access to the server through other cron jobs.
"After ensuring that all cloud monitoring and security services are terminated or deleted, the attacker terminates the entry point process that exploits CVE-2023-22527 and downloads the XMRig miner to begin mining activities," Esmail wrote. Once cryptomining begins, the attackers attacker then removed all traces of their activity by clearing log and bash history.


### Further Mitigations Against Atlassian Confluence Attacks
Staying on top of bug patching for software, operating systems, and applications is the most effective way to prevent such vulnerabilities from being exploited, but Trend Micro also made other suggestions for administrators of cloud environments. Those include practicing network segmentation, which can reduce the impact of exploit-based attacks, and that organizations should conduct regular security audits and vulnerability assessments to help uncover and address weaknesses in infrastructure before exploit occurs. Beyond that, organizations should have a solid incident response plan in place to ensure a swift and effective reaction in case of compromise.



[Authored by: Elizabeth Montalbano, Contributing Writer....]
