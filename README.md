# Neto Enhanced Ecommerce
A Google Tag Manager (GTM) implementation of Google Enhanced Ecommerce (EE) for the Neto eCommerce platform. Includes a container file for quickly importing into GTM as well as the custom scripts required to push data from Neto into the GTM data layer. This implementation supports the following EE features:

- Measuring Product Impressions
- Measuring Product Clicks
- Measuring Views of Product Details
- Measuring Additions or Removals from a Shopping Cart
- Measuring Promotion Impressions
- Measuring Promotion Clicks
- Measuring Checkout Steps
- Measuring Purchases

While this implementation was designed for the [Neto Skeletal theme](https://github.com/NetoECommerce/Skeletal) it can be easily configured to work with a number of Neto themes.

## Before you Start
Ensure you already have a Google Analytics and Google Tag Manager account before proceeding with this guide.

## Guide

### Preparing Google Analytics
Google Analytics must first be configured to accept enhanced ecommerce data. Go to Admin > Ecommerce Settings and turn on both the _Enable Ecommerce_ and _Enable Enhanced Ecommerce Reporting_ options. Next, add the following labels for each of the checkout steps:

1. Email
2. Billing
3. Terms
4. Payment

Once complete it should look something like the following:

_image coming here_

Finally, go to Admin > Tracking Info > Tracking Code and find your analytics tracking code. It should look something like _UA-122xxxxxx-1_

### Preparing Google Tag Manager
Go to Admin > Import Container. Select container.json, choose to import it into a new or your existing workspace and choose the merge option.

This will configure everything you need in terms of tracking info.

### Preparing Neto
In the Neto control panel, go to Settings and Tools > All Settings and Tools > Custom Scripts > Add New. Name the script something relevant such as Google Tag Manager - Enhanced Ecommerce.

Copy each of the scripts from the scripts folder into the relevant tabs.


## License
The code and the documentation are released under the MIT License.
