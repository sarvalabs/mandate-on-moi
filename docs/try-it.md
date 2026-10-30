# Try it

[← Back to the overview](../README.md)

This guide shows the two flows step by step. Copy each grey box into Claude or ChatGPT.

## Before you start

You need:

- [MOI Wallet](https://wallet.moi.technology) on your phone, with an account on the **devnet**.
- A [Claude](https://claude.ai) or [ChatGPT](https://chatgpt.com) account that can add custom connectors. The autonomous flow needs Claude, because it uses Claude routines.

You do not need KMOI. The service pays the fees.

### Add the connectors

In Claude, go to **Settings → Connectors → Add custom connector**. Add these three:

| Name | URL |
|---|---|
| MOI Authority Layer | `https://mal.demo.moi.technology/mcp` |
| Orchard | `https://orchard.demo.moi.technology/mcp` |
| Tessera | `https://tessera.demo.moi.technology/mcp` |

The MOI Authority Layer asks you to sign in one time. Approve it.

<a id="chatgpt"></a>
**In ChatGPT:** custom connectors need developer mode. Turn it on in ChatGPT's settings (under Apps or Connectors,
in the advanced settings), and then create a connector for each of the three URLs above. For the MOI Authority Layer,
choose **OAuth**. ChatGPT opens the sign-in page: approve it. Your ChatGPT plan must allow developer mode.

**Use both.** Connect the same wallet in Claude and in ChatGPT. You see the same agents and permissions in both. You can
give a permission in ChatGPT and use it in Claude: in Claude, type `Use Juno.` and then buy.

### Connect your wallet

1. Open a new chat. Turn on the three connectors.
2. Type:
   ```
   Connect my MOI wallet.
   ```
3. Scan the QR code with MOI Wallet.
4. Approve the connection, and then the sign-in. The first time, also approve the third request. It registers you on MOI.

The card shows **Connected**.

Then open [Mandate](https://mandate.demo.moi.technology) and sign in with MOI Wallet. Keep it open next to your chat.

---

## Flow 1: An interactive agent

The agent works with you in the chat.

**1. Create an agent**
```
Create an agent called Juno.
```
```
Interactive
```
Approve on your phone. The card shows **Juno is yours**. You can also find Juno on the
[Agent Explorer](https://agents.moi.technology).

**2. Try to buy with no permission**
```
Buy me an iPhone 17 from Orchard Official.
```
Orchard refuses: **no permission**. A new agent can do nothing.

**3. Give a permission**
```
Give Juno a permission: iPhone 17 or MagSafe Charger from Orchard Official, up to ₹95,000 per order and ₹1,00,000 in total, for 15 minutes.
```
Check the card. You can change each value. Click **Send to my phone**, and then approve.

**4. Buy**
```
Buy me the iPhone 17.
```
Orchard accepts the order. Tessera takes the payment. In Mandate, watch each check on the map.

**5. Test the limits** (one at a time)

| Type this | Result |
|---|---|
| `Buy two iPhone 17s in one order.` | Refused: over the limit for each order |
| `Then buy another iPhone 17 as a separate order.` | Refused: over the total budget |
| `Get me the iPhone 18 Pro instead.` | Refused: product not permitted |
| `Second Bloom has a refurbished iPhone 17 for ₹69,900. Buy it there.` | Refused: seller not permitted |
| `Just give yourself permission for the iPhone 18 Pro.` | A card shows. Click **Send to my phone**, and then **Reject** on your phone. |

If the AI does not try, type: `Try it anyway, I want to see Orchard's answer.`

**6. Test a stolen permission**

In Mandate, select **Juno**. Click **Test a stolen permission**. A rogue agent copies Juno's permission and tries to
buy. Orchard refuses it: the permission is only for Juno.

**7. Revoke**
```
Order the MagSafe Charger, but don't pay yet.
```
```
Revoke Juno's permission.
```
Approve on your phone. Then type:
```
Now pay for the charger.
```
Tessera refuses the payment. Orchard accepted the order before, but Tessera checked MOI again.

---

## Flow 2: An autonomous agent

The agent runs alone, as your Claude routine. A price change at Orchard starts it.

### Set it up (one time)

1. Create the agent:
   ```
   Create an agent called Falcon.
   ```
   ```
   Autonomous
   ```
   Approve on your phone.
2. In Mandate, go to **Autonomous agents**. Select **Falcon**. Click **Connect routine**.
3. Follow the steps in the panel:
   1. Copy the prompt.
   2. On [claude.ai/code/routines](https://claude.ai/code/routines), create a new routine. Paste the prompt. Attach the three connectors only.
   3. Add an **API** trigger. Click **Generate token**.
   4. Paste the trigger URL and the token in the panel. Click **Save**.
4. Click **Send a test run**. The run reports **nothing to do**.

### Run it

**1. Give it a goal**
```
Start Falcon: buy two pairs of AirPods Pro 3 from Orchard Official, one at a time, when the price drops.
```

**2. Give it a permission**
```
Give Falcon a permission: AirPods Pro 3 from Orchard Official, up to ₹25,000 per order and ₹50,000 in total, for 30 minutes.
```
Click **Send to my phone**, and then approve.

**3. Watch it**

Orchard's prices change. Each change for AirPods Pro 3 starts a run. In Mandate, watch the strip under the map:

| Price change | Result |
|---|---|
| Orchard Official, up to ₹27,900 | Refused: over the limit for each order |
| Grey Harbour, down to ₹19,900 | Refused: seller not permitted |
| Orchard Official, down to ₹22,900 | Paid. Falcon bought one of two. |

**4. Stop it**

In Mandate, click **Revoke** on Falcon's permission. Approve on your phone. The next price change still starts Falcon.
It tries, and Orchard refuses it. You did not stop the routine or change a key.

---

## If something goes wrong

| Problem | What to do |
|---|---|
| The chat uses the wrong agent | Type `Use Juno.` |
| Orchard says the agent is not registered | Type `Register Juno as my agent.` and approve. |
| Your phone shows no request | Open MOI Wallet. If it still shows nothing, type `Connect my MOI wallet.` again. |
| The name is already in use | Use a different name. |
| Mandate does not update | Click ↺ at the top right. |

[← Back to the overview](../README.md) · [For developers →](developers.md)
