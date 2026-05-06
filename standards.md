# Standards & API Reference

> Project: Product Analytics Platform · Generated: 2026-05-06

## Industry Standards & Specifications

### Privacy & Data Protection Regulations

**GDPR — EU General Data Protection Regulation (EU 2016/679)**
- Official: https://gdpr.eu/
- Lawful-basis and consent requirements for any behavioural event collection covering EU data subjects. Drives cookie-free and first-party-data architectures; GDPR enforcement reached €5.88 billion in cumulative fines since 2018, with €1.2 billion in 2024 alone. Any analytics platform collecting user-level events for EU users must implement opt-in consent for non-essential cookies, data deletion APIs, and record-of-processing activities.

**CCPA / CPRA — California Consumer Privacy Act and its Privacy Rights Act Amendment**
- Official: https://oag.ca.gov/privacy/ccpa
- Compliance guide: https://secureprivacy.ai/blog/ccpa-requirements-2026-complete-compliance-guide
- Requires data mapping of all collected personal data, opt-out of sale, and deletion rights. The CPPA approved comprehensive regulatory amendments in September 2025; some requirements took effect January 1, 2026, with further phases through 2030. Violations cost $2,500 per unintentional breach and $7,500 per intentional violation.

**US Multi-State Privacy Laws — 2025–2026 Wave**
- Summary: https://usercentrics.com/guides/data-privacy/data-privacy-laws/
- In 2025, comprehensive privacy laws became effective in Delaware, Iowa, Maryland, Minnesota, Nebraska, New Hampshire, New Jersey, and Tennessee. Indiana, Kentucky, and Rhode Island laws took effect January 1, 2026 — bringing the total to 20+ states. Analytics products sold in the US must now treat GPC signals and opt-out of sale as legally required across multiple jurisdictions, not just California.

**ISO/IEC 27001:2022 — Information Security Management Systems**
- Official: https://www.iso.org/standard/27001
- Table-stakes requirement for enterprise sales of any cloud analytics platform handling user behavioural data. Enterprise procurement teams routinely require ISO 27001 certification as a prerequisite for signing data processing agreements.

**ISO/IEC 27701:2025 — Privacy Information Management Systems (PIMS)**
- Official: https://www.iso.org/standard/27701
- Guide: https://www.isms.online/iso-27701/getting-started-2025/saas-data-processing/
- Published October 2025, this revision restructures PIMS as a standalone management system (no longer an extension of ISO 27001 only), providing a structured framework for managing PII processing obligations as controller or processor. Enterprise analytics buyers increasingly expect both ISO 27001 and ISO 27701 credentials. The 2025 revision adds stronger alignment with GDPR, CCPA, and a risk-based approach to protecting personal data.

### Consent & Opt-Out Signals

**Global Privacy Control (GPC)**
- Spec: https://w3c.github.io/gpc/explainer
- Official site: https://globalprivacycontrol.org/
- An HTTP header and JavaScript property signal that tells a site the user wants to opt out of sale and sharing of personal information. As of April 2026, GPC is legally recognised as a required opt-out signal in twelve US states. California's Opt Me Out Act (AB 566, signed October 2025) requires all browsers to include built-in GPC functionality by January 1, 2027. Current baseline is 5–10% of traffic sending GPC signals, projected to reach 30–40% by 2027 as browser defaults change. Analytics platforms must suppress tracking cookies and third-party data sharing when a GPC signal is detected.

**IAB Transparency & Consent Framework (TCF) v2.3**
- Spec: https://iabtechlab.com/standards/gdpr-transparency-and-consent-framework/
- Guide: https://iabeurope.eu/transparency-consent-framework/
- TCF v2.3 was released June 19, 2025; the mandatory migration deadline for CMPs and vendors to drop support for TCF 2.2 strings is February 28, 2026. Analytics tools integrated with ad-adjacent stacks must implement TCF v2.3 for EU consent signal propagation. TCF v2.3 tightens legal-basis requirements: vendors may only use consent (not legitimate interest) for personalisation and measurement purposes under the Belgian DPA's ruling.

**Google Consent Mode v2**
- Developer guide: https://developers.google.com/tag-platform/security/guides/consent
- Compliance guide: https://www.didomi.io/blog/google-consent-mode-v2-what-you-need-to-know
- Mandatory since March 2024 for all EU operations to retain remarketing and advertising measurement capabilities. v2 adds `ad_user_data` and `ad_personalization` consent signals on top of v1's `analytics_storage` and `ad_storage`. As of June 2026, `ad_storage` becomes the sole authority for all advertising data collected for linked Google Ads accounts. Any analytics platform feeding Google's measurement ecosystem must implement Consent Mode v2 and use a certified CMP.

### Observability & Telemetry Standards

**OpenTelemetry (OTEL) — Semantic Conventions**
- Spec: https://opentelemetry.io/docs/specs/semconv/
- Events spec: https://opentelemetry.io/docs/specs/semconv/general/events/
- OpenTelemetry v1.41.0 (latest stable). Vendor-neutral standard for telemetry (traces, metrics, logs, events). OpenTelemetry Events are structured logs with a semantic name; the project is building a library of standard events with official names, attributes, and payload structures for common use cases. Behavioural product analytics and engineering observability are converging — analytics tools with OTEL-compatible event schemas allow product and engineering data to share pipelines.

**OpenTelemetry GenAI Semantic Conventions**
- Spec: https://opentelemetry.io/docs/specs/semconv/gen-ai/
- Events spec: https://opentelemetry.io/docs/specs/semconv/gen-ai/gen-ai-events/
- Standardises attributes, spans, events, and metrics for generative AI workloads including token usage, provider/model metadata, and conversation-level telemetry. Marked as evolving (opt-in). Directly relevant to the LLM analytics module described in the feature spec — a product analytics platform tracking AI products should align its token-cost and conversation-quality metrics with GenAI semantic conventions to enable cross-tool compatibility.

**Apache Kafka — Distributed Event Streaming**
- Official: https://kafka.apache.org/
- Apache 2.0 licence. De-facto standard for high-throughput distributed event streaming underpinning real-time analytics pipelines. Core architecture: Producers, Topics (partitioned log), Brokers, Consumer Groups, Kafka Streams (client library), and Kafka Connect (external system integration). PostHog, and most enterprise analytics pipelines, use Kafka as the event ingestion backbone before writing to ClickHouse or similar OLAP stores.

**ClickHouse — OLAP Columnar Database**
- Official: https://clickhouse.com/
- GitHub: https://github.com/ClickHouse/ClickHouse
- Apache 2.0 licence. The dominant open-source OLAP engine for product analytics — used by PostHog, OpenPanel, and Plausible. ClickHouse 26.2 released February 2026 with improved JOIN capabilities (hash, sort-merge, grace hash, full sorting merge), advanced semi-structured data modelling, and vectorised query execution. Its HTTP interface and native protocol enable direct SQL access from analytics front-ends and data pipelines alike.

### API & Data Format Standards

**OpenAPI Specification 3.1 (OAS 3.1)**
- Official: https://spec.openapis.org/oas/v3.1.0
- Industry-standard machine-readable REST API description format, aligned with JSON Schema draft 2020-12. Any product analytics platform exposing a public REST API should publish an OAS 3.1 document to enable SDK auto-generation, API gateway integration, and third-party tooling (Postman, Stoplight, Redocly).

**JSON Schema (draft 2020-12)**
- Official: https://json-schema.org/specification
- Standard for describing and validating JSON data structures. Used by Snowplow for event schema validation (JSONSchema-based self-describing events), by OpenAPI 3.1, and as the basis for most analytics SDKs' event payload validation. Essential for instrumentation schema governance and drift detection.

**RFC 6749 — OAuth 2.0 Authorization Framework**
- Standard: https://datatracker.ietf.org/doc/html/rfc6749
- The industry-standard framework for delegated API access. Analytics platform APIs should use OAuth 2.0 Authorization Code + PKCE for user-facing integrations and client credentials for server-to-server. RFC 9700 and OWASP recommend sender-constrained tokens (DPoP, mTLS) and strict server-side validation of signature, issuer, audience, expiry, and scope for every API call.

**OpenID Connect 1.0 (OIDC)**
- Spec: https://openid.net/specs/openid-connect-core-1_0.html
- Identity layer on top of OAuth 2.0; the standard mechanism for SSO in enterprise analytics platforms. FAPI 2.0 Security Profile (https://openid.net/specs/fapi-security-profile-2_0-final.html) provides a hardened profile for high-value API access. Note: CVE-2025-27370 and CVE-2025-27371 (disclosed by the OpenID Foundation, 2025) identified a JWT audience vulnerability in OAuth 2.0 and OIDC implementations requiring validation updates.

**RFC 9110 — HTTP Semantics / REST**
- Standard: https://datatracker.ietf.org/doc/html/rfc9110
- The canonical HTTP semantics specification (2022, supersedes RFC 7231). Analytics APIs should be RESTful with well-defined resource representations, status codes, and caching headers. TLS 1.2+ is now mandatory — Mixpanel deprecated TLS 1.0/1.1 support in April 2026.

### Security Standards

**OWASP API Security Top 10 (2023)**
- Official: https://owasp.org/API-Security/editions/2023/en/0x11-t10/
- Project: https://owasp.org/www-project-api-security/
- Key risks for analytics APIs include: Broken Object-Level Authorisation (API1), Broken Authentication (API2), Excessive Data Exposure (API3), and Unrestricted Resource Consumption (API4 — especially relevant for high-volume event ingestion endpoints). Gartner forecasts that by 2025 more than half of data theft incidents originate from unsecured APIs.

**Model Context Protocol (MCP)**
- Spec: https://spec.modelcontextprotocol.io/
- Open standard (by Anthropic) enabling AI assistants to interact with external tools and data sources via structured, permission-controlled context. Mixpanel launched an MCP Server (public beta September 2025, US data centres) giving Claude, ChatGPT, and Cursor conversational access to Mixpanel analytics data. An AI-native analytics platform should consider MCP server exposure as a first-class integration target for AI assistant workflows.

---

## Similar Products — Developer Documentation & APIs

### Amplitude

- **Description:** Enterprise-grade behavioural analytics platform with funnel, retention, cohort, session replay, and AI-powered insight surfacing.
- **API Documentation:** https://amplitude.com/docs/apis/analytics
- **API Reference (Postman):** https://www.postman.com/amplitude-dev-docs/amplitude-developers/collection/2hjpzte/amplitude-analytics-apis
- **HTTP API Quickstart:** https://amplitude.com/docs/apis/analytics/http-api-quickstart
- **SDKs/Libraries:** JavaScript, iOS, Android, Python, Go, Java, .NET, React Native, Flutter — see https://amplitude.com/docs/get-started/get-data-in
- **Developer Guide:** https://amplitude.com/docs
- **Standards:** REST/JSON; OpenAPI documented; basic authentication (base64-encoded API key + secret in header) for Dashboard REST API; HTTPS required; up to 5 concurrent requests across all REST endpoints.
- **Authentication:** API Key + Secret Key (basic auth); project-scoped tokens.

---

### Mixpanel

- **Description:** Event-based product analytics with funnel, retention, session replay, heatmaps, Spark AI NLQ, MCP Server, and Metric Trees.
- **API Documentation:** https://developer.mixpanel.com/reference/overview
- **Developer Hub:** https://developer.mixpanel.com/
- **MCP Server Documentation:** https://docs.mixpanel.com/docs/mcp
- **SDKs/Libraries:** JavaScript, iOS, Android, React Native, Flutter, Python, Ruby, PHP, Java — https://docs.mixpanel.com/docs/tracking-methods/sdks/javascript
- **Developer Guide:** https://docs.mixpanel.com/
- **Standards:** REST/JSON; TLS 1.2+ mandatory (TLS 1.0/1.1 deprecated April 2026); API key and secret authentication; MCP Server uses the open Model Context Protocol specification.
- **Authentication:** API Secret (server-side); Project Token (client-side SDKs); OAuth not currently advertised for analytics APIs.

---

### PostHog

- **Description:** Open-source all-in-one developer platform for product analytics, session replay, feature flags, A/B testing, surveys, error tracking, LLM analytics, and data warehouse.
- **API Documentation:** https://posthog.com/docs/api
- **Capture API:** https://posthog.com/docs/api/capture
- **SDK Comparison:** https://posthog.com/docs/libraries
- **SDKs/Libraries:** JavaScript, iOS, Android, React Native, Flutter, Python, Ruby, PHP, Java, Go, Node, .NET; 50+ community SDKs — https://posthog.com/docs/libraries
- **Developer Guide:** https://posthog.com/docs
- **GitHub:** https://github.com/PostHog/posthog
- **Standards:** REST/JSON; OpenAPI available; public endpoints (`/i/v0/e`, `/flags`) use project token (no auth); private management endpoints use personal API key (Bearer token). MIT-licensed core; EE features under proprietary licence.
- **Authentication:** Project API key for event capture (public); Personal API key (Bearer token) for management APIs.

---

### Heap / Contentsquare

- **Description:** Autocapture-based product analytics (Heap) combined with digital experience analytics, session replay, heatmaps, and voice-of-customer (Contentsquare). Post-acquisition, migrating to unified CSQ SDK.
- **Heap Developer Documentation:** https://developers.heap.io/docs/web
- **Contentsquare Documentation:** https://docs.contentsquare.com/en/
- **Unified CSQ SDK (Mobile):** iOS, Android, Flutter, React Native, Cordova, Capacitor — https://docs.contentsquare.com/
- **Developer Guide:** https://developers.heap.io/
- **Standards:** REST/JSON; proprietary autocapture schema; Contentsquare CSQ SDK ≥ 0.1.0 required for Heap integration sync. Segment, mParticle, RudderStack ingest compatibility.
- **Authentication:** API keys; enterprise data processing agreements required post-migration.

---

### Pendo

- **Description:** Product analytics with in-app guidance, NPS/surveys, session replay, AI churn prediction, Agent Analytics for LLM products, cross-channel orchestration, and roadmapping.
- **Developer Hub:** https://www.pendo.io/developers/
- **Engage API:** https://engageapi.pendo.io/
- **Mobile SDK (GitHub):** https://github.com/pendo-io/pendo-mobile-sdk
- **SDKs/Libraries:** JavaScript (Web SDK), iOS, Android, React Native, Flutter, Xamarin Forms, Xamarin MAUI — https://support.pendo.io/hc/en-us/articles/27862809568667-Pendo-developer-APIs
- **Developer Guide:** https://support.pendo.io/hc/en-us/articles/38099922926875
- **Standards:** REST/JSON; install-script based web instrumentation; mobile SDKs are native per-platform. API key authentication for Engage API.
- **Authentication:** API Key (Engage API); project-scoped install key for SDK initialisation.

---

### FullStory (Datadog)

- **Description:** Session replay and digital experience analytics with FullCapture (auto-recording all interactions), Smart Chapters AI segmentation, heatmaps, and integration with Datadog observability.
- **Developer Guide:** https://developer.fullstory.com/
- **Help Center (Developer):** https://help.fullstory.com/hc/en-us/categories/360001589674-Developer
- **Datadog API Documentation:** https://docs.datadoghq.com/
- **SDKs/Libraries:** JavaScript (web), iOS, Android; Datadog SDKs for RUM integration — https://docs.datadoghq.com/developers/
- **Developer Guide:** https://developer.fullstory.com/
- **Standards:** REST/JSON; HTTP API for custom data capture, segment retrieval, and privacy management. API key authentication.
- **Authentication:** API key; Datadog integration uses Datadog API + App keys.

---

### Segment (Twilio)

- **Description:** Customer Data Platform (CDP) for collecting events from any source and routing to 400+ destinations. Not a product analytics tool itself, but the dominant event ingestion middleware used by Amplitude, Mixpanel, PostHog, and Pendo.
- **API Documentation:** https://docs.segmentapis.com/
- **API Reference:** https://reference.segmentapis.com/
- **Developer Documentation:** https://segment.com/docs/
- **SDKs/Libraries:** JavaScript, iOS, Android, Python, Ruby, Java, Go, .NET and more — https://segment.com/docs/
- **Developer Guide:** https://segment.com/docs/guides/
- **Standards:** REST/JSON; the Segment Spec (Track, Page, Identify, Group, Alias calls) has become a de-facto standard for product analytics event schemas — RudderStack, PostHog, and others implement Segment API compatibility. OAuth 2.0 for workspace management APIs.
- **Authentication:** Write Key for event ingestion; OAuth 2.0 for Segment Public API (workspace/source/destination CRUD).

---

### RudderStack

- **Description:** Open-source Segment-compatible CDP for event collection and routing. Apache 2.0-licensed server and most SDKs; 200+ destination integrations.
- **Documentation:** https://www.rudderstack.com/docs/
- **GitHub:** https://github.com/rudderlabs/rudder-server
- **SDKs/Libraries:** JavaScript, Kotlin (Android), Swift (iOS), macOS, watchOS, tvOS, and more — https://www.rudderstack.com/docs/get-started/rudderstack-open-source/
- **Developer Guide:** https://www.rudderstack.com/docs/
- **Standards:** REST/JSON; fully Segment API-compatible (same Track/Page/Identify schema) — existing Segment integrations can switch to RudderStack without changing application code. Apache 2.0 (core server) and MIT (most SDKs).
- **Authentication:** Write Key for event ingestion; workspace access tokens for management APIs.

---

### Snowplow

- **Description:** Open-source behavioural data infrastructure (Customer Data Infrastructure / Customer Context Layer) for high-fidelity event collection with JSONSchema-validated self-describing events, enrichment pipeline, and real-time delivery to data warehouses.
- **Documentation:** https://docs.snowplow.io/docs/
- **Tracking Plans API:** https://docs.snowplow.io/docs/event-studio/programmatic-management/tracking-plans-api/
- **GitHub:** https://github.com/snowplow/snowplow
- **JavaScript Tracker:** https://github.com/snowplow/snowplow-javascript-tracker
- **Analytics SDKs:** Scala, JavaScript, Go, Python, .NET — https://docs.snowplow.io/docs/api-reference/analytics-sdk/
- **Standards:** Events divided into canonical events (structured, native warehouse columns) and self-describing events (JSON Schema-validated custom schemas). Apache 2.0 licence for open-source trackers and enrichment. REST HTTP collector endpoint. JSONSchema for event schema governance — directly relevant to instrumentation schema management and drift detection features.
- **Authentication:** Collector endpoint is open/write-only (project-specific collector URL); Snowplow BDP (commercial) uses API keys for management APIs.

---

### OpenPanel

- **Description:** Open-source Mixpanel-inspired product analytics platform with funnels, cohorts, session replay, A/B testing, and real-time dashboards. Cookieless by design; full feature parity between cloud and self-hosted.
- **Website / Documentation:** https://openpanel.dev/
- **GitHub:** https://github.com/Openpanel-dev/openpanel
- **SDKs:** JavaScript, Next.js, React, Vue, Python, Ruby, PHP — https://openpanel.dev/
- **Standards:** REST/JSON; ClickHouse backend with direct SQL access; AGPL-3.0 licence (network-use clause applies to modifications offered as SaaS). Vercel edge middleware integration.
- **Authentication:** API key for event ingestion and REST API.

---

## Notes

**Emerging / Still-Evolving Areas**

- **OpenTelemetry Events Standard for Product Analytics:** OTel's semantic conventions for business-level behavioural events (distinct from engineering telemetry) are still being defined. The project is building a library of standard events, but no formal "product analytics" semantic convention namespace exists as of May 2026. Teams converging engineering observability and product analytics should watch https://opentelemetry.io/docs/specs/semconv/ for new event namespaces.

- **W3C Privacy Sandbox Discontinuation:** Google officially discontinued the Privacy Sandbox initiative in April 2025 and retired the Topics API, Protected Audience, and Attribution Reporting API suite in October 2025. Privacy-preserving measurement alternatives (W3C Privacy-Preserving Attribution Level 1 Working Draft — https://www.w3.org/news/2025/first-public-working-draft-privacy-preserving-attribution-level-1/) remain in active development but have no stable implementation. Analytics platforms should monitor W3C Privacy and Advertising Working Group outputs rather than implement deprecated Privacy Sandbox APIs.

- **MCP as an Analytics Integration Primitive:** The Model Context Protocol (open standard) is rapidly becoming the integration layer between analytics data stores and AI assistants. Mixpanel's MCP Server (September 2025 beta) is the first production deployment in the category. Any AI-native analytics platform should build MCP server support as a first-class feature to enable conversational analytics via Claude, ChatGPT, Cursor, and similar tools without custom integrations.

- **IAB TCF v2.3 Migration Deadline:** February 28, 2026 is the hard deadline for all CMPs and analytics vendors to migrate from TCF 2.2 to TCF 2.3 string formats. Platforms integrating with ad-measurement stacks should have completed this migration.
