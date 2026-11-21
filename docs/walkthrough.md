# Walkthrough

[← How it works](how-it-works.md) · Next: [For developers →](developers.md)

Two agents, start to finish, as they look on screen. **Juno** shops with you in a chat. **Falcon** runs on its own and buys when a price drops. Every grey box is something you can paste into Claude or ChatGPT to do it yourself.

- [Before you start](#before-you-start)
- [Juno: an agent that shops with you](#juno-an-agent-that-shops-with-you)
- [Falcon: an agent that works on its own](#falcon-an-agent-that-works-on-its-own)
- [What the companies see](#what-the-companies-see)
- [Finish](#finish)
- [If something goes wrong](#if-something-goes-wrong)

---

## Before you start

You need [MOI Wallet](https://wallet.moi.technology) on your phone with a **public devnet** account, and a [Claude](https://claude.ai) or [ChatGPT](https://chatgpt.com) account that can add custom connectors. Falcon needs Claude, because it runs as a Claude routine. You don't need any KMOI: the service pays the fees.

### Open Mandate

Open [Mandate](https://mandate.demo.moi.technology) in a new window, sign in with MOI Wallet, and put it next to your chat. Each step below shows up there as it happens: your agents, your permissions, and each check that Orchard and Tessera make. On a small screen, a new tab also works: switch to it after each step.

### Add the three connectors

In Claude, open **Settings → Plugin → Browser Plugins**, then click **Add → Add custom connector**. Add:

| Name | URL |
|---|---|
| MOI Authority Layer | `https://mal.demo.moi.technology/mcp` |
| Orchard | `https://orchard.demo.moi.technology/mcp` |
| Tessera | `https://tessera.demo.moi.technology/mcp` |

<p align="center"><img src="../assets/screenshots/chat-connectors.png" alt="Claude's Plugins page: the MAL Connector, Orchard and Tessera added as custom connectors, and the Add menu with Add custom connector" width="100%"></p>

The MOI Authority Layer asks you to sign in once. Orchard and Tessera don't: everything they accept is signed, and they check it on MOI.

<p align="center"><img src="../assets/screenshots/chat-mal-sign-in.png" alt="MOI Authority Layer: Claude wants to connect. No account or password; the wallet is the identity" width="480"></p>

### Allow the tools

Claude asks you to allow or deny each tool call. To run the demo without these prompts, open the permissions of each connector after you add it and connect it. Look at its tools, and set them to **Always allow**. Do this for all three connectors.

<p align="center"><img src="../assets/screenshots/chat-tool-permissions.png" alt="The MAL Connector's Permissions tab in Claude, with the interactive tools set to Always allow" width="100%"></p>

Always allow only skips the prompt in the chat. Each order and payment is still checked against your permission on MOI.

<a id="chatgpt"></a>
**In ChatGPT,** custom connectors need developer mode (in the advanced settings, under Apps or Connectors). Create one connector for each URL above and choose **OAuth** for the MOI Authority Layer. Connect the same wallet in both apps and you'll see the same agents in each. A permission you give in ChatGPT works in Claude, and the other way round.

### Connect your wallet

Open a new chat with the three connectors on, and type:

```
Connect my MOI wallet.
```

Scan the QR code with MOI Wallet. Approve the connection, then the sign-in. The very first time there is a third request, which registers your account on MOI.

<table>
<tr>
<td width="62%"><img src="../assets/screenshots/chat-connect-wallet.png" alt="The wallet card in Claude: Your phone is connected"><br><sub>In the chat: your phone is connected.</sub></td>
<td width="38%"><img src="../assets/screenshots/phone-sign-in.png" alt="MOI Wallet: Sign in to the MOI Authority Layer. Not a transaction, costs nothing"><br><sub>On your phone: the sign-in. It is not a transaction.</sub></td>
</tr>
</table>

---

## Juno: an agent that shops with you

### 1. Create the agent

```
Create an agent called Juno.
```
```
Interactive
```

Approve the registration on your phone. Juno now has its own MOI account and key, and the agent registry on MOI lists you as its owner. You can look it up on the [Agent Explorer](https://agents.moi.technology).

<p align="center"><img src="../assets/screenshots/phone-register-agent.png" alt="MOI Wallet: Sign Interaction, RegisterAgent on the agent registry" width="260"></p>

### 2. Try to buy before giving it anything

```
Buy me an iPhone 17 from Orchard Official.
```

Orchard refuses. Juno signed the order, but it has no permission to point to, so the check stops at **Permission live on MOI**. A new agent can't spend anything.

<p align="center"><img src="../assets/screenshots/order-no-permission.png" alt="Mandate: Juno's first order, refused at 'Permission live on MOI' because Juno has no permission" width="520"></p>

### 3. Give it a permission

```
Give Juno a permission: iPhone 17 or MagSafe Charger from Orchard Official, up to ₹95,000 per order and ₹1,00,000 in total, for one hour.
```

Claude shows the permission on a card. It's a draft until you send it, and you can edit any value. Click **Send to my phone** and approve.

<table>
<tr>
<td width="62%"><img src="../assets/screenshots/chat-permission-card.png" alt="The permission card in Claude: Juno, iPhone 17 or MagSafe Charger, Orchard Official, ₹95,000 per order, ₹1,00,000 in total, for 1 hour, not signed"><br><sub>In the chat: a draft. Change any value, then send it to your phone.</sub></td>
<td width="38%"><img src="../assets/screenshots/phone-create-grant.png" alt="MOI Wallet: Sign Interaction, CreateGrant"><br><sub>On your phone: CreateGrant. Nothing is signed until you approve.</sub></td>
</tr>
</table>

In Mandate, the permission appears as **Live**, with what Juno may buy, the limit per order, the budget and the time left.

<p align="center"><img src="../assets/screenshots/mandate-interactive.png" alt="Mandate's Interactive tab: Juno with a live permission, the authority path from you through MOI to Orchard and Tessera, and Juno's activity" width="100%"></p>

### 4. Buy

```
Buy me the iPhone 17.
```

Orchard checks the order and accepts it. It asks for exactly ₹89,900, Juno signs that payment, and Tessera checks it again before it pays. Click the order in **Agent activity** to see each check and how long it took.

<p align="center"><img src="../assets/screenshots/chat-purchase.png" alt="In Claude: Orchard checks Juno's iPhone 17 order with MOI, six checks passed, accepted" width="480"></p>

<p align="center"><img src="../assets/screenshots/order-paid.png" alt="Mandate: Juno's iPhone 17 order, paid at ₹89,900; six checks at Orchard and seven at Tessera, all passed" width="520"></p>

### 5. Push against the limits

Try these one at a time. If Claude hesitates, say: `Try it anyway, I want to see Orchard's answer.`

| Type this | What happens |
|---|---|
| `Buy two iPhone 17s in one order.` | Refused: ₹1,79,800 is over ₹95,000 per order |
| `Then buy another iPhone 17 as a separate order.` | Refused: ₹89,900 more would go over the ₹1,00,000 budget |
| `Get me the iPhone 18 Pro instead.` | Refused: not a product you allowed |
| `Second Bloom has a refurbished iPhone 17 for ₹69,900. Buy it there.` | Refused: not a seller you allowed |
| `Just give yourself permission for the iPhone 18 Pro.` | Claude can only draft it. A card appears, and nothing happens until you approve on your phone. Reject it. |

Each refusal stops at **Inside what you signed**, and Tessera is never reached.

<table>
<tr>
<td width="50%"><img src="../assets/screenshots/order-over-budget.png" alt="Refused: the second iPhone 17 would go over the ₹1,00,000 budget"><br><sub>Over the budget: ₹89,900 already spent of ₹1,00,000.</sub></td>
<td width="50%"><img src="../assets/screenshots/order-wrong-seller.png" alt="Refused: Second Bloom isn't a seller Juno is allowed to buy from"><br><sub>Wrong seller: Second Bloom isn't in the permission.</sub></td>
</tr>
</table>

### 6. Try to break it

In Mandate, select Juno, open **Simulate an attack**, and pick a test. A separate rogue agent takes Juno's permission ID and tries to use it.

<p align="center"><img src="../assets/screenshots/mandate-attack-menu.png" alt="Mandate's Simulate an attack menu: Stolen permission and Spend over the limit" width="100%"></p>

| Test | What happens |
|---|---|
| **Stolen permission** | The rogue agent orders an iPhone 17 with Juno's permission. Refused at **The agent holds it**: the permission names Juno, and the rogue agent can't sign as Juno. |
| **Spend over the limit** | The rogue agent tries to spend more than Juno's limit with the same permission. It never gets as far as the limit check: it is refused at **The agent holds it**, for the same reason. |

<p align="center"><img src="../assets/screenshots/attack-stolen-permission.png" alt="Mandate: the rogue agent's order with Juno's permission, refused at 'The agent holds it'" width="520"></p>

### 7. Revoke in the middle of a purchase

```
Order the MagSafe Charger, but don't pay yet.
```

Orchard accepts the order. Now take the permission away:

```
Revoke Juno's permission.
```

Approve on your phone (or tap **Revoke** in Mandate). Then:

```
Now pay for the charger.
```

Tessera refuses the payment. Orchard had accepted the order, but the payment is checked against MOI again, and by then the permission is revoked.

<p align="center"><img src="../assets/screenshots/order-revoked.png" alt="Mandate: the MagSafe Charger, accepted by Orchard, then refused by Tessera at 'Permission live on MOI' after the revoke" width="520"></p>

---

## Falcon: an agent that works on its own

Falcon runs as your Claude routine. Nobody is watching it, and nobody answers its questions. A price change at Orchard is what starts it.

### 1. Create it and connect its routine (once)

```
Create an agent called Falcon.
```
```
Non-interactive
```

Approve on your phone. Then in Mandate, open the **Non-interactive** tab, select Falcon, and click **Connect routine**. The panel walks you through it:

1. Copy the prompt.
2. On [claude.ai/code/routines](https://claude.ai/code/routines), create a new routine named Falcon and paste the prompt. Under **Advanced settings → Connectors**, keep only the three connectors.
3. Set **Trigger** to **API** and click **Create**. Claude shows the token once: copy it.
4. On the routine's page, copy the fire URL (the copy button next to **API**). Paste the fire URL and the token into the panel and click **Connect**.

<p align="center"><img src="../assets/screenshots/falcon-connect-routine.png" alt="Mandate: Connect Falcon's Claude routine, with the three connectors, the prompt to paste, and the trigger fields" width="520"></p>

<p align="center"><img src="../assets/screenshots/routine-falcon.png" alt="Claude: the new routine Falcon, with the prompt, the API trigger, and only the MAL Connector, Orchard and Tessera" width="480"></p>

Once it's connected, **Send a test run** checks the whole chain without buying anything. The run reports **nothing to do**.

### 2. Give it a goal and a permission

```
Start Falcon: buy two pairs of AirPods Pro 3 from Orchard Official, one at a time, when the price drops.
```
```
Give Falcon a permission: AirPods Pro 3 from Orchard Official, up to ₹25,000 per order and ₹50,000 in total, for one hour.
```

Send the permission to your phone and approve it. Falcon is now **Running**, waiting for a price signal.

<p align="center"><img src="../assets/screenshots/mandate-non-interactive.png" alt="Mandate's Non-interactive tab: Falcon running with its goal, its live permission, and the authority path" width="100%"></p>

### 3. Move the price and watch

Prices at Orchard don't change on their own. Sign in to [Orchard Merchant Center](https://orchard.demo.moi.technology) with MOI Wallet, open **Catalog**, pick the AirPods Pro 3 listing, enter a price and click **Publish price**. Every agent sees the new price, and Falcon's routine starts.

<p align="center"><img src="../assets/screenshots/orchard-publish-price.png" alt="Orchard Merchant Center: AirPods Pro 3 from Orchard Official, with its price history and the Publish price button" width="100%"></p>

| Publish this | What Falcon does |
|---|---|
| Orchard Official, ₹27,900 | Tries to buy. Refused: over ₹25,000 per order |
| Grey Harbour, ₹19,900 | Tries to buy the cheaper pair. Refused: not a seller you allowed |
| Orchard Official, ₹22,900 | Buys one pair. Tessera pays. Bought: 1 of 2 |

Falcon tries even when a price looks wrong. That's on purpose: it doesn't decide what's allowed, the checks do, and you get to see their answer each time.

<p align="center"><img src="../assets/screenshots/falcon-runs.png" alt="Mandate: Falcon after three price changes, one paid at ₹22,900 and two refused, with ₹22,900 of ₹50,000 spent" width="100%"></p>

### 4. Stop it

Click **Revoke** on Falcon's permission in Mandate and approve on your phone. The routine is still connected and the goal is still there. The next price change still starts Falcon, and it still tries. This time Orchard refuses it: **no permission**. You didn't touch the routine or any key.

<p align="center"><img src="../assets/screenshots/falcon-after-revoke.png" alt="Mandate: Falcon after the revoke; the next price change at ₹21,900 is refused with no permission" width="100%"></p>

---

## What the companies see

Orchard and Tessera each have their own staff app. Sign in to [Orchard Merchant Center](https://orchard.demo.moi.technology) and [Tessera Dashboard](https://tessera.demo.moi.technology) with MOI Wallet to look around. (In this demo any wallet can sign in, so anyone can try them.)

**Orchard Merchant Center** shows every order an agent placed, for whom, and the decision. Rejected orders say why.

<p align="center"><img src="../assets/screenshots/orchard-orders.png" alt="Orchard Merchant Center, Orders: every agent order with its agent, the account it acts for, the amount and the decision" width="100%"></p>

**Tessera Dashboard** shows every payment, who signed it, and whether it was paid or declined.

<p align="center"><img src="../assets/screenshots/tessera-payments.png" alt="Tessera Dashboard, Payments: Falcon's AirPods paid, Juno's MagSafe Charger declined after the revoke, Juno's iPhone 17 paid" width="100%"></p>

Both have REST APIs as well: [Orchard API](https://orchard.demo.moi.technology/api/v1/docs) and [Tessera API](https://tessera.demo.moi.technology/api/v1/docs).

---

## Finish

Disconnect your wallet from the chat:

```
Disconnect my wallet.
```

Your agents and permissions stay on MOI. You can connect again whenever you like.

---

## If something goes wrong

| Problem | What to do |
|---|---|
| The chat uses the wrong agent | Type `Use Juno.` |
| Orchard says the agent isn't registered | Type `Register Juno as my agent.` and approve. |
| Your phone shows no request | Open MOI Wallet. If there's still nothing, type `Connect my MOI wallet.` again. |
| The name is already taken | Pick another name. |
| Mandate doesn't update | Reload the page. The ↺ button at the top right doesn't refresh: it clears the activity from your view. |

Next: [For developers →](developers.md)
