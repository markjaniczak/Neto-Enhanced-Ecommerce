# Neto Enhanced Ecommerce
A Google Tag Manager (GTM) implementation of Google Enhanced Ecommerce for the Neto eCommerce platform. Includes a container file for quickly importing into GTM as well as the custom scripts required to push data from Neto into the GTM data layer.

## Before you Start
Ensure you already have a Google Analytics and Google Tag Manager account before proceeding with this guide.

## Guide

### Preparing Neto
In the Neto control panel, go to Settings and Tools > All Settings and Tools > Custom Scripts > Add New. Name the script something relevant such as Google Tag Manager - Enhanced Ecommerce.

Copy each of the scripts from the scripts folder into the relevant tabs.

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


## License
The code and the documentation are released under the MIT License.
