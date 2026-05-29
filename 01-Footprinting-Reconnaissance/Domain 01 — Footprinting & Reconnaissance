# Domain 01 — Footprinting & Reconnaissance

> **Goal:** Gather maximum information about a target before any active engagement.  
> CEH Weightage: ~16% of exam

---

## What is Footprinting?

Footprinting is the first phase of ethical hacking — collecting information about the target system, network, or organization **without directly interacting** with it (passive) or by interacting carefully (active).

**Two Types:**

| Type | Description | Example Tools |
|------|-------------|---------------|
| Passive | No direct contact with target | Whois, Google Dorking, Shodan |
| Active | Direct interaction with target | Nmap, Traceroute, Ping |

---

## Key Concepts

### 1. Information to Gather
- IP address range, domain names, DNS records
- Employee names, email IDs, phone numbers
- Operating system, web server details
- Network topology, open ports

### 2. OSINT (Open Source Intelligence)
Collecting data from **publicly available sources**:
- Company website, social media, job postings
- WHOIS records, DNS records
- Search engines (Google, Bing, Shodan)
- Public databases (LinkedIn, Glassdoor)

### 3. Google Dorking (Google Hacking)
Using advanced Google search operators to find sensitive info:

| Operator | Use | Example |
|----------|-----|---------|
| `site:` | Search within a domain | `site:target.com` |
| `filetype:` | Find specific file types | `filetype:pdf site:target.com` |
| `intitle:` | Search in page title | `intitle:"index of"` |
| `inurl:` | Search in URL | `inurl:admin` |
| `cache:` | View cached page | `cache:target.com` |

### 4. DNS Footprinting
Extracting DNS records to map the network:

| Record Type | Purpose |
|-------------|---------|
| A | Maps hostname to IPv4 address |
| AAAA | Maps hostname to IPv6 address |
| MX | Mail server records |
| NS | Name server records |
| CNAME | Canonical name (alias) |
| PTR | Reverse DNS lookup |
| SOA | Start of Authority |

---

## Tools Used

### Whois
```bash
whois target.com
whois <IP-address>
```
Reveals: Domain owner, registrar, registration dates, name servers

### nslookup
```bash
nslookup target.com
nslookup -type=mx target.com       # Mail servers
nslookup -type=ns target.com       # Name servers
nslookup -type=any target.com      # All records
```

### dig (Domain Information Groper)
```bash
dig target.com
dig target.com MX                  # Mail records
dig target.com NS                  # Name servers
dig target.com ANY                 # All records
dig -x <IP>                        # Reverse lookup
dig axfr @nameserver target.com    # Zone transfer attempt
```

### theHarvester
```bash
theHarvester -d target.com -b google       # Google search
theHarvester -d target.com -b linkedin     # LinkedIn
theHarvester -d target.com -b all          # All sources
```
Collects: Email IDs, subdomains, IPs, employee names

### Maltego
- GUI-based OSINT tool
- Maps relationships between people, orgs, domains, IPs
- Uses "transforms" to gather and visualize data

### Shodan
- Search engine for internet-connected devices
- Reveals: Open ports, banners, software versions
- Example: `shodan search "apache" country:"IN"`

### Recon-ng
```bash
recon-ng
marketplace install all
workspaces create target_name
modules load recon/domains-hosts/google_site_web
options set SOURCE target.com
run
```

---

## Techniques

### Email Footprinting
- Find email format (firstname.lastname@company.com)
- Tools: Hunter.io, theHarvester, LinkedIn
- Email headers reveal: originating IP, mail server, timestamp

### Website Footprinting
- `robots.txt` — reveals hidden directories
- `sitemap.xml` — lists all website pages
- View page source, check comments for sensitive info
- Wayback Machine (archive.org) — view old versions of site

### Network Footprinting
- Traceroute — maps network path to target
```bash
traceroute target.com      # Linux
tracert target.com         # Windows
```

### Social Engineering Recon
- LinkedIn: Employee names, designations, technologies used
- Job postings: Reveal tech stack (e.g., "Must know AWS, Docker")
- GitHub: Leaked credentials, internal code

---

## Countermeasures

- Restrict WHOIS information (use domain privacy)
- Disable zone transfers on DNS servers
- Configure `robots.txt` carefully
- Implement email security (SPF, DKIM, DMARC)
- Monitor for OSINT exposure regularly
- Train employees on social engineering awareness

---

## CEH Exam Tips

- Know the difference between active vs passive footprinting
- Remember which tools are used for which purpose
- Whois → domain info; theHarvester → emails; Maltego → visualization
- Zone transfer (`dig axfr`) is a common exam scenario
- Google dorks are frequently tested

---

## Lab Exercise

**Objective:** Perform passive footprinting on a target domain (use your own domain or a practice site like `scanme.nmap.org`)

```bash
# Step 1: WHOIS lookup
whois scanme.nmap.org

# Step 2: DNS records
dig scanme.nmap.org ANY

# Step 3: Email harvesting
theHarvester -d nmap.org -b google -l 50

# Step 4: Traceroute
traceroute scanme.nmap.org
```

> ⚠️ Only perform on authorized targets. `scanme.nmap.org` is explicitly authorized by Nmap for scanning practice.
