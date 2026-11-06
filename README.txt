BUSINESS TOOLS — FULL AUDIT BUILD

WHAT WAS CHECKED
- Customer registration remains name + four-digit code.
- Admin login remains the existing admin password.
- Existing Supabase project URL and publishable key are retained.
- Existing email function, package.json, and netlify.toml are preserved byte-for-byte from the prior email-ready package.
- Customer requests are stored in Admin History; Customer History contains administrator messages only.
- Customer can delete their own administrator messages. Admin can delete individual records, a customer's history, or a customer account.
- Admin can open a separate private message box for each customer.
- Admin can publish/clear bank information; customer requests wait 15 seconds before showing published information or unavailable status.
- After the second unsuccessful bank-information attempt, the existing support email is sent using the preserved Netlify function, then the site waits another 15 seconds and checks bank information again.
- Customer service form no longer shows the wording “Add Funds / Submit Request”; Facebook Page uses “Create Page” and other service forms use “Submit Request”.
- Existing service prices, gift-card totals, and ADS card visual were preserved. The ADS PIN remains fictional-only and is never stored or transmitted. The FB area remains a test-profile form and does not collect passwords or 2FA codes; real passwords, 2FA codes, or bank PINs are not collected.
- Admin dashboard includes per-customer website lock/unlock and subscription-request controls after the included SQL migration is applied.

SUBSCRIPTION PLANS
- 1 week: NGN 3,800
- 2 weeks: NGN 7,600
- 3 weeks: NGN 11,400
- 4 weeks: NGN 15,200
A locked customer can select a plan and confirm. After 15 seconds, the site displays the admin-published bank information or “Bank Not Available”. The request appears in Admin Dashboard. The admin must verify payment and unlock that specific customer. Unlocking lasts for the selected number of weeks.

IMPORTANT: DATABASE STEP REQUIRED
The lock/subscription feature needs the SQL migration in:
supabase/migrations/20261106_align_subscription_rpc_responses.sql
The lock tables and base RPCs have already been installed in this project during this chat. Before deploying this recovered website build, run supabase/migrations/20261106_align_subscription_rpc_responses.sql once in the SAME Supabase project. It aligns the subscription request and admin access RPC response shapes with this website. Do not rerun the earlier base migration.

EMAIL PRESERVATION
The Netlify function file netlify/functions/send-email.mjs is byte-for-byte identical to the previous email-ready package. package.json and netlify.toml are also preserved. Keep the existing Netlify environment variables GMAIL_USER and GMAIL_APP_PASSWORD unchanged. Deploy the COMPLETE project folder, not only public/index.html, so Netlify publishes the existing email function.

DEPLOY
Deploy the complete folder contents: public/index.html, package.json, netlify.toml, netlify/functions/send-email.mjs. Keep the supabase folder with the migration for reference. Use the existing Netlify site and retain its existing environment variables.

VERIFICATION LIMITS
- JavaScript syntax and package structure are checked locally.
- The intended Supabase project is not authorized to the connected Supabase tool, so the migration was not applied remotely. Apply the included SQL once in the existing project before deploying this build.
- Live email delivery and two-device behavior cannot be verified from this workspace because private Netlify settings and the live site are not accessible here. The email implementation itself was preserved byte-for-byte.


RECOVERED WEBSITE BUILD
This package was recovered from the BUSINESS TOOLS files already uploaded in the earlier conversation. The customer login now calls the existing login_customer RPC and handles its locked response token. Subscription prices match the agreed NGN 3,800 / 7,600 / 11,400 / 15,200 plans. The periodic customer-session check also recognizes SUBSCRIPTION_REQUIRED.
