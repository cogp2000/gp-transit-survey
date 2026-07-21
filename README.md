# Galena Park Transit Survey

This package contains:

- `index.html` — complete bilingual survey website
- `city-logo.png` — City of Galena Park logo used by the site
- `Code.gs` — Google Apps Script receiver that writes responses to a private Google Sheet

## 1. Create the Google Sheet

1. Sign in to the City Google account.
2. Create a new Google Sheet.
3. Name it something like `Galena Park Transit Survey Responses`.
4. Do not make the Sheet public.

## 2. Add the Apps Script receiver

1. In the Sheet, open **Extensions → Apps Script**.
2. Delete the sample code.
3. Paste the complete contents of `Code.gs`.
4. Save the project.
5. Select **Deploy → New deployment**.
6. Choose **Web app**.
7. Set **Execute as** to yourself/the City account.
8. Set **Who has access** to **Anyone**.
9. Deploy and authorize the script.
10. Copy the Web App URL. It should begin with:
   `https://script.google.com/macros/s/.../exec`

## 3. Connect the HTML form

Open `index.html` and find:

```js
const APPS_SCRIPT_URL = "PASTE_YOUR_GOOGLE_APPS_SCRIPT_WEB_APP_URL_HERE";
```

Replace the placeholder with the Web App URL, keeping the quotation marks.

## 4. Publish with GitHub Pages

1. Create a repository in the City GitHub account.
2. Upload `index.html` and `city-logo.png` to the root of the repository.
3. Open **Settings → Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select the `main` branch and `/root`.
6. Save.
7. GitHub will display the public survey URL after deployment.

## Important IP-address note

A static GitHub Pages form submitting directly to Google Apps Script does not reliably provide the respondent’s IP address to Apps Script. The included form records timestamps, browser user-agent information, referrer, and all submitted answers without adding any verification step.

Reliable IP collection would require an additional server-side proxy, such as a Cloudflare Worker. Do not advertise IP collection in the privacy notice unless that proxy is actually installed and tested.

## Testing checklist

Before sharing the survey publicly:

1. Submit one test in English.
2. Submit one test in Spanish.
3. Test on a phone.
4. Test all conditional fields.
5. Confirm the Google Sheet receives every field.
6. Confirm named testimonials require a name.
7. Confirm follow-up and focus-group selections require an email or telephone number.
8. Confirm the final City privacy and public-information language with the City Attorney.


## Connected production endpoint

The current `index.html` is connected to:

`https://script.google.com/macros/s/AKfycbzrsoj-pVIwlZEn25g0DmakKuY-Gv59TEuxs9hj1K8r4UmcDqc6OUIUTdzBzY9yRKJc/exec`
