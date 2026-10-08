# Kettle & Fern: a tracking and lifecycle lab

A small demo tea store used as a hands-on lab for event tracking, lifecycle marketing, experimentation and marketing automation. It is a learning project: no real orders are taken and no real customers are involved.

**Live site:** `https://YOUR-USERNAME.github.io/kettle-fern/` (replace with your address once Pages is on)

## What this project is

A single-page store with three teas, a cart, a mock checkout and an email signup. Every meaningful action sends a GA4-style event to the `dataLayer`, which Google Tag Manager (container `GTM-KD7RCPJK`) reads and forwards to Google Analytics 4. A live event log at the bottom of the page shows what is being sent.

## Events tracked

| Event | When it fires | Key parameters |
|---|---|---|
| `view_item_list` | Page load | `item_list_name`, `items` |
| `select_item` | Click on a tea name | `item_list_name`, `items` |
| `add_to_cart` | Click Add to cart | `currency`, `value`, `items` |
| `begin_checkout` | Click Go to checkout | `currency`, `value`, `items` |
| `purchase` | Click Place order (demo only) | `transaction_id`, `currency`, `value`, `items` |
| `cta_click` | Click the hero button | `cta_id`, `cta_location` |
| `sign_up` | Submit the email form | `method`, `signup_location` |

Design notes:
- Ecommerce events follow GA4's recommended names and item structure.
- The `ecommerce` object is cleared before each ecommerce push so values do not carry over between events.
- The email address is deliberately never sent to the `dataLayer`, because personal data should stay out of analytics tags.

## Project roadmap

1. **Event tracking** (in progress): GTM container, GA4 property, custom events verified in debug mode, written tracking plan.
2. **Lifecycle and CRM:** connect the site's events to a CRM tool and build three flows: welcome, browse or cart abandonment, and win-back.
3. **Experimentation:** baselines, sample size and power, an A/A test and experiment write-ups, practised on a large public e-commerce events dataset.
4. **Automation:** scheduled reporting and lead-handling workflows using Make, Zapier or n8n, with AI steps.

## Files

- `index.html`: the whole site (HTML, CSS and JavaScript in one file)
- `README.md`: this file

## Limitations

- Traffic is too low for real experiments, so experimentation work is done on a separate public dataset.
- The checkout is a mock. No payment is processed and no order data is stored.
