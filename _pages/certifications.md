---
layout: page
title: "Certifications"
permalink: /certifications/
description: "My cybersecurity certifications and professional achievements"
---

## Current Certifications

<div class="certifications-grid">
{%- for cert in site.certifications -%}
    <div class="certification-card">
        <div class="cert-badge">
            {%- if cert.badge_image -%}
                <img src="{{ cert.badge_image | relative_url }}" alt="{{ cert.title }} Badge">
            {%- else -%}
                <div class="badge-placeholder">
                    <i class="fas fa-certificate"></i>
                </div>
            {%- endif -%}
        </div>
        <div class="cert-info">
            <h3>{{ cert.title }}</h3>
            <p class="cert-issuer">{{ cert.issuer }}</p>
            <p class="cert-date">{{ cert.date | date: "%B %Y" }}</p>
            {%- if cert.credential_id -%}
                <p class="cert-id">ID: {{ cert.credential_id }}</p>
            {%- endif -%}
            <a href="{{ cert.url | relative_url }}" class="cert-link">View Details</a>
        </div>
    </div>
{%- endfor -%}
</div>

## Certification Roadmap

I'm continuously working towards new certifications to expand my knowledge and skills. Here's my current learning roadmap:

### In Progress
- CCNA

### Planned
- CompTIA Security+
- CISSP
- HTB Certified Defensive Security Analyst (HTB CDSA)
- eJPT & eCPPT or CPTS
- OSCP
- OSEP
- HTB Certified Web Exploitation Expert (HTB CWEE)
- MALDEV Academy
- OSEE

## Why Certifications Matter

Certifications serve several important purposes in my professional development:

1. **Validation of Knowledge** - They provide external validation of my skills and knowledge
2. **Structured Learning** - They provide a structured path for learning new technologies and concepts
3. **Industry Recognition** - They demonstrate commitment to the field and professional standards
4. **Continuous Improvement** - They encourage continuous learning and skill development

## Learning Approach

For each certification, I follow a structured approach:

1. **Assessment** - Evaluate current knowledge and identify knowledge gaps
2. **Study Plan** - Create a comprehensive study plan with timelines
3. **Hands-on Practice** - Apply knowledge through labs and practical exercises
4. **Documentation** - Document the learning journey and key insights
5. **Certification** - Take the exam and earn the certification
6. **Application** - Apply the knowledge in real-world scenarios

Each certification journey is documented in detail, including study resources, challenges faced, and lessons learned.
