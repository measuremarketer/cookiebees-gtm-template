<p align="center"><img src="logo.png" width="96" height="96" alt="Cookiebees"></p>

# Cookiebees tag template for Google Tag Manager

Send ecommerce events and first-party customer data from Google Tag Manager to [Cookiebees](https://cookiebees.io), the attribution, CDP and CRM platform for stores.

Use this template when your store's data layer is not in GA4's standard shape, or when you want to choose in Tag Manager exactly which values each event carries. If your data layer already pushes GA4 ecommerce events, the Cookiebees tag reads them on its own and you do not need this template.

## What it does

- Sends any event to Cookiebees: `purchase`, the checkout steps, cart and product events, or an event name of your own.
- Reads GA4's `ecommerce` object from the data layer, and lets you map any order value to one of your own variables: order id, value, currency, tax, shipping, discount, coupon, affiliation, payment type, shipping tier and items.
- Sends customer information mapped from your variables: email, phone, first and last name, street, city, state, zip, country and external id. Raw values are hashed by Cookiebees before they go to any ad platform.
- Carries any parameters of your own.

## Install

1. In Tag Manager, open **Templates**, and under **Tag Templates** choose **Search Gallery**. Find **Cookiebees** and add it to your workspace.
   Until the template is listed in the gallery: choose **New**, then the menu at the top right, **Import**, and select `template.tpl` from this repository.
2. Create a tag of type **Cookiebees**.
3. Enter your **tracking key**. It is in Cookiebees under Settings, Tracking, Install the code, and starts with `mmtrk_`.
4. Choose the **event name**.
5. Under **The Cookiebees tag**, keep "Is already installed on my site" if the Cookiebees tag is on your pages (recommended: it then loads from your own tracking domain). Otherwise choose "Load it for me".
6. Map your order values and customer information, add a trigger for the event, and publish.

Create one tag per event.

## Avoid sending an event twice

If the Cookiebees tag on your site listens to the data layer itself (its address contains `auto=1`), it already sends GA4-shaped events. Use this template only for the events your data layer does not push in GA4's shape, or install the Cookiebees tag without `auto=1`.

## Fields

| Field | What to enter |
| --- | --- |
| Cookiebees tracking key | Your workspace's key, starting with `mmtrk_`. |
| Event name | A standard event, or Custom with your own name. |
| The Cookiebees tag | Whether the tag is already on the site, or the template should load it. |
| Read the ecommerce object from the data layer | On when your data layer pushes GA4's `ecommerce` object. |
| Map order values | One row per value your data layer names differently. Mapped values win over the ecommerce object. |
| Customer data | One row per piece of customer information. |
| Your own parameters | Any name and value to keep with the event. |

`items` must be an array of objects with `item_id`, `item_name`, `price` and `quantity`.

## Permissions

| Permission | Why |
| --- | --- |
| Accesses global variables `cbq`, `cbq.q` | The queue the Cookiebees tag reads events from. |
| Injects scripts from `https://app.cookiebees.io/*` | Only when you choose "Load it for me". |
| Reads the data layer key `ecommerce` | Only when "Read the ecommerce object" is on. |

## Documentation

The full specification, with every event, parameter and shape of customer data Cookiebees reads: [knowledgebase.cookiebees.io/tracking/data-layer-and-cbq](https://knowledgebase.cookiebees.io/tracking/data-layer-and-cbq/)

## License

Apache License 2.0. See [LICENSE](LICENSE).
