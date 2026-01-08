<h1 align="center">
  ShellHunter
</h1>

<p align="center">
  A comprehensive security testing tool for identifying Shellshock (CVE-2014-6271) vulnerabilities in web applications
<br/><br/>
  
<img alt="Python 3.8" src="https://img.shields.io/badge/python-3.8-yellow.svg">
<img alt="Supported_OS Linux orange" src="https://img.shields.io/badge/Supported_OS-Linux-orange.svg">
<img alt="Supported OS Mac" src="https://img.shields.io/badge/Supported_OS-Mac-orange.svg">
</p>

---

## ⚠️ Legal Disclaimer

**THIS TOOL IS FOR AUTHORIZED SECURITY TESTING ONLY**

ShellHunter is designed for security professionals and researchers to test systems **with explicit authorization**. Unauthorized access to computer systems is illegal and punishable by law.

### Important Legal Notices:

- ✅ **DO**: Use this tool only on systems you own or have written permission to test
- ✅ **DO**: Ensure you have proper authorization before conducting any security assessments
- ✅ **DO**: Follow responsible disclosure practices when vulnerabilities are found
- ✅ **DO**: Comply with all applicable local, state, and federal laws

- ❌ **DO NOT**: Use this tool on systems without explicit written authorization
- ❌ **DO NOT**: Use this tool for malicious purposes or illegal activities
- ❌ **DO NOT**: Attempt to exploit vulnerabilities for unauthorized access

**By using ShellHunter, you agree to use it responsibly and legally. The authors and contributors are not responsible for any misuse or damage caused by this tool.**

---

## 📖 About ShellHunter

ShellHunter is a Python-based security tool designed to identify and test for Shellshock vulnerabilities in web applications and servers. It provides penetration testers and security researchers with a robust framework for detecting CVE-2014-6271 and related bash vulnerabilities through automated testing of Common Gateway Interface (CGI) endpoints.

The tool supports multi-threaded scanning, custom payload execution, and comprehensive reporting, making it an essential utility for security assessments and vulnerability research.

---

## 🐚 What is Shellshock?

**Shellshock** (also known as **Bashdoor**) is a family of critical security vulnerabilities in the Unix Bash shell, first disclosed on September 24, 2014. The vulnerability affects Bash versions 1.14 through 4.3.

### Technical Overview:

Shellshock allows attackers to execute arbitrary commands by exploiting the way Bash processes environment variables. When Bash is invoked by applications (particularly web servers using CGI scripts), specially crafted environment variables can contain malicious code that gets executed automatically.

### Impact:

- **Remote Code Execution (RCE)**: Attackers can execute arbitrary commands on vulnerable systems
- **Unauthorized Access**: Gain control of web servers and network services
- **Data Breach**: Access sensitive information and system resources
- **Lateral Movement**: Use compromised systems to attack other network resources

### CVE References:
- CVE-2014-6271 (Original Shellshock)
- CVE-2014-7169 (Incomplete fix)
- CVE-2014-7186 & CVE-2014-7187 (Additional vectors)

---

## ✨ Features

- 🎯 **Multi-target Scanning**: Test individual hosts, IP ranges, or import target lists from files
- 🧵 **Multi-threaded Operations**: Fast scanning with configurable thread pools
- 🔧 **Custom Payloads**: Define custom shell commands for payload execution
- 🔍 **Multiple Exploit Variants**: Test all known Shellshock payload variations
- 🌐 **CGI Path Discovery**: Automated testing of common CGI endpoints
- 🔐 **SSL/TLS Support**: Test HTTPS-enabled web applications
- 📊 **Comprehensive Reporting**: Detailed output logs for vulnerable targets
- ⚡ **Automatic Exploitation**: Execute commands on identified vulnerable systems
- 🐛 **Debug Mode**: Detailed debugging information for troubleshooting
- 📝 **Configurable Timeouts**: Adjust connection timeouts for different network conditions
- 🎨 **Color-coded Output**: Easy-to-read terminal output with status indicators

---

## 📋 Requirements

### System Requirements:
- **Operating System**: Linux or macOS
- **Python Version**: Python 3.8 or higher

### Python Dependencies:
- `urllib3` - HTTP client library
- `shodan` - Shodan API integration (optional)
- `ipinfo` - IP information lookup (optional)

---

## 🚀 Installation

### Step 1: Clone the Repository

```bash
git clone https://github.com/httpEduardo/ShellTHEbest.git
cd ShellTHEbest
```

### Step 2: Install Python Dependencies

Using pip package manager:

```bash
pip install shodan
pip install ipinfo
```

Or install all dependencies at once:

```bash
pip install urllib3 shodan ipinfo
```

### Step 3: Verify Installation

Check if the tool is working correctly:

```bash
python main.py --help
```

You should see the ShellHunter banner and help menu.

---

## 🎯 Quick Start Guide

### Basic Vulnerability Check

Test a single target for Shellshock vulnerability:

```bash
python main.py --file targets.txt --check
```

### Scan an IP Range

Test multiple hosts in an IP range:

```bash
python main.py --range 192.168.1.1,192.168.1.100 --check
```

### Execute Custom Command

Test with a custom shell command:

```bash
python main.py --file targets.txt --cmd-cgi "whoami" --thread 20
```

---

## 📚 Usage Examples

### Example 1: Check Single Target from File

Create a file `targets.txt` with your target URLs:
```
http://example.com
http://testsite.com
```

Run the scan:
```bash
python main.py --file targets.txt --check --thread 10
```

### Example 2: Scan IP Range with SSL

```bash
python main.py --range 10.0.0.1,10.0.0.254 --ssl --check --timeout 10
```

### Example 3: Test All Shellshock Payloads

```bash
python main.py --file targets.txt --all --check
```

### Example 4: Execute Commands on Vulnerable Targets

```bash
python main.py --file targets.txt --check --exec-vuln "cat /etc/passwd"
```

### Example 5: Custom CGI Path Testing

```bash
python main.py --file targets.txt --cgi-file custom_cgi.txt --check
```

### Example 6: Debug Mode

Enable detailed debugging output:
```bash
python main.py --file targets.txt --check --debug
```

---

## 🔧 Command Reference

| Argument | Short | Description | Example |
|----------|-------|-------------|---------|
| `--help` | `-h` | Display help message and exit | `--help` |
| `--file` | | Input target host list from file | `--file targets.txt` |
| `--range` | | Define IP range for scanning | `--range 192.168.1.1,192.168.1.100` |
| `--cmd-cgi` | | Define shell command to execute in payload | `--cmd-cgi "whoami"` |
| `--exec-vuln` | | Execute commands on vulnerable targets | `--exec-vuln "cat /etc/passwd"` |
| `--thread` | `-t` | Set number of concurrent threads | `--thread 20` |
| `--check` | | Check for Shellshock vulnerability | `--check` |
| `--ssl` | | Enable HTTPS requests | `--ssl` |
| `--cgi-file` | | Define custom CGI wordlist file | `--cgi-file wordlist/cgi.txt` |
| `--timeout` | | Set connection timeout (seconds) | `--timeout 5` |
| `--all` | | Test all available payloads | `--all` |
| `--debug` | `-d` | Enable debug mode | `--debug` |

---

## 📁 Project Structure

```bash
├── assets/
│   ├── autor.json          # Author information
│   ├── config.json         # Configuration settings
│   ├── exploits.json       # Shellshock exploit payloads
│   └── prints/             # Screenshots and images
│       ├── banner.png
│       ├── print00.png
│       ├── print01.png
│       ├── print02.png
│       └── print03.png
├── modules/
│   ├── __init__.py
│   ├── banner_shock.py     # Banner display module
│   ├── color_shock.py      # Terminal color formatting
│   ├── debug_shock.py      # Debug functionality
│   ├── file_shock.py       # File operations handler
│   ├── request_shock.py    # HTTP request handler
│   ├── shodan_shock.py     # Shodan API integration
│   └── thread_shock.py     # Multi-threading handler
├── output/
│   └── vuln.txt            # Vulnerability scan results
├── wordlist/
│   └── cgi.txt             # Common CGI paths
├── LICENSE                 # GNU GPL v3 License
├── main.py                 # Main application entry point
└── README.md               # This file
```

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve ShellHunter, please follow these guidelines:

### How to Contribute:

1. **Fork the Repository**: Create your own fork of the project
2. **Create a Branch**: Make a new branch for your feature (`git checkout -b feature/AmazingFeature`)
3. **Make Changes**: Implement your improvements or bug fixes
4. **Test Thoroughly**: Ensure your changes don't break existing functionality
5. **Commit Changes**: Write clear, descriptive commit messages (`git commit -m 'Add some AmazingFeature'`)
6. **Push to Branch**: Push your changes to your fork (`git push origin feature/AmazingFeature`)
7. **Open Pull Request**: Submit a PR with a detailed description of your changes

### Contribution Ideas:

- 🐛 Bug fixes and error handling improvements
- 📚 Documentation enhancements
- 🆕 New exploit payload variants
- ⚡ Performance optimizations
- 🧪 Test coverage improvements
- 🌐 Additional protocol support

---

## 🛡️ Responsible Disclosure

If you discover a vulnerability using this tool:

1. **Do Not** publicly disclose the vulnerability immediately
2. **Contact** the affected organization through their security contact or responsible disclosure program
3. **Provide** detailed information about the vulnerability, including steps to reproduce
4. **Allow** reasonable time (typically 90 days) for the organization to patch the issue
5. **Coordinate** public disclosure timing with the affected organization

This approach helps protect users while ensuring vulnerabilities are properly addressed.

---

## 📜 License

This project is licensed under the **GNU General Public License v3.0** (GPL-3.0).

You are free to:
- ✅ Use the software for any purpose
- ✅ Study how the program works and modify it
- ✅ Redistribute copies
- ✅ Distribute modified versions

**Conditions:**
- 📢 Disclose source code when distributing
- 📢 License derivative works under GPL-3.0
- 📢 State changes made to the code
- 📢 Include the original copyright notice

See the [LICENSE](LICENSE) file for full license text.

---

## 📚 References

### Shellshock Vulnerability Information:
- [Wikipedia: Shellshock (software bug)](https://en.wikipedia.org/wiki/Shellshock_(software_bug))
- [CVE-2014-6271 Details](https://nvd.nist.gov/vuln/detail/CVE-2014-6271)
- [NIST: Shellshock CVE-2014-7186 & CVE-2014-7187](https://en.wikipedia.org/wiki/Shellshock_(software_bug)#CVE-2014-7186_and_CVE-2014-7187_Details)

### Technical Resources:
- [Exploit Database: CVE-2014-6271](https://github.com/opsxcq/exploit-CVE-2014-6271)
- [Brazilian Tech Blog: Shellshock Analysis](https://blog.inurl.com.br/search?q=shellshock)
- [Manual do Usuário: Shellshock Bash Vulnerability](https://manualdousuario.net/shellshock-bash-falha/)
- [Darren Martyn: VisualDoor SonicWall SSL-VPN Exploit](https://darrenmartyn.ie/2021/01/24/visualdoor-sonicwall-ssl-vpn-exploit)

---

## 🗺️ Roadmap

This project was created to study Python programming and interact with APIs like Shodan and IPinfo.

**Completed Features:**
* ✅ Command-line interface structure
* ✅ ASCII banner display
* ✅ File management class
* ✅ HTTP request management class
* ✅ Shell execution on vulnerable targets
* ✅ Process debugging capabilities

**Future Enhancements:**
* ⬜ Web-based dashboard interface
* ⬜ Enhanced reporting with HTML/PDF output
* ⬜ Integration with additional vulnerability databases
* ⬜ Support for authenticated scans
* ⬜ Docker containerization
* ⬜ CI/CD integration examples

---

## 👤 Author

**Created by:** VOID (Cleiton Pinheiro / Mr. Cl0wn)

---

## ⭐ Support

If you find ShellHunter useful, please consider:
- ⭐ Starring the repository
- 🐛 Reporting bugs and issues
- 💡 Suggesting new features
- 🤝 Contributing code improvements

---

**Remember: Always obtain proper authorization before testing any systems. Unauthorized access is illegal and unethical.**
