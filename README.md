# Clean Rows

Static B2B prospecting website for enterprise, SaaS and agency teams. The current white, ink and emerald design and animation system are preserved.

## Pages

- `dist/index.html`: ICP-based positioning for LinkedIn research, account-based campaigns and email outreach. Includes a targeting demo, quality workflow, field explorer with personal and company LinkedIn profiles in positions 3 and 4, process and audience tabs, pricing, order examples, FAQs and sample-request form.
- `dist/calculator.html`: standalone cost calculator, reached through the homepage footer. Uses the existing volume, seat and monthly/yearly calculations and states comparison assumptions.
- `dist/site-ui.js`: shared navigation and reading progress.
- `dist/app.js` and `dist/content.js`: homepage interactions and dynamic copy.
- `dist/calculator.js`: calculator interactions and the `set_lead_volume` WebMCP tool.

The public files contain no bounce-rate messaging or em dashes. Existing business facts and pricing are user-supplied. Phone availability remains qualified. The copy does not claim that LinkedIn profile URLs can be directly uploaded as advertising audiences.

## Forms and hosting

`netlify.toml` publishes `dist/`. On Netlify the form uses the original `lead` form; enable form detection and check real delivery before running ads. For a Netlify custom domain, set `data-contact-mode="netlify"` on the body.

On local or other static hosting, a valid sample request opens a WhatsApp draft to +91 8469847308. The visitor reviews it and presses Send. Opening a draft is not treated as delivered.

The existing Sites review URL is private. The original Netlify site is separate. Policy links request the documents by email because dedicated policy pages were not supplied.

## Validation

Checked both pages at 320, 390, 768, 1024 and 1440px with no page overflow or clipped headings/controls. Tested targeting toggles, reordered field keyboard navigation, process/support and enterprise/SaaS tabs, plan-to-form selection, required-field validation, footer-to-calculator navigation, mobile menu and Escape. Calculator shows $93 at 10K monthly, $400 at 50K monthly and $4,800 at 50K yearly. Browser error log was empty. No messages or requests were sent.

All local assets, cross-page links, anchors and IDs pass static validation. JavaScript syntax passes. Source is committed to the existing Sites Git remote.

The file preview has 10 field groups. Name and business email remain first and second; personal and company LinkedIn profiles are third and fourth. Remaining fields keep their original relative order.

The workflow logo strip uses original Instantly, Smartlead, lemlist, Apollo, HubSpot and LinkedIn artwork stored locally. Google Sheets has been replaced in this strip. The equal groups animate left to right, pause on hover or keyboard focus, and become a static grid for reduced-motion preferences. Provenance is in `LOGO-SOURCES.json`.

## Lead attribution (UTM tracking)

`dist/tracking.js` runs on both pages. On arrival it saves the visit's `utm_source`, `utm_medium`, `utm_campaign`, `utm_term`, `utm_content`, ad click IDs (`gclid`, `fbclid`, `li_fat_id`, `msclkid`), external referrer and landing page in `localStorage`. Visits with no tags are recorded as the referring site or `(direct)`, and a direct revisit never overwrites a tagged source. The first-ever source is kept separately as `first_touch`.

Every call to action gets a `data-cta` label in the form `page-section-purpose`, for example `home-hero-free-leads`, `home-pricing-plan-growth` or `calculator-page-free-leads`. The last one clicked in the tab is sent with the request.

Where it shows up:
- **WhatsApp requests** (Vercel and other static hosting): a `Ref:` line at the end of the message, e.g. `Ref: linkedin / paid / sept_saas / ad_a, button: home-pricing-plan-growth`.
- **Direct WhatsApp links** (FAQ and contact): the chat opens pre-filled with the same `Ref:` line.
- **Netlify forms**: hidden fields `utm_*`, `click_id`, `cta`, `landing_page`, `referrer` and `first_touch` on each submission.

Tag links you share like: `https://clean-rows.vercel.app/?utm_source=linkedin&utm_medium=paid&utm_campaign=sept_saas&utm_content=ad_a`.
