# BlitzMap

**BlitzMap** is a fast, threaded Nmap wrapper for scanning subdomains, extracting open ports, and filtering noisy results. It’s built for easy automation in reconnaissance workflows like bug bounty hunting, red teaming, or infrastructure auditing.

## 🔍 Features

- ✅ Reads subdomains from a file  
- 🚀 Launches concurrent Nmap scans on each subdomain  
- 🧠 Parses the output to extract open ports  
- 🔇 Filters noisy hosts with too many open ports (default: >100)  
- 💾 Saves filtered `host:port` pairs to `good_ports.txt`  

## 📦 Requirements

- Python 3.6 or higher
- [`nmap`](https://nmap.org/) installed and accessible in your `$PATH`

## 📁 Installation

Clone this repository:

```bash
git clone https://github.com/M4rgs/BlitzMap.git
cd BlitzMap
```

Make sure Nmap is installed:

```bash
nmap --version
```

## ⚙️ Usage

1. **Create a file of subdomains**, e.g., `subs.txt`:

```
api.example.com
login.example.com
shop.example.com
```

2. **Run the script**:

```bash
python3 BlitzMap.py subs.txt
```

3. After scanning, you'll get:
- Output files per subdomain (e.g., `api.example.com.out`)
- Final filtered results in:  
  👉 `good_ports.txt`

## 📝 Output Example

Example contents of `good_ports.txt`:

```
api.example.com:443
login.example.com:80
shop.example.com:8080
```

## ⚠️ Notes

- The script scans **all 65535 TCP ports** using Nmap’s `-p-` option. Runtime depends on network and target size.
- Hosts with excessive open ports (e.g., wildcard domains, load balancers) are filtered by default.
- You can adjust concurrency in the script by modifying `max_concurrent_scans` (default is `15`).


