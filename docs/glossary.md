# Glossary

[← Back to the overview](../README.md)

| Word | Meaning |
|---|---|
| **Agent** | An AI that acts for you. In Mandate, each agent has its own identity and its own key. |
| **Interactive agent** | An agent that works with you in a Claude or ChatGPT chat. |
| **Non-interactive agent** | An agent that runs alone, as a Claude routine. A price change starts it. |
| **Permission** | What you allow an agent to do: products, sellers, amounts, and time. Your phone signs it. MOI keeps it. In the protocol, it is a **grant**. |
| **Revoke** | You stop a permission. The next request under it fails. |
| **Agent registry** | A record on MOI of each agent and its owner. The owner can pause or retire the agent. |
| **Owner** | The user or organization that registered the agent. |
| **Grantor** | The user or organization that signs a grant. The grantor can be a different party from the owner. |
| **Grantee** | The agent that a grant names. Only this agent can act under the grant. |
| **Verifier** | Any party that checks a grant on MOI before it acts, for example a resource server or the MAL Gateway. |
| **Resource server** | A service that an agent calls, for example an API or an MCP server. |
| **Tenant** | An organization that puts its resource servers behind the MAL Gateway. |
| **Resource owner** | A user who signs in to a resource server through the gateway, so that an agent can use that account. |
| **Policy enforcement point** | The component that checks each call before it gets to a resource server. The MAL Gateway is the policy enforcement point. |
| **DID** | A decentralized identity, for example `did:moi:<account>`. Each user, organization and agent has one. |
| **MOI** | The network that keeps the permissions, the agent registry, and the identities. |
| **MOI Wallet** | The app on your phone that holds your key and signs your requests. |
| **MOI Authority Layer** | The connector for Claude and ChatGPT. It creates agents and sends your writes to your phone. Also called **MAL**. |
| **MAL Gateway** | The enforcement point. Every agent call passes through it and is checked against the grant and the tenant's policy before it gets to a resource server. |
| **Policy** | A tenant's own rules for every agent call, written in [Cedar](https://www.cedarpolicy.com). A call needs both the permission and the policy to say yes. |
| **Vault** | Where the gateway keeps service keys and resource owners' OAuth tokens. Agents never see them. |
| **Mandate** | The web app that shows your agents, your permissions, and every check. |
| **Orchard** | A merchant in the demo. It sells Apple products and checks each order on MOI. |
| **Tessera** | A payment gateway in the demo. It checks each payment on MOI again. |
| **Connector** | A way for Claude or ChatGPT to use a service, through MCP. |
| **MCP** | The Model Context Protocol. It connects an AI to tools and services. |
| **Routine** | A Claude task that runs in the cloud, without a chat. |
| **Run pass** | A pass that lets one routine run act as one agent, for 20 minutes. |
| **Audit log** | The gateway's record of every decision, allowed or denied. Each entry is chained to the one before it, so a change is visible. |
| **Scope** | The limits inside a permission. |
| **Public devnet** | The public MOI development network. The demo runs on it. |
| **KMOI** | The token that pays the network fees on MOI. |
| **Voyage** | The explorer for MOI. |
| **Agent Explorer** | The explorer for agents on MOI, and their owners. |

[← Back to the overview](../README.md)
