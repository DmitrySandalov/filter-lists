# Filter Lists

A collection of filter lists for [uBlock Origin](https://github.com/gorhill/uBlock) and other ad/content blockers.

## Available Lists

### Microsoft Attack Simulation Training Domains

Blocks phishing-simulation URL domains used by Microsoft Defender for Office 365 Attack Simulation Training.

| Format | File | Description |
|--------|------|-------------|
| **Adblock Plus** (uBlock Origin, AdGuard, etc.) | [`ms-attack-simulation-domains.txt`](ms-attack-simulation-domains.txt) | `||domain^` syntax, blocks domain + subdomains |
| **Hosts file** (Pi-hole, /etc/hosts, etc.) | [`ms-attack-simulation-domains-hosts.txt`](ms-attack-simulation-domains-hosts.txt) | `127.0.0.1 domain` syntax, system-wide blocking |

**Domains:** 130+ (auto-updated weekly)  
**Source:** [Microsoft Learn - Get started using Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started)  
**Update Schedule:** Weekly on Mondays via GitHub Actions  
**License:** GPL-3.0  

#### Usage

**Adblock Plus format (uBlock Origin, AdGuard, etc.):**

*Option 1: Direct URL import (simplest)*
1. Open uBlock Origin Dashboard → Filter lists → Import
2. Paste: `https://raw.githubusercontent.com/DmitrySandalov/filter-lists/main/ms-attack-simulation-domains.txt`
3. Click "Apply changes"

*Option 2: Via custom assets.json (appears in built-in list picker)*
1. Create a custom assets.json with the entry from [`assets.json.entry`](assets.json.entry)
2. In uBO: Settings → Filter lists → Import → paste your assets.json URL
3. Enable "Microsoft Attack Simulation Training domains" under Security group

**Hosts file format (Pi-hole, /etc/hosts, routers, etc.):**
- Pi-hole: Group Management → Adlists → Add: `https://raw.githubusercontent.com/DmitrySandalov/filter-lists/main/ms-attack-simulation-domains-hosts.txt`
- /etc/hosts: Append contents of the file
- Router DNS blocking: Use the URL in your router's blocklist feature

**Note:** Both formats block the domain and all subdomains (including www). Blocking these domains will hide clicks from your own simulation reports.

## Auto-Update

The lists are automatically updated weekly via [GitHub Actions](.github/workflows/update-ms-attack-simulation.yml):
- Fetches the latest domains from Microsoft Learn
- Regenerates both Adblock Plus and hosts file formats with updated version/date
- Commits changes only if domains have changed

To trigger manually: [Run workflow](https://github.com/DmitrySandalov/filter-lists/actions/workflows/update-ms-attack-simulation.yml)

## License

[GPL-3.0](LICENSE) - Free to use, modify, and distribute.