Terminal snapshot:

![alt text](image.png)
---

MD file created:

# Intelligence Brief: ElevenLabs

**Generated:** 2026-06-06
**URL:** https://elevenlabs.io/
**Meeting:** Meeting with CEO (Mati Staniszewski)

---

## Phase 1 — Company Overview

### What Is It?
ElevenLabs is an AI audio company building the foundational infrastructure for voice and sound across three platforms — enterprise voice agents (ElevenAgents), creator-facing audio generation (ElevenCreative), and developer APIs (ElevenAPI) — spanning 70+ languages. The central bet: voice will become the dominant interface for human-technology interaction, and ElevenLabs will own the full audio stack end-to-end.

### Founders & Team
| Name | Role | Background |
|------|------|-----------|
| Mati Staniszewski | CEO & Co-founder | Mathematics, Imperial College London; ex-BlackRock (Portfolio Analytics, Aladdin Wealth launch); ex-Palantir (Deployment Strategist); TIME100 AI 2025 |
| Piotr Dabkowski | CTO & Co-founder | Ex-Google (ML research); MPhil; leads research and engineering on audio models |

**Team size:** > **Educated guess:** ~300–500 employees, based on scale of enterprise operations, offices in San Francisco and Warsaw, multiple product lines, and Series D hiring pace.
**Advisors:** None publicly listed. Board includes Andrew Reed (Sequoia, joined Series D).

*Background note:* Mati and Piotr are childhood friends from Warsaw. They co-founded ElevenLabs in May 2022 after Mati noticed dramatic improvements in voice quality from early ML demos Piotr was experimenting with.

### Funding
| Round | Amount | Date | Lead Investor |
|-------|--------|------|--------------|
| Seed / Series A | > **Educated guess:** ~$21M combined | 2022–2023 | Unknown |
| Series B | $80M | January 2024 | a16z, Sequoia, Nat Friedman, Daniel Gross |
| Series C | $180M | January 2025 | a16z + ICONIQ Growth (co-led) |
| Series D | $500M | February 2026 | Sequoia Capital |
| Series D (third close) | (part of $500M) | May 2026 | BlackRock, Wellington, D.E. Shaw, Schroders |

**Other investors:** NEA, World Innovation Lab (WiL), Valor, Endeavor Catalyst, Lunate, Lightspeed, BOND, Evantic Capital; strategic: Deutsche Telekom, LG Technology Ventures, HubSpot Ventures, NTT DOCOMO Ventures, RingCentral Ventures, NVIDIA (NVentures), Salesforce, Santander, KPN
**Total raised:** ~$781M (confirmed: five rounds since 2022)
**Valuation:** $11B (February 2026)

### Runway
Not a meaningful concern at this stage. ElevenLabs had $500M ARR as of April 2026 and just raised $500M in February 2026, eyeing an IPO. > **Educated guess:** At $500M ARR with ~40–50% gross margins typical of AI infrastructure companies (significant GPU/compute spend), the company is likely near or approaching operating profitability at enterprise scale; the Series D funds product expansion and international GTM, not survival.

### Product
ElevenLabs operates three product lines:
- **ElevenAgents** — enterprise voice + chat AI agents for customer support, conversational commerce, and public sector use cases. Deployed at scale by Klarna (10x faster resolutions for 35M US customers), Revolut (8x reduction in ticket resolution time across 30+ languages), and Deutsche Telekom.
- **ElevenCreative** — text-to-speech, voice cloning, dubbing, music generation (ElevenMusic), and audio localization across 70+ languages. Used by media companies (Washington Post, TIME, Bertelsmann, HarperCollins) and gaming studios (Epic Games, Paradox Interactive). Partnerships with Matthew McConaughey and Michael Caine for licensed voice IP (Iconic Marketplace).
- **ElevenAPI** — low-latency foundational audio models for developers to build voice-enabled applications. Used by Twilio, Duolingo, Chess.com, Harvey, Perplexity, Cisco.
- **Mission initiative:** $1B pledged in free voice restoration technology for 1M people living with permanent voice loss.

### Key Risks
1. **Premium pricing creates competitive vulnerability:** ElevenLabs charges ~5x more per minute than Cartesia and significantly more than open-source alternatives (Chatterbox, Fish Audio). As voice quality commoditizes, enterprise procurement teams will push back.
2. **OpenAI/Google treating voice as a first-class product would be existential:** Today, big tech treats audio as secondary. If that changes — especially with GPT-4o voice or Gemini Live scaling — ElevenLabs' moat narrows to brand, integrations, and language breadth.
3. **IPO path creates execution pressure:** At $11B valuation and $500M ARR, public market expectations will be demanding. Sustaining 100%+ YoY growth (from $330M to $500M ARR in ~4 months) while managing enterprise sales cycles is operationally intensive.
4. **Pre-revenue concentration in enterprise:** Named clients like Deutsche Telekom and Revolut likely represent outsized ARR. Losing a single marquee customer would be a visible setback heading into IPO prep.

### Recruiting Framing
- **Founder quality signal:** Mati Staniszewski is exceptionally credentialed — Imperial College math, BlackRock (quant/platform work), Palantir, TIME100 AI 2025. He brings both technical fluency and operational seriousness. Piotr is a deep ML researcher. This is a rare founder pairing of a world-class operator and a world-class researcher who have known each other for 15+ years.
- **Team composition:** Described as "IOI medalists and ex-founders" — technical bar is very high. Culture is lean, intentional about remote collaboration, minimal meetings, fast experimentation.
- **Growth trajectory:** Series D ($500M), ARR growing from $330M to $500M in ~4 months, Fortune 500 penetration at 72%+, IBM and Spotify partnerships just signed. Company is clearly accelerating.
- **Culture signals:** Empowers individuals to make decisions from day one, values deep documentation, embraces remote-first thoughtful collaboration. The Warsaw Summit (November 2025) signals they take culture and team cohesion seriously for a distributed company.

---

## Phase 2 — Client & Persona Deep-Dive

### Who Buys This?
**ElevenAgents (enterprise voice agents):** VP/Head of Customer Experience, VP of Contact Center Operations, or Chief Digital Officer at a mid-market to enterprise company (500+ seat call center). Budget authority sits with CX leadership or CTO, typically $200K–$2M annual contracts based on call volume. These buyers are measured on cost-per-resolution, NPS, and agent utilization — they get promoted by cutting headcount costs while improving CSAT, and fired when an AI agent embarrasses the company publicly.

**ElevenCreative / ElevenAPI:** CTO, Head of Product, or Head of Engineering at a company building a product with audio as a feature (fintech apps, gaming studios, media companies, language-learning apps). Budget is usually a line item in infrastructure or product development spend. These buyers care about latency, uptime SLAs, API reliability, and per-character pricing.

### What Do They Do Without This Product?
**Enterprise CX teams:** Legacy IVR systems (Nuance, Avaya, Genesys) or human call centers. Typical cost is $6–$12 per call with 5–15 minute average handle times. Multilingual support requires either separate regional staffing or heavy localization work. Escalation rates are high; resolution often requires multiple transfers.

**Developers building audio features:** Either pay for competing TTS APIs (Google TTS, Amazon Polly — lower quality), use in-house models (expensive to train and maintain), or accept lower-quality voice in their product. Dubbing and localization historically required professional studios and voice actors — weeks of turnaround, $3K–$15K per language per video.

### Where Does the Product Intervene?
- **ElevenAgents:** Replaces the IVR + first-line human agent layer. Customer calls → voice AI handles routing, resolution, and follow-through — no human needed for Tier 1 queries.
- **ElevenCreative/API:** Intervenes at content production: where a company would commission a voice actor or dubbing studio, ElevenLabs generates broadcast-quality audio in minutes.

### Pain Points
1. **Cost of human support at scale:** A 35M-customer platform like Klarna can't staff enough agents to handle first-line calls; ElevenLabs cut resolution time 10x and removed human handle time from Tier 1.
2. **Multilingual content is prohibitively expensive:** Localizing a video into 10 languages with a dubbing studio costs $30K–$150K+ and takes weeks. ElevenLabs does it in hours.
3. **Voice quality of existing APIs is recognizably synthetic:** Users tolerate Google/Amazon TTS for navigation apps; they reject it for customer service or media. ElevenLabs' quality crosses the "uncanny valley" threshold where users don't realize it's AI.

### Named Clients or Pilots
| Client | Use Case | Metric |
|--------|----------|--------|
| Klarna | First-line phone support for 35M US customers | 10x faster resolutions |
| Revolut | Customer support agents across UK/EU | 8x reduction in ticket resolution time; 30+ languages |
| Deutsche Telekom | Enterprise voice agents (also strategic investor) | — |
| Better.com | Mortgage lead conversion | 2x lead-to-lock conversion; 41% lower origination costs |
| TVS Motor | Lead capture voice agents | 35% lift in lead capture |
| Cars24 | Sales conversion + CSAT | +35% conversion, +20% CSAT |
| eDreams Odigeo | Multilingual CX | Double-digit resolution speed gain across 5 languages |
| Deliveroo | Outbound partner/rider communications | Reached 75% of riders and partners |
| Everlywell | Health screening (Spanish-speaking members) | 3.5x conversion rate |
| Epic Games, Duolingo, Chess.com | In-product audio | — |
| Walt Disney Studios, TIME, Washington Post | Media/audio localization | — |
| Ukrainian Government | Public sector voice AI | — |
| IBM | Integration into watsonx Orchestrate (announced March 2026) | — |
| Spotify | AI-generated audiobook production (announced May 2026) | — |

### What Gets Displaced?
- **IVR and call center platforms:** Nuance (Microsoft), Genesys, Avaya, NICE — legacy systems get replaced or dramatically reduced in scope.
- **Human voice-over artists and dubbing studios:** For content localization, a category worth billions globally.
- **Multilingual customer support headcount:** Companies like Revolut were staffing for 30+ language support; ElevenLabs collapses this into one deployment.
- **Ad hoc TTS APIs:** Google Cloud TTS, Amazon Polly, Microsoft Azure TTS — still cheaper for low-quality use cases, but lose when quality matters.

---

## Phase 3 — Competitive Landscape

### Direct Competitors

| Company | Funding | Positioning | vs ElevenLabs |
|---------|---------|-------------|----------------|
| Cartesia | > **Educated guess:** ~$80M | Ultra-low latency (~40ms TTFB), cheapest API pricing (~1/5th of ElevenLabs) | ElevenLabs wins on voice quality, language breadth, and full-stack platform; Cartesia wins on latency and price for commodity real-time use cases |
| Deepgram | $130M (Series C, Jan 2026) at $1.3B | Strong STT + voice agents, enterprise reliability, "vertical AI audio stack" | ElevenLabs wins on TTS quality and language breadth; Deepgram wins on STT accuracy and enterprise DevOps integration |
| Fish Audio | > **Educated guess:** Bootstrapped/small | Cheapest TTS API (~$15/M characters vs ElevenLabs' ~$80/M), open-source, wins TTS-Arena blind tests | ElevenLabs wins on enterprise features, support, and compliance; Fish Audio wins on cost for developer projects |
| OpenAI (GPT-4o voice / Realtime API) | Platform | Multimodal voice built into GPT-4o; growing developer adoption | ElevenLabs wins on audio-specific quality, 70+ language dubbing, enterprise agents; OpenAI wins on integration with existing GPT workflows |
| Google (Gemini Live / Cloud TTS) | Platform | Native integration with Google Cloud, long history in TTS | ElevenLabs wins on voice naturalness, voice cloning, enterprise customization; Google wins on cost-at-scale for commodity audio |
| Resemble AI | > **Educated guess:** ~$20M | Voice cloning and voice security (deepfake detection) | Narrower scope; competes only in voice cloning; ElevenLabs is a superset |

### Differentiation Assessment

- **Claim:** *"The most realistic, versatile AI voices in 70+ languages"*
  **Assessment:** Real and currently defensible. Independent benchmarks (TTS-Arena, direct user comparisons) consistently rate ElevenLabs highest on naturalness. The 70+ language dubbing capability is genuinely differentiated — no competitor matches this at scale. However, Fish Audio has won some blind TTS quality tests, and open-source models are closing the gap quickly. This claim will need continuous R&D investment to remain accurate.

- **Claim:** *"Full-stack audio AI platform" (TTS + STT + voice cloning + music + agents)*
  **Assessment:** Real and the most defensible moat. No single competitor covers all of TTS, STT, voice cloning, dubbing, music generation, and enterprise agents in one product. This cross-product data flywheel (more users → better models → more users) creates compounding advantage that pure-play API companies can't easily replicate.

- **Claim:** *"Enterprise-grade safety and compliance"*
  **Assessment:** Credible effort — dedicated safety team, multi-layered safeguards, active policy engagement — but hard to fully verify from outside. In the voice cloning space, misuse risk is real and has generated negative press. The $1B voice restoration initiative is a clever brand move that also signals values.

### Genuine White Space
ElevenLabs is the only company building a **full-stack audio intelligence company** that spans creation, localization, and enterprise deployment. No well-funded competitor owns the combination of TTS + STT + dubbing + voice cloning + music + agents. This platform breadth means ElevenLabs can serve both the developer API buyer and the enterprise CX buyer and the individual creator — three distinct segments competitors must pick between.

### Where It's Crowded
- **Real-time voice agent infrastructure:** Cartesia and Deepgram compete directly and are significantly cheaper. Enterprise buyers building voice agents can mix-and-match (Deepgram for STT, Cartesia for TTS) rather than using ElevenLabs' full stack.
- **API-level TTS for commodity use cases:** Google, Amazon, and Microsoft already own the low-end (cheap, fast, good enough). ElevenLabs is over-engineered and over-priced for navigation, alerts, or basic read-aloud features.
- **Music generation:** ElevenMusic enters a crowded field (Suno, Udio, Meta's MusicGen) without a clear quality lead.

### Key Competitive Risk
**OpenAI shipping a dedicated voice product.** Today, GPT-4o voice is a byproduct of a multimodal model — it's not purpose-built for enterprise call centers or audio localization. If OpenAI launched a dedicated enterprise voice agent product (very plausible given its Realtime API trajectory), it would immediately compete for ElevenLabs' fastest-growing segment (ElevenAgents) with the advantage of existing enterprise OpenAI relationships and bundling leverage. ElevenLabs' strongest defense is its 4-year head start on audio-specific model quality and its enterprise customer lock-in through custom voice models.

---

*Sources:*

*Tier 1 (company-owned):*
- *[ElevenLabs About Page](https://elevenlabs.io/about)*
- *[ElevenLabs Series D Blog Post](https://elevenlabs.io/blog/series-d)*
- *[ElevenLabs Series C Blog Post](https://elevenlabs.io/blog/series-c)*
- *[ElevenLabs Customer Stories](https://elevenlabs.io/customer-stories)*
- *[IBM Press Release — ElevenLabs Partnership](https://newsroom.ibm.com/2026-03-25-enterprise-ai-finds-its-voice-elevenlabs-and-ibm-bring-premium-voice-capabilities-to-agentic-ai)*

*Educated guess sources (secondary / estimated):*
- *[TechCrunch — Series D](https://techcrunch.com/2026/02/04/elevenlabs-raises-500m-from-sequioia-at-a-11-billion-valuation/)*
- *[CNBC — $11B Valuation](https://www.cnbc.com/2026/02/04/nvidia-backed-ai-startup-elevenlabs-11-billion-valuation.html)*
- *[Wikipedia — ElevenLabs](https://en.wikipedia.org/wiki/ElevenLabs)*
- *[Sacra — Revenue & Valuation Analysis](https://sacra.com/c/elevenlabs/)*
- *[Mati Staniszewski — Wikipedia](https://en.wikipedia.org/wiki/Mati_Staniszewski)*
- *[TIME100 AI 2025 — Mati Staniszewski](https://time.com/collections/time100-ai-2025/7305868/mati-staniszewski/)*
- *[Deepgram — ElevenLabs Alternatives Comparison](https://deepgram.com/learn/text-to-speech-elevenlabs-alternatives)*
- *[Telnyx — State of Voice AI 2026](https://telnyx.com/resources/state-of-voice-ai-trust-execution-2026)*
