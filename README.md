# OpsGuardian Forge Privacy Notice

Last updated: 1 November 2026

## Who provides the app

OpsGuardian Forge (the “App”) is provided by Sergei Marianchik, an independent developer. To contact the provider about the App or privacy requests, email **luxors09@gmail.com**.

Your organization operates its Jira site and may have its own privacy notice and rules for work items. Atlassian provides the Forge platform and Jira services and processes information under its own applicable terms and notices. The roles of the parties depend on the circumstances.

## Information the App accesses

When a user requests a comparison, the App uses that user's Jira permissions to retrieve the selected current and reference work items and comments. It accesses issue keys, summaries, descriptions, update times, status category, components, labels, priority, work type, and comment identifiers and content. Work items and comments may contain information about their creators or other people mentioned in them, including sensitive or confidential information. The App receives the requesting user's Atlassian account ID from Forge to bind the review to that user.

The App displays selected fields and may show excerpts from comments marked as a resolution or fix to the authorized user. A comparison is not an independently verified diagnosis or remediation.

## Use and storage

The App uses the information to create and display the requested comparison, verify that the reference work item is resolved, re-check access and freshness, and reduce duplicate notes.

The current implementation does not save the comparison or the requesting user's account ID in a Forge key-value preview record. Instead it sends the user a signed, short-lived preview token containing issue keys, digests and an expiry; the token is bound to the user and installation. It is signed, not encrypted. The App processes the comparison during the request and again when the user confirms; the token is accepted for 15 minutes.

To reduce duplicate writes, Forge storage retains a hashed key derived from the issue pair and a status or Jira comment receipt. These values are not necessarily anonymous in context. The App sets no automatic expiry on these duplicate-prevention records. Older versions may have created preview or other privacy-related records; handling of historical records is under review and may depend on the installation and Atlassian's retention policies.

If the user chooses **Post internal note**, the App writes an internal Jira Service Management comment containing the reference issue key and a marker. The note does not copy the comparison text. The issue key reveals that a reference work item exists; access to that item is controlled by the Jira site. The note is stored in the organization's Jira site and is subject to that site's permissions and retention settings. Deleting or uninstalling the App does not itself delete Jira comments.

Forge and Jira may generate service logs and maintain backups under Atlassian's policies. The App's manifest does not declare external network egress. The App uses Atlassian APIs and Forge-hosted storage; it does not send the comparison to an external AI service as part of its current workflow.

## Retention and uninstall

The preview token expires after 15 minutes. Duplicate-prevention records have no automatic expiry in the current version; they may remain until removed or handled under the applicable Forge installation lifecycle. Jira comments are retained according to the site's settings and administration. Forge's uninstall retention, logs and backups are governed by Atlassian's current policies; the provider cannot promise immediate removal from those systems.

## Privacy requests

For questions or a request concerning personal data, contact **luxors09@gmail.com**. Please identify the relevant Jira site and work item when you can do so safely; do not include passwords, API tokens or unnecessary sensitive information. The provider will assess the request, use proportionate steps to verify identity and authority when needed, and coordinate with the site administrator or Atlassian as appropriate. Information in work items or Jira comments may need action by the site administrator. Locating data mentioned in unstructured text and historical app records may require manual investigation.

Depending on applicable law and the circumstances, you may have rights to request access, correction or erasure, to object to or restrict certain processing, or to complain to a relevant data protection authority. Any applicable exceptions and response requirements depend on the request and jurisdiction.

## Changes

This notice may be updated when the App or its data practices change. The date above identifies the latest update.


## Release update — 4 November 2026

This section describes the 4 November release candidate and supersedes conflicting descriptions above for that version. Earlier installed versions may retain the previous behavior.

The updated review writes a generic internal acknowledgement with an installation-bound marker, without copying the reference issue key or comparison text. The ordinary comparison workflow does not persist a personal profile.

An indexed personal-data subsystem maintains an account directory and structured records in Forge KVS. Account IDs, retrieval times and any registered profile fields remain until erased or refreshed. The scheduled process reports indexed accounts to Atlassian and handles closed/updated responses by atomically erasing the indexed record and directory entry and checking absence by direct reads. Administrators can request indexed-account erasure. Rate-limit delays are respected and ambiguous failures require reconciliation.

Eligible expired structured historical preview records can be migrated atomically into that directory, removing the original copy. Records with arbitrary content, active previews or unknown schemas require further review; migration does not silently discard them. The indexed erasure result applies to that indexed storage only. Legacy subject coverage remains under review and its automated reporting remains restricted. The app does not claim automatic erasure of all historical content, other installations, Jira notes, platform logs or backups.

For a privacy request, contact luxors09@gmail.com. We assess identity and authority, inspect the relevant installation and legacy matches, perform and verify supported actions, coordinate remaining work with the site administrator or Atlassian, and explain any outstanding data or retention limits. Duplicate-prevention records remain identifiable in context and have no automatic expiry.
