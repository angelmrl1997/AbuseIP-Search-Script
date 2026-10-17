# AbuseIPDB Threat Intelligence Lookup (`ipsearcher.py`)

A comprehensive Python utility to inspect single IP addresses or process bulk IP lists against the **AbuseIPDB API v2**. It displays detailed information and color-coded risk bars directly in the terminal and automatically generates an interactive HTML dashboard with client-side searching and risk-based filtering.

---

## Table of Contents

1. [Features](#features)
2. [How It Works](#how-it-works)
3. [Prerequisites & Dependencies](#prerequisites--dependencies)
4. [Installation Guide](#installation-guide)
5. [Configuration & Full Script Code](#configuration--full-script-code)
6. [Usage & Execution](#usage--execution)
7. [Corporate Proxy & SSL Troubleshooting](#corporate-proxy--ssl-troubleshooting)

---

## Features

- **Single IP Lookup (`-i`)**: Checks geolocation, ISP, domain, 90-day report count, reported attack categories, and displays an ANSI color-coded confidence score bar in the terminal.
- **Bulk File Processing (`-f`)**: Extracts IPv4 addresses from text files (supports newlines, commas, spaces, or CIDR notation like `/32`), showing live terminal output for each entry.
- **Interactive HTML Dashboard**: When processing a file, automatically generates an HTML report featuring real-time search, quick filters (*All / Malicious / Suspicious / Clean*), progress bars, and risk badges.
- **Corporate Proxy & SSL Ready**: Built-in support to bypass SSL verification failures caused by corporate inspection firewalls and proxies.

---

## How It Works

1. **Query Engine**: Connects via HTTPS to the official AbuseIPDB endpoint (`https://api.abuseipdb.com/api/v2/check`) using your private API key.
2. **Category Normalization**: Parses numerical attack category IDs returned by the API (e.g., SSH, Port Scan, Brute-Force, Bad Web Bot) and translates them into human-readable labels.
3. **Regex Extraction**: When given a text file, a regular expression extracts valid IPv4 addresses and discards duplicates while preserving order.
4. **Interactive Dashboard**: The generated `.html` file is completely standalone (no external CSS/JS frameworks required) and can be opened in any web browser.

---

## Prerequisites & Dependencies

- Python 3.8+ (or Anaconda / Miniconda)
- An active API key from [AbuseIPDB](https://www.abuseipdb.com/)
- Required Python libraries:
  - `requests`
  - `urllib3`

---

## Installation Guide

### Option 1: Using Anaconda (Recommended)

1. Open **Anaconda Prompt** from the Windows Start menu.
2. Install the necessary package:
   ```bash
   conda install requests