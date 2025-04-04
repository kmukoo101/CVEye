# CVEye

**CVEye** is a cross-platform vulnerability scanner written in Python, aimed to help network defenders and cybersecurity students identify open ports, outdated services, weak credentials, and CVEs. 

---

## Features

- Scans all privileged TCP and UDP ports
- Banner grabbing for service detection
- CVE detection using flexible regex patterns (`cve_hints.json`)
- Credential brute-force attempts (FTP, MySQL)
- Threaded scanning for speed
- Saves results as `.log` and `.json`
- Runs on macOS, Windows, Linux

---

## ⚙ Requirements

- Python 3.6 or higher  
- Optional:  
  - `pymysql` → for MySQL brute-force  
  - `ftplib` → included in standard library

Install optional module:
```bash
pip install pymysql
```

---

## Usage

### Run scanner
```bash
python cveye.py 192.168.1.10
```

### Optional Arguments
```bash
--start-port      Start of port range (default: 1)
--end-port        End of port range (default: 1024)
--no-udp          Disable UDP scanning
```

Example:
```bash
python cveye.py 10.0.0.5 --start-port 20 --end-port 100 --no-udp
```

---

## CVE Matching

This tool uses a file called `cve_hints.json` to match known service banners to vulnerabilities
(FTP, SSH, HTTP Servers, SMB, Mail Servers, SQL, RDP / Windows Services, Telnet and other services.) 

Example `cve_hints.json`:
```json
{
    "vsftpd 2\\.3\\.4": "CVE-2011-2523",
    "ProFTPD 1\\.3\\.5": "CVE-2015-3306",
    "Pure-FTPd 1\\.0\\.21": "CVE-2005-1125",
    "OpenSSH_7\\.2p2": "CVE-2016-10012",
    "OpenSSH_6\\.6\\.1": "CVE-2015-5600",
    "Dropbear sshd 2016\\.72": "CVE-2016-7406",
    "Apache/2\\.2\\.8": "CVE-2009-1890",
    "Apache/2\\.4\\.49": "CVE-2021-41773",
    "Apache/2\\.4\\.50": "CVE-2021-42013",
    "nginx/1\\.4\\.0": "CVE-2013-2028",
    "nginx/1\\.20\\.0": "CVE-2021-23017",
    "Microsoft-IIS/6\\.0": "CVE-2017-7269",
    "Samba 3\\.0\\.0": "CVE-2003-0201",
    "Samba 4\\.7\\.0": "CVE-2017-12150",
    "Exim 4\\.87": "CVE-2016-1531",
    "Exim 4\\.92": "CVE-2019-15846",
    "Postfix 2\\.9\\.6": "CVE-2014-2270",
    "MySQL 5\\.5\\.20": "CVE-2012-2122",
    "MySQL 5\\.1\\.63": "CVE-2012-0112",
    "MariaDB 10\\.1\\.37": "CVE-2019-2503",
    "Remote Desktop Protocol 6\\.1": "CVE-2012-0152",
    "RDP 5\\.2": "CVE-2003-0812",
    "NetKit telnet 0\\.17": "CVE-2001-0554",
    "Lighttpd/1\\.4\\.35": "CVE-2014-2323",
    "Jetty/9\\.4\\.18": "CVE-2020-27216",
    "OpenVPN 2\\.4\\.1": "CVE-2017-7479"
}
```

---

## Output

- `scan_results_YYYYMMDD_HHMMSS.log` → human-readable log
- `scan_results_YYYYMMDD_HHMMSS.json` → machine-readable output

Includes:
- Open ports
- CVEs matched
- Successful login credentials

---

## ⚠ Legal Notice

**CVEye is for authorized testing and educational purposes only.**  
Do not scan networks you don’t own or have explicit permission to audit.

