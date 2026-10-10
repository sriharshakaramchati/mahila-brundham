# Mahila Brundham monthly contribution site
Mobile one-pager for a temple women's group (monthly Rs 5,000 / Rs 6,000 collection, first week): QR/UPI/bank, member status (Google sign-in or personal WhatsApp link), collector dashboard (admin.html), reminders to unpaid members only. Placeholders live in config.js. Backend: Code.gs (Google Apps Script, collector's own account). See SETUP.md.

# Setup (collector's Google account, free)
1. New Google Sheet -> Extensions -> Apps Script. Paste Code.gs. Edit CFG (GPay/PhonePe number, collector name, confirm group name).
2. Project Settings -> Script properties: ADMIN_PASSCODE (dashboard passcode), GOOGLE_CLIENT_ID (public ID already in config.js).
3. Run `setup` once, then `seedMembers` once (loads the 20 members from the diary). Authorize when asked.
4. Deploy -> New deployment -> Web app -> Execute as: Me, Access: Anyone. Copy the /exec URL into config.js `backendUrl`.
5. Add the real UPI QR as qr.png (set `qrImage`), UPI ID, bank, WhatsApp number in config.js.
6. Fill each member's mobile number in the sheet (Members tab, Phone). Then in admin.html use "WhatsApp" to send each unpaid member her personal link (works without Google), or members sign in with Google and enter their registered mobile once.
Monthly: on the 1st the script archives last month to the History tab and resets everyone to pending. On the 1st, 4th and 7th it emails unpaid members who have linked a Google account. Everyone else is reached with the WhatsApp buttons.
