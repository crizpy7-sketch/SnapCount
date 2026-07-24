# Naeri Desserts — Custom Cake Order App

A single-file, mobile-first web app that lets customers place custom cake orders and
sends them straight to you via **WhatsApp** or **email** — no backend, no monthly fees.
Just one `index.html` you can host anywhere.

## Features
- 🎂 **Guided order form** — occasion, date, size/servings, flavor, extras, design details, allergies, contact, pickup/delivery.
- 💵 **Live price estimate** that updates as the customer chooses (fully editable in the code).
- 💬 **Sends the order to you** via WhatsApp, email, or copy-to-clipboard — pre-formatted and ready.
- 🌎 **Bilingual EN / ES** toggle (your audience is bilingual).
- 🖼️ **Style gallery** — tap a cake style to pre-fill the order.
- ⏰ **Lead-time check** — flags rush orders (under 5 days) and adds a rush fee.
- 💾 Saves the customer's in-progress order on their device so they don't lose it.
- 📱 Designed phone-first, works great on iPhone; accessible and responsive.

## ⚙️ Set it up (2 minutes)
Open `index.html` and edit the `CONFIG` block near the top of the `<script>`:

```js
const CONFIG = {
  businessName: "Naeri Desserts",
  whatsapp: "",                        // your WhatsApp number, digits only w/ country code, e.g. "19560001234"
  email:    "naeridesserts@gmail.com", // where email orders arrive
  facebook: "https://www.facebook.com/....",   // your Facebook page
  instagram:"https://www.instagram.com/....",  // your Instagram
  minLeadDays: 5,                      // orders sooner than this get a rush fee
  rushFee: 25,
  currency: "$"
};
```

> **Set your WhatsApp number** so the “Send via WhatsApp” button goes straight to your chat.
> Format: country code + number, digits only (US numbers start with `1`). Example: `19561234567`.

### Adjust prices
Edit the `SIZES`, `EXTRAS`, and `FULFIL` arrays (right below `CONFIG`) — each item's `price`
feeds the estimate. Add or remove flavors in `FLAVORS` and occasions in `OCCASIONS`.

## 🚀 Publish it (free options)
It's just one file, so any static host works:
- **Netlify Drop** — drag the `naeri-desserts` folder onto https://app.netlify.com/drop
- **GitHub Pages** — enable Pages on this repo and point it at this folder
- **Vercel** — import the repo and deploy

Then share the link in your Facebook/Instagram bio as “Order here 🎂”.

## Notes
- Orders are delivered through the customer's own WhatsApp/email — nothing is stored on a
  server, so there's nothing to maintain and no privacy liability.
- Want real online payments, an order dashboard, or automatic deposit collection later?
  That needs a small backend (e.g. Stripe + a database) — easy to add as a next step.
