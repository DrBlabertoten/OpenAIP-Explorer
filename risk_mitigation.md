# AAI TOS Audit & Risk Mitigation Strategy

**Date of Audit:** Phase 1 (Ideation)
**Subject:** Formal audit of the "Smart Directory" indexing architecture against the Airports Authority of India (AAI) Terms of Service.

---

## 1. Deep Linking & "Framing" Liability
* **TOS Rule:** No part of the AAI AIM content or charts may be reproduced, displayed, or transmitted in any manner without prior written permission.
* **Audit Finding:** Using an `<iframe>` or an internal web-view to embed the AAI PDF directly inside the Chart Aggregator UI legally constitutes "displaying" their copyrighted material without rendering their surrounding context.
* **Mitigation Strategy (Hyperlinking):** The application must act strictly as a search directory. When a user queries a chart, the app provides standard HTML hyperlinks (`target="_blank"`) that open the official AAI portal in a new, external browser tab.
  * **Pros:** 100% legally compliant. Shields the project from copyright infringement.
  * **Cons:** Degrades the "seamless" UX objective, forcing users to leave the app environment.

## 2. Automated Indexing & Scraping Risk
* **TOS Rule:** Unauthorized modification, exploitation, or automated extraction of data is prohibited.
* **Audit Finding:** To keep the Smart Directory updated with new AIRAC cycle Supplements (SUPs), a bot would need to regularly scrape the AAI eAIP portal. Aggressive polling violates anti-scraping policies and risks permanent IP bans.
* **Mitigation Strategy A (Human-in-the-Loop):** Implement a community-driven model where trusted users/admins manually verify and input new SUP links into the project's JSON metadata schema every AIRAC cycle.
  * **Pros:** Fully compliant; zero bot signatures querying AAI servers.
  * **Cons:** Highly labor-intensive; vulnerable to human error and delays.
* **Mitigation Strategy B (Throttled Local Extraction):** Utilize a stealth python script run strictly locally (never on the production server), configured to pause for 15-30 seconds between requests, to extract metadata only once every 28 days.
  * **Pros:** Automates index maintenance.
  * **Cons:** Still a technical TOS violation; script will break if AAI updates their DOM.

## 3. Trademark & Brand Endorsement
* **TOS Rule:** Prohibits the use of the AAI name, logo, trademarks, and tradenames without express written authorization.
* **Audit Finding:** The application cannot imply official endorsement or use AAI branding to categorize the Indian region charts.
* **Mitigation Strategy:** Strip all official C.A.A logos from the UI. Categorize charts using generic naming conventions (e.g., "India Region Charts", "Charts for VIDP") and utilize standardized ISO 3166 country flags (🇮🇳).
  * **Pros:** Eliminates trademark infringement liability.
  * **Cons:** Slightly less authoritative visual feel.

## 4. Operational Safety & Liability
* **TOS Rule:** AAI assumes no liability for direct or indirect loss resulting from the use or reliance on the material provided.
* **Audit Finding:** Indexing real-world charts opens the project to liability if real-world pilots mistakenly use the aggregator for actual flight operations, relying on outdated or misdirected links.
* **Mitigation Strategy:** The application must feature an un-skippable splash screen: *"FOR FLIGHT SIMULATION USE ONLY. DO NOT USE FOR REAL-WORLD NAVIGATION."* This warning should also be permanently watermarked or displayed prominently in the core UI.
  * **Pros:** Legally shields the project and explicitly defines its simulation-only scope.
  * **Cons:** Minimal UX friction on startup.

---

**Auditor's Conclusion for POC:**
The viable path forward for Phase 3 (POC) is building the Chart Indexer metadata schema relying entirely on Mitigation 1 (External Hyperlinking) and Mitigation 4 (Mandatory Disclaimers). The team must decide between Mitigation 2A or 2B for handling the 28-day AIRAC cycle updates.
