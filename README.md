# Amazon Scraper Actor

## What is Amazon Scraper actor?
The Amazon Scraper is a data scraping tool designed to simplify your market research on Amazon. It's the perfect assistant for extracting a great deal of detailed product information, customer reviews, and much more. Whether you're digging into specific product URLs or making a wide keyword search, this tool is your best assistant to get valuable insights from Amazon's massive e-commerce platform. Easy to use and incredibly flexible, the Amazon Scraper actor saves you time and effort, making your research process a breeze.

### Key features
- 🗝️ Versatile Keyword Search: Just type in a keyword, and the tool gathers a wide array of product details, including titles, descriptions, and features.
- 🔗 Direct Product URL Scraping: Get in-depth information about a specific product by simply entering its URL.
*(For instance, using the URL https://www.amazon.com/EXCELLENT-ELITE-SPANKER-Tactical-Adjustable/dp/B0725FT5ZW will fetch information for that particular product.)*
- 📂 Category Scraping: Explore entire categories and gather data on all listed products with ease.
*(For example, https://www.amazon.com/s?i=specialty-aps&bbn=16225007011&rh=n%3A16225007011%2Cn%3A1292115011 targets the Computer Monitors subcategory.)*
- 🛒 Seller Products Fetching: Extract details on all products offered by a specific seller using their profile URL.
- 🔍 Utilization of Search URLs: Direct Amazon search URLs can also be used for scraping.
*(For example, the URL https://www.amazon.com/s?k=tactical+dog+harness can be used to scrape information on tactical dog harnesses.)*
- 💬 In-depth Review Extraction: Dive deep into customer reviews to understand market sentiments towards any product.
- 🌍 Multi-TLD Compatibility: The scraper supports various Amazon TLDs, enabling queries on different Amazon international websites like .com, .co.uk, .de, and others. This feature allows for a broader and more diverse data extraction, accommodating global market research and analysis.
- 📍 Postal Code for Location Specificity: Refine your search results geographically by entering the local postal code, ensuring more relevant data collection. However, it's important to note that not all countries may support the location setting by postal code.

## Use Cases | Who Can Use Amazon Scraper
- **Market researchers** to monitor market trends, consumer preferences, and competitive insights.
- **E-commerce businesses** for optimizing product listings, pricing strategies, and understanding competitor offerings.
- **Startups** to validate product ideas and identify niches within Amazon's marketplace.
- Data analysts for **collecting large datasets for analysis, forecasting, and reporting**.
- **Content creators** to generate product-related content by extracting detailed information and reviews.
- Developers to **integrate Amazon data into apps or websites** for enhanced user experiences.
- **Dropshippers** to identify profitable products to list in online stores.
- Corporate strategists to **make informed decisions** on product launches, market entry, and expansion.
- **Digital marketers** to tailor marketing campaigns based on in-depth product and market insights.
- **Brand managers** to monitor brand presence, customer feedback, and market positioning on Amazon.
- Academic researchers for **conducting studies on consumer behavior, e-commerce trends,** and product dynamics.
- SEO specialists to improve product visibility and **search rankings on Amazon**.

## Input
Either start with a keyword or specific store URLs to your research.

💡When you want to scrape over a specific list URL, just copy and paste the link as one of the **startUrl**.

![](https://cdn.epctex.com/actors/amazon/1.png)

If you start with a keyword, and you want to localize your search, you can choose a specific Amazon domain, and further localize it by entering a postal code.

![](https://cdn.epctex.com/actors/amazon/2.png)

You can limit the number of output results by either writing a number for number of listing items or list end page. Also, if you want to scrape product reviews too, don’t forget to switch it on, and limit the comments page if you want to.

💡If you would like to scrape only the first page of a list then put the link for the page and have the *endPage* as 1.

💡With the last approach that is explained above you can also fetch any interval of pages. If you provide the 5th page of a list and define the *endPage* parameter as 6 then you'll have the 5th and 6th pages only.

![](https://cdn.epctex.com/actors/amazon/3.png)

It is recommended to keep the other options as default.

![](https://cdn.epctex.com/actors/amazon/4.png)

### Input Parameters Explained

- *search*: (Optional) (String)
Enter the keyword for Amazon search. This keyword is used to find products related to your query on the Amazon platform.
<br/>

- *startUrls*: (Optional) (Array)
Specify URLs to initiate the scraping process. These should be either a list URL or a detail URL of the product or category you're interested in.
<br/>

- *amazonTld*: (Optional) (String)
Choose the specific Amazon top-level domain (TLD) that corresponds to your target country. For example, select 'Germany' to use amazon.de. This setting influences both search results and the functionality of the postal code feature. Ensure accurate selection for optimal location setting.
<br/>

- *postalCode*: (Optional) (String)
Input the local postal code to increase the specificity of location-based data. This option should be utilized in conjunction with the 'Amazon Country Domain' setting. Please note that the effectiveness of this feature varies, as not all countries may support location filtering by postal code.
<br/>

- *getReviews*: (Optional) (Bool)
Toggle this option to enable the extraction of product reviews.
<br/>

- *reviewsEndPage*: (Optional) (Number)
Specify the page number at which you wish to stop collecting reviews. By default, the scraper will continue until no more pages are available.
<br/>

- *maxItems*: (Optional) (Number)
You can limit scraped items. This should be useful when you search through the big lists or search results.
<br/>

- *proxy*: (Required) (Proxy Object)
Proxy configuration.
<br/>

- *extendOutputFunction*: (Optional) (String)
Function that takes a JQuery handle ($) as an argument and returns an object with data.
<br/>

- *customMapFunction*: (Optional) (String)
Function that takes each object's handle as an argument and returns the object with executing the function.

This solution requires the use of **Proxy servers**, either your own proxy servers or you can use [Apify Proxy](https://www.apify.com/docs/proxy).

### Amazon Scraper Input Examples

#### Fetch a Single Product
![](https://cdn.epctex.com/actors/amazon/5.png)

```json
{
  "startUrls": [
    "https://www.amazon.com/EXCELLENT-ELITE-SPANKER-Tactical-Adjustable/dp/B0725FT5ZW"
  ],
  "endPage": 2,
  "maxItems": 10,
  "proxy": {
    "useApifyProxy": true
  }
}
```

#### Fetch Products of a Category
![](https://cdn.epctex.com/actors/amazon/6.png)

```json
{
  "startUrls": [
    "https://www.amazon.com/s?i=specialty-aps&bbn=16225007011&rh=n%3A16225007011%2Cn%3A1292115011"
  ],
  "endPage": 2,
  "maxItems": 10,
  "proxy": {
    "useApifyProxy": true
  }
}
```

#### Fetch Results of a Search
![](https://cdn.epctex.com/actors/amazon/7.png)

```json
{
  "startUrls": [
    "https://www.amazon.com/s?k=tactical+dog+harness"
  ],
  "endPage": 2,
  "maxItems": 10,
  "proxy": {
    "useApifyProxy": true
  }
}
```

#### Fetch Results of a Search by Keyword
![](https://cdn.epctex.com/actors/amazon/8.png)

```json
{
  "search": "tactical dog harness",
  "amazonTld": ".com",
  "endPage": 2,
  "maxItems": 10,
  "proxy": {
    "useApifyProxy": true
  }
}
```

#### Fetch Products of a Seller
![](https://cdn.epctex.com/actors/amazon/9.png)

```json
{
  "startUrls": [
    "https://www.amazon.com/sp?ie=UTF8&seller=A2OVB8DG3JN6N0"
  ],
  "amazonTld": ".com",
  "endPage": 2,
  "maxItems": 10,
  "proxy": {
    "useApifyProxy": true
  }
}
```

#### Fetch Product Reviews
![](https://cdn.epctex.com/actors/amazon/10.png)

```json
{
  "startUrls": [
    "https://www.amazon.com/EXCELLENT-ELITE-SPANKER-Tactical-Adjustable/dp/B0725FT5ZW"
  ],
  "amazonTld": ".com",
  "getReviews": true,
  "reviewsEndPage": 2,
  "endPage": 2,
  "maxItems": 10,
  "proxy": {
    "useApifyProxy": true
  }
}
```

### Compute Unit Consumption
The actor is optimized to run blazing fast and scrape as many items as possible. Therefore, it forefronts all the detailed requests. If the actor doesn't block very often it'll scrape 100 listings in 2 minutes with ~0.02-0.04 compute units.

### Bugs, fixes, updates, and changelog
This scraper is under active development. If you have any feature requests you can create an issue from [here](https://github.com/epctex/amazon-scraper/issues).

## During the Run
During the run, the actor will output messages letting you know what is going on. Each message always contains a short label specifying which page from the provided list is currently specified. When items are loaded from the page, you should see a message about this event with a loaded item count and total item count for each page.

If you provide incorrect input to the actor, it will immediately stop with a failure state and output an explanation of what is wrong.

### Amazon Export
During the run, the actor stores results into a dataset. Each item is a separate item in the dataset.

You can manage the results in any language (Python, PHP, Node JS/NPM). See the FAQ or <a href="https://www.apify.com/docs/api" target="blank">our API reference</a> to learn more about getting results from this Amazon actor.

## Output

### Product Detail

```json
{
	"type": "product",
	"title": "TSPRO Tactical Dog Vest Harnesses with Handle 1.5 inch Wide Military Grade Strong Padded Thick Dog Harnesses Heavy Duty Dog Harnesses Quick-Release Buckle for Medium Large Dogs(Khaki-L)",
	"url": "https://www.amazon.com/TSPRO-Tactical-Harnesses-Military-Quick-Release/dp/B0BPSRP1ZR/ref=sr_1_43?dib=eyJ2IjoiMSJ9.sSdvwLMclQZDy2UPq_En39-40LSoj2nej9GjYGXj76z5tyCniBvXFTVLTW1KgHfCHGB9X3vfJCK-VBj5qdUgeBBFGVRxs133M6EU1dnmTM0eKhYhGYH4JeRu5SJZ3wtkceVJjNPbHKSsEESaG2jytA.Ne54E_KFU9hMXNKmqgVvo0Ia0ALV8Q1WexY_0mwu_3k&dib_tag=se&keywords=tactical+dog+harness&qid=1705102403&sr=8-43",
	"inStock": true,
	"maxQuantitySelection": "28",
	"brand": "TSPRO",
	"price": {
		"value": 39.99,
		"currency": "$"
	},
	"listPrice": {
		"value": 49.99,
		"currency": "$"
	},
	"shippingPrice": {
		"value": null,
		"currency": null
	},
	"shippingText": "FREE delivery Friday, January 19",
	"stars": 4.3,
	"starsBreakdown": {
		"5star": 0.56,
		"4star": 0.28,
		"3star": 0.09,
		"2star": 0.04,
		"1star": 0.04
	},
	"reviewsCount": 61,
	"answeredQuestions": null,
	"categories": [
		"Pet Supplies",
		"Dogs",
		"Collars, Harnesses & Leashes",
		"Harnesses",
		"Vest Harnesses"
	],
	"images": [
		"https://m.media-amazon.com/images/I/41eyNo1+QcL.jpg",
		"https://m.media-amazon.com/images/I/513eeIytxiL.jpg",
		"https://m.media-amazon.com/images/I/51HVaBo003L.jpg",
		"https://m.media-amazon.com/images/I/512TCT4DDDL.jpg",
		"https://m.media-amazon.com/images/I/51gDJ23dT2L.jpg",
		"https://m.media-amazon.com/images/I/51KhvTc12-L.jpg"
	],
	"seller": {
		"name": "TSPRO OUTDOOR",
		"url": "https://www.amazon.com/gp/help/seller/at-a-glance.html/ref=dp_merchant_link?ie=UTF8&seller=A2TYHXPD5TQ99B&asin=B0BPSRP1ZR&ref_=dp_merchant_link&isAmazonFulfilled=1",
		"id": "A2TYHXPD5TQ99B"
	},
	"variants": [
		{
			"title": "S-(Neck:17\"-25\",Chest:21\"-26\")",
			"url": "/dp/B0BPSPGMK2/ref=twister_B0BPSSCC42?_encoding=UTF8&psc=1",
			"price": ""
		},
		{
			"title": "M-(Neck:23.5\"-28\",Ches:23\"-31.5\")",
			"url": "/dp/B0BPSRCN8K/ref=twister_B0BPSSCC42?_encoding=UTF8&psc=1",
			"price": ""
		},
		{
			"title": "L -(Neck:25.5\"-36\",Chest:27\"-35.5\")",
			"url": "",
			"price": ""
		}
	],
	"features": [
		{
			"key": "Size",
			"value": "L -(Neck:25.5\"-36\",Chest:27\"-35.5\")"
		},
		{
			"key": "Color",
			"value": "Khaki"
		},
		{
			"key": "Pattern",
			"value": "Solid"
		},
		{
			"key": "Brand",
			"value": "TSPRO"
		},
		{
			"key": "Material",
			"value": "Nylon"
		}
	],
	"featureBullets": [
		"Tactical Dog Vest Harnesses.Well made and high guality genuine nylon material,the nylon dog Harnesses is thick, tough yet comfortable,and the soft padded interior provides a comfortable wearing and prevents your dog from rubbing against the skin.Double-layered nylon webbing with multiple lines of stitching for toughness and durability to take on all types of adventures and weather.When you receive and feel the Harnesses you will know that it was made with quality and care.",
		"Premium dog harnesses with handle.This training dog Harnesses has a padded control handle which is very comfortable for grip and makes control of your tactical dog easier in tough situations.When used for leisure walking,there is 3 extra D rings to attach your favorite dog training clicker or garbage bag capsule,worth the money.",
		"Heavy duty dog Harnesses & Quick-release buckles. The dog Harnesses with 2 quick release buckles and slider is easy to adjust the comfortable fit and take on/off.quick-release buckle with a smooth locking mechanism.Equipped with 3 large D-Rings for quick and easy leash attachment.Please follow the size chart to measure your dog carefully before purchasing to ensure the Harnesseses is fit well to your dog.Please kindly find the size chart.",
		"Padded Thick Dog Harnesses avoids any sensitive areas such as the under arms and neck which may be prone to rubbing, does not restrict natural shoulder movement. Ideal for mastiff, German Shepherd,Pit Bull,Labrador Retriever,Australian Shepherd,Boxers, Pointers ,Puppy,American/English Bulldog,Siberian Husky,Doberman, Belgian Malinois,Hurley Dog etc. for Small or Medium to Extra Large dogs breeds,and great for dog training, patrol,hiking, hunting, camping, working, runing, traveling,etc.",
		"100% Quality Warranty: Your satisfaction is our first priority, we take care of all quality-related issues with a REPLACEMENT OR FULL REFUND with 90days; If you encounter any problem while using, never hesitate to send email to us and we will make it all right for you."
	],
	"productAlert": "",
	"description": "",
	"specs": [],
	"reviewsLink": "https://www.amazon.com/TSPRO-Tactical-Harnesses-Military-Quick-Release/product-reviews/B0BPSRP1ZR/ref=cm_cr_dp_d_show_all_btm?ie=UTF8&reviewerType=all_reviews",
	"delivery": "Friday, January 19",
	"returnPolicy": "Free returns are available for the shipping address you chose. You can return the item for any reason in new and unused condition: no shipping charges    Learn more about free returns.   Free returns are available for the shipping address you chose. You can return the item for any reason in new and unused condition: no shipping charges    Learn more about free returns.   Free returns are available for the shipping address you chose. You can return the item for any reason in new and unused condition: no shipping charges    Learn more about free returns.",
	"relatedItems": [],
	"manufacturerHtml": "\n        <style type=\"text/css\">\n    /*\n     * Used when device = desktop\n     * Configured in: configuration/brazil-config/global/brand-story.cfg\n     */\n\n    /* Because the carousel is implemented as an ol list,\n       any lists in the card text will have a secondary list style (letters).\n       This will give an incorrect appearance to viewers,\n       so we set all lists to the primary list style (numbers). */\n    .aplus-brand-story-card ol li {\n        list-style: decimal;\n    }\n\n    /* Top level containers */\n    .aplus-module .apm-brand-story-hero {\n      -moz-box-sizing: border-box;\n      -webkit-box-sizing: border-box;\n      box-sizing: border-box;\n      width: 1464px;\n      height: 625px;\n      background-color: #fff;\n    }\n\n    .aplus-module .apm-brand-story-card {\n      -moz-box-sizing: border-box;\n      -webkit-box-sizing: border-box;\n      box-sizing: border-box;\n      width: 362px;\n      height: 453px;\n      background-color: #fff;\n    }\n\n    .apm-brand-story-hero,\n    .apm-brand-story-card {\n      -moz-box-sizing: border-box;\n      -webkit-box-sizing: border-box;\n      box-sizing: border-box;\n      position: relative;\n      width: 100%;\n      height: 100%;\n      float: none;\n    }\n\n    .aplus-module.brand-story-card-1-four-asin .apm-brand-story-card {\n      /* Only 12px to account for image cell border */\n      padding: 12px;\n    }\n\n    /* Full background image (Hero 1 & Card 2) */\n    .aplus-module .apm-brand-story-background-image {\n      -moz-box-sizing: border-box;\n      -webkit-box-sizing: border-box;\n      box-sizing: border-box;\n      overflow: hidden;\n      position: absolute;\n      width: 100%;\n      height: 100%;\n    }\n\n    /* Card 1 small images */\n    .aplus-module .apm-brand-story-image-row {\n      -moz-box-sizing: border-box;\n      -webkit-box-sizing: border-box;\n      box-sizing: border-box;\n      height: 185px;\n      padding: 0px;\n      margin: auto;\n      display: flex;\n    }\n\n    .aplus-module .apm-brand-story-image-row .apm-brand-story-image-cell {\n      /* Use content-box to ensure image size matches editor schema */\n      -moz-box-sizing: content-box;\n      -webkit-box-sizing: content-box;\n      box-sizing: content-box;\n      padding: 0px;\n      margin: 0px;\n      width: 166px;\n      border: 1px solid #fff;\n    }\n\n    .aplus-module .apm-brand-story-image-row .apm-brand-story-image-cell .apm-brand-story-image-link {\n      display: block;\n      width: 100%;\n      height: 100%;\n    }\n\n    .aplus-module .apm-brand-story-image-row .apm-brand-story-image-cell .apm-brand-story-image-link .apm-brand-story-image-img {\n      display: block;\n      width: 100%;\n      height: 100%;\n      object-fit: cover;\n    }\n\n    /* Card 3 logo image */\n    .aplus-module .apm-brand-story-logo-image {\n        -moz-box-sizing: content-box;\n        -webkit-box-sizing: content-box;\n        box-sizing: content-box;\n        height: 145px;\n        margin: 0px 4px;\n        padding: 20px;\n        padding-bottom: 0px;\n    }\n\n    /* Text overlays */\n    .aplus-module .apm-brand-story-text-bottom {\n      -moz-box-sizing: border-box;\n      -webkit-box-sizing: border-box;\n      box-sizing: border-box;\n      position: absolute;\n      bottom: 13px;\n      left: 13px;\n    }\n\n    .aplus-module .apm-brand-story-hero .apm-brand-story-text-bottom {\n        background-color: rgba(0,0,0,0.6);\n        color: #fff;\n        padding: 13px 65px 13px 13px; /* accounts for overlap of first card */\n        width: 437px;\n    }\n\n    .aplus-module.brand-story-card-2-media-asset .apm-brand-story-text-bottom {\n        background-color: rgba(255,255,255,0.6);\n        color: #000;\n        padding: 13px;\n        width: 336px;\n    }\n\n    .aplus-module.brand-story-card-1-four-asin .apm-brand-story-text {\n        margin-top: 8px;\n    }\n\n    .aplus-module.brand-story-card-1-four-asin .apm-brand-story-text.apm-brand-story-text-single {\n        margin-top: 20px;\n    }\n\n    .aplus-module.brand-story-card-1-four-asin .apm-brand-story-text h3 {\n        white-space: nowrap;\n        overflow: hidden;\n        text-overflow: ellipsis;\n    }\n\n    .aplus-module .apm-brand-story-slogan-text {\n        -moz-box-sizing: content-box;\n        -webkit-box-sizing: content-box;\n        box-sizing: content-box;\n        margin: 0px 4px;\n        padding: 20px;\n    }\n\n    .aplus-module .apm-brand-story-faq {\n        -moz-box-sizing: content-box;\n        -webkit-box-sizing: content-box;\n        box-sizing: content-box;\n        padding-top: 10px;\n    }\n\n    .aplus-module .apm-brand-story-faq-block {\n        margin: 0px 10px;\n        padding: 10px;\n    }\n</style>\n                 <style>\n    .aplus-v2 .apm-brand-story-carousel-container {\n        position: relative;\n    }\n\n    .aplus-v2 .apm-brand-story-carousel-hero-container,\n    .aplus-v2 .apm-brand-story-carousel-hero-container > div {\n        position: absolute;\n        width: 100%;\n    }\n</style>\n\n\n    <style>\n        /*\n          Ensuring the carousel takes only the space it needs.\n          The sizes need to be set again on the absolutely positioned elements so they can take up space.\n        */\n        .aplus-v2 .apm-brand-story-carousel-container,\n        .aplus-v2 .apm-brand-story-carousel-hero-container {\n            height: 625px;\n            width: 100%;\n            max-width: 1464px;\n            margin-left: auto;\n            margin-right: auto;\n            overflow: hidden;\n        }\n\n        /*\n          This centers the carousel vertically on top of the hero image container and after the logo area (125px).\n          Margin-top = (heroHeight - cardHeight - logoAreaHeight) / 2 + logoAreaHeight\n        */\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-row-inner{\n            margin-top: 149px;\n        }\n\n        /*\n          Cards need to have a width set, otherwise they default to 50px or so.\n          All cards must have the same width. The carousel will resize itself so all cards take the width of the largest card.\n          The left margin is for leaving a space between each card.\n        */\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-card {\n            width: 362px;\n            margin-left: 30px !important;\n        }\n\n        /* styling the navigation buttons so they are taller, flush with the sides, and have a clean white background */\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-left,\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-right {\n            padding: 0px;\n        }\n\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-left .a-button-image,\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-right .a-button-image {\n            border: none;\n            margin: 0px;\n        }\n\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-left .a-button-image .a-button-inner,\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-right .a-button-image .a-button-inner {\n            background: #fff;\n            padding: 20px 6px;\n        }\n\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-left .a-button-image .a-button-inner {\n            border-radius: 0px 4px 4px 0px;\n        }\n\n        .aplus-v2 .apm-brand-story-carousel .a-carousel-col.a-carousel-right .a-button-image .a-button-inner {\n            border-radius: 4px 0px 0px 4px;\n        }\n    </style>\n  <div> \n        <div class=\"apm-brand-story-carousel-container\">\n             <div class=\"apm-brand-story-carousel-hero-container\">\n                             <div class=\"celwidget aplus-module brand-story-hero-1-image-logo aplus-brand-story-hero\" cel_widget_id=\"aplus-brand-story-hero-1-image-logo\">\n            <div class=\"apm-brand-story-hero\">\n    <div class=\"apm-brand-story-background-image\">\n                                      <img alt=\"TSPRO Tactical Dog Collar\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/S/aplus-media-library-service-media/449a808d-f02e-4625-8b65-d9f74d194792.__CR0,0,1464,625_PT0_SX1464_V1___.jpg\"><noscript><img alt=\"TSPRO Tactical Dog Collar\" src=\"https://m.media-amazon.com/images/S/aplus-media-library-service-media/449a808d-f02e-4625-8b65-d9f74d194792.__CR0,0,1464,625_PT0_SX1464_V1___.jpg\"/></noscript>   </div>\n\n     </div>\n<div style=\"clear:both\"></div>\n   </div>\n               </div>\n\n                     <div id=\"apm-brand-story-carousel\" data-a-carousel-options=\"{&quot;minimum_gutter_width&quot;:10,&quot;show_partial_next&quot;:true,&quot;name&quot;:&quot;brand-story-carousel&quot;,&quot;single_page_align&quot;:&quot;left&quot;,&quot;circular&quot;:false,&quot;carousel_display_strategy&quot;:&quot;single&quot;,&quot;currentGutter&quot;:10}\" class=\"a-begin a-carousel-container a-carousel-static a-carousel-display-stretchyGoodness a-carousel-transition-slide apm-brand-story-carousel size-cards a-carousel-container\"><input autocomplete=\"on\" type=\"hidden\" class=\"a-carousel-firstvisibleitem\"> <div class=\"a-row a-carousel-controls a-carousel-row a-carousel-has-buttons\"><div class=\"a-carousel-row-inner\"><div class=\"a-carousel-col a-carousel-left\"><a class=\"a-button a-button-image a-carousel-button a-carousel-goto-prevpage\" tabindex=\"0\" href=\"#\"><span class=\"a-button-inner\"><i class=\"a-icon a-icon-previous\"><span class=\"a-icon-alt\">Previous page</span></i></span></a></div><div class=\"a-carousel-col a-carousel-center\"><div class=\"a-carousel-viewport\"><ol class=\"a-carousel\" role=\"list\">  <li class=\"a-carousel-card apm-brand-story-carousel-card-0\" role=\"listitem\">   </li>      <li class=\"a-carousel-card apm-brand-story-carousel-card-1\" role=\"listitem\">           <div class=\"celwidget aplus-module brand-story-card-3-about aplus-brand-story-card\" cel_widget_id=\"aplus-brand-story-card-3-about\">\n            <div class=\"apm-brand-story-card\">\n    <div class=\"apm-brand-story-logo-image\">\n                                      <img alt=\"TSPRO dog collars\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/S/aplus-media-library-service-media/1fd0c8fe-5278-4404-a290-baa61fa19452.__CR0,0,315,145_PT0_SX315_V1___.jpg\"><noscript><img alt=\"TSPRO dog collars\" src=\"https://m.media-amazon.com/images/S/aplus-media-library-service-media/1fd0c8fe-5278-4404-a290-baa61fa19452.__CR0,0,315,145_PT0_SX315_V1___.jpg\"/></noscript>   </div>\n    <div class=\"apm-brand-story-slogan-text\">\n                                          <p> <span class=\"a-text-bold\">The world is coloful, let's make our dogs colorful too!</span> </p>     <p> Wish our products can convey your caring to your dogs. Henri Matisse, one of the recognition as a leading figure in modern art. The aesthetics of Fauvism are reflected in his work: bold colors, concise shapes, harmonious compositions and strong ornamentation. The founder of the TSPRO brand agrees with this concept. So the TSPRO brand has a dog collars &amp; leashes in 10 colors! </p>    </div>\n</div>\n<div style=\"clear:both\"></div>\n   </div>\n </li>    <li class=\"a-carousel-card apm-brand-story-carousel-card-2\" role=\"listitem\">           <div class=\"celwidget aplus-module brand-story-card-2-media-asset aplus-brand-story-card\" cel_widget_id=\"aplus-brand-story-card-2-media-asset\">\n            <div class=\"apm-brand-story-card\">\n    <div class=\"apm-brand-story-background-image\">\n                                      <img alt=\"TSPRO Tactical Dog Collars\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/S/aplus-media-library-service-media/a647cbde-36ad-4397-9e17-27072198d823.__CR0,0,362,453_PT0_SX362_V1___.jpg\"><noscript><img alt=\"TSPRO Tactical Dog Collars\" src=\"https://m.media-amazon.com/images/S/aplus-media-library-service-media/a647cbde-36ad-4397-9e17-27072198d823.__CR0,0,362,453_PT0_SX362_V1___.jpg\"/></noscript>   </div>\n\n     <div class=\"apm-brand-story-text-bottom\">\n                                               <h3> Premium Dog Collars &amp; leashes </h3>                                    <p> <span class=\"a-text-bold\">10 colors choice!</span> </p>    </div>\n     </div>\n<div style=\"clear:both\"></div>\n   </div>\n </li>    <li class=\"a-carousel-card apm-brand-story-carousel-card-3\" role=\"listitem\">           <div class=\"celwidget aplus-module brand-story-card-1-four-asin aplus-brand-story-card\" cel_widget_id=\"aplus-brand-story-card-1-four-asin\">\n                  <div class=\"apm-brand-story-card\">\n    <div class=\"apm-brand-story-image-row\">\n      <div class=\"apm-brand-story-image-cell\">\n          <a class=\"a-link-normal apm-brand-story-image-link\" target=\"_blank\" rel=\"noopener noreferrer noopener\" href=\"/dp/B09QJQN4NZ/ref=emc_bcc_2_i\">                               <img alt=\"TSPRO Tactical Dog Collar 1.5 inch Wide Dog Collar Military Grade Strong Dog Collar Thick Dog Col...\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"apm-brand-story-image-img a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/I/51uMHMu%2BXzL.__AC_SR166,182___.jpg\"><noscript><img alt=\"TSPRO Tactical Dog Collar 1.5 inch Wide Dog Collar Military Grade Strong Dog Collar Thick Dog Col...\" src=\"https://m.media-amazon.com/images/I/51uMHMu%2BXzL.__AC_SR166,182___.jpg\"/></noscript>   </a> </div>\n      <div class=\"apm-brand-story-image-cell\">\n          <a class=\"a-link-normal apm-brand-story-image-link\" target=\"_blank\" rel=\"noopener noreferrer noopener\" href=\"/dp/B0B5L1J6HP/ref=emc_bcc_2_i\">                               <img alt=\"TSPRO Premium Dog Collar with Handle Thick Dog Collar Adjustable Dog Collar Heavy Duty Quick-Rele...\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"apm-brand-story-image-img a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/I/51eIj0VXIGL.__AC_SR166,182___.jpg\"><noscript><img alt=\"TSPRO Premium Dog Collar with Handle Thick Dog Collar Adjustable Dog Collar Heavy Duty Quick-Rele...\" src=\"https://m.media-amazon.com/images/I/51eIj0VXIGL.__AC_SR166,182___.jpg\"/></noscript>   </a> </div>\n    </div>\n\n    <div class=\"apm-brand-story-image-row\">\n      <div class=\"apm-brand-story-image-cell\">\n          <a class=\"a-link-normal apm-brand-story-image-link\" target=\"_blank\" rel=\"noopener noreferrer noopener\" href=\"/dp/B0BBKTVFYK/ref=emc_bcc_2_i\">                               <img alt=\"TSPRO Hands Free Dog Leash Adjustable Walking Running Dog Leash with Control Safety Padded Handle...\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"apm-brand-story-image-img a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/I/41W-ylMpdvL.__AC_SR166,182___.jpg\"><noscript><img alt=\"TSPRO Hands Free Dog Leash Adjustable Walking Running Dog Leash with Control Safety Padded Handle...\" src=\"https://m.media-amazon.com/images/I/41W-ylMpdvL.__AC_SR166,182___.jpg\"/></noscript>   </a> </div>\n      <div class=\"apm-brand-story-image-cell\">\n          <a class=\"a-link-normal apm-brand-story-image-link\" target=\"_blank\" rel=\"noopener noreferrer noopener\" href=\"/dp/B0BPSQFDF9/ref=emc_bcc_2_i\">                               <img alt=\"TSPRO Tactical Dog Vest Harnesses with Handle 1.5 inch Wide Military Grade Strong Padded Thick Do...\" src=\"https://images-na.ssl-images-amazon.com/images/G/01/x-locale/common/grey-pixel.gif\" class=\"apm-brand-story-image-img a-lazy-loaded\" data-src=\"https://m.media-amazon.com/images/I/41ZCuXTya9L.__AC_SR166,182___.jpg\"><noscript><img alt=\"TSPRO Tactical Dog Vest Harnesses with Handle 1.5 inch Wide Military Grade Strong Padded Thick Do...\" src=\"https://m.media-amazon.com/images/I/41ZCuXTya9L.__AC_SR166,182___.jpg\"/></noscript>   </a> </div>\n    </div>\n\n      <div class=\"apm-brand-story-text \">\n                                                <h3> Dog Collar  &amp; leash &amp; harness </h3>    <p class=\"apm-brand-story-stores-link\"> <a class=\"a-link-normal\" target=\"_blank\" rel=\"noopener noreferrer noopener\" href=\"/stores/page/970D0CB8-E546-42DD-BBD9-2A368E1EC548?store_ref=storeRecs_dp_aplus\"> Visit the Store </a> </p>  </div>\n     </div>\n<div style=\"clear:both\"></div>\n   </div>\n </li>    <li class=\"a-carousel-card apm-brand-story-carousel-card-4\" role=\"listitem\">           <div class=\"celwidget aplus-module brand-story-card-4-questions aplus-brand-story-card\" cel_widget_id=\"aplus-brand-story-card-4-questions\">\n            <div class=\"apm-brand-story-card\">\n    <div class=\"apm-brand-story-faq\">\n       <div class=\"apm-brand-story-faq-block\">\n                                                   <h4> Why Choose TSPRO? </h4>                                    <p> TSPRO specialize in providing fashionable and high-quality dog wearing products for large and medium-sized dogs. </p>     <p> If you want a present for your dog, a good idea is to give him or her a TSPRO dog collar. </p>    </div>\n            <div class=\"apm-brand-story-faq-block\">\n                                                   <h4> Are our products of high quality? </h4>                                    <p> *Rugged materials &amp; quality accessories of Premium durability and dirt/water/scratch resistance. </p>     <p> *100% Highly Quality : Your satisfaction is our first priority. </p>       </div>\n            <div class=\"apm-brand-story-faq-block\">\n                                                   <h4> Can I offer my advice? </h4>                                    <p> Let's co-design &amp; Custom product programs to create product that suits different needs and purposes. </p>    </div>\n          </div>\n</div>\n<div style=\"clear:both\"></div>\n   </div>\n </li>   </ol></div></div><div class=\"a-carousel-col a-carousel-right\"><a class=\"a-button a-button-image a-carousel-button a-carousel-goto-nextpage\" tabindex=\"0\" href=\"#\"><span class=\"a-button-inner\"><i class=\"a-icon a-icon-next\"><span class=\"a-icon-alt\">Next page</span></i></span></a></div></div></div> <span class=\"a-end aok-hidden\"></span></div> </div>\n        <div class=\"aplus-brandstory-pagination\">\n             </div>\n    </div>\n <script type=\"text/javascript\">(function(f) {var _np=(window.P._namespace(\"BrandStoryAplusModule\"));if(_np.guardFatal){_np.guardFatal(f)(_np);}else{f(_np);}}(function(P) {\n    P.when('brand-story-carousel').execute(function (init) {\n        init();\n    });\n}));</script>    "
}
```

### Product Review

```json
{
	"id": "R3DTY0V0B9QQS6",
	"type": "review",
	"productAsin": "B072LDFT1C",
	"score": 4,
	"title": "Sizing is weird",
	"url": "https://www.amazon.com/gp/customer-reviews/R3DTY0V0B9QQS6/ref=cm_cr_arp_d_rvw_ttl?ie=UTF8&ASIN=B0725FT5ZW",
	"helpfulCount": "",
	"dateAndLocation": "Reviewed in the United States on November 26, 2023",
	"description": "By all measurements my dog should have been a large but a large was way too big.  Medium fit a lot better but the front neck area is still too loose by just a bit.  With that said if they had a small it would definitely not fit her torso. An optional lower half that is more adjustable would be great.Sizing problems aside it's a really good looking vest. I like the number and spacing of the attachment points as well as the elastic on top. I use it to store my dogs poop tube (available on Amazon) so she can carry her own poop.  It looks well build but as my dog is slightly reactive I'm not going to trust the leash attachment point, that's my dog's problem and not the product though.",
	"isVerified": true,
	"specs": {
		"Size": "L",
		"Color": "Coyote Brown"
	},
	"images": []
}
```


## How to use Amazon Scraper
https://www.youtube.com/watch?v=Aa5SOI5EHNU&ab_channel=epctex

## FAQ
**Is it legal to scrape from Amazon?**
It’s legal to extract public data from Amazon, however, personal information and sensitive data are not. ⚖️

**Can I customize the data extracted by Amazon Scraper?**
Yes, Amazon Scraper allows for customization in the data extraction process. Users can specify what information they need, such as specific product details or review types, making the tool versatile for different use cases. ⚙️

**Can Amazon Scraper extract data from any Amazon region?**
Yes, Amazon Scraper supports multiple Amazon top-level domains (TLDs), enabling users to extract data from various international Amazon websites. 🌍

**Do I need technical skills to use Amazon Scraper?**
Amazon Scraper is designed to be user-friendly, with a straightforward interface that requires minimal technical knowledge. Users can easily input their search criteria to start scraping data. 🛠️

**Is there a limit to the amount of data I can scrape with Amazon Scraper?**
While there is no fixed limit, users can set a maximum number of items to scrape to manage the scope of their data collection. This ensures that users can tailor the scraping process to their specific needs. 📏

## Contact
Please visit us through [epctex.com](https://epctex.com) to see all the products that are available for you. If you are looking for any custom integration or so, please reach out to us through the chat box in [epctex.com](https://epctex.com). In need of support? [devops@epctex.com](mailto:devops@epctex.com) is at your service.
