# Jobbly release checklist

Do not publish the rewritten policy or submit the app until the first six items are complete.

1. Implement a separate affirmative permission screen before the first Gemini transfer. Name Google Gemini, explain the purpose and data, and store permission version and timestamp on the server.
2. Add AI withdrawal under Profile → Settings → AI and data sharing. Enforce withdrawal in the backend, explain which application features stop, and keep account deletion and privacy rights available.
3. Stop requiring personnummer, birth date, gender and full address for every application. Request personnummer only when the specific employer form actually requires it.
4. Extend account deletion to remove all user objects from Supabase `application-runs`, including CV and cover-letter copies, question screenshots and any diagnostic artifacts. Test deletion failures and retries.
5. Implement and document the approved retention schedule for applications, messages, automation data, logs, backups and processor copies.
6. Enforce the 18-year minimum during onboarding and before AI use. Keep the terms and policy at 18; answer App Store age-rating questions separately.
7. Create and test `support@jobbly.se`, publish a support page, add Support/Contact under Profile → Settings, and enter the working Support URL in App Store Connect.
8. Confirm the live Supabase region and plan, Render workspace/log settings, Gemini paid billing and DPA, Resend domains and region, Superwall settings, and all processor agreements and subprocessors.
9. Update App Store Connect privacy answers for contact data, identifiers, user content, location, purchases, product interaction and applicable diagnostics. Use the existing GitHub Pages privacy URL.
10. Remove or narrowly scope `NSAllowsArbitraryLoads`, run an end-to-end release test, and obtain Swedish privacy-lawyer review of legal bases, personnummer, retention, transfers and the need for a DPIA.
