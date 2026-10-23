# Solutions Summary

Brief summaries of the production WordPress and WooCommerce solutions in this portfolio. Each one was built for a real store, tested live, and is still solving the problem it was written for.

## Monument Builder for WooCommerce
[monument-builder](https://github.com/jaybeetech14/monument-builder)

A complete product configurator for monument and headstone retailers. Customers design engraved monuments in the browser, choosing per-line text, fonts, colors, and sizes, and watch the result update on a live Fabric.js canvas preview. The configured design flows cleanly through cart and checkout, and the shop gets a production-ready proof image attached to every order, a printable production sheet for the shop floor, custom order statuses for the fulfillment pipeline, and CSV bulk import for large catalogs. Built as 16 single-responsibility classes so each piece, canvas, cart, proof generation, imports, can be maintained on its own.

## WooCommerce Subscription Renewal Handler
[subscription-renewal-handler](https://github.com/jaybeetech14/subscription-renewal-handler)

Automates subscription renewals end to end. On every renewal payment it grants download access to the current month's file and awards tiered store credit, then revokes stale download permissions so only the current file is ever accessible. The hard part was reliability: it detects renewals directly from HPOS order meta because the stock detection reads the legacy posts table and silently fails on HPOS stores, covers three separate payment hooks with idempotency guards so renewals never double-award, and includes a manual retry tool and an admin debug log viewer. Roughly 1,000 lines, debugged against a live subscription store.

## Hardscape Mileage Delivery for WooCommerce
[hardscape-delivery](https://github.com/jaybeetech14/hardscape-delivery)

Mileage-based delivery pricing at checkout, powered by the Google Distance Matrix API. Customers pick pickup or delivery, enter an address, and see the fee calculated live from configurable distance tiers, while out-of-range addresses are rejected with a clear message instead of a broken total. The detail most delivery plugins get wrong: it recalculates tax on the delivery address rather than the billing address. Includes a merchant settings tab, server-side validation, and the delivery address on admin orders and customer emails.

## Discount Rules: Unlimited Elements Grid Compatibility
[discount-rules-ue-grid-compat](https://github.com/jaybeetech14/discount-rules-ue-grid-compat)

Fixes a display bug where product grids built with Unlimited Elements showed prices twice whenever a discount-rules plugin set sale prices dynamically instead of storing them. Three surgical interventions solve it: a price HTML guard that lets the grid own price display in the shop loop, a sale badge correction so discounted items still show the Sale badge, and CSS cleanup that styles the strikethrough and sale prices properly. It touches nothing outside the shop loop, so the rest of the store is unaffected.

## WordPress Code Snippets
[wp-code-snippets](https://github.com/jaybeetech14/wp-code-snippets)

Small, production-tested snippets, each solving one real problem:

- **Store Credit Button Reposition**: pure CSS that moves the WooCommerce Apply Store Credit button where customers actually look for it, below coupons on desktop and at the top of totals on mobile.
- **Trash Past Workshops Cron**: an hourly WP-Cron job that automatically trashes expired workshop posts after 5 PM site time on the event date, so stale events never linger on the site.
- **Recurring Events (ACF)**: a recurring and multi-day event system built on ACF fields, with occurrence expansion, an upcoming events grid shortcode, and an Elementor loop filter.
