# Brave Search - API

> **Source**: [https://api-dashboard.search.brave.com/app/documentation/general/security](https://api-dashboard.search.brave.com/app/documentation/general/security)


[](https://api-dashboard.search.brave.com/app/dashboard)  [](https://api-dashboard.search.brave.com/app/dashboard)  [Documentation](https://api-dashboard.search.brave.com/app/documentation) [Web Search](https://api-dashboard.search.brave.com/app/documentation/web-search) [Summarizer Search](https://api-dashboard.search.brave.com/app/documentation/summarizer-search) [AI Grounding](https://api-dashboard.search.brave.com/app/documentation/ai-grounding) [Image Search](https://api-dashboard.search.brave.com/app/documentation/image-search) [Video Search](https://api-dashboard.search.brave.com/app/documentation/video-search) [News Search](https://api-dashboard.search.brave.com/app/documentation/news-search) [Suggest](https://api-dashboard.search.brave.com/app/documentation/suggest) [Spellcheck](https://api-dashboard.search.brave.com/app/documentation/spellcheck) [General](https://api-dashboard.search.brave.com/app/documentation/general) [API Versioning](https://api-dashboard.search.brave.com/app/documentation/general/api-versioning)[Privacy Notice](https://api-dashboard.search.brave.com/app/documentation/general/privacy-policy)[Terms of Service](https://api-dashboard.search.brave.com/app/documentation/general/terms-of-service)[Security](https://api-dashboard.search.brave.com/app/documentation/general/security)[Status Updates](https://api-dashboard.search.brave.com/app/documentation/general/status-updates)   [Login](https://api-dashboard.search.brave.com/login) [Register](https://api-dashboard.search.brave.com/register) # Brave Search API Security Info

  Brave takes our customers’ security and privacy very seriously.
As an API provider for some of the biggest names in tech, we’ve
passed numerous vendor audits and are always happy to answer security
questions from potential customers.

Internally, we require security and privacy reviews from our dedicated
security and privacy teams, both during the design phase and
implementation phase of new features, as well as for new vendor
requests and certain bug fixes. A member of the security and privacy
teams must sign off on any changes or specs that warrant review.
github.com/brave/brave-browser/wiki/Security-reviews
outlines the types of changes which explicitly require security
sign-off. In addition, we often require threat modeling as part
of specification design, usually as a “Security and Privacy Considerations”
section in the spec.

Brave highly prioritizes responsiveness to external security reports.
We have an extremely active bug bounty program at
hackerone.com/brave; as of October 2024,
our average time to triage is about 10 hours and average time to
resolution is about 4 days. We also solicit security reports at
security@brave.com. We contracted an
external penetration test of Brave Search (prior to development of the API)
via a HackerOne Challenge
in May 2021; 2 high severity and 1 medium severity were reported
and fixed promptly. In addition, Brave Search API’s last external penetration
test was completed in April 2025, and we are in the process of being certified
for SOC 2 (proof can be provided upon request to customers).

Our Data Protection Officer (DPO) advises on our compliance
with data protection and privacy laws such as the EU’s General
Data Protection Regulation (GDPR) and ePrivacy Directive, and
the California Consumer Privacy Act (CCPA) and California
Privacy Rights Act (CPRA). They also participate in security
and privacy reviews, handle
Right to Be Forgotten
(RTFB) requests, and ensure our
privacy policy is up
to date. Brave adopts a baseline standard to data protection based on
common data protection principles but we adapt our approach where
necessary and appropriate for specific jurisdictions and rules.
Compliance, as with all organizations subject to data protection
law, is an ongoing process and considered within the security and
privacy review process established within Brave. ISO standards
such as 27001 and 27701 provide guidance for establishing,
implementing, maintaining and continuously improving our approach
to information security and privacy information management.

Brave takes the utmost care in preventing malicious content from
persisting in the search index and addresses feedback
in a timely manner. For example:

We have a business continuity plan available upon request and
regularly perform backups.

Brave grants access to resources under the principle of least
privilege. Access requests are subject to security/privacy
reviews and promptly revoked upon termination. Note that all Brave
staff and contractors are bound by a confidentiality policy.
We enable SSO and non-SMS MFA when possible for our employees.
The Brave Search API dashboard also supports login via non-SMS MFA.
Our production deployment and access control policies are available
upon request.

Third-party services and dependencies are subject to security
and privacy review upon initialization. We use a combination of
Dependabot and Socket.dev for automated third party dependency
security scanning whenever a dependency changes or a new
vulnerability is released.

Our security incident handling policy is available upon request.
Security events in Search products are monitored by the Search
SecOps team. We will promptly notify affected customers and the
relevant regulatory authorities if we experience a data breach
according to our obligations and risks to individuals.

For more info, please contact privacy@brave.com
for privacy and data protection inquiries or security@brave.com
for security inquiries.

 