# Product Analytics Platform

**Candidate #38** — A privacy-first, open-source product analytics platform combining event ingestion, session replay, feature flags, and A/B testing in a single deployable application.

## Market Opportunity

The product analytics market is **$12–18 billion in 2026**, growing at **12–22% CAGR through 2030–2034**. The market is dominated by Amplitude, Mixpanel, and PostHog—but consolidation (Contentsquare acquired Heap and Hotjar; Datadog acquired FullStory) is creating openings for open-source alternatives.

**Market dynamics:**
- PostHog is the leading open-source option but self-hosting is operationally complex (ClickHouse + Kafka + Redis)
- No tool combines privacy-first tracking with enterprise-grade product analytics at an accessible price
- Event-based pricing at scale ($5K–$50K/month for high-volume consumer apps) creates budget uncertainty
- In-app guidance and AI-powered insights are rapidly moving from differentiator to table-stakes

## What This Platform Solves

A **lightweight, privacy-first, all-in-one product analytics platform** that combines event analytics, session replay, feature flags, A/B testing, and surveys in a single self-hostable application—without privacy compromises.

**Core value proposition:**
- **Cookieless tracking**: No cookies, no PII, GDPR-compliant by default
- **All-in-one suite**: Event analytics + session replay + feature flags + A/B testing (others charge separately)
- **Simple self-hosting**: Docker Compose deployment; no Kafka or Kafka required (unlike PostHog)
- **LLM analytics**: Native module for AI product teams tracking token costs and model quality
- **Affordable**: Cloud tier from free/€100 month; self-hosted free
- **Open-source core**: MIT licence; no network-use obligations

## Competitive Differentiation

| Aspect | This Platform | PostHog | Amplitude | Mixpanel | OpenPanel |
|--------|---------------|---------|-----------|----------|-----------|
| **Self-Hostable** | Yes (simple) | Yes (complex) | No | No | Yes |
| **All-in-One** | Yes | Yes | No | No | Yes |
| **Cookieless** | Yes | Yes | No | No | Yes |
| **LLM Analytics** | Yes | Yes | No | No | No |
| **Open Source** | Yes (MIT) | Yes (MIT) | No | No | Yes (AGPL) |
| **Price** | Free/€100+ | Free/$500+/mo | Free/$49+/mo | Free/custom | Free/custom |

## Key Features

### Must-Have (MVP)
- Event ingestion (SDK + API) with funnel, retention, cohort analysis
- Session replay linked to funnel drop-offs with configurable privacy masking
- Cookieless, GDPR-compliant event collection
- Role-based team workspaces with shared dashboards
- Data warehouse export (BigQuery, Snowflake minimum)
- Open-source core under MIT licence with documented self-host path

### Should-Have (v1.1)
- Natural language query interface (NLQ) for non-technical users
- Feature flags and A/B testing integrated in the same platform
- AI-powered anomaly detection with plain-English explanation
- LLM analytics module (token usage, model latency, conversation quality)
- Session replay AI clustering and summarization

### Nice-to-Have (Backlog)
- In-app guide and onboarding overlay builder (no-code)
- Audience activation to ad platforms and CRMs
- Differential privacy or synthetic cohort option
- AI-assisted event instrumentation from codebase analysis
- Mobile autocapture SDK for iOS/Android

## Technology Stack

**Backend**: TypeScript/Node.js or Python, ClickHouse or PostgreSQL  
**Frontend**: React, TypeScript  
**Session Replay**: rrweb (open-source)  
**Feature Flags**: Custom implementation  
**A/B Testing**: Statsig-inspired architecture  
**Licensing**: MIT (fully permissive)

## Market Entry Strategy

1. **MVP Launch** (months 1–5): Event analytics + session replay + basic feature flags
2. **Feature Expansion** (months 6–10): A/B testing, LLM analytics module, anomaly detection
3. **AI Features** (months 11–16): NLQ interface, session replay clustering, AI instrumentation suggestions
4. **Monetization**: Open-source core + managed cloud tier (free–€500/month), enterprise support ($2K+/month)

## Why This Matters

- **PostHog self-hosting complexity**: ClickHouse + Kafka + Redis is operationally heavy. Simpler alternative captures teams without DevOps expertise
- **Privacy+enterprise analytics gap**: No tool combines privacy-first tracking with event depth (funnels, cohorts, retention) at an accessible price point
- **LLM analytics is nascent**: Only PostHog and Amplitude have native modules. This is a high-growth segment for AI product teams.
- **All-in-one economics**: Buying event analytics + session replay + feature flags + A/B testing separately costs $5K–$20K+/month. Single platform at €100–500/month is compelling
- **Consolidation risk**: Contentsquare (Heap+Hotjar), Datadog (FullStory) are buying up specialized tools. Open-source all-in-one prevents lock-in

## Success Metrics

- **Year 1**: 2,000+ active deployments, $250K ARR from cloud + support contracts
- **Year 2**: 8,000+ active deployments, $1.5M ARR; featured in G2 Leaders
- **Year 3**: 20,000+ active deployments, $5M+ ARR; adopted by 200+ Series B+ SaaS companies
