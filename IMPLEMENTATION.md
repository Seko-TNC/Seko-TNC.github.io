# RafTek multilingual homepage rollout

The homepage takes a store owner from a familiar task, changing a price, to an image-led explanation, benefits for their staff, a one-section trial and a live demo request. English is the default. Visitors can choose Nederlands or Türkçe at the top of every homepage.

## 1. Make a branch and identify the publishing folder

1. Open the RafTek repository and find **Settings → Pages**. If it publishes from a branch, note the branch and folder. If it uses GitHub Actions, inspect the workflow to see which directory it uploads.
2. Create a branch from the publishing source, for example `raftek-multilingual-homepage`. Copy the files into that branch first. Keep a record of the last live commit, so you can revert this change in one operation.
3. Check the intended host before making the campaign live. GitHub’s Pages terms restrict using the service to run an online business and sites primarily facilitating commercial transactions. Review those limits for RafTek’s use. The same files can be published on a static host such as Cloudflare Pages using the GitHub repository as the source. With Cloudflare Pages, select the directory containing `index.html` as the output directory. The package needs no build step.

[GitHub Pages publishing source](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site) · [GitHub Pages limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits) · [Cloudflare Pages static HTML guide](https://developers.cloudflare.com/pages/framework-guides/deploy-anything/)

## 2. Copy the seven website files

Extract the ZIP. Put these files alongside the existing homepage, preserving the two language subfolders. Verify the layout in the GitHub file listing. For a `/docs` publishing source, the paths below are relative to `docs/`. The implementation guide can stay on your computer.

| File to copy | Public page or purpose |
| --- | --- |
| `index.html` | English homepage at `/` |
| `nl/index.html` | Dutch homepage at `/nl/` |
| `tr/index.html` | Turkish homepage at `/tr/` |
| `thanks.html` | English submission confirmation |
| `nl/thanks.html` | Dutch submission confirmation |
| `tr/thanks.html` | Turkish submission confirmation |
| `raftek-pilot.css` | Shared layout, colour and responsive styles |

Retain the existing `assets/` folder, `favicon.svg`, `privacy.html` and any custom-domain configuration such as `CNAME`. The new homepage files are complete HTML documents. You can upload them using GitHub’s web interface or copy them into a local checkout. In the web editor, use the pencil icon to replace an existing file. To create a nested file, choose **Add file → Create new file** and enter a path such as `nl/index.html`. If your current homepage runs a translation script, the new homepage files supply each language directly in HTML.

| Existing image path from the earlier RafTek package | Placement |
| --- | --- |
| `assets/raftek-esl-brand.png` | Opening product image on all three pages |
| `assets/esl-uk.png` | English label example |
| `assets/esl-netherlands.png` | Dutch label example |
| `assets/esl-turkey-promo.png` | Turkish promotion example |

Check those names and letter case against your repository. If your image lives at a different path, edit the corresponding `src`. For the shared hero image, also edit the absolute `og:image` URL in each homepage and adjust `width` and `height` if the replacement has a different aspect ratio. If you change the example pictured, update both its alt text and caption. Label artwork can show sample prices in different currencies, while the caption explains what the visitor is seeing.

## 3. Preview the branch locally

From the directory containing the new `index.html` in a local copy, run:

```bash
python3 -m http.server 8000
```

Open [English](http://localhost:8000/), [Nederlands](http://localhost:8000/nl/) and [Türkçe](http://localhost:8000/tr/). If you edit entirely on GitHub, download the test branch as a ZIP and serve its publishing directory the same way. Copying the new files into the existing checkout keeps the original images available for this preview.

Switch between languages from each page. On a phone, check that the headline and demo button are legible and the label images are visible. Click **How it works**, expand an FAQ, and follow **Request a live demo** to the form. The localized confirmation pages can also be opened directly for layout checks. Their direct URLs do not test submission.

If you have an unfamiliar retailer available, ask them to explain what the product does, find the demo request without prompting, and say what they expect to happen after submitting. Ask what questions they would still need answered before trying it in a store.

[GOV.UK moderated usability testing](https://www.gov.uk/service-manual/user-research/using-moderated-usability-testing)

## 4. Configure and test demo enquiries

1. The three forms use the existing FormSubmit endpoint `https://formsubmit.co/contact@raftek.net`. If you change the recipient, update the three `action` URLs and the email links beside the forms.
2. Check the destination in each form. The `_next` field uses the public URLs `https://raftek.net/thanks.html`, `https://raftek.net/nl/thanks.html` and `https://raftek.net/tr/thanks.html`. The **Page language** field and the email subject identify the language to use when you reply. If production uses a different hostname, update the absolute URLs in the three forms, canonical and alternate tags, and social metadata together.
3. Check that the existing privacy notice describes the actual enquiry workflow, including the use of FormSubmit, and that it is linked next to the send button. If you already have Dutch and Turkish notices, point the two notice links in each homepage to its translated notice. If the shared notice is English, label its link **Privacyverklaring (Engels)** and **Gizlilik bildirimi (İngilizce)** on those pages until translations are ready.
4. Test on the deployed site or a staging copy. Send a clearly labelled test from each language and check that the inbox receives it, the subject and reply address are correct, and the browser reaches the matching confirmation page. Follow any FormSubmit activation email and submit a fresh test after activation. Also check the CAPTCHA path and the direct email fallback. Staging submissions will use the specified `_next` URL, so substitute the staging hostname in a disposable test copy if needed.
5. Reply to legitimate enquiries in the language used on the page. Agree a time and send a meeting invitation. The on-site wording promises an email to arrange a time, so a submission means a request has been sent.

[FormSubmit documentation](https://formsubmit.co/documentation) · [FormSubmit help](https://formsubmit.co/help) · [W3C forms guidance](https://www.w3.org/WAI/tutorials/forms/)

### Let visitors choose a time directly

The ZIP is ready for email scheduling. Once you have a public booking link and have opened test slots, add the following link **above each form** in the `#contact` section. Use the corresponding text and real scheduling URL for each language. Keep the request form available for visitors who prefer arranging the time by email.

```html
<!-- English, index.html -->
<p><a class="button" href="https://YOUR-BOOKING-URL">Choose a time for a live demo</a></p>

<!-- Dutch, nl/index.html -->
<p><a class="button" href="https://YOUR-BOOKING-URL">Kies een tijd voor een live demo</a></p>

<!-- Turkish, tr/index.html -->
<p><a class="button" href="https://YOUR-BOOKING-URL">Canlı demo için saat seçin</a></p>
```

Test the booking flow in a private tab from each language, including the visitor’s time zone, the confirmation invitation, cancellation and rescheduling. If the booking page is only available in one language, identify that language next to its link. The email form remains useful even if no slots are open.

## 5. Publish and check the public URLs

Review the changes in a pull request. Once the preview and enquiry path pass, merge into the publishing branch or deploy that branch through your hosting workflow. On the deployed domain, repeat the checks for `/`, `/nl/` and `/tr/`. Test all three inbox deliveries once on the final hostname, especially if you previously tested only on staging. If the deployment needs to be rolled back, revert the release commit and redeploy.

The language links work even with JavaScript disabled. Each page declares its language with `lang`, has its own canonical URL, and lists all three language variants with reciprocal `hreflang` links. English is also the `x-default` fallback. Keep those declarations in sync if URLs change. The website content and confirmation pages are translated. A third-party CAPTCHA or scheduling service can have its own language behaviour.

[Google multilingual sites guidance](https://developers.google.com/search/docs/specialty/international/managing-multi-regional-sites) · [Google localized page variants](https://developers.google.com/search/docs/specialty/international/localized-versions) · [W3C language selection](https://www.w3.org/International/questions/qa-when-lang-neg.en)

## 6. Track whether the funnel produces demos

Start with a simple lead log using the inbox and calendar. Give each genuine enquiry one row with language, date received, agreed demo date, whether it was held and whether a pilot was agreed. If you enable direct booking, include calendar bookings in the same log and deduplicate visitors who also emailed.

| Stage | Count it when |
| --- | --- |
| Valid request | A genuine retailer submits the form or emails |
| Confirmed demo | Both sides have a time, including self-service bookings |
| Held demo | The retailer attends |
| Agreed pilot | The retailer and RafTek agree the scope of a trial in one store section |

For the email route, compare confirmed demos with valid requests from the same period and allow time for replies. Compare held demos with confirmed demos whose appointment date has passed. Record the language where volume is sufficient to interpret differences. A button click gives you an indication of interest, while inbox and calendar records tell you whether it led to a meeting.

## Why the page is ordered this way

- **Make the unfamiliar tangible.** Noetel et al.’s review of reviews found that putting related text and visuals close together and calling attention to pertinent details can improve learning. The design puts the price-change explanation beside a captioned label. The findings come from learning research, so any effect on RafTek enquiries needs to be measured with retailers. [Noetel et al., 2022](https://doi.org/10.3102/00346543211052329)
- **Make the form easy to complete.** In a 65-person controlled study, Seckler et al. found that combined form improvements reduced completion time and submission attempts. The demo form uses visible labels, three required fields and one optional question. The study measures usability and supplies no RafTek conversion estimate. [Seckler et al., 2014](https://edoc.unibas.ch/entities/publication/6d0819d7-ce1d-4216-9c27-ee8a2bbc300a)
- **Carry the explanation into a conversation.** Lundin and Kindström’s case study of a B2B supplier and four customers examines how firms combine digital and human interactions across the buying journey. RafTek can use the site to explain the product, the demo to show a live update, and one store section to evaluate fit. [Lundin and Kindström, 2023](https://doi.org/10.1016/j.jbusres.2022.113639)
