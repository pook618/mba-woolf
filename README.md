<div align="center">
<img width="1200" height="475" alt="GHBanner" src="https://github.com/user-attachments/assets/0aa67016-6eaf-458a-adb2-6e31a0763ed6" />
</div>

# Pickering Woolf MBA

This contains everything you need to run your app locally.

View your app in AI Studio: https://ai.studio/apps/a9445da4-cc84-4528-8915-0982358d6f99

## Run Locally

**Prerequisites:**  Node.js


1. Install dependencies:
   `npm install`
2. Copy `.env.example` to `.env.local`
3. Run the app:
   `npm run dev`

## Form Email Setup

The site supports two form submission modes:

1. Static email fallback:
   Set `VITE_FORM_RECIPIENT_EMAIL=admissions@pickering.education` in `.env.local`. When visitors submit a form, their email client opens with the enquiry prefilled.

2. Production endpoint:
   Forms submit to the same-origin Cloudflare Worker API by default. Set `VITE_FORM_ENDPOINT` only if you intentionally route a form to a different endpoint.

For Cloudflare deployment, create a Turnstile widget and set `VITE_TURNSTILE_SITE_KEY` at build time. Add `TURNSTILE_SECRET_KEY`, `LARK_WEBHOOK_URL`, and optional `BREVO_API_KEY` with `npx wrangler secret put ...`.

## Worker and Lark Setup

Local frontend development uses `npm run dev`. Full stack Worker development uses `npm run build && npm run worker:dev`, which serves `dist` and `/api/*` through Cloudflare Workers runtime.

To sync leads to Lark or Feishu, create a group custom bot, copy its webhook URL, and set it with `npx wrangler secret put LARK_WEBHOOK_URL`. If Lark is not configured or temporarily unavailable, the Worker still returns a successful form response after validation.

## Social Links

WhatsApp, email, and website links are always available. Add optional desktop and mobile social links with `VITE_SOCIAL_LINKEDIN_URL`, `VITE_SOCIAL_INSTAGRAM_URL`, and `VITE_SOCIAL_FACEBOOK_URL` in `.env.local`.
