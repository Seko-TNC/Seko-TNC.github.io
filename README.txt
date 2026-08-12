RAFTEK WEBSITE — REVIEWED RELEASE
==================================

This package is ready for GitHub Pages.

UPLOAD
------
Upload all files to the root of the GitHub Pages repository.

The CNAME file is already configured for:
raftek.net

CONTACT FORM
------------
The contact form is configured to send enquiries to:
contact@raftek.net

GitHub Pages is static hosting, so the form uses FormSubmit as the form-delivery service.

FIRST-TIME FORM ACTIVATION
1. Publish the website.
2. Open https://raftek.net
3. Submit the contact form yourself once.
4. Check contact@raftek.net for the FormSubmit activation message.
5. Confirm/activate the form.
6. Submit another test enquiry.
7. Confirm that:
   - the email arrives;
   - Reply goes to the visitor's submitted email;
   - the form redirects to https://raftek.net/thanks.html.

LOGO
----
The header currently displays the text:
RafTek

To use a logo image instead:

1. Create a folder named:
   assets

2. Upload the logo, for example:
   assets/logo.png

3. In index.html replace:
   <a class="brand" href="#top" aria-label="RafTek home">RafTek</a>

   with:
   <a class="brand brand-logo" href="#top" aria-label="RafTek home">
     <img src="assets/logo.png" alt="RafTek">
   </a>

4. If desired, make the same change on:
   privacy.html
   thanks.html
   404.html

RELEASE CONTENTS
----------------
index.html       Main website
style.css        Site styling and responsive layout
script.js        EN/NL/TR translation and navigation behaviour
privacy.html     Privacy notice
thanks.html      Contact-form thank-you page
404.html         Custom not-found page
favicon.svg      Browser-tab icon
robots.txt       Search-engine crawler instructions
sitemap.xml      Search-engine sitemap
CNAME            Custom-domain configuration
.nojekyll        Ensures GitHub Pages serves the static files directly
README.txt       This file

IMPORTANT
---------
The privacy notice is a practical baseline for the current site and form setup.
If RafTek's legal entity details, registered address, form provider, hosting
arrangements, marketing activity, analytics or data-retention practices change,
review and update the notice accordingly.


PRODUCT IMAGES
--------------
The website now includes an assets folder with six optimised ESL images:

assets/raftek-esl-brand.png
assets/esl-netherlands.png
assets/esl-uk.png
assets/esl-turkey-promo.png
assets/esl-turkey-standard.png
assets/esl-turkey-multibuy.png

The branded RafTek label is used in the homepage hero.
The regional examples are displayed in the ESL Solutions section.
The remaining Turkish examples demonstrate alternate shelf-label layouts.

These files have been tightly cropped around the transparent product image
to avoid the large empty canvases in the original PhotoRoom exports.
