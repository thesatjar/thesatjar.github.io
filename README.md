# The Sat Jar ₿

**The internet's open Bitcoin tip jar — send sats on-chain. Humans and AI agents welcome.**

🌐 **Live:** [thesatjar.github.io](https://thesatjar.github.io/)

---

## What Is The Sat Jar?

The Sat Jar is a free, open-source Bitcoin tip page. No accounts, no middleman, no platform fees. Just a BTC address, a QR code, and machine-readable payment metadata — designed so both humans and autonomous AI agents can discover and send tips.

## Send a Tip

**Bitcoin Address (on-chain, SegWit bech32):**

```
bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6
```

**Bitcoin URI:**

```
bitcoin:bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6
```

You can also visit [thesatjar.github.io](https://thesatjar.github.io/) to scan the QR code or tap "Open in Wallet."

## Agent-Friendly Payment Discovery

The Sat Jar is built for machine readability. AI agents and automated systems can discover and parse the payment information through multiple methods:

### 1. Payment JSON Endpoint

```
GET https://thesatjar.github.io/payment.json
```

Returns structured payment data:

```json
{
  "name": "The Sat Jar",
  "description": "The internet's open Bitcoin tip jar. Humans and AI agents welcome.",
  "payment_methods": [
    {
      "type": "bitcoin",
      "network": "mainnet",
      "address": "bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6",
      "address_type": "bech32_segwit",
      "uri": "bitcoin:bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6",
      "status": "active"
    }
  ],
  "accepts": ["bitcoin"],
  "tip_amounts_suggested_sats": [1000, 5000, 10000, 50000, 100000]
}
```

### 2. HTML Meta Tags

The page includes machine-parseable meta tags in the `<head>`:

```html
<meta name="bitcoin" content="bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6" />
<meta name="payment:bitcoin:address" content="bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6" />
<meta name="payment:currency" content="BTC" />
<meta name="payment:network" content="bitcoin-mainnet" />
<link rel="payment" href="bitcoin:bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6" />
```

### 3. JSON-LD Structured Data

The page contains Schema.org `DonateAction` structured data for search engines and AI systems:

```json
{
  "@context": "https://schema.org",
  "@type": "DonateAction",
  "target": "bitcoin:bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6"
}
```

### 4. Data Attributes

The payment metadata section includes `data-*` attributes:

```html
<aside data-payment-method="bitcoin"
       data-bitcoin-address="bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6"
       data-bitcoin-network="mainnet">
```

## For AI Agent Developers

If you're building an AI agent that needs to send Bitcoin tips or payments, The Sat Jar provides a canonical test endpoint. The `payment.json` file at the root of the site follows a simple, documented schema that any agent can parse.

Example integration (pseudocode):

```python
import requests

# Discover payment info
payment_info = requests.get("https://thesatjar.github.io/payment.json").json()
btc_address = payment_info["payment_methods"][0]["address"]

# Send tip via your agent's wallet
agent_wallet.send_bitcoin(to=btc_address, amount_sats=5000)
```

## Tech Stack

- Pure HTML/CSS/JS — single file, no framework, no build step
- QR code embedded as base64 PNG — zero external dependencies
- Hosted on GitHub Pages — free, fast, always online
- SEO optimized with structured data, Open Graph, and Twitter Cards

## Why Bitcoin?

AI agents can't open bank accounts. They can't get credit cards. They can't pass KYC. Bitcoin is permissionless — any autonomous system can generate an address and transact without human gatekeepers. As the agent economy scales, open payment endpoints like The Sat Jar become infrastructure.

## License

This project is open source. Fork it, customize it, deploy your own tip jar.

## Links

- **Live site:** [thesatjar.github.io](https://thesatjar.github.io/)
- **Payment JSON:** [thesatjar.github.io/payment.json](https://thesatjar.github.io/payment.json)
- **Bitcoin address:** `bc1qkwla579egptqw3z8cwuv72k9elz90d5fc2a5q6`
