# Votingportaldemo
# CommonGround: Online Voting Prototype

A responsive, multi-page-style online voting demo where citizens can browse elections, sign in, cast one ballot per election, and get a confirmation reference. Administrators can create elections and monitor accounts and usage from a dedicated portal.

Built with vanilla JavaScript, Bootstrap 5 and Firebase. There is no build step and nothing to install.

>  **Demo only.** This is a front-end prototype, not an official election system. It does not verify voter identity or eligibility, protect ballot secrecy, or provide the auditability needed for real elections. It is not affiliated with any government department. Do not enter real personal information.

## Features

**For voters**
- Browse open and closed elections with details and ballot options
- Register and sign in with email and password (Firebase Authentication)
- Ballot, review, submit flow with a confirmation reference
- One vote per election, enforced in the app and in the database rules
- Personal dashboard with voting activity and session details

**User sessions**
- "Keep me signed in on this device" option (persistent vs. tab-only session)
- Automatic sign-out after 30 minutes of inactivity (7 days for remembered sessions), with a warning beforehand
- Session data cleared on sign out

**For administrators**
- Separate admin sign in and access-request flow
- Admin approval handled by a Firebase Cloud Function that sets a custom `admin` claim
- Create elections that appear publicly straight away
- View registered accounts, recorded ballots and page-usage stats

## Tech stack

| Area | Tools |
|---|---|
| Front end | HTML, CSS, JavaScript (ES modules), Bootstrap 5, Bootstrap Icons |
| Routing | Lightweight hash router |
| Auth | Firebase Authentication (email/password, custom claims) |
| Data | Firebase Realtime Database with security rules |
| Backend | Firebase Cloud Functions (admin approval) |

## Getting started

1. Enable **Email/Password** under Firebase Console → Authentication → Sign-in method.
2. Publish `database.rules.json` to your Realtime Database.
3. Run the dev server and open the URL it prints:
   ```bash
   node dev-server.mjs
   # http://localhost:5173
   ```
4. *(Optional)* Deploy the Cloud Function to activate the first admin:
   ```bash
   firebase deploy --only functions
   ```

Use your own Firebase config in `firebase.js`.

## What I learned

- Structuring a single-page app without a framework (routing, state, rendering)
- Firebase Auth flows, persistence modes and custom claims
- Writing Realtime Database rules that make votes write-once and keep user data private
- Handling async auth state and race conditions in the browser

## Limitations / next steps

- Real identity verification and eligibility checks
- Ballot secrecy and an audit trail
- Live results instead of sample figures
- Password reset and email verification
- 
view live demo at votingsitesoutha.netlify.app
