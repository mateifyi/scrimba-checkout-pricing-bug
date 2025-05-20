# scrimba-checkout-pricing-bug
*A pricing discrepancy discovered via legacy route behavior and UI version mismatch on Scrimba’s platform.*

---

This repo highlights how an outdated interface route caused a persistent pricing inconsistency in a real production app — and how it was caught and resolved.

## 🧠 Summary

While using Scrimba — a platform I genuinely value for learning — I noticed a subtle but persistent pricing discrepancy depending on how the subscription page was accessed.

This wasn’t a cosmetic issue. It was a **functional pricing inconsistency** caused by legacy UI routing and live billing logic being slightly out of sync.
- Scrimba had two UI layers active: a legacy version (/home) and a newer version (/pricing) for managing subscriptions.
- Navigating to v1.scrimba.com/home?pricing exposed a different subscription price than the one shown on the official v2 flow.
- This legacy flow passed the outdated price into **Stripe Checkout**, which completed payment successfully.
- 🧨 **Impact**: Users could pay less than intended if they accessed billing via the legacy route.

This repo documents:
- How it was found
- What caused it
- Why it mattered
- And how Scrimba's team responded quickly and professionally to patch it

---

## 🔍 What I Found

- Scrimba had two UI layers active: a **legacy version (`/home`)** and a newer version (`/pricing`) for managing subscriptions.
- Navigating to `v1.scrimba.com/home?pricing` exposed a **different subscription price** than the one shown on their updated site.
- This path allowed the legacy price to persist all the way through to **Stripe Checkout**, which accepted the transaction with no errors.
- Result: Users could access **an outdated subscription tier** simply by taking the wrong path.

---

## 🧪 How I Verified It

- Accessed both URLs as a logged-in user
- Compared price points (e.g., 85 RON/month vs. 77 RON/month)
- Verified that the old price could still be paid
- Took screenshots before and after contacting support
- Reported the issue clearly with steps to reproduce

---

## 📸 Screenshots

You can find the screenshots that document the bug, the old pricing path and the fixed UI in the `/screenshots` folder.

 ---

## ✅ What Happened Next

- Scrimba’s support (thanks Emma!) was **quick, clear, and proactive**
- They immediately escalated to their dev team
- The `/home?pricing` legacy route was updated to redirect to the correct `/pricing` path
- They also applied a **subscription discount** to my account as thanks — much appreciated!
- Issue resolved, clean and fast

---

## 📘 Why I Wrote This

This was a rare case where a **UX oversight led to a real billing inconsistency**. No security issue, no trickery (: - just a leftover legacy route that was still functioning in production.

I’m documenting this because:
- Frontend bugs that ride on legacy routing are hard to catch, because they don’t throw errors — just unexpected behavior.
- It’s a perfect example of how **frontend versioning**, **UX flow**, and **payment logic** all intersect
- Scrimba’s team handled it perfectly, and that deserves to be noted 

---

## 🙏 Thanks

Huge thanks to the Scrimba team for their fast and open response, glad to be of help.

---

## 📜 License

[Creative Commons Attribution 4.0](LICENSE)

---

**Tags:** `ux-bug`, `checkout-flow`, `frontend-routing`, `legacy-ui`, `pricing`, `stripe`, `scrimba`, `case-study`
