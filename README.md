# CricForm: files to publish

This folder is ready to push to GitHub and serve with GitHub Pages. It holds the public pages that Google Play needs, plus the answer sheets for the Play Console forms.

## What is in here

| File | Purpose |
|---|---|
| `index.html` | Small landing page that links to the three pages below |
| `privacy.html` | Privacy Policy. Same text as the policy inside the app (build 0.27.17), including the sentence about the route line stored on the device |
| `terms.html` | Terms and Conditions (same text as in the app) |
| `account-deletion.html` | Account and data deletion page. This is the URL for Play Console's "Delete account URL" field |
| `app-ads.txt` | AdMob verification file, generated from the release build |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |
| `play-console/01` to `06` | Answers for Data safety, location and permissions, ads and Advertising ID, content rating, trader details, and the other App content forms |

Nothing here contains passwords, keys or signing details. The only personal detail is the support email address, which is already in the app's policy and is required to be public.

## Publish with GitHub Pages

1. Create a new public repository on GitHub. Two choices:
   - A project repository, for example `cricform`. Your pages will be at `https://<your-github-username>.github.io/cricform/privacy.html`.
   - A user site, a repository named exactly `<your-github-username>.github.io`. Your pages will be at `https://<your-github-username>.github.io/privacy.html`. Choose this one if you want `app-ads.txt` to work, because AdMob needs it at the root of the developer website.
2. Upload the files from this folder (everything except `play-console`, which you can keep private, though it contains nothing secret). Keep `.nojekyll` and `app-ads.txt`.
3. In the repository: Settings > Pages > Build and deployment > Source: "Deploy from a branch", Branch: `main`, folder `/ (root)`. Save.
4. Wait a minute or two, then open each URL on your phone while signed out of every account (a private browser tab works). All of these must open without a login:
   - `.../privacy.html`
   - `.../terms.html`
   - `.../account-deletion.html`
   - `.../app-ads.txt` (should show one line starting with `google.com, pub-`)
5. Put the exact tested URLs into Play Console: Privacy policy (App content), Delete account URL (App content > Data safety and Account deletion), and the developer website (Store settings).

## Things to know

- The policy date: the hosted `privacy.html` says "Updated 22 November 2026" because the route-line sentence was added after 8 November. The copy inside the 0.27.17 app still shows "Updated 8 November 2026", because the app was built before the date was refreshed. The text is the same. Set the same date in `src/legal.json` and rebuild at your next release so both match.
- Play Console must show the same support email, developer name and policy text as these pages.
- `app-ads.txt` only counts when it is served from the root of the website you list as your developer website in Play Console. A project page under `/cricform/` does not count.
- Keep a dated copy of these pages in the repository's history; Google and users may ask what the policy said on a given day.
- The pages state honestly that deletion of every native Bat Lab record by the in-app button has not been verified on a phone. Test Settings > Delete account on a phone with a test account before production and update the pages if the result changes anything.

## Order of work in Play Console

1. Publish the pages and test the URLs.
2. `play-console/05_TRADER_AND_DEVELOPER_DETAILS.md`, then `06_OTHER_APP_CONTENT_ANSWERS.md` for privacy policy, target audience, app access and Health apps.
3. `01_DATA_SAFETY_ANSWERS.md`, `02_LOCATION_AND_PERMISSIONS.md`, `03_ADS_AND_ADVERTISING_ID.md`, `04_CONTENT_RATING_ANSWERS.md`.
4. Upload `CricForm-0.27.17-release.aab` to internal testing, then closed testing, then production at a small percentage.
