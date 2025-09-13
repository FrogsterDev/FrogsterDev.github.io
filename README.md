# Cybersecurity Portfolio

Was this generated with Cursor IDE? Maybe... doesn't matter the purpose is to have a place to put my writeups and stuff
like that... also it looks nice.

A professional Jekyll-based portfolio website for showcasing cybersecurity certifications, technical writeups, and learning progress. This site is designed to be hosted on GitHub Pages and provides a comprehensive platform for documenting your cybersecurity journey.

## Features

- **Professional Design**: Modern, responsive design with a cybersecurity theme
- **Certification Tracking**: Document and showcase your cybersecurity certifications
- **Technical Writeups**: Detailed analysis of security vulnerabilities and penetration testing
- **Learning Progress**: Track your continuous learning journey with progress indicators
- **GitHub Pages Ready**: Optimized for deployment on GitHub Pages
- **SEO Optimized**: Built-in SEO features for better search engine visibility
- **Mobile Responsive**: Works perfectly on all device sizes

## Site Structure

```
├── _certifications/     # Certification documentation
├── _writeups/          # Technical writeups and analysis
├── _learning/          # Learning progress and modules
├── _layouts/           # Jekyll layouts
├── _includes/          # Reusable components
├── _pages/             # Static pages
├── _sass/              # SCSS stylesheets
├── assets/             # CSS, JS, and images
└── _config.yml         # Jekyll configuration
```

## Getting Started

### Prerequisites

- Ruby 3.1 or higher
- Bundler gem
- Git

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/frogsterdev/frogsterdev.github.io.git
   cd frogsterdev.github.io
   ```

2. **Install dependencies**
   ```bash
   bundle install
   ```

3. **Serve locally**
   ```bash
   bundle exec jekyll serve
   ```

4. **View the site**
   Open your browser and navigate to `http://localhost:4000`

### Customization

#### Personal Information
Update the following files with your information:

- `_config.yml` - Site configuration, social links, navigation
- `_pages/about.md` - Personal information and background
- `_pages/contact.md` - Contact information

#### Adding Content

## 📝 Content Creation Guide

### 🔐 Creating Certifications

**Step 1: Create the file**
```bash
# Navigate to the certifications directory
cd _certifications/

# Create a new certification file (use kebab-case for filename)
touch comp-tia-security-plus.md
# or
touch aws-security-specialty.md
```

**Step 2: Use the certification template**
```yaml
---
layout: certification
title: "CompTIA Security+"
issuer: "CompTIA"
date: 2024-01-15
credential_id: "COMP001234567"
verification_url: "https://www.credly.com/badges/example"
description: "CompTIA Security+ is a globally recognized certification that validates baseline cybersecurity skills and knowledge."
skills:
  - Network Security
  - Threats and Vulnerabilities
  - Identity and Access Management
  - Risk Management
  - Cryptography
  - Security Architecture
learning_journey: |
  ## My Security+ Journey
  
  The CompTIA Security+ certification was my first major step into the cybersecurity field...
  
  ### Study Approach
  - **Duration**: 3 months of focused study
  - **Resources**: Official CompTIA study guide, practice exams
  - **Practice**: Set up a home lab environment
  
  ### Key Learning Areas
  1. **Network Security**: Understanding firewalls, VPNs
  2. **Threats and Vulnerabilities**: Identifying attack vectors
  3. **Identity and Access Management**: Authentication and authorization
  
  ### Challenges Overcome
  - Balancing study time with work commitments
  - Understanding complex cryptographic concepts
  
  ### Impact on Career
  This certification opened doors to entry-level cybersecurity positions...
---

# CompTIA Security+ Certification

## Overview
[Your detailed content here...]

## Skills Validated
[Describe the skills this certification validates...]

## Study Resources Used
[List the resources you used...]

## Practical Applications
[How you've applied this knowledge...]

## Next Steps
[What certifications you plan to pursue next...]
```

**Step 3: Add badge image (optional)**
```bash
# Add your certification badge image
mkdir -p assets/images/certifications/
# Place your badge image in this directory
# Reference it in the front matter: badge_image: "/assets/images/certifications/security-plus-badge.png"
```

### 📊 Creating Technical Writeups

**Step 1: Create the directory structure**
```bash
# Create the date-based directory structure
mkdir -p _writeups/2024/01/15

# Create the writeup file
touch _writeups/2024/01/15/sql-injection-analysis.md
```

**Step 2: Use the writeup template**
```yaml
---
layout: writeup
title: "SQL Injection Vulnerability Analysis"
date: 2024-01-15
category: "Web Application Security"
difficulty: "Medium"
description: "A detailed analysis of SQL injection vulnerabilities found during a web application security assessment."
tags:
  - SQL Injection
  - Web Security
  - Penetration Testing
  - Database Security
toc: true
---

# SQL Injection Vulnerability Analysis

## Executive Summary
[Brief overview of the assessment and key findings...]

## Scope and Objectives
**Target Application**: [Application name and version]  
**Assessment Type**: [Authorized penetration test, CTF, etc.]  
**Scope**: [What was assessed]  
**Objective**: [What you were trying to achieve]

## Methodology
### Reconnaissance Phase
- [Steps taken to gather information]

### Vulnerability Discovery
- [How you found the vulnerabilities]

### Exploitation
- [How you exploited the findings]

## Findings
### 1. [Vulnerability Name]
**Location**: [Where it was found]  
**Severity**: [High/Medium/Low]  
**CVSS Score**: [If applicable]

#### Vulnerability Details
[Detailed explanation of the vulnerability]

#### Proof of Concept
```http
[Code examples or HTTP requests]
```

#### Impact
[What the impact would be]

## Remediation Recommendations
1. **Immediate Actions**
   - [What should be done right away]

2. **Long-term Improvements**
   - [Longer-term security improvements]

## Lessons Learned
[What you learned from this assessment]

## Tools Used
- [List of tools and technologies used]

## Conclusion
[Summary and final thoughts]
```

**Step 3: Add supporting files (optional)**
```bash
# Create a directory for writeup assets
mkdir -p _writeups/2024/01/15/assets/
# Add screenshots, diagrams, or other supporting files
```

### 📚 Creating Learning Modules

**Step 1: Create the file**
```bash
# Navigate to the learning directory
cd _learning/

# Create a new learning module
touch ethical-hacking-fundamentals.md
```

**Step 2: Use the learning template**
```yaml
---
layout: learning
title: "Ethical Hacking Fundamentals"
status: "In Progress"  # Planned, In Progress, Completed
progress: 45
duration: "16 weeks"
description: "Comprehensive study of ethical hacking techniques, penetration testing methodology, and security assessment practices."
objectives:
  - Master penetration testing methodology (OSCP-style)
  - Learn reconnaissance and information gathering techniques
  - Understand common attack vectors and exploitation methods
  - Practice with hands-on labs and vulnerable machines
  - Develop report writing and documentation skills
resources:
  - title: "The Web Application Hacker's Handbook"
    description: "Comprehensive guide to web application security testing"
    url: "https://www.amazon.com/Web-Application-Hackers-Handbook-Exploiting/dp/1118026470"
  - title: "HackTheBox Academy"
    description: "Interactive learning platform for ethical hacking"
    url: "https://academy.hackthebox.com/"
progress_notes: |
  ## Phase 1: Foundation (Weeks 1-4) ✅ COMPLETED
  
  **Reconnaissance and Information Gathering**
  - Mastered passive and active reconnaissance techniques
  - Learned to use tools like theHarvester, Recon-ng, and Shodan
  - Practiced DNS enumeration and subdomain discovery
  - Completed 15+ reconnaissance challenges on TryHackMe
  
  **Key Achievements:**
  - Successfully enumerated target networks without detection
  - Identified multiple attack vectors through information gathering
  - Documented findings in professional format
  
  ## Phase 2: Vulnerability Assessment (Weeks 5-8) 🔄 IN PROGRESS
  
  **Network Scanning and Enumeration**
  - Currently learning advanced Nmap techniques
  - Practicing service enumeration and version detection
  - Working through port scanning evasion methods
  - Completed 8/12 network scanning labs
  
  **Current Focus:**
  - Web application vulnerability scanning
  - Database enumeration techniques
  - Network service exploitation
---

# Ethical Hacking Fundamentals

## Learning Overview
[Description of what you're learning...]

## Learning Objectives
By the end of this module, you will be able to:
1. **Conduct Professional Reconnaissance**: [Specific skills]
2. **Perform Vulnerability Assessments**: [Specific skills]
3. **Execute Exploitation Techniques**: [Specific skills]
4. **Document Findings**: [Specific skills]

## Course Structure
### Phase 1: Foundation & Reconnaissance (Weeks 1-4)
- **Information Gathering**: [Topics covered]
- **Network Discovery**: [Topics covered]

### Phase 2: Vulnerability Assessment (Weeks 5-8)
- **Network Scanning**: [Topics covered]
- **Service Enumeration**: [Topics covered]

## Hands-on Labs
### Lab Environment Setup
- **VirtualBox**: [Description]
- **Kali Linux**: [Description]

### Completed Labs
- **Reconnaissance**: [Number] information gathering exercises
- **Network Scanning**: [Progress] network enumeration labs

## Assessment Methods
- **Weekly Labs**: 40% of total grade
- **Practical Challenges**: 30% of total grade
- **Final Project**: 20% of total grade
- **Documentation**: 10% of total grade

## Next Steps
Upon completion of this module, consider pursuing:
- **OSCP Certification**: [Description]
- **CEH Certification**: [Description]
```

### 🎯 Content Best Practices

#### File Naming Conventions
- **Certifications**: Use kebab-case (e.g., `comp-tia-security-plus.md`)
- **Writeups**: Use descriptive names (e.g., `sql-injection-analysis.md`)
- **Learning Modules**: Use descriptive names (e.g., `ethical-hacking-fundamentals.md`)

#### Front Matter Guidelines
- Always include the required `layout` field
- Use consistent date formats (YYYY-MM-DD)
- Add relevant tags for better organization
- Include descriptions for SEO

#### Content Structure
- Use clear headings (H1, H2, H3)
- Include code blocks with syntax highlighting
- Add images and diagrams where helpful
- Keep content scannable with bullet points and lists

#### Images and Assets
```bash
# Create organized asset directories
mkdir -p assets/images/certifications/
mkdir -p assets/images/writeups/
mkdir -p assets/images/learning/

# Reference images in your content
![Description](/assets/images/certifications/security-plus-badge.png)
```

### 🔧 Quick Commands

**Create a new certification:**
```bash
touch _certifications/$(echo "Your Certification Name" | tr '[:upper:]' '[:lower:]' | sed 's/ /-/g').md
```

**Create a new writeup:**
```bash
DATE=$(date +%Y/%m/%d)
mkdir -p _writeups/$DATE
touch _writeups/$DATE/$(echo "Your Writeup Title" | tr '[:upper:]' '[:lower:]' | sed 's/ /-/g').md
```

**Create a new learning module:**
```bash
touch _learning/$(echo "Your Learning Module" | tr '[:upper:]' '[:lower:]' | sed 's/ /-/g').md
```

### 📄 Creating Additional Pages

**Step 1: Create a new page**
```bash
# Navigate to the pages directory
cd _pages/

# Create a new page
touch resume.md
# or
touch tools.md
# or
touch resources.md
```

**Step 2: Use the page template**
```yaml
---
layout: page
title: "Your Page Title"
permalink: /your-page-url/
description: "Brief description of what this page contains"
---

# Your Page Title

Your page content goes here...

## Section 1
Content for section 1...

## Section 2
Content for section 2...
```

**Step 3: Add to navigation (optional)**
```yaml
# In _config.yml, add to the navigation section:
navigation:
  - title: "Your New Page"
    url: "/your-page-url/"
```

### 🎨 Customizing the Theme

#### Color Scheme
```scss
// In assets/css/main.scss, modify the CSS variables:
:root {
  --primary-color: #00ff88;        // Main accent color
  --secondary-color: #0066cc;      // Secondary accent color
  --accent-color: #ff6b35;         // Accent color
  --bg-primary: #0a0a0a;           // Main background
  --bg-secondary: #1a1a1a;         // Secondary background
  --text-primary: #ffffff;         // Main text color
  --text-secondary: #b0b0b0;       // Secondary text color
}
```

#### Typography
```scss
// Change fonts in assets/css/main.scss:
:root {
  --font-primary: 'Your-Font', sans-serif;
  --font-mono: 'Your-Mono-Font', monospace;
}
```

#### Layout Modifications
```html
<!-- Modify _layouts/default.html for global changes -->
<!-- Modify _layouts/home.html for homepage changes -->
<!-- Modify _layouts/page.html for standard page changes -->
```

### 📁 File Organization Tips

#### Directory Structure Best Practices
```
frogsterdev.github.io/
├── _certifications/           # All certification files
│   ├── comp-tia-security-plus.md
│   ├── aws-security-specialty.md
│   └── oscp.md
├── _writeups/                # Organized by date
│   ├── 2024/
│   │   ├── 01/
│   │   │   ├── 15/
│   │   │   │   ├── sql-injection-analysis.md
│   │   │   │   └── assets/          # Supporting files
│   │   │   └── 20/
│   │   │       └── xss-vulnerability.md
│   │   └── 02/
│   └── 2023/
├── _learning/                # Learning modules
│   ├── ethical-hacking-fundamentals.md
│   ├── cloud-security-aws.md
│   └── incident-response.md
├── _pages/                   # Static pages
│   ├── about.md
│   ├── contact.md
│   ├── resume.md
│   └── tools.md
└── assets/                   # Static assets
    ├── images/
    │   ├── certifications/   # Certification badges
    │   ├── writeups/         # Writeup screenshots
    │   └── learning/         # Learning diagrams
    ├── css/
    └── js/
```

#### Naming Conventions
- **Files**: Use kebab-case (lowercase with hyphens)
- **Directories**: Use lowercase with hyphens
- **Images**: Use descriptive names with hyphens
- **Dates**: Use YYYY-MM-DD format

### 🔍 SEO and Metadata

#### Page-Level SEO
```yaml
---
layout: page
title: "Your Page Title"
permalink: /your-url/
description: "SEO-friendly description (150-160 characters)"
keywords: "cybersecurity, security, penetration testing"
author: "Your Name"
---
```

#### Content SEO Tips
- Use descriptive headings (H1, H2, H3)
- Include alt text for images
- Add meta descriptions
- Use relevant tags
- Create internal links between related content

### 🚀 Deployment Workflow

#### Local Development
```bash
# Start development server
bundle exec jekyll serve

# Build for production
bundle exec jekyll build

# Check for errors
bundle exec jekyll build --trace
```

#### GitHub Pages Deployment
```bash
# Add and commit changes
git add .
git commit -m "Add new certification: [Certification Name]"

# Push to GitHub
git push origin main

# GitHub Actions will automatically build and deploy
```

#### Styling
- Modify `_sass/main.scss` for custom styling
- Update CSS variables in `:root` for color scheme changes
- Add custom fonts in the `_layouts/default.html`

## Content Guidelines

### Certifications
Each certification should include:
- Title and issuer
- Date earned
- Credential ID (if applicable)
- Skills gained
- Learning journey documentation

### Writeups
Technical writeups should follow this structure:
- Executive summary
- Scope and objectives
- Methodology
- Findings and impact
- Remediation recommendations
- Lessons learned

### Learning Modules
Learning progress should include:
- Learning objectives
- Progress tracking
- Resources used
- Practical applications
- Next steps

## Deployment

### GitHub Pages

1. **Push to GitHub**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

2. **Enable GitHub Pages**
   - Go to repository Settings
   - Navigate to Pages section
   - Select "GitHub Actions" as source
   - The site will build automatically

3. **Custom Domain (Optional)**
   - Add a `CNAME` file with your domain
   - Configure DNS settings as per GitHub Pages documentation

### Manual Deployment

```bash
# Build the site
bundle exec jekyll build

# Deploy to your web server
rsync -av _site/ user@server:/path/to/website/
```

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Jekyll for the static site generator
- Font Awesome for icons
- Google Fonts for typography
- The cybersecurity community for inspiration

## Support

If you have any questions or need help customizing this portfolio:

- Open an issue on GitHub
- Check the [Jekyll documentation](https://jekyllrb.com/docs/)
- Review the [GitHub Pages documentation](https://docs.github.com/en/pages)

## Roadmap

- [ ] Add dark/light theme toggle
- [ ] Implement search functionality
- [ ] Add RSS feed for writeups
- [ ] Create certification verification system
- [ ] Add interactive learning progress charts
- [ ] Implement comment system for writeups

---

**Stay secure!** 🛡️

Built with ❤️ for the cybersecurity community.
