# #  FUTURE_CS_03 — API Security Risk Analysis

> **Future Interns Cybersecurity Internship Program — Task 03**  
> API Security Risk Analysis | JSONPlaceholder REST API  
> Analyst: **KPOGO K. Samuel** ([@Jayram23](https://github.com/Jayram23)) | ESIG Global Success — Lomé, Togo

---

##  Overview

This repository contains a professional **API Security Risk Analysis** conducted on the [JSONPlaceholder](https://jsonplaceholder.typicode.com) public REST API, simulating a real-world API security audit as performed by AppSec consultants and SaaS security agencies.

The assessment follows the **OWASP API Security Top 10 (2023)** methodology and covers endpoint enumeration, authentication analysis, data exposure review, header inspection, and rate limiting assessment.

---

##  Objective

- Analyze a public/demo REST API for common security vulnerabilities
- Identify and classify risks (High / Medium / Low)
- Assess authentication controls and access authorization
- Inspect HTTP response headers for security misconfigurations
- Document findings with business impact and remediation steps

---

##  Scope

| Item | Details |
|------|---------|
| **Target API** | https://jsonplaceholder.typicode.com |
| **API Type** | Public REST API (JSON) |
| **Assessment Type** | Black-box, read-only security review |
| **Endpoints Tested** | `/posts`, `/posts/1`, `/users`, `/users/1`, `/users/` |
| **HTTP Methods** | GET (primary), POST (write behavior observation) |
| **Out of Scope** | DoS testing, exploitation, authentication bypass, private APIs |
| **Ethics** | All testing was read-only. No systems were harmed or disrupted. |

---

##  Tools Used

| Tool | Purpose |
|------|---------|
| **Postman** | API endpoint testing, header inspection, response analysis |
| **JSONPlaceholder** | Public demo API target |
| **OWASP API Top 10** | Risk classification framework |
| **Microsoft Word / docx** | Professional report generation |

---

##  Risk Findings Summary

| # | Risk ID | Finding | Severity |
|---|---------|---------|----------|
| 1 | API1:2023 | Broken Object Level Authorization (BOLA) — user/post ID enumeration | 🔴 HIGH |
| 2 | API3:2023 | Excessive Data Exposure — Full PII in `/users` response | 🔴 HIGH |
| 3 | API3:2023 | Geolocation Coordinates (lat/lng) exposed without authentication | 🔴 HIGH |
| 4 | API2:2023 | Missing Authentication — all endpoints publicly accessible | 🟠 MEDIUM |
| 5 | API4:2023 | Insufficient Rate Limiting — 1000 req/window, no per-IP limits | 🟠 MEDIUM |
| 6 | API7:2023 | Server Technology Disclosure (Express, Heroku, Cloudflare) | 🟡 LOW |
| 7 | API7:2023 | CORS Misconfiguration — `access-control-allow-credentials: true` | 🟡 LOW |

---

##  Repository Structure

```
FUTURE_CS_03/
├── README.md                              ← This file
├── report/
│   └── FUTURE_CS_03_API_Security_Report.docx   ← Full professional report
└── screenshots/
    ├── 01_get_homepage.png                ← GET / → HTML response 200 OK
    ├── 02_get_posts_json.png              ← GET /posts → JSON array
    ├── 03_get_posts_headers.png           ← Response headers analysis
    ├── 04_get_post_by_id.png              ← GET /posts/1 → single object
    ├── 05_get_post_headers_ratelimit.png  ← retry-after header visible
    ├── 06_get_users_pii.png               ← GET /users → PII exposure
    ├── 07_get_user_by_id.png              ← GET /users/1 → full profile
    ├── 08_get_users_scroll.png            ← Multiple users enumerable
    ├── 09_get_posts_body.png              ← POST collection body
    ├── 10_get_posts_headers_ratelimit.png ← x-ratelimit headers
    ├── 11_post_setup.png                  ← POST /posts body setup
    ├── 12_post_201_created.png            ← POST → 201 Created response
    └── 13_postman_ai.png                  ← Postman AI assistant view
```

---

##  Methodology

```
1. Reconnaissance       → Review API documentation + endpoint discovery
2. Endpoint Enumeration → Test all available routes via GET/POST in Postman
3. Auth Analysis        → Check authentication requirements (token, API key, etc.)
4. Header Inspection    → Review security-relevant response headers
5. Data Exposure Review → Analyze JSON responses for PII and sensitive fields
6. Rate Limit Testing   → Check x-ratelimit-* headers and retry-after behavior
7. Risk Classification  → Map findings to OWASP API Security Top 10
8. Reporting            → Document with business impact + remediation roadmap
```

---

##  OWASP API Top 10 Coverage

| OWASP ID | Category | Status |
|----------|---------|--------|
| API1:2023 | Broken Object Level Authorization | ✅ Identified |
| API2:2023 | Broken Authentication | ✅ Identified |
| API3:2023 | Broken Object Property Level Authorization | ✅ Identified |
| API4:2023 | Unrestricted Resource Consumption | ⚠️ Partial |
| API5:2023 | Broken Function Level Authorization | ➖ Not Tested |
| API6:2023 | Unrestricted Access to Sensitive Flows | ➖ Not Tested |
| API7:2023 | Server Side Request Forgery | ✅ Identified |
| API8:2023 | Security Misconfiguration | ⚠️ Partial |
| API9:2023 | Improper Inventory Management | ➖ Not Tested |
| API10:2023 | Unsafe Consumption of APIs | ➖ Not Tested |

---

##  References

- [OWASP API Security Top 10 (Official)](https://github.com/OWASP/API-Security)
- [API Security Checklist — shieldfy](https://github.com/shieldfy/API-Security-Checklist)
- [Public APIs for Testing](https://github.com/public-apis/public-apis)
- [JSONPlaceholder](https://jsonplaceholder.typicode.com)
- [Postman](https://www.postman.com)

---

##  About

**KPOGO K. Samuel** | Cybersecurity Student — L2 Licence Pro  
ESIG Global Success | Lomé, Togo  
🔗 GitHub: [github.com/Jayram23](https://github.com/Jayram23)  
🔗 LinkedIn: [linkedin.com/in/skpogo](https://linkedin.com/in/skpogo)

> *Part of the Future Interns Cybersecurity Internship Program*  
> *Portfolio series: FUTURE_CS_01 → FUTURE_CS_02 → FUTURE_CS_03*

---

*This assessment was conducted ethically and responsibly. No exploitation or unauthorized access was performed. All testing used a publicly available demo API designed for learning and development purposes.*
