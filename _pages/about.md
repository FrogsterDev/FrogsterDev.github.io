---
layout: page
title: "About Me"
permalink: /about/
description: "Learn about my cybersecurity journey and professional background"
---

## My Journey
My journey in cybersecurity began during high school when I participated in the Cybertron CTF competition, organized by a partner of the Wrocław University of Science and Technology (PWR). Although I didn't place on the podium, these experiences ignited my passion for cybersecurity. While I have extensive programming experience, I'm eager to expand my expertise and develop new skills in:

- **Penetration Testing** - Identifying vulnerabilities in systems and applications
- **Security Architecture** - Designing secure systems from the ground up
- **Incident Response** - Responding to and mitigating security incidents
- **Security Awareness** - Educating others about cybersecurity best practices

## Skills & Expertise

### Technical Skills
In progress...

### Certifications
I believe in continuous learning and professional development. My certifications include:

{% for certification in site.certifications %}
- [{{ certification.title }}]({{ certification.url | relative_url }}) - {{ certification.issuer }}
{% endfor %}

### Tools & Technologies
- **Security Tools**: Burp Suite, OWASP ZAP, Nmap, Metasploit, Wireshark
- **Cloud Platforms**: AWS
- **Programming**: Rust, C/C++, Python, PowerShell, Bash, JavaScript
- **Operating Systems**: Linux (Arch BTW), Windows, macOS, TempleOS

## Philosophy

I am deeply passionate about cybersecurity and believe it represents one of the most critical investments in today's digital age. My fascination with the field extends to understanding both offensive and defensive security techniques, including the intricate world of malware analysis and development. A pivotal moment in my journey was reading Kevin Mitnick's "The Art of Deception," which opened my eyes to a fundamental truth: cybersecurity transcends pure technical knowledge. The human element - social engineering, psychology, and behavioral patterns - plays an equally crucial role in building robust security systems. This holistic understanding drives my approach to cybersecurity, combining technical expertise with an appreciation for human factors.

## Contact

Feel free to reach out if you'd like to discuss cybersecurity, collaborate on projects, or just connect with a fellow security enthusiast!

- **Email**: [jakub.zabski@protonmail.com](mailto:your.email@example.com)
- **LinkedIn**: [Your LinkedIn Profile](https://linkedin.com/in/jakubzabski)
- **GitHub**: [Your GitHub Profile](https://github.com/frogsterdev)
