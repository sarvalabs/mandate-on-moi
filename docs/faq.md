# FAQ

[← Back to the overview](../README.md)

### What is Mandate?

Mandate is a web app and a set of services for AI agents. You give each agent a permission that you sign on your
phone. Each service checks the permission on MOI before it acts.

### How is a permission different from an API key?

An API key lets an agent do everything that the key can do. A permission lets an agent do only what you signed: the
products, the sellers, the amounts, and the time. Each service checks the permission. You can revoke it with one tap.

### Where is my key?

Your key is in MOI Wallet, on your phone. It never leaves your phone, and no service can sign as you. It signs your sign-in, your permissions and revokes, your agents' registrations, and a payment when you choose to pay an order yourself.

### Where is the agent's key?

Each agent has its own key. The agent wallet in the MOI Authority Layer keeps it, encrypted. The key never goes to
Claude. The key signs only as that agent, never as you.

### What is the MAL Gateway?

The one place every agent call goes through. It checks the call against your grant and the tenant's own policy, adds the real service key from a vault, and records the decision. A tenant can use it in our cloud or run it in its own infrastructure. [More →](mal-gateway.md)

### What happens if someone tricks the agent?

The agent can try to buy something outside the permission. Orchard and Tessera refuse it. The limits are on MOI, not
in the model.

### What happens if someone steals the permission?

A permission names the agents that can use it. If a different agent uses it, Orchard and Tessera refuse it.

### How fast does a revoke work?

The revoke is recorded on MOI when you approve it. Orchard and Tessera check MOI for each request. They refuse the
agent from its next request.

### Can another person give a permission to my agent?

Yes. The grantor, the user who gives the permission, decides its limits. You, as the owner, decide if your agent is active. If you
pause or retire the agent, it stops for all permissions.

### Why do I sign in to the MOI Authority Layer connector?

The sign-in gives your chat (Claude or ChatGPT) a private connection to the service. Your wallet then proves who you are. Without the
sign-in, anyone with the URL could reach the tools that act as your agents.

### How do I disconnect my wallet?

In a chat, type `Disconnect my wallet.` The service ends the connection to your phone and unlinks your account from the
connector, for all your chats in that app. Nothing changes on MOI: your agents and permissions stay, and a live
permission still works until you revoke it or it expires. To stop an agent, revoke its permission or pause it.

While you are disconnected, your non-interactive agents cannot run. A price change starts the routine, but the run is
refused. Connect your wallet again to continue. You can also connect a different wallet.

Mandate has its own sign-in. To sign out of Mandate, use **Sign out** in Mandate.

### Why do Orchard and Tessera need no sign-in?

They keep nothing of yours. Each order and payment comes signed by the agent. They check everything on MOI.

### Do I need KMOI?

No. On the public devnet, the service pays the network fees for you.

### Is the money real?

No. The prices at Orchard are simulated, and Tessera keeps a ledger. The permissions, the revokes, and the agent
registrations are real records on the MOI public devnet.

### Why does my phone show encoded data?

MOI Wallet shows each request as encoded data. The card in the chat shows the same request in plain words. It also
tells you the name of the request on your phone, for example **CreateGrant** or **RegisterAgent**.

### Which AI can I use?

Interactive agents work in Claude and in ChatGPT, through the same three connectors. Non-interactive agents run as Claude
routines.

### Can I give a permission in ChatGPT and use it in Claude?

Yes. Your identity is your wallet account, not your chat app. Connect the same wallet in both. A permission that you
give an agent in one chat is on MOI, so the agent can use it in the other.

[← For developers](developers.md) · [Glossary →](glossary.md)
