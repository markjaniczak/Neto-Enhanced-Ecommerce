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

![Google Analytics step setup](https://imgur.com/2b8b287a-4004-4fb6-bd3a-974a6910a538)

Finally, go to Admin > Tracking Info > Tracking Code and find your analytics tracking code. It should look something like `UA-xxxxxxxxx-1`.

### Preparing Google Tag Manager
Go to Admin > Import Container. Select container.json, choose to import it into a new or your existing workspace and choose the merge option. The container has everything you need for gathering tracking information from the webstore such as clicks, views, cart and checkout events. It also has the tags required to send this data to Google Analytics.

Depending on your theme you may need to tweak a few settings once you've imported the container for all of the tracking features to work. These can be found in the _Neto - Configuration_ folder.

#### Carousel Plugin
Banner clicks are tracked based on the class name of the banners. Most Neto themes will use the Bootstrap carousel so you won't need to change anything here but if you're using a different carousel plugin you will need to specify which one. If you're unsure, check with [Neto support](https://www.netohq.com.au).

The following carousel plugins have been preconfigured in this container:
- Bootstrap
- Owl Carousel 2
- Slick

If you're using one of the above, just change the `Carousel Plugin` variable to the name above exactly. If you're using a different carousel plugin you will need to update this variable and add the corresponding slide and carousel class to the `Lookup Table - Carousel Container Class` and `Lookup Table - Carousel Slide Class` lookup tables.

#### Banner URLs
Banner views are tracked based off part of the banner image URL. Almost all Neto sites will use a URL like `/assets/marketing/banner.jpg` but this can vary as it's an editable option. If you open one of the banner images on your site and you see it's located elsewhere you will need to update the `Promotion URL` variable.

#### Thumbnails
Product thumbnail clicks and views are tracked using the class of the thumbnail container. In most Neto themes this will be `thumbnail` but this can vary too. If your theme uses a different class for thumbnail containers you will need to update the `Thumbnail Container Class` variable.

### Preparing Neto
In the Neto control panel, go to Settings and Tools > All Settings and Tools > Custom Scripts > Add New. Name the script something relevant such as `Google Tag Manager - Enhanced Ecommerce`. Copy the contents of each file from the scripts folder into the relevant tabs:

- page_header.html > Page Header
- page_footer.html > Page Footer
- purchase_confirmation.html > Purchase Confirmation (Thank You Page)
- product_page.html > Product Page (under description)
- product_thumbnails.html > Product Thumbnails

### Finished

That's all that's required to get Google's Enhanced Ecommerce running with a Neto store. While EE can track more than what's in this implementation such as:

- AJAX search results impressions and clicks
- Parts finder clicks
- Popup clicks
- Chat application clicks
- Custom goals

The above would generally require bespoke customisation.

### Advanced Configuration
Unfortunately, list names of where a product or banner appear cannot be easily obtained without further customisation to your theme. By default this implementation will list the location of a product view or banner view as the page type. i.e. the list for a product view on a category page will appear as `category`.

To be able to specify the list for product views you will need to do two things:

1. Remove the caching function from product thumbnails. In each thumbnail template of your theme you will likely find the following at the start of the file:

`[%CACHE type:'gallery' id:'[@inventory_id@]'%]`

and the following at the end of the file:

`[%/CACHE%]`

You can safely remove these lines from each thumbnail template.

2. Add the following line just before each thumb_list function where you want to specify the list name:

`[%set [@list_name@]%]LIST_NAME[%/set%]`

## License
The code and the documentation are released under the MIT License.
