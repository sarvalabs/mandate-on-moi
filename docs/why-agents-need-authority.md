# Why agents need authority

[← Overview](../README.md) · Next: [The MOI Authority Layer →](moi-authority-layer.md)

Older software did only what its code told it to do. AI agents are different. You give an agent a goal in plain words. The agent then decides the steps: which data to read, which tool to use and which request to send.

Agents now do work, not only answer questions. They do this work within organizations and across them.

## Three questions about each action

When a user acts, the system knows who the user is. The user signs in, and the role of the user controls the rest. When an agent acts, the system must know three things:

1. **Who is this agent?** Not the app or the model, but this one agent.
2. **Who does it act for?** Each agent acts for a user or an organization: its owner. The owner is responsible for the agent.
3. **What can it do?** Not all that its owner can do. Only the task that it got: these records, this amount, until this date.

The answer to the third question is the **authority** of the agent. Today's tools cannot give this answer.

## What agents use today

Agents get access in the same way as apps: with a password, an API key, a service account or an OAuth token. Each of these answers only one question: "Can the holder get in?"

- **A key gives all the access of its owner.** An agent that must read one customer record can read all of them. An agent that must pay one invoice can pay any invoice.
- **The task stays behind.** The request of the user stays in the chat. The service sees a valid key. It does not see the task.
- **Agents give work to other agents.** Each agent gives the same key to the next agent. After two or three steps, nobody knows who allowed what.
- **To stop one agent, you must change the key.** This also stops all other apps that use the same key. Thus, keys often stay active after the task is complete.
- **The record is weak.** The log shows that somebody used the key. It does not show who allowed the action, or the limits.

## Agents can make mistakes

A model reads all the text that it gets: documents, emails, web pages and replies from other agents. Some of this text tries to trick the model. Also, a model can simply make a mistake. You can make a model more difficult to trick, but you cannot make it safe. If an agent holds a key, the key allows all that the agent does. Thus, the limit must be outside the model.

## What must be true

Before users and organizations can trust agents with real work, three things must be true:

1. **The authority is clear and signed.** The grantor states exactly what the agent can do, and signs it. The grantor is the user or organization that gives the authority.
2. **The resource server checks it before each action.** The service gets the authority from a source that it trusts. It does not get it from the agent.
3. **The grantor can revoke it in one step.** There is no key to change and no company to call. Nothing else stops. All authority that the agent gave to other agents also stops.

| | A key, token or service account | A signed permission |
|---|---|---|
| What the agent can do | All that the key allows | Only what the grantor signed |
| When an agent gives work to another agent | It gives the same key | It can give only less authority |
| Who checks it | Nobody, after the key is valid | The resource server, before each action |
| How you stop it | Change the key. Other apps also stop. | One revoke, everywhere |
| Proof of what was allowed | A log that shows the key was used | A signed record of who allowed what |
| If somebody tricks the agent | The agent does all that the key allows | The agent cannot go past the signed limits |

## How MOI answers the three questions

[MOI](https://moi.technology) is the participant layer for AI agents. On MOI, each user, organization and agent has its own account and identity.

| Question | Answer on MOI |
|---|---|
| Who is this agent? | Its own MOI identity, `did:moi:…`, and its own key |
| Who does it act for? | The agent registry on MOI. It records the owner and the status of each agent. |
| What can it do? | A permission in the **[MOI Authority Layer](moi-authority-layer.md)**. The grantor signs it. Any verifier can check it. The grantor can revoke it in one step. |

The **[MAL Gateway](mal-gateway.md)** applies these answers. All agent calls go through it. It checks each call against the permission before the call gets to the service.

## Why the demo uses shopping

Authority is necessary for each action of an agent: to read company data, to approve expenses, to change prices or to move money. **Mandate**, the demo in these documents, uses shopping and payment, because a limit on money is easy to see. You give an agent a permission on your phone. The agent buys inside the permission. The agent is refused outside the permission. You revoke the permission with one tap. Orchard is the shop and Tessera is its payment gateway.

The method is not only for shopping. Change the products and amounts to tables and rows, or to claims and limits. All the checks work in the same way.

Next: [The MOI Authority Layer →](moi-authority-layer.md)
