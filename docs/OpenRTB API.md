## Table of Contents

[Introduction](openrtb-api#Introduction)

- [Why RTB](openrtb-api#section--why-rtb-)
- [Our technology](openrtb-api#section--our-technology-)

[BID REQUEST Specifications](openrtb-api#bid-request-specifications)

- [1. Bid Request Object](openrtb-api#section--1-bid-request-object-)
- [2. Imp Object](openrtb-api#section--2-imp-object-)
- [3. App Object](openrtb-api#section--3-app-object-)
- [4. Device Object](openrtb-api#section--4-device-object-)
- [5. Site Object](openrtb-api#section--5-site-object-)
- [6. User Object](openrtb-api#section--7-user-object-)
- [7. Regs Object](openrtb-api#section--8-regs-object-)

[NATIVE AD: Technical Integration](openrtb-api#native-ad-technical-integration)

- [1. About the Native Ad Format](openrtb-api#section--1-about-the-native-ad-format-)
- [2. Endpoint for Native Request](openrtb-api#section--2-endpoint-for-native-request-)
- [3. Native Request Details](openrtb-api#section--3-native-request-details-)
- [4. Native Request Parameters](openrtb-api#section--4-native-request-parameters-)
- [5. Sample Native Request Body](openrtb-api#section--5-sample-native-request-body-)
- [6. Sample Native Response](openrtb-api#section--6-sample-native-response-)

[BANNER AD: Technical Integration](openrtb-api#banner-ad-technical-integration)

- [1. About the Banner Ad Format](openrtb-api#section--1-about-the-banner-ad-format-)
- [2. Endpoint for Banner Ad Request](openrtb-api#section--2-endpoint-for-banner-ad-request-)
- [3. Banner Request Details](openrtb-api#section--3-banner-request-details-)
- [4. Sample Banner Request Parameters](openrtb-api#section--4-sample-banner-request-parameters-)
- [5. Sample Banner Request Body](openrtb-api#section--5-sample-banner-request-body-)
- [6. Sample Banner Response](openrtb-api#section--6-sample-banner-response-)

[VIDEO AD: Technical Integration](openrtb-api#video-ad-technical-integration)

- [1. About the Video Ad Format](openrtb-api#section--1-about-the-video-ad-format-)
- [2. Endpoint for Video Request](openrtb-api#section--2-endpoint-for-video-request-)
- [3. Video Request Details](openrtb-api#section--3-video-request-details-)
- [4. Sample Video Request Parameters](openrtb-api#section--4-sample-video-request-parameters-)
- [5. Sample Video Request Body](openrtb-api#section--5-sample-video-request-body-)
- [6. Sample Video Response](openrtb-api#section--6-sample-video-response-)
- [7. Sample Device Response](<>)

[SKAdNetwork](openrtb-api#skadnetwork)

[Get Started](openrtb-api#get-started)

## Introduction

## **Why RTB?**

Verve (formerly known as PubNative) introduces its RTB solution in order to deliver mobile ads at scale. By pushing this supply-side specification, we allow publishers to enrich their inventory and to deliver better experiences to their users. Our goal is to increase the programmatic delivery of ads by establishing a common framework on the buy-side, which will facilitate the exchange of diverse ad formats.

## **Our technology**

Verve built its RTB platform in full respect of the “OpenRTB Native Ads API Specification Version 1.1” and “OpenRTB API Specification Version 2.3” defined by the IAB.

## BID REQUEST Specifications

Our bid request parameters are based on [IAB's OpenRTB API Specifications version 2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf).

## **1. Bid Request Object**

The top-level bid request contains a globally unique bid request or auction ID, together with a series of subordinate objects that provide detailed data to potential buyers. Among these  
are the Site and App objects, which describe the type of published media in which the impression(s)  
appear. You will find all of the recommended and required bid request parameters below.  
For definitions of the parameters, please check the _Object: BidRequest_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Definition",
    "h-3": "Status",
    "0-0": "**id**",
    "0-1": "**string**",
    "0-2": "Unique ID of the bid request, provided by the exchange.",
    "0-3": "**required**",
    "1-0": "**imp**",
    "1-1": "**object array**",
    "1-2": "Array of [Imp objects](openrtb-api#section--2-imp-object-) representing the impressions offered. At least 1 Imp object is required.",
    "1-3": "**required**",
    "2-0": "**app**",
    "2-1": "**object**",
    "2-2": "Details via an [App object](openrtb-api#section--3-app-object-) about the publisher’s app (i.e., non-browser applications). Only applicable and recommended for apps.",
    "2-3": "**required**",
    "3-0": "**device**",
    "3-1": "**object**",
    "3-2": "Details via a [Device object]\\(openrtb-api#section- -4-device-object-) about the user’s device to which the impression will be delivered.",
    "3-3": "**required**",
    "4-0": "site",
    "4-1": "object",
    "4-2": "Details via a [Site object](openrtb-api#section--5-site-object-)  about the publisher’s website. Only applicable and recommended for websites.",
    "4-3": "recommended",
    "5-0": "user",
    "5-1": "object",
    "5-2": "Details via a [User object](openrtb-api#section--7-user-object-) about the human user of the device; the advertising audience.",
    "5-3": "recommended",
    "6-0": "test",
    "6-1": "integer; default 0",
    "6-2": "Indicator of test mode in which auctions are not billable, where 0 = live mode, 1 = test mode.",
    "6-3": "recommended",
    "7-0": "at",
    "7-1": "integer, default 2",
    "7-2": "Auction type, where 1 = First Price, 2 = Second Price Plus. Exchange-specific auction types can be defined using values  \ngreater than 500.",
    "7-3": "recommended",
    "8-0": "tmax",
    "8-1": "integer",
    "8-2": "Maximum time in milliseconds to submit a bid to avoid timeout. This value is commonly communicated offline",
    "8-3": "recommended",
    "9-0": "wseat",
    "9-1": "string array",
    "9-2": "Whitelist of buyer seats allowed to bid on this impression. Seat IDs must be communicated between bidders and the exchange a priori. Omission implies no seat restrictions.",
    "9-3": "recommended",
    "10-0": "allimps",
    "10-1": "integer; default 0",
    "10-2": "Flag to indicate if Exchange can verify that the impressions offered represent all of the impressions available in context (e.g., all on the web page, all video spots such as pre/mid/post roll) to support road-blocking. 0 = no or unknown, 1 = yes, the impressions offered represent all that are available.",
    "10-3": "recommended",
    "11-0": "cur",
    "11-1": "string array",
    "11-2": "Array of allowed currencies for bids on this bid request using ISO-4217 alpha codes. Recommended only if the exchange accepts multiple currencies.",
    "11-3": "recommended",
    "12-0": "bcat",
    "12-1": "string array",
    "12-2": "Blocked advertiser categories using the IAB content categories.",
    "12-3": "recommended",
    "13-0": "badv",
    "13-1": "string array",
    "13-2": "Block list of advertisers by their domains (e.g., \"ford.com”).",
    "13-3": "recommended",
    "14-0": "regs",
    "14-1": "object",
    "14-2": "A [Regs object](openrtb-api#section--8-regs-object-) that specifies any industry, legal, or  governmental regulations in force for this request.",
    "14-3": "recommended",
    "15-0": "",
    "15-1": "",
    "15-2": "",
    "15-3": ""
  },
  "cols": 4,
  "rows": 16,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## **2. Imp Object**

For definitions of the parameters, please check the _Object: Imp_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Definition",
    "h-3": "Status",
    "0-0": "**id**",
    "0-1": "**string**",
    "0-2": "A unique identifier for this impression within the  context of the bid request (typically, starts with 1 and increments).",
    "0-3": "**required**",
    "1-0": "**banner**",
    "1-1": "**object**",
    "1-2": "A [Banner object](openrtb-api#section--4-sample-banner-request-parameters-); required if this impression is offered as a banner ad opportunity.",
    "1-3": "**required (If this impression is offered as a banner ad opportunity)**",
    "2-0": "**video**",
    "2-1": "**object**",
    "2-2": "A [Video object](openrtb-api#section--4-sample-video-request-parameters-);  \nrequired if this impression is offered as a video ad opportunity.",
    "2-3": "**required (If this impression is offered as a video ad opportunity)**",
    "3-0": "**native**",
    "3-1": "**object**",
    "3-2": "A [Native object](openrtb-api#section--4-native-request-parameters-); required if this impression is offered as a native ad opportunity.",
    "3-3": "**required (If this impression is offered as a native ad opportunity)**",
    "4-0": "displaymanager",
    "4-1": "string",
    "4-2": "Name of ad mediation partner, SDK technology, or player responsible for rendering ad (typically video or mobile). Used by some ad servers to customize ad code by partner. Recommended for video and/or apps.",
    "4-3": "recommended",
    "5-0": "displaymanagerserv",
    "5-1": "string",
    "5-2": "Version of ad mediation partner, SDK technology, or player  \nresponsible for rendering ad (typically video or mobile). Used  \nby some ad servers to customize ad code by partner.  \nRecommended for video and/or apps.",
    "5-3": "recommended",
    "6-0": "instl",
    "6-1": "integer",
    "6-2": "1 = the ad is interstitial or full screen, 0 = not interstitial.",
    "6-3": "recommended",
    "7-0": "tagid",
    "7-1": "string",
    "7-2": "Identifier for specific ad placement or ad tag that was used to initiate the auction. This can be useful for debugging of any issues, or for optimization by the buyer.",
    "7-3": "recommended",
    "8-0": "bidfloor",
    "8-1": "float; default 0",
    "8-2": "Minimum bid for this impression expressed in CPM.",
    "8-3": "recommended",
    "9-0": "bidfloorcur",
    "9-1": "string; default \"USD\"",
    "9-2": "Currency specified using ISO-4217 alpha codes. This may be different from bid currency returned by bidder if this is allowed by the exchange.",
    "9-3": "recommended",
    "10-0": "secure",
    "10-1": "integer",
    "10-2": "Flag to indicate if the impression requires secure HTTPS URL creative assets and markup, where 0 = non-secure, 1 = secure. If omitted, the secure state is unknown, but non-secure HTTP support can be assumed.",
    "10-3": "recommended",
    "11-0": "iframebuster",
    "11-1": "string array",
    "11-2": "Array of exchange-specific names of supported iframe busters.",
    "11-3": "recommended",
    "12-0": "pmp",
    "12-1": "object",
    "12-2": "A Pmp object (Section 3.2.17) containing any private marketplace deals in effect for this impression.",
    "12-3": "recommended",
    "13-0": "ext",
    "13-1": "object",
    "13-2": "Placeholder for exchange-specific extensions to OpenRTB.",
    "13-3": "recommended",
    "14-0": "rwdd",
    "14-1": "integer; default 0",
    "14-2": "Indicates whether the user receives a reward for viewing the ad  \nad, where 0 = no, 1 = yes.",
    "14-3": "recommended"
  },
  "cols": 4,
  "rows": 15,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## **3. App Object**

For definitions of the parameters, please check the _Object: App_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Definition",
    "h-3": "Status",
    "0-0": "**bundle**",
    "0-1": "**string**",
    "0-2": "Application bundle or package name (e.g., com.foo.mygame);  \nintended to be a unique ID across exchanges.",
    "0-3": "**required**",
    "1-0": "id",
    "1-1": "string",
    "1-2": "Exchange-specific app ID.",
    "1-3": "recommended",
    "2-0": "name",
    "2-1": "string",
    "2-2": "App name (may be aliased at the publisher’s request).",
    "2-3": "recommended",
    "3-0": "domain",
    "3-1": "string",
    "3-2": "Domain of the app (e.g., “mygame.foo.com”).",
    "3-3": "recommended",
    "4-0": "storeurl",
    "4-1": "string",
    "4-2": "App store URL for an installed app; for QAG 1.5 compliance.",
    "4-3": "recommended",
    "5-0": "cat",
    "5-1": "string array",
    "5-2": "Array of IAB content categories of the app.",
    "5-3": "recommended",
    "6-0": "sectioncat",
    "6-1": "string array",
    "6-2": "Array of IAB content categories that describe the current section of the app.",
    "6-3": "recommended",
    "7-0": "pagecat",
    "7-1": "string array",
    "7-2": "Array of IAB content categories that describe the current page or view of the app.",
    "7-3": "recommended",
    "8-0": "ver",
    "8-1": "string",
    "8-2": "Application version.",
    "8-3": "recommended",
    "9-0": "privacypolicy",
    "9-1": "integer",
    "9-2": "Indicates if the app has a privacy policy, where 0 = no, 1 = yes.",
    "9-3": "recommended",
    "10-0": "paid",
    "10-1": "integer",
    "10-2": "0 = app is free, 1 = the app is a paid version.",
    "10-3": "recommended",
    "11-0": "publisher",
    "11-1": "object",
    "11-2": "Details about the Publisher  of the app.",
    "11-3": "recommended",
    "12-0": "content",
    "12-1": "object",
    "12-2": "Details about the Content within the app.",
    "12-3": "recommended",
    "13-0": "keywords",
    "13-1": "string",
    "13-2": "Comma separated list of keywords about the app.",
    "13-3": "recommended",
    "14-0": "ext",
    "14-1": "object",
    "14-2": "Placeholder for exchange-specific extensions to OpenRTB.",
    "14-3": "recommended"
  },
  "cols": 4,
  "rows": 15,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## **4. Device Object**

For definitions of the parameters, please check the _Object: Device_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

| Parameter      | Type       | Definition                                                                                                                                                         | Status       |
| :------------- | :--------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------- | :----------- |
| **ua**         | **string** | Browser user agent string.                                                                                                                                         | **required** |
| **os**         | **string** | Device operating system (e.g., “iOS”).                                                                                                                             | **required** |
| **ip**         | **string** | IPv4 address closest to device.                                                                                                                                    | **required** |
| geo            | object     | Location of the device assumed to be the user’s current location defined by a [Geo object](openrtb-api#section--6-geo-object-).                                    | recommended  |
| dnt            | integer    | Standard “Do Not Track” flag as set in the header by the browser, where 0 = tracking is unrestricted, 1 = do not track.                                            | recommended  |
| lmt            | integer    | “Limit Ad Tracking” signal commercially endorsed (e.g., iOS, Android), where 0 = tracking is unrestricted, 1 = tracking must be limited per commercial guidelines. | recommended  |
| ipv6           | string     | IP address closest to device as IPv6.                                                                                                                              | recommended  |
| devicetype     | integer    | The general type of device.                                                                                                                                        | recommended  |
| make           | string     | Device make (e.g., “Apple”).                                                                                                                                       | recommended  |
| model          | string     | Device model (e.g., “iPhone”).                                                                                                                                     | recommended  |
| osv            | string     | Device operating system version (e.g., “3.1.2”).                                                                                                                   | recommended  |
| js             | integer    | Support for JavaScript, where 0 = no, 1 = yes.                                                                                                                     | recommended  |
| pxratio        | float      | The ratio of physical pixels to device independent pixels.                                                                                                         | recommended  |
| connectiontype | integer    | Network connection type.                                                                                                                                           | recommended  |
| ifa            | string     | ID sanctioned for advertiser use in the clear (i.e., not hashed).                                                                                                  | recommended  |
| didsha1        | string     | Platform device ID (e.g., Android ID); hashed via SHA1.                                                                                                            | recommended  |
| didmd5         | string     | Platform device ID (e.g., Android ID); hashed via MD5.                                                                                                             | recommended  |
| dpidm5         | string     | Hardware device ID (e.g., IMEI); hashed via MD5.                                                                                                                   | recommended  |
| macsha1        | string     | MAC address of the device; hashed via SHA1.                                                                                                                        | recommended  |
| macmd5         | string     | MAC address of the device; hashed via MD5.                                                                                                                         | recommended  |
| ext            | string     | Placeholder for exchange-specific extensions to OpenRTB.                                                                                                           | recommended  |

## Device Ext Object

[block:parameters]
{
  "data": {
    "h-0": "Attribute",
    "h-1": "Type",
    "h-2": "Description",
    "0-0": "inputlanguage",
    "0-1": "string",
    "0-2": "A string array containing the languages setup on the user's device keyboard. (i.e. “en-US, en” )",
    "1-0": "diskspace",
    "1-1": "int",
    "1-2": "An integer value describing the available disk space on the device in megabytes, where i.e. \"18201\" = device has 18201 MB of available disk space.",
    "2-0": "totaldisk",
    "2-1": "int",
    "2-2": "An integer value describing the total disk space on the device in megabytes, where i.e. \"63989\" = 63989 MB of total disk space.",
    "3-0": "ringmute",
    "3-1": "int",
    "3-2": "(Android only) An integer value describing the device sound setting during time of ad request describing if sound is set to ring or mute, where  \n\"0\" = mute and  \n\"1\" = ring.",
    "4-0": "charging",
    "4-1": "int",
    "4-2": "An integer value describing if the device is connected to a charger, where:  \n\"0\" = unplugged and  \n\"1\" = plugged into power outlet",
    "5-0": "headset",
    "5-1": "bool",
    "5-2": "A boolean value indicating if the device is connected to a headset, where:  \n\"1\" = device is connected to any headset and  \n\"0\" = no headset is connected",
    "6-0": "batterylevel",
    "6-1": "int",
    "6-2": "An integer passed describing percent battery remaining on the user's device, segmented into buckets, where  \n100-85% = 8  \n84-70% = 7  \n69-55% = 6  \n54-40% = 5  \n39-25% = 4  \n21-10% = 3  \n9-5% = 2  \n\\< 5% = 1",
    "7-0": "batterysaver",
    "7-1": "bool",
    "7-2": "A boolean value indicating if battery saver (\"Low Power Mode\" on iOS) has been enabled, where  \n\"1\" = battery saver,  \n\"0\" = not enabled",
    "8-0": "darkmode",
    "8-1": "bool",
    "8-2": "A boolean value indicating if dark mode is enabled on the device, where  \n\"1\" = dark mode enabled,  \n\"0\"= not enabled",
    "9-0": "airplane",
    "9-1": "bool",
    "9-2": "A boolean value indicating if airplane mode is enabled, where \"1\" = airplane mode enabled, \"0\" = not enabled",
    "10-0": "dnd",
    "10-1": "bool",
    "10-2": "Android only) A boolean value indicating if “do not disturb” setting is enabled, where  \n\"1\" = do not disturb enabled,  \n\"0\" = not enabled.",
    "11-0": "atts",
    "11-1": "int",
    "11-2": "(iOS 14 + only) An integer passed to represent the app's app tracking authorization status, where  \n  \n0 = not determined  \n1 = restricted  \n2 = denied  \n3 = authorized",
    "12-0": "bluetooth",
    "12-1": "bool",
    "12-2": "A boolean value indicating if the device is connected to bluetooth where  \n\"1\" = connected to bluetooth  \n“0” = not connected to bluetooth"
  },
  "cols": 3,
  "rows": 13,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]


## Device Geo Object

| Attribute | Type    | Description                                                                                                                                                                                                                                                                               |
| :-------- | :------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| lat       | Float   | Latitude from -90.0 to +90.0, where negative is south                                                                                                                                                                                                                                     |
| long      | Float   | Longitude from -180.0 to +180.0, where negative is west                                                                                                                                                                                                                                   |
| type      | Integer | Type - 1 - represents directly passed from device. 2 - Ip derived                                                                                                                                                                                                                         |
| utcoffset | integer | Local time as the number +/- of minutes from UTC                                                                                                                                                                                                                                          |
| accuracy  | Integer | Estimated location accuracy in meters; recommended when lat/lon are specified and derived from a device’s location services (i.e., type = 1). Note that this is the accuracy as reported from the device. Consult OS specific documentation (e.g., Android, iOS) for exact interpretation |
| lastfix   | Integer | The time accuracy of the location. The number of seconds since the location was retrieved. Format is in total number of seconds.                                                                                                                                                          |
| ipservice | Integer | Enrichment provider                                                                                                                                                                                                                                                                       |
| metro     | String  | Zip code of the device                                                                                                                                                                                                                                                                    |
| zip       | string  | ZIP or postal code                                                                                                                                                                                                                                                                        |
| Country   | String  | Country code using ISO-3166-1-alpha-3                                                                                                                                                                                                                                                     |
| Region    | String  | Region code using ISO-3166-2; 2-letter state code if USA                                                                                                                                                                                                                                  |
| City      | String  | City using United Nations Code for Trade & Transport Locations. See Appendix A for a link to the codes                                                                                                                                                                                    |
| ext.isp   | String  | Internet Service Provider name                                                                                                                                                                                                                                                            |
| ext.org   | Strin   | Internet Service Provider name.                                                                                                                                                                                                                                                           |

```json Sample Geo Device Object
"device": {
    "dnt": 2,
    "ua": "Mozilla/5.0 (iPhone; CPU iPhone OS 8_1_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12B440 Safari/600.1.4",
    "ip": "8.8.8.8",
    "geo": {
        "lat": 0,
        "lon": 0,
        "country": "USA",
        "region": "CA",
        "city": "Mountain View",
        "zip": "94040",
        "type": 2, // 1- GPS, 2- IP address
        "utcoffset": 120,
        "accuracy": 400,
        "ipservice": 2,
        "ext": {
        	"isp":"Google",
        	"org":"Google"
        }
    },
    "carrier": "Google",
    "language": "en",
    "make": "Apple",
    "model": "iphone",
    "os": "iOS",
    "osv": "8",
    "connectiontype": 2, // 0 -Unknown, 1- Ethernet, 2 - WIFI, 3 -Cellular Network – Unknown Generation
    "devicetype": 1, // 1 - Mobile/Tablet
    "ifa": "1E2DFA89-47FD-9941-DF1FC4E6484C",
    "ext": {
        "airplane": 0,
        "batterylevel": 8, // 100-85% = 8 , 84-70% = 7, 69-55% = 6, 54-40% = 5, 39-25% = 4, 21-10% = 3, 9-5% = 2, < 5% = 1  
        "batterysaver": 1,
        "bluetooth": 1,
        "charging": 0,
        "darkmode": 0,
        "dnd": 0, // 0- Do Not Disturb disabled, 1- Do Not Disturb enabled
        "headset": 0, //0- No headset connected, 1- Headset connected
        "inputLanguage": [
            "en"
        ],
        "ringmute": 0, // 0- Mute, 1- Ring
        "diskspace": 1821, //MB of data
        "totaldisk": 128000 //MB of data
    }
},

```

## **5. Site Object**

For definitions of the parameters, please check the _Object: Site_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

| Parameter     | Type         | Definition                                                                          | Status      |
| :------------ | :----------- | :---------------------------------------------------------------------------------- | :---------- |
| id            | string       | Exchange-specific site ID.                                                          | recommended |
| name          | string       | Site name (may be aliased at the publisher’s request).                              | recommended |
| domain        | string       | domain string Domain of the site (e.g., “mysite.foo.com”).                          | recommended |
| cat           | string array | Array of IAB content categories of the site.                                        | recommended |
| sectioncat    | string array | Array of IAB content categories that describe the current section of the site.      | recommended |
| pagecat       | string array | Array of IAB content categories that describe the current page or view of the site. | recommended |
| page          | string       | URL of the page where the impression will be shown.                                 | recommended |
| ref           | string       | Referrer URL that caused navigation to the current page.                            | recommended |
| search        | string       | Search string that caused navigation to the current page.                           | recommended |
| mobile        | integer      | Mobile-optimized signal, where 0 = no, 1 = yes.                                     | recommended |
| privacypolicy | integer      | Indicates if the site has a privacy policy, where 0 = no, 1 = yes.                  | recommended |
| publisher     | object       | Details about the Publisher  of the site.                                           | recommended |
| content       | object       | Details about the Content within the site.                                          | recommended |
| keywords      | string       | Comma separated list of keywords about the site.                                    | recommended |
| ext           | object       | Placeholder for exchange-specific extensions to OpenRTB.                            | recommended |

## **6. User Object**

For definitions of the parameters, please check the _Object: User_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

| Parameter  | Type         | Definition                                                                                                                                                                                                                    | Status      |
| :--------- | :----------- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------- |
| id         | string       | Exchange-specific ID for the user. At least one of id or buyerid is recommended.                                                                                                                                              | recommended |
| buyerid    | string       | Buyer-specific ID for the user as mapped by the exchange for the buyer. At least one of buyerid or id is recommended.                                                                                                         | recommended |
| yob        | integer      | Year of birth as a 4-digit integer.                                                                                                                                                                                           | recommended |
| gender     | string       | Gender, where “M” = male, “F” = female, “O” = known to be other (i.e., omitted is unknown).                                                                                                                                   | recommended |
| keywords   | string       | Comma separated list of keywords, interests, or intent.                                                                                                                                                                       | recommended |
| customdata | string       | Optional feature to pass bidder data that was set in the exchange’s cookie. The string must be in base85 cookie safe characters and be in any format. Proper JSON encoding must be used to include “escaped” quotation marks. | recommended |
| geo        | object       | Location of the user’s home base defined by a [Geo object](openrtb-api#section--6-geo-object-). This is not necessarily their current location.                                                                               | recommended |
| data       | object array | Additional user data. Each Data object represents a different data source.                                                                                                                                                    | recommended |
| ext        | object       | Placeholder for exchange-specific extensions to OpenRTB.                                                                                                                                                                      | recommended |

## **7. Regs Object**

For definitions of the parameters, please check the _Object: Regs_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf))

| Parameter | Type    | Definition                                                                                                             | Status      |
| :-------- | :------ | :--------------------------------------------------------------------------------------------------------------------- | :---------- |
| coppa     | integer | Flag indicating if this request is subject to the COPPA regulations established by the USA FTC, where 0 = no, 1 = yes. | recommended |
| ext       | object  | Placeholder for exchange-specific extensions to OpenRTB.                                                               | recommended |

## NATIVE AD: Technical Integration

## **1. About the Native Ad Format**

We support native ads using the following components. Please keep in mind that the components must be specified in the ad request.

| Component      | Description                              | Standard case            |
| :------------- | :--------------------------------------- | :----------------------- |
| Main Image     | Large image preview for the ad           | Usually 1200x627px image |
| Icon Image     | Small icon for the ad                    | Usually 80x80px image    |
| Title          | Headline or title for the ad             | Text                     |
| Text           | Open text field describing the ad        | Text                     |
| Call to Action | Text field for the call to action button | Text                     |
| Star Rating    | For app installs, the app store rating   | Rating on scale of 0~5   |

## **2. Endpoint for Native Request**

```http
https://dsp.pubnative.net/bid/v1/request?apptoken=<APP-TOKEN>&zoneid=<YOUR-ZONE-ID>
```

- PubNative uses a latency-based load balancer-- the same endpoint works globally, regardless of location.
- <APP-TOKEN>: can be obtained from PubNative publisher dashboard. Please consult with account manager for this.
- <YOUR-ZONE-ID>: use default as 1

## **3. Native Request Details**

- Request Method should be POST
- Ensure that the bid request body is sent along with the endpoint.
- Set headers in the request to the following:

```text Header
x-openrtb-version: 2.3
Content-Type:application/json
Accept-Charset:utf-8
```

## **4. Native Request Parameters**

If you are not sure what parameter and values to pass, please check the table below. For the definition of each parameter, please check the _Object: Native_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf)).

| Parameter   | Type          | Definition                                                                                                                   | Status       |
| :---------- | :------------ | :--------------------------------------------------------------------------------------------------------------------------- | :----------- |
| **request** | **string**    | Request payload complying with the Native Ad Specification.                                                                  | **required** |
| ver         | string        | Version of the Native Ad Specification to which request complies; highly recommended for efficient parsing.                  | recommended  |
| api         | integer array | List of supported API frameworks for this impression. If an API is not explicitly listed, it is assumed not to be supported. | recommended  |
| battr       | integer array | Blocked creative attributes.                                                                                                 | recommended  |
| ext         | object        | Placeholder for exchange-specific extensions to OpenRTB.                                                                     | recommended  |

## **5. Sample Native Request Body**

```json App
{
    "id": "30-54e260ae-7456-48de-809c-e983a32e940b",
    "tmax": 1500,
    "cur": [
        "USD"
    ],
    "imp": [
        {
            "id": "a672c7f1-f982-461e-8a6b-35de4acdf763",
            "instl": 0,
            "secure": 0,
            "native": {
                "request": "{\"native\":{\"ver\":\"1\",\"layout\":6,\"assets\":[{\"id\":0,\"required\":0,\"title\":{\"len\":100}},{\"id\":2,\"required\":1,\"img\":{\"type\":1,\"wmin\":50,\"hmin\":50}},{\"id\":3,\"required\":0,\"data\":{\"type\":2,\"len\":90}},{\"id\":4,\"required\":0,\"data\":{\"type\":3}},{\"id\":5,\" required\":0,\"data\":{\"type\":12,\"len\":15}},{\"id\":1,\"required\":0,\"img\":{\"type\":3,\"wmin\":300,\"hmin\":250}}]}}"
            },
            "rwdd": 0,
            "bidfloor": 0.01
        }
    ],
    "device": {
        "dnt": 2,
        "ua": "Mozilla/5.0 (iPhone; CPU iPhone OS 8_1_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12B440 Safari/600.1.4",
        "ip": "8.8.8.8",
        "geo": {
            "lat": 0,
            "lon": 0,
            "country": "USA",
            "region": "CA",
            "city": "Mountain View",
            "zip": "94040",
            "type": 2
        },
        "carrier": "Google",
        "language": "en",
        "make": "Apple",
        "model": "iphone",
        "os": "iOS",
        "osv": "8",
        "connectiontype": 2,
        "devicetype": 1,
        "ifa": "1E2DFA89-47FD-9941-DF1FC4E6484C",
        "ext": {
            "airplane": 0,
            "batterylevel": 8,
            "batterysaver": 1,
            "bluetooth": 1,
            "charging": 0,
            "darkmode": 0,
            "dnd": 0,
            "headset": 0,
            "inputLanguage": [
                "en"
            ],
            "ringmute": 0,
            "diskspace": 1821,
            "totaldisk": 128000
        },
        "at": 2,
        "bcat": [
            "IAB24",
            "IAB25",
            "IAB26"
        ],
        "user": {
            "id": "098a1c70-94db-409d-8c8e-10983e689518"
        },
        "app": {
            "id": "1008118",
            "name": "Test_Android",
            "bundle": "com.android.test",
            "cat": [
                "IAB2-1",
                "IAB2-2"
            ],
            "storeurl": "https://play.google.com/store/apps/details?id=com.android.test",
            "keywords": "test, android",
            "privacypolicy": 1,
            "publisher": {
                "id": "pub12345",
                "name": "Publisher A"
            }
        }
    }
```
```json Web
{
  "id": "30-54e260ae-7456-48de-809c-e983a32e940b",
  "tmax": 1500,
  "cur": [
    "USD"
  ],
  "imp": [
    {
      "id": "a672c7f1-f982-461e-8a6b-35de4acdf763",
      "instl": 0,
      "secure": 0,
      "native": {
        "request": "{\"native\":{\"ver\":\"1\",\"layout\":6,\"assets\":[{\"id\":0,\"required\":0,\"title\":{\"len\":100}},{\"id\":2,\"required\":1,\"img\":{\"type\":1,\"wmin\":50,\"hmin\":50}},{\"id\":3,\"required\":0,\"data\":{\"type\":2,\"len\":90}},{\"id\":4,\"required\":0,\"data\":{\"type\":3}},{\"id\":5,\" required\":0,\"data\":{\"type\":12,\"len\":15}},{\"id\":1,\"required\":0,\"img\":{\"type\":3,\"wmin\":300,\"hmin\":250}}]}}"
      },
      "bidfloor": 0.01
    }
  ],
  "device": {
    "dnt": 0,
    "devicetype": 1,
    "geo": {
      "country": "USA",
      "type": 2,
      "lat": 37.751,
      "lon": -97.822
    },
    "connectiontype": 6,
    "language": "en",
    "model": "Nexus 5X",
    "make": "LGE",
    "carrier": "311-480",
    "didsha1": "e2660d7edf9f7ea18a301d5b913b5e633561d1e2",
    "ifa": "69144c0f-1fb5-4201-8951-5a64be39e134",
    "os": "android",
    "osv": "7.1.1",
    "ua": "Dalvik/2.1.0 (Linux; U; Android 7.1.1; Nexus 5X Build/N4F26O)",
    "ip": "174.204.16.28"
  },
  "at": 2,
  "bcat": [
    "IAB24",
    "IAB25",
    "IAB26"
  ],
  "user": {
    "id": "098a1c70-94db-409d-8c8e-10983e689518"
  },
  "site": {
    "id": "1345135123",
    "name": "Site ABCD",
    "domain": "siteabcd.com",
    "cat": [
      "IAB2-1",
      "IAB2-2"
    ],
    "page": "http://siteabcd.com/page.htm",
    "ref": "http://referringsite.com/referringpage.htm",
    "privacypolicy": 1,
    "publisher": {
      "id": "pub12345",
      "name": "Publisher A"
    }
  }
}
```

## **6. Sample Native Response**

```json
{
    "id": "30-54e260ae-7456-48de-809c-e983a32e940b",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "dfa946e82b63472984f6454567279060",
                    "impid": "a672c7f1-f982-461e-8a6b-35de4acdf763",
                    "price": 0.01,
                    "adid": "test_campaign",
                    "nurl": "http://got.pubnative.net/dspv1/winnotice?ap=${AUCTION_PRICE}&t=yxXyP7cxSbGUWd_HEgzcLCYrzfUnnHkCWkOzV5sOK-RgUHk1_IUtayyP-HK20Q5TQ8jNM1QNB7nszMaJcbOSRfCBsQ",
                    "adm": "{\"native\":{\"assets\":[{\"id\":4,\"data\":{\"label\":\"rating\",\"value\":\"4.50\"}},{\"id\":5,\"data\":{\"label\":\"cta\",\"value\":\"Test me\"}},{\"id\":1,\"img\":{\"url\":\"http://cdn.pubnative.net/assets/mock_main_image.jpg\",\"w\":300,\"h\":250}},{\"id\":0,\"title\":{\"text\":\"PubNative Content Info\"}},{\"id\":2,\"required\":1,\"img\":{\"url\":\"http://cdn.pubnative.net/assets/mock_icon.jpg\",\"w\":50,\"h\":50}},{\"id\":3,\"data\":{\"label\":\"description\",\"value\":\"Pubnative Test Ad\"}}],\"link\":{\"url\":\"http://got.pubnative.net/click/rtb?aid=1008118&t=cD2xSi4VtfNdWk0_gVrQCOhJxwdrTFZXe9VKQYhA2YUBcRZPEWsJOt4ilYasAKbyuKTruh_v4lJNr7zUc9W1u8gev2eaaMHdGgsuiwQtbFxbyoaAVNEUJFpx0E_Hdvmpx7qgxkQKKNekewZwJApED6F7NalLG4LLYI4Z031WOfRT7oi7Nfkun-7jdE1L03QppuY6aruKsdsG-aexh4lqFnFGZX0URfG_Ftai7ua6fkDnr8-yiXd-yMXhSQjtfmFbNLyQSMPX_azTpcIT1muZrmPvJ4_S_Q_gY8KUf5J1fidnfS1jN3LOeW84GxCBnpjnzSRurVoS-wSzygvkt4LU15JTWHTWVEaVEFxB1W-vK01UskrQn-1hImd8Gtp6gy39ISYlhWkbTePjQrbcp54AjT9HTR6B4NWviYbG9fEBmcDpubEnGiBIztOYa_hmOtw1mVxszCa4FgaC2M5jwltbx1iuByfcGVgIiQxAkltWvwDpLwIAMJ8CzOXOFSY5fI0dKnFygDHimM7vMr7DcGZODWWnb-c6F6kaGelfLH_eoSc2tVEnbVVpB3mvs6mOZIE9FUms6y2Epc5MQW5IJdOEntRZryYNQFUJImxKC9_BVAdx2_V_8-93kc9TZkWWoZRPhoxhIA\",\"clicktrackers\":[\"http://mock-dsp.pubnative.net/tracker/clk?app_id=1008118&beacon=1&p=${AUCTION_PRICE}\",\"http://mock-dsp.pubnative.net/tracker/clk?app_id=1008118&beacon=2&p=${AUCTION_PRICE}\"]},\"imptrackers\":[\"http://got.pubnative.net/rtb/beacon?t=WiNGlVZWd1t8gxUdC3ls2XgFJ4TyNoXEamlxzu91qGjifY8KgCZJeaxcUGO51h5Gt6VZyxh8nySQG1VXFoywXwII- -ILXJhWsfp_zx671xBw1ScTwvwM3gkLlTSqRKYZBYCmoPFyUGng&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=1x6SLfSJJvo7J7Dv0FppBNrTBsSacqRKY_cE53bY3FAsl1XeACKaIwQXqeDn4Z6etV6PKOOVw3jz0tUNbW_fnh8s9Ng7OaKRnZSNrwgVEQ3oNZNwEhC_sYHAxbh4ogxAhU_4ntr_JYF53CuegNVYDwE&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=nhiwXs2HODx6mYKtA13pGIUJ7fb7Oq7hy4cLUVmGeTBUIgMSkausUe9sdZu1d-F-BEH6LiS3yOBvNOGgD3T0FpPEU3ytfwdjXP3cVKMYJMP3kyYiFG7ON6ys0ff-jCXZ0tE3_1Sx0PeDscHotcwbkCs&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=SucIlpiKbu1CTkNjL6ED63xWY-PMR79WINYBQ1E2pUS5T-BtSMM5Y1kPtS4qfljeH536uGl5hsVgD9fHwpPRfAyih4GZCZCmtYwl2YcFKVX2ZbEj_2zjZJw6-nu71GyRTJwZ1HRtXwn9WpQ-RnRjf0I&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=29jxnKwqwMhz-57j9y1RlkWSVqk3y-E7LFDUPJl02TqvEVP5S6xovuVcFBC4GLvOPqLoA6AhwuX34s-w3u-s5_DGvA7rxCL6lO_h1Guu593pIrQAu6jWgb5O6jZpK-Ouf6BKHds0RLAxiP5DHymUa_U&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=6PsrSiuXp1Hly-BHjzlrz6DJOADMcw27k4JqhSbnHPVLKHCxhxUnnfKV6ZsJUlYk-qUYwsUHBGxDa6Q8FrE-wpd1sOuuuQyxpHJZ8McJa0h4i0koXkMp6zxfIv4peCr8fIlpnmkvLG_Dfzi8ZvCHeZc&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=ImmP3n_EwTQCjK0dyw-E_wrxlbMTwUXbupO2w_pWo1B5HGetFH11yxjaJx6DAehfPRl7X0iXa7Em4CGRi6IT43vVere1CVEsv-vWC3nqNk10495KYVxMeTqF7X66Cs-wh6uQr8bJ4ERAN57aV0PKhm4&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=uSIMS1wS-Of4KC8k6mjAzfm1x6Ug31M1HXABxPFm_ypuPPvIi6Y5khwb3z6O7OFd1Uu3HExuuxjrBYlnd6KLjg_WrO6-qnX0Nc2OIGKiQ4ka7xvZfvsbT-CN0hzAJ5UPBnfA_ImBLTWYXL4S0WFdVZ0&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=o1XOQYNBrKTI_aQvuHjBZnI8jCkr59T5SW6X1f9fl1eUx6JmcDBBniwyDNBUkdptKqmlvcRqF5oTZE2WrkgQIXKBvwyU-RnVO0HucN7dGU3QKAcoyOcZMJDIpoxSu79QSKCJLIWaAM94N1NqbxsEKHA&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=ibTKopug071TDzPZwSspeOdWqA6RU3NMjB2-jm8gdpjTJkFzh36c46e8jncCotz3NJG7ZmUQbiJKfKzC6eDxPKsjNQ_lvv_ius4FSgraE3PvTdeigRYYD5TzRemX0JxZjZkh2VkK3zyTi6kXAMmW7qg&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=fOzwTvtgf6exzog8i-6ZTKgeLRDMcT_wmWpadJmAaARQzFXvddjEv0do5Im6ZjcAb968ca89O9Re4a4Fin6c3-53azxNndQkceJJ_oxmOzMirNawyQn_2zAvcbrm2lc3FIQq0NHDr-SdQoSMmp_I00xt&p=${AUCTION_PRICE}\",\"http://got.pubnative.net/rtb/beacon?t=TRgZZa2qAjJyiYM0B9r4InX6Dpm9X0TlYJQueTy0v5OyYZ8KRzZzY12j1G3QaFsd7DrRZDBy3T8P9kD-wpzPQx5NWOtaNi8hJAlm4budhF1nJBJ8QAbTbSESCkuU7MkDeAQlr4uzbmNk9VSKO0MOLbsaUdIFyGS2k9QyfqFRc3DWfJN_HK2owtu_34l_B__LNlBnI5198IzcBGptCVZwkhR46PWY7SN1SjtaLUAR1Nb6yes4DuXu3nv9OmvNMYGk6LXdA4Tjne7Hkg3FD_-pyuMNyA4CU54JQiSWkW3vtJvIHzNPDuzzhUlwrvMVQB9etXQPKnIsRlIoehiZ03BPRo5pCWsL5aLCjworyAE4QWEJHGZAJT3Iycp5Mxdpar2aJdLzxTGY93gDZw9q6CUIf5911UP8cjpR7pvprsHkDUz-iJv91yZEdGffqeIZjA2w3fg-Z76enbtophEmlfcudpQTZXyflmbIaikdhQAm2GANstvqcjunbKrL17FQiQ7sXDsepLoqztJPqRNzVbKUFVA23SZjLzJ7F246uQ8ATU0Lzx1Es9eeXJ80VaCrMatScH-g09SrMf8xfPMpKnBrx2QgIcTPeU5Mm_2_zkDShLkcy8EzFDfZe8I3wZ34yRhFaz1pgPc_aAmgIXJ1wRSqv9HHgxuuyfskbx27VJ-gvD9CKlpplRuNERO48s-xFfUN20KlLpQEVtc2VchE57EYpcOXvrYwRxDq0PpoRYCJt2YkoPCx91P-aRy8TnSOO8RXQJTrhNkT_fWgCZL-e6nihvtkmN-S7rSERKgR4eS8fSLSLWwow8Dp-lMWcckDWoKH5Kdy5Ky5n59Pwggz_cGBKGyQCSzoPAY6tc_objgDNwT2JwwU1m06s6kotvVsn08Qp- -nRlp9u8qj7sg_J1LSjdPFxtSUXf11PvdpLycDM_84-30SV5kqBOjC28L9E4QYsXXWBB_pcrF6ybkW8HSIYiIcWnz-QiVMOUBnTVcdWq-FbHZd4RGswbCyG65mBXPL_EAJljSd3wl7psET-4KGcs-Pj68_oIcpYjD9XzoBGyQioKaz9wyXOsJiS-xbeuEQ-j195_6pPKm3_94j4ZkX80x-1cfrVEkpXCNfW_EXEX9hER3EuL87lvLW0Ii-Ycw3pa50SiOFM4Z3Ye9zzmiJ2mjILq_lAqL0KqcoUE3bzrjHc_ES_6oiPEdD1lgulkVB3iFZnLQhF4t6jUKFbaCcgYixtehps-YnZSs2YXbmZofRGlza0N5u5AW-UbOf-DPR-4luoR917RHk3YNVTdgqk1gCamgudqhI&p=${AUCTION_PRICE}\"]}}",
                    "adomain": [
                        "pubnative.net"
                    ],
                    "iurl": "http://got.pubnative.net/rtb/beacon?t=HH1LxYlb8NXCLx_kb5fPzSWGJJtDDV48jm6AuR6VIXXCTI2qjB6u7XADoev1LTQSSRWm8YiNUhLPUD3x2pbTZN4VI1su0efy4HsZhf71njM-vtBTf_eNj_xQZamn0Z_vrV4yXk6syg2E&p=${AUCTION_PRICE}",
                    "cid": "test_campaign",
                    "crid": "test_creative",
                    "attr": [
                        4
                    ]
                }
            ]
        }
    ],
    "cur": "USD"
}
```

## BANNER AD: Technical Integration

## **1. About the Banner Ad Format**

We currently support standard format ads (a.k.a "display") using any of the following ad sizes. Please note that ad sizes other than those listed here are not supported. Please keep in mind that these components must be specified in the ad request. 

- 160 x 600
- 250 x 250
- 300 x 50
- 300 x 250
- 300 x 600
- 320 x 50
- 320 x 100
- 320 x 480
- 480 x 320
- 728 x 90
- 768 x 1024
- 1024 x 768

## **2. Endpoint for Banner Ad Request**

```http
https://dsp.pubnative.net/bid/v1/request?apptoken=<APP-TOKEN>&zoneid=<YOUR-ZONE-ID>
```

- PubNative uses a latency-based load balancer-- the same endpoint works globally, regardless of location.
- <APP-TOKEN>: can be obtained from PubNative publisher dashboard. Please consult with account manager for this.
- <YOUR-ZONE-ID>: use default as 1

## **3. Banner Request Details**

- Request Method should be POST
- Ensure that the bid request is in the body of the request
- Set headers in the request to the following:

```text Header
x-openrtb-version: 2.3
Content-Type:application/json
Accept-Charset:utf-8
```

## **4. Sample Banner Request Parameters**

If you are not sure what parameter and values to pass, please check the table below. For the definition of each parameter, please check the _Object: Banner_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf)).

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Definition",
    "h-3": "Status",
    "0-0": "**w**",
    "0-1": "**integer**",
    "0-2": "Width of the impression in pixels. If neither wmin nor wmax are specified, this value is an exact width requirement. Otherwise it is a preferred width.",
    "0-3": "**required**",
    "1-0": "**h**",
    "1-1": "**integer**",
    "1-2": "Height of the impression in pixels. If neither hmin nor hmax are specified, this value is an exact height requirement. Otherwise it is a preferred height.",
    "1-3": "**required**",
    "2-0": "wmax",
    "2-1": "integer",
    "2-2": "Maximum width of the impression in pixels. If included along with a w value then w should be interpreted as a recommended or preferred width.",
    "2-3": "recommended",
    "3-0": "hmax",
    "3-1": "integer",
    "3-2": "Maximum height of the impression in pixels. If included along with an h value then h should be interpreted as a recommended or preferred height.",
    "3-3": "recommended",
    "4-0": "wmin",
    "4-1": "integer",
    "4-2": "Minimum width of the impression in pixels. If included along with a w value then w should be interpreted as a recommended or preferred width.",
    "4-3": "recommended",
    "5-0": "hmin",
    "5-1": "integer",
    "5-2": "Minimum height of the impression in pixels. If included along with an h value then h should be interpreted as a recommended or preferred height.",
    "5-3": "recommended",
    "6-0": "id",
    "6-1": "string",
    "6-2": "Unique identifier for this banner object. Recommended when  \nBanner objects are used with a [Video object](openrtb-api#section--4-sample-video-request-parameters-) to  \nrepresent an array of companion ads. Values usually start at 1 and increase with each object; should be unique within an impression.",
    "6-3": "recommended",
    "7-0": "btype",
    "7-1": "integer array",
    "7-2": "Blocked banner ad types.",
    "7-3": "recommended",
    "8-0": "battr",
    "8-1": "integer array",
    "8-2": "Blocked creative attributes.",
    "8-3": "recommended",
    "9-0": "pos",
    "9-1": "integer",
    "9-2": "Ad position on screen.",
    "9-3": "recommended",
    "10-0": "mimes",
    "10-1": "string array",
    "10-2": "Content MIME types supported. Popular MIME types may include “application/x-shockwave-flash”, “image/jpg”, and “image/gif”.",
    "10-3": "recommended",
    "11-0": "topframe",
    "11-1": "integer",
    "11-2": "Indicates if the banner is in the top frame as opposed to an iframe, where 0 = no, 1 = yes.",
    "11-3": "recommended",
    "12-0": "expdir",
    "12-1": "integer array",
    "12-2": "Directions in which the banner may expand.",
    "12-3": "recommended",
    "13-0": "api",
    "13-1": "integer array",
    "13-2": "List of supported API frameworks for this impression. Refer to List 5.6 in [IAB's v2.3 specifications](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf). If an API is not explicitly listed, it is assumed not to be supported.",
    "13-3": "recommended",
    "14-0": "ext",
    "14-1": "object",
    "14-2": "Placeholder for exchange-specific extensions to OpenRTB.",
    "14-3": "recommended"
  },
  "cols": 4,
  "rows": 15,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


## **5. Sample Banner Request Body**

```json App
{
    "id": "92d6421e44a44dff9f05b29be0ca5bef",
    "imp": [
        {
            "id": "94628ee5-fe99-436d-94b5-f3270ad06529",
            "banner": {
                "w": 300,
                "h": 250
            },
            "tagid": "1",
            "bidfloor": 0.01,
            "bidfloorcur": "USD",
            "secure": 1
        }
    ],
    "app": {
        "id": "1008118",
        "name": "Test_Android",
        "bundle": "com.android.test",
        "cat": [
            "IAB2-1",
            "IAB2-2"
        ],
        "storeurl": "https://play.google.com/store/apps/details?id=com.android.test",
        "keywords": "test, android",
        "privacypolicy": 1,
        "publisher": {
            "id": "pub12345",
            "name": "Publisher A"
        }
    },
    "device": {
        "ua": "Dalvik/2.1.0 (Linux; U; Android 6.0; MotoG3 Build/MPI24.65-25)",
        "ip": "107.219.186.28",
        "geo": {
            "lat": 33.9775,
            "lon": -118.2133,
            "country": "USA",
            "region": "CA",
            "city": "los angeles",
            "zip": "90001",
            "type": 1
        },
        "carrier": "att internet services",
        "language": "en",
        "model": "Moto G3",
        "os": "Android",
        "osv": "6.0",
        "connectiontype": 2,
        "devicetype": 1,
        "ifa": "03F9F0E4-937D-4F85-9275-F530E0107B2F",
        "ext": {
            "airplane": 0,
            "batterylevel": 8,
            "batterysaver": 1,
            "bluetooth": 1,
            "charging": 0,
            "darkmode": 0,
            "dnd": 0,
            "headset": 0,
            "inputLanguage": [
                "en"
            ],
            "ringmute": 0,
            "diskspace": 1821,
            "totaldisk": 128000
        }
    },
    "user": {
        "id": "50cf7979-18a7-51dd-9645-091009ad842f"
    },
    "at": 2,
    "tmax": 1500,
    "allimps": 0,
    "cur": [
        "USD"
    ],
    "bcat": [
        "IAB24",
        "IAB25",
        "IAB26"
    ]
}
```
```json Web
{
  "id": "92d6421e44a44dff9f05b29be0ca5bef",
  "imp": [
    {
      "id": "94628ee5-fe99-436d-94b5-f3270ad06529",
      "banner": {
        "w": 300,
        "h": 250
      },
      "tagid": "1",
      "bidfloor": 0.01,
      "bidfloorcur": "USD"
    }
  ],
  "site": {
    "id": "1345135123",
    "name": "Site ABCD",
    "domain": "siteabcd.com.com",
    "cat": [
      "IAB2-1",
      "IAB2-2"
    ],
    "page": "http://siteabcd.com/page.htm",
    "ref": "http://referringsite.com/referringpage.htm",
    "privacypolicy": 1,
    "publisher": {
      "id": "pub12345",
      "name": "Publisher A"
    }
  },
  "device": {
    "ua": "Dalvik/2.1.0 (Linux; U; Android 6.0; MotoG3 Build/MPI24.65-25)",
    "ip": "107.219.186.28",
    "geo": {
      "lat": 33.9775,
      "lon": -118.2133,
      "country": "USA",
      "region": "CA",
      "city": "los angeles",
      "zip": "90001",
      "type": 1
    },
    "carrier": "att internet services",
    "language": "en",
    "model": "Moto G3",
    "os": "Android",
    "osv": "6.0",
    "connectiontype": 2,
    "devicetype": 1,
    "ifa": "03F9F0E4-937D-4F85-9275-F530E0107B2F"
  },
  "user": {
    "id": "50cf7979-18a7-51dd-9645-091009ad842f"
  },
  "at": 2,
  "tmax": 1500,
  "allimps": 0,
  "cur": [
    "USD"
  ],
  "bcat": [
    "IAB24",
    "IAB25",
    "IAB26"
  ]
}
```

## **6. Sample Banner Response**

```json
{
    "id": "92d6421e44a44dff9f05b29be0ca5bef",
    "seatbid": [
        {
            "bid": [
                {
                    "id": "9cafcb3224fb45839f509abcca974f5c",
                    "impid": "94628ee5-fe99-436d-94b5-f3270ad06529",
                    "price": 0.01,
                    "adid": "test_campaign",
                    "nurl": "https://got.pubnative.net/dspv1/winnotice?ap=${AUCTION_PRICE}&t=8m0OJBZ7871n3RGbrC6jz8mmgocK3okt1DBd_36kZURw8Vf56tf2wDF-Nd7e4i1XnxggaauMDjNEst1xmIrGW-JitQ",
                    "adm": "<a href=\"http://ads.com/click/112770_1386565997\"><img src=\"https://cdn.pubnative.net/widget/v3/assets/300x250.jpg\" width=\"300\" height=\"250\" border=\"0\" alt=\"Advertisement\" /></a><img src=\"http://mock-dsp.pubnative.net/tracker/nurl?app_id=1008118&p=${AUCTION_PRICE}\" style=\"display:none\"/><img src=\"https://got.pubnative.net/impression?aid=1008118&t=QduxwF1RKZT6blfGfU2pjf5vOxe3GWrj9k9Fy8xHWoclDkRFCCqNXV-HcDU74JlYzXikknQ5ndfxRfkLTXrlUIpNLZTtR5sJW_ynhlClj9yVphyIxT-E21TVNjyEYPdjDfpx-ruNp7_xkN8zkGCfq6eqOoZmASdD7ZxUNeL52IsWEhrkRxOIGpwuiXSxI-M7taWBMF3eEB6ZMvW7Sh2rawLmjL1i8tCd-62MVdY4Z2wIQr7CkD6Nm7UDnUs4bKGNrVn1Y7wwnpl9iEo5UGuqCstkuMugwxwxT__qtdrnIO13GkzAR4qpKVfaaK15xJjJn9CRAbx88jsWAYLwpcAXOcFztVOLFbEc-9nJryuMz32DlHd_ghHCHTRikA_olUFoC9gpnlkEp16a4X5OgbOuGtg5ZOEOjJ22BHDKw9jbdjy_eQY-ClBwFUFSolO6hl8F-AHkw3S3mnM-RC1E89KdX9I19Esdme7QIJmhcnQS5qZYJWiLTiwc-rzpb-QXxlG0SK0WT1iqQBO8JYjD8CYgzlvsIsDCa5_BuUXtV8__8_zpveVt0jgYQhwDrl4vWI4aTmMGi8PyDemEBhPufmsra6jrKwZ9ZOSmxsBppJk3YJgJE4uSwWiBw91GSxgHj8kUGaOREqsC9KGLm9ABcqtm-ImoCYas1ZeiyilfInrxUTqBStqIDbgqbROoTW8GhdySNX2OE7nTEDQ1hqkSVqLuJVM0i4-Iu7BEzOBa8pIaHSPKrhHlzVkdbWQdcDqI7O1Y16aK6rrenRsC5-eWmCPAsCuTQ7-_PGUMrFYqZFKHowPzd-Mwnil_Ne16&ap=${AUCTION_PRICE}&px=1\" style=\"display:none\"/>",
                    "adomain": [
                        "pubnative.net"
                    ],
                    "iurl": "https://got.pubnative.net/rtb/beacon?t=q8JQ4OLM0au1mRj81xoNIg6cYepOvPKYSoF1PBC1Xhlxfdb7UqNeHKEqdz54MIM4-NJC6KbcbcQXYILR1H9mTAu07JwrdH7v0RFoxv9XKXpdwDAaRVaMFvQV5n_5uLmFR-6_-THn-ZOU&p=${AUCTION_PRICE}",
                    "cid": "test_campaign",
                    "crid": "test_creative",
                    "attr": [
                        4
                    ]
                }
            ]
        }
    ],
    "cur": "USD"
}
```

## VIDEO AD: Technical Integration

## **1. About the Video Ad Format**

We currently support video ads, including but not limited to the following ad sizes. Please keep in mind that these components must be specified in the ad request.

- 320 x 480
- 480 x 320
- 300 x 250
- 1024 x 768
- 768 x 1024

## **2. Endpoint for Video Request**

```http
https://dsp.pubnative.net/bid/v1/request?apptoken=<APP-TOKEN>&zoneid=<YOUR-ZONE-ID>
```

- PubNative uses a latency-based load balancer-- the same endpoint works globally, regardless of location.
- <APP-TOKEN>: can be obtained from PubNative publisher dashboard. Please consult with account manager for this.
- <YOUR-ZONE-ID>: use default as 1

## **3. Standard Video Request Details**

- Request Method should be POST
- Ensure that the bid request is in the body of the request
- Set headers in the request to the following:

```text Header
x-openrtb-version: 2.3
Content-Type:application/json
Accept-Charset:utf-8
```

## **4. Sample Video Request Parameters**

If you are not sure what parameter and values to pass, please check the table below. For the definition of each parameter, please check the _Object: Video_ section in [OpenRTB Spec v2.3](https://www.iab.com/wp-content/uploads/2015/06/OpenRTB-API-Specification-Version-2-3.pdf)).

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Type",
    "h-2": "Definition",
    "h-3": "Status",
    "0-0": "**w**",
    "0-1": "**integer**",
    "0-2": "Width of the video player in pixels.",
    "0-3": "**required**",
    "1-0": "**h**",
    "1-1": "**integer**",
    "1-2": "Height of the video player in pixels.",
    "1-3": "**required**",
    "2-0": "maxduration",
    "2-1": "integer",
    "2-2": "Maximum video ad duration in seconds",
    "2-3": "recommended",
    "3-0": "minduration",
    "3-1": "integer",
    "3-2": "Minimum video ad duration in seconds.",
    "3-3": "recommended",
    "4-0": "startdelay",
    "4-1": "integer",
    "4-2": "Indicates the start delay in seconds for pre-roll, mid-roll, or post-roll ad placements.",
    "4-3": "recommended",
    "5-0": "linearity",
    "5-1": "integer",
    "5-2": "Indicates if the impression must be linear, nonlinear, etc. If none specified, assume all are allowed.",
    "5-3": "recommended",
    "6-0": "sequence",
    "6-1": "integer",
    "6-2": "If multiple ad impressions are offered in the same bid request,  \nthe sequence number will allow for the coordinated delivery  \nof multiple creatives.",
    "6-3": "recommended",
    "7-0": "protocols",
    "7-1": "integer array",
    "7-2": "Array of supported video bid response protocols. At least one supported protocol must be specified in  \neither the protocol or protocols attribute.",
    "7-3": "recommended",
    "8-0": "battr",
    "8-1": "integer array",
    "8-2": "Blocked creative attributes.",
    "8-3": "recommended",
    "9-0": "pos",
    "9-1": "integer",
    "9-2": "Ad position on screen.",
    "9-3": "recommended",
    "10-0": "mimes",
    "10-1": "string array",
    "10-2": "Content MIME types supported. Popular MIME types may include “video/x-ms-wmv” for Windows Media and  \n“video/x-flv” for Flash Video.",
    "10-3": "recommended",
    "11-0": "maxextended",
    "11-1": "integer",
    "11-2": "Maximum extended video ad duration if extension is allowed. If blank or 0, extension is not allowed. If -1, extension is allowed, and there is no time limit imposed. If greater than 0,  \nthen the value represents the number of seconds of extended play supported beyond the maxduration value.",
    "11-3": "recommended",
    "12-0": "api",
    "12-1": "integer array",
    "12-2": "List of supported API frameworks for this impression. If an API is not explicitly listed, it is assumed not to be  \nsupported.",
    "12-3": "recommended",
    "13-0": "ext",
    "13-1": "object",
    "13-2": "Placeholder for exchange-specific extensions to OpenRTB.",
    "13-3": "recommended",
    "14-0": "minbitrate",
    "14-1": "integer",
    "14-2": "Minimum bit rate in Kbps. Exchange may set this dynamically or universally across their set of publishers.",
    "14-3": "recommended",
    "15-0": "maxbitrate",
    "15-1": "integer",
    "15-2": "Maximum bit rate in Kbps. Exchange may set this dynamically or universally across their set of publishers.",
    "15-3": "recommended",
    "16-0": "boxingallowed",
    "16-1": "integer; default 1",
    "16-2": "Indicates if letter-boxing of 4:3 content into a 16:9 window is allowed, where 0 = no, 1 = yes.",
    "16-3": "recommended",
    "17-0": "playbackmethod",
    "17-1": "integer array",
    "17-2": "Allowed playback methods. If none specified, assume all are allowed.",
    "17-3": "recommended",
    "18-0": "delivery",
    "18-1": "integer array",
    "18-2": "Supported delivery methods (e.g., streaming, progressive). If none specified, assume all are supported.",
    "18-3": "recommended",
    "19-0": "companionad",
    "19-1": "object array",
    "19-2": "Array of [Banner objects](openrtb-api#section--4-sample-banner-request-parameters-) if companion ads are available.",
    "19-3": "recommended",
    "20-0": "companiontype",
    "20-1": "integer array",
    "20-2": "Supported VAST companion ad types.  \nRecommended if companion Banner objects are included via the companionad array.",
    "20-3": "recommended",
    "21-0": "integer",
    "21-1": "integer",
    "21-2": "Indicates if the player will allow the video to be skipped, where 0 = no, 1 = yes.",
    "21-3": "recommended",
    "22-0": "skipmin",
    "22-1": "integer",
    "22-2": "Default 0 Videos of total duration greater than this number of seconds can be skippable; only applicable if the ad is skippable.",
    "22-3": "recommened",
    "23-0": "skipafter",
    "23-1": "integer",
    "23-2": "Default 0 Number of seconds a video must play before skipping is enabled; only applicable if the ad is skippable.",
    "23-3": "recommended",
    "24-0": "plcmt",
    "24-1": "integer",
    "24-2": "Video placement type for the impression. 1 = instream, 2 = companion, 3 = Interstitial, 4 = standalone",
    "24-3": "recommended"
  },
  "cols": 4,
  "rows": 25,
  "align": [
    "left",
    "left",
    "left",
    "left"
  ]
}
[/block]


> 📘 About Rewarded Video placements
> 
> Due to the fact that there was no Rewarded Video parameter defined in oRTB versions prior to oRTB 2.6, we currently support the following RV parameter signals in a bid request. It is recommended to use any of them to signal us that your video request is for Rewarded Video (RV) placement.
> 
> - Bidrequest.imp.video.ext.rewarded = 1 (integer) /true (boolean)
> - Bidrequest.imp.video.ext.is_rewarded = 1 (integer) /true (boolean)
> - Bidrequest.imp.video.ext.videotype = "rewarded" [string]
> - Bidrequest.imp.video.ext.placementtype = "rewarded" [string]
> - Bidrequest.imp.ext.is_rewarded_inventory = 1 (integer) /true (boolean)
> - Bidrequest.ext.placementtype = "rewarded" [string]

## **5. Sample Video Request Body**

```json
{
    "id": "5de66583-4534-4df8-a9ee-0feb2116bb5b",
    "imp": [
      {
        "id": "0526d52d-c988-45db-b911-d128e6e47a29",
        "video": {
          "mimes": [
            "video/mp4"
          ],
          "minduration": 5,
          "maxduration": 30,
          "protocols": [
            1,
            2,
            3,
            4,
            5,
            6
          ],
          "w": 320,
          "h": 568,
          "linearity": 1,
          "playbackmethod": [
            1,
            2,
            3,
            4
          ],
          "delivery": [
            1,
            2
          ],
          "api": [
            3,
            5
          ],
        "skip":1,
          "skipmin":10,
          "skipafter":10,
          "companiontype": [
            1,
            2,
            3
          ]
        },
        "displaymanager": "sampledisplaymanager",
        "displaymanagerver": "2.0.0",
        "instl": 1,
        "tagid": "35",
        "bidfloor": 0.01,
        "bidfloorcur": "USD",
        "rwdd": 0
      }
    ],
    "app": {
      "id": "66755",
      "name": "Meloman bykov",
      "bundle": "1210207476",
      "storeurl": "https://itunes.apple.com/us/app/meloman-great-player/id1210207476?mt=8&uo=4",
      "cat": [
        "IAB14",
        "IAB1-6"
      ],
      "ver": "1.0",
      "privacypolicy": 0,
      "paid": 0,
      "publisher": {
        "id": "1582",
        "name": "Ð Ð¾Ð¼Ð°Ð½"
      },
      "ext": {
        "sdk": "2.0.0",
        "session_uptime": 30,
        "session_id": 9,
        "app_uptime": 501,
        "impressions_count": 3,
        "clicks_count": 0,
        "bcat": [],
        "badv": [],
        "packagename": "com.bykov.meloman"
      }
    },
    "device": {
      "ua": "Mozilla/5.0 (iPhone; CPU iPhone OS 10_2 like Mac OS X) AppleWebKit/602.3.12 (KHTML, like Gecko) Mobile/14C89",
      "geo": {
        "lat": 58.5539,
        "lon": 50.0399,
        "type": 2,
        "country": "USA",
        "zip": "613043",
        "utcoffset": 180
      },
      "lmt": 0,
      "ip": "50.62.160.240",
      "devicetype": 4,
      "make": "Apple",
      "model": "x86_64",
      "os": "iOS",
      "osv": "10.2",
      "hwv": "x86_64",
      "h": 568,
      "w": 320,
      "ppi": 326,
      "pxratio": 2,
      "js": 1,
      "connectiontype": 2,
      "ifa": "0C231BF4-9256-4196-96CF-A1D12B5297CF",
      "ext": {
        "battery": -100,
        "rooted": "false",
        "airplane": 0,
        "batterylevel": 8,
        "batterysaver": 1,
        "bluetooth": 1,
        "charging": 0,
        "darkmode": 0,
        "dnd": 0,
        "headset": 0,
        "inputLanguage": [
            "en"
        ],
        "ringmute": 0,
        "diskspace": 1821,
        "totaldisk": 128000
      }
    },
    "user": {
      "gender": "O",
      "geo": {
        "lat": 58.5539,
        "lon": 50.0399,
        "type": 2,
        "country": "USA",
        "zip": "613043",
        "utcoffset": 180
      }
    },
    "at": 2,
    "tmax": 1500,
    "allimps": 0,
    "cur": [
      "USD"
    ],
    "bcat": [],
    "badv": [],
    "regs": {
      "coppa": 0
    }
  }
```

## **6. Sample Video Response**

```json
{
  "id": "c8c055a5d10c11e7962ba0369fcef2b0",
  "seatbid": [
    {
      "bid": [
        {
          "id": "d8b8cc4b9e2943b2a415b33fe5ff5c98",
          "impid": "1",
          "price": 15.11,
          "adid": "10993",
          "nurl": "https://got.pubnative.net/dspv1/winnotice?ap=${AUCTION_PRICE}&t=9IFYOZB7A70cs4zY0a0dkqqNS1twbmXgVJQWB4cWWS3nWuNx4imL6qSyPY0REInW-V3Zx6L8P_oSnRmDToc7H1DpUObPGXqRSv_1Q7VMtvcWLm9MtKSlJvd4J7YxJxRiupVIVnxP",
          "adm": "<VAST version=\"2.0\"><Ad id=\"223626102\"><InLine><AdTitle>PubNative Mobile Video</AdTitle><Description>Advanced Mobile Monetization</Description><Error><![CDATA[http://got.pubnative.net/video/event?err=[ERRORCODE]&t=-WbRBrXu0NbZ6uh_E9JaE_FIj-xjHR5bZIN6wlweUyO-Cm61vq3s-nzDnIVjEwKiK-G_YCN9hLWLJghB9dsoYOL49JOqB8fRL5wHfEW5k1z1vFsOSLCxUxVmQ74Jcr0fd1T1BwuE9hH5RFX13c8NwEbscYIHO_h2d8KQQXDNgJNYN-KE4Twt6_ZvQl6Ivy7q1djJ8mLnbRKSoQ8mM0u00bTBd1nmtiIc8DK20gG3KRvjr5THhQBCjlZbGknPV_9UjmsRvG22O7xUAu9ZNGr_NPUsTtmUX4d6osWIg6o9W6Pzjep4FH4lM0IVCIFLY4qq0n7DTHI9yfFJE1FfN_TLTo0lV6M_qvpwFFR1nlqi65yMzS7wuEZSGPKy8pD0fz86qZPsGTXhjV4mGy1y-6gMxiIynsWJnKJlBMMr81bS126xpmUK_NLaLq6dTEAUxsSI4VM1-uDE_VcjXOyQdjSpM4rWVrHT2tXBjgu3Lpo174yqtAWwKVWZTP17cFTd_HpP0x2qa4E4C6L5wf0as9nOIK874cwaW0daq7ye6-czrGyYTNLTqK_V_mly3Kjm3R48WpINp1cS65NQy-TIxIZ86eqcsvR7xFHHcX9Lxc0ueOx73yDfYnK9JxhOfTKNPQ7Q1DVUTyNUZ5x8k_ARuVd5x4G6PdDpkAWk4fqnZJQr48jADYqux2qAMw77vwX8xS9o86fScX-JIfaU-4aZE7rRn_BRP-a2yR5T-Lig_3xuW06VoqFn4kUZyvJT_mB0_W1LcFRdJtrnlBxxqhTg4fxnQ6WkS2jpiNNZa-7A5JUP1lOi11X6_d9eeUKeacLLU6c-vZAA7umnlyVwC8qeohOe5kGlWjrTEWe8ho9_u8zIGo6Trcwfr3XMHqtF-Hr5sPVRyb_zs7A6HNL0QQLExr5pHOhAbj7BNl3VOWB5NAwcepVBWjj7UTeeeaMDLCP_E3xEJuipPwyh2qiwqs7DxxzeRHvsr0Xh-xhLFnWth38QCY8MEhMvFyyckxpXoFR41Hi1QZGZm-YkOSPiVFv6T_4zlkW82KhDgp2m3cHljGCXQ4yui1DIgS7YkKJXoESuFkcXPDfjUQ]]></Error><AdSystem version=\"2.0\">PubNative</AdSystem><Impression><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/iurl?app_id=1038058&beacon=vast1&p=0.03475]]></Impression><Impression><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp//v1/tracker/iurl?app_id=1038058&beacon=vast2&p=0.03475]]></Impression><Impression><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/nurl?app_id=1038058&p=0.03475]]></Impression><Impression><![CDATA[http://got.pubnative.net/impression?aid=1038058&t=j_4KnwuKJxsDWrV_GXQIR7T-7DQygEAeR6Mdy0XPr3Y_CBfXoyOOed1hXstV-V1AA2CNV24DUYXpbqStSlUlyVm7KRMmuDbUDCMBMv46Nb7WuKTUdi6zY7r3LgMsO92t_NMhpseQimOdyqphINmnJDESYxNqCi9MjVU6KyLxTnx4hdQcHw8nZKlqyi2cpsFdgO5OwYGJ9uRraheM23wyQXp_DaCFINTUNhGpN5OLVnFjjhA33reR_0trQcRW6ETpzQZPmOMgt63HiLh2yU-lygurKxecmhaJXGz_2brnRqZyd0STrTox5IAMMlzS_QtDELjzaKhj2ZHJg5kc4piBzmeLJaEG2JF2fsfIM_NZd3wft0mdrFvvKgbDyxNQGsFJ2KHFJcngez0sqZ4esLQbatOq-cKdYMjf5wnIaP9CcbiDp8MjfuMx17lZqpzY0h8q_teAKsenrZGa-nZj1b1CalFSCI1pSthlwsBiJlNF7TukJCs5z64sfrxuBEfa3m7i6w-6_fScjiz32IhkQQ9c21qqzpZ67NWjB47KmYNltsWKZZOfCcAfBrS_YfWAnF9uOhUY-xJcqQauy06zHjfz2Yt0_wMc-2vrSdJn4lKUyunAL0uXUfbL5bwTqxj1y8RYk5gBH_LFZNKdONN2V8UUaaeWToWqe-jtD081qXLltKkiXWqDRrQ6kvpBHmzYzGEhH7FYanq9sdCthiRXmBWXjM_y0ebU4iu2LGlTTDgwr1HK7HZ6BhajF9-ZWQxXTrXbzN3L8m5Nz7SrlA4TDfPUcPTHsFeuu-D9wxb7BbdHVGnP4pph7LbkfhHU9nTm9kvZwQ8qRFA9SACFjH9cpmLHBphmr8vUrk4jrEGPVlFS1Jwd1E68ER5_D16EgFstK_hqWW89KXkWMV4VPCfJwAt7bSEClkQfe3iS3DX2oULVNmwf4JVHkHCNhk9t89rxv72I0pTQgUxDnHfnqm0rjx2W4OHtsLwXlXniZX1ZOfZexGDdAfLQcUU- -bQzqOcMGCSrSFL0T-AW8rWWAAESdrxcvP6lrsnsmd9v4WKZE7zHklRxjcyIVo7nuo9EpJA&ap=${AUCTION_PRICE}]]></Impression><Creatives><Creative sequence=\"1\"><CompanionAds><Companion width=\"480\" height=\"320\"><HTMLResource>&lt;img src=&#34;https://cdn.pubnative.net/widget/v3/assets/easysound_320x480.jpg&#34;&gt;</HTMLResource><CompanionClickThrough><![CDATA[https://pubnative.net]]></CompanionClickThrough><TrackingEvents><Tracking event=\"creativeView\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/companionView]]></Tracking></TrackingEvents></Companion></CompanionAds></Creative><Creative sequence=\"1\"><Linear><Duration>00:00:14</Duration><TrackingEvents><Tracking event=\"start\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/videoStart]]></Tracking><Tracking event=\"midpoint\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/midPoint]]></Tracking><Tracking event=\"midpoint\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/midPoint2]]></Tracking><Tracking event=\"firstQuartile\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/firstQuartile]]></Tracking><Tracking event=\"firstQuartile\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/firstQuartile2]]></Tracking><Tracking event=\"thirdQuartile\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/thirdQuartile]]></Tracking><Tracking event=\"thirdQuartile\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/thirdQuartile]]></Tracking><Tracking event=\"complete\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/complete]]></Tracking><Tracking event=\"complete\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/complete2]]></Tracking><Tracking event=\"mute\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/mute]]></Tracking><Tracking event=\"pause\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/pause]]></Tracking><Tracking event=\"fullscreen\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/fullscreen]]></Tracking><Tracking event=\"fullscreen\"><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/fullscreen2]]></Tracking><Tracking event=\"creativeView\"><![CDATA[http://got.pubnative.net/video/event?t=i2xuTCYVfZMkkixt7HF6Y9TPs1qWwko15KPXNrOBcSII5tIFjAwbVA3iWDxsFabCuuVO-Hd1nrpJwv_nFZu2cUTfKMQ9sPf6SH8LUbcDsXm__dpqds1oBTZVo9tb_oWQGCKI5Tl4zGPsPkTyiX7ThN5REItfZYYUJtuSNxoCBiQ71HgEubPvrnYBX7Jhy4n7W6FbTsjfo_63oJZBztthouMBYdL9wxelUT2a4iPy6cSw9GJjSDD7sz956rm9nh8mgTXfCsd3XXTPM894AdQS6kjRq7AQ3-dYr0-K16M67FiTAQFGgC5Jcuvilu7oPwaf_yEwC5M5wjZbbWQEPBLPX922bsysB5NGRn5rbjVxTcZ0hL9C229J-wn4924LWgiyhsb-zxvebxjAu7bm-Z_Xi9dSM3L0_-y5677Z6PFfX8UYaDd_T2m-maCyRsFRtDNYHshxoJg6k868986uluNV4-GncnrtsBelcF9oFghl9cpxZ_Iyrow_5I8mwMGkPDtuivPx6flG2y7SSuc5hPeb6cAc6yvYMO1_yJO1ZRVGyaULD9Z6zoUxJfsKF1zAZeodNnIoh2f4ZjVJqbEwdV862HnNC_8XeXStH8lFZqFgcRRWEpxCUruVlEXtBPKreOa73u10tAt5vRQJIi6p9FvIUYgEGtjbB2om09vD-eeXvTZz7pH0YZ4bh1M6EWa1rOllALATZMFRzO4kerPq3yDgNjYQ6mPtZX6JR18H5biWST5_VixyOb3Bql1pot5JA59w7UzlR7LsPNRHrDCJZFXsM1vw-ab9MTjJd48lJsyVpNK67BuaxrXw25VorCj7CF8HGQirnXSSNMJ6a1uWe6taA76iObNt84SECrcwTbK-RtWm35BOyzY9p0UCmc_BNSzfclWYN3qWts3xpZrc1XC1f_ozswbnnLUAhhYC29skj0672MOyetWrqh70fpANRuHfEAYlbGXIHG3ZH_N9I228gadsGjBAIpfsL_-60NTgZgRbngUfVgOOzq1uWTdl98iN0jGEQqXS3htf9tPmBayGW8Ek0zbahlDjJD_5ZmZEsDR6g4Ad3PLBa7L-0226Thgj8XiYrGaDLKhPVDQ]]></Tracking><Tracking event=\"start\"><![CDATA[http://got.pubnative.net/video/event?t=zpy-Dh3CaXNWeEgwVsXBZn6F2IdbiT5qjEGt8AIKyod6kld7RQGBc_xY31SNTg-m4ZNiifoV41MJzvHgPo6K9y7yMwGWPpZTPqB5M_43qjvtXDUFqhZD3ZdGm3tbQbhpJy87oFaXqdx2I0Mz4FaQQy1wR78oBPenXc2EVQ5QCFQwrPxuP_Hn_0LrxNmE5sITMeqKPAvDJU0n9ub61_FpRUBM7Ar_B_ZJuPHy4mVaqSVsKwTlQlnlJ4Ou4R-hIs6-393qvPvbtnLrANVwe7hqgyQooeycDiMTMK6lFR-OHeoYVtU6eXeTPhVLtf5Nd_K0ss22CgU6dGE_TqaiGmCb6s1R9qCBKY6qFDoegHb_SlnX7NiRbNtK1cQd_982YJ04LpA8WCOvsjegFFPsn4LfWEeqO164m_rqL1BnRi8LesH6IQmTWCmCFl0DfjpNNAU6ojpZAOv5nB2BsOuFHW4NGi3qNHNXTB2Ved64MQbc_hxzom3zs9CJwl-LFHBDojKXhFiH_cG94oJF5YMGqsoEPLfWRilrMqaerVJatEyjrlMnyDywrKdKKDlNYuVVT-512M9q81I-p_FVF2gE1UfqGypBUpv_VAwS1WzPhVC4uuHUXzB4F4d8PqJy3-ArdR79vh59jOJZUXdvSRtToFEpt8avmgvY65M2vYMnALj-PeuGa05OXoXL3foGUc8yle3-St4MktLLnV3t5ghzys1XYJw9xNYI_h76tRzyD429XNc2pl06dGtJrfAj4FFIM3_ZDIFIomvHD6a5Ji7UHKEJBmNPavsjdJ1IohxPh3TyCOKvtD2eqVeR0PkevfATr0GAbfrLEbAiyofvr5euN9Mb1zlBhfKnup5KIPXLxA7u6HdFXWrM_orEOQaSZ0ZpBxvxO6H5z60ysx9pT98Goz6znX1owj2iwO1KoMX0Vm1HgVqbyFtV-O22u7oiW-TNlJmtaDcqk106v4zOJqy32Ayi1t828Cr5nDq3RlcaWGGyb5U6zTYFfeEQEecjnNtX7tAA3XDaMCoCwK-ZqpsokD7cGCOfOCcmxIQBSB4BLCxlYd7bnwEiG3gnxLjbCeHHeAom9pe_MQ]]></Tracking><Tracking event=\"midpoint\"><![CDATA[http://got.pubnative.net/video/event?t=qFSXrJB2GD9N62z90HpunguEw1ruib264SEqs_Ix-Cgeo04bjX2J9h3eJG-WzfRnVeC-gK0QJcFFSF38L_oyH_UUNky0p6nhlBqtN0VwSchvuR6h1QpJNaUlzyN_G5oZ4p0IO80HZuOiG5eFKANpRDstZysrKpu17A89T0fPRXR1RZIyZ9huRzcPRqGssR0-QfyfzUqK8Tp6Zt4cCr7JjT03OuJfZLxhryNZY7ju3SdowrRMYSNsueQtE7i5IoBaDmtGeUd63xmHzawLJUEu5tWKh0OYqN12XvhyOZjo1-xFG8H0EicMKWtl2nwvbZE2plk8dqDLCYIjJckQULADkZ1H_eTdR0fwRvp_BW6QFhhB0M9S4cjEGYxSXac8G-eURpb2luphgkokBGtMT3YtBMG2do37xEItH2JqY2uEEHByNDX2-UVDBxL3cKP_iI4BMcAMkD-DiARUVYvfd9yH8u9FtTQlIXWmcv2PG15_DQ8xb3vOQmn-nm4JeaFEO9YHUoWBFB-5bCpCt-ddsgMSGrn-UTqOtuKhJtYQwgHrJ4Z-J4IdEAR-AUpQC6mK6AGLXBac70xNe4TYo009uz_KcuYt938GGl58QkdsuBYxLeary-xmMqoDoY62uaEMvNEfhuB_MYA5nhWJMUJ4NrEubPKKLdelY8HbOGKs9PkoOTL8HS6O70PIQn_Zz93v4s3wN-OtGudRe52ODb2OrBWSQ1_pConkUK6Lgjh9Y4mQmTxtyY1CFKSwgUgO5gJgFxx9Jas_gFo6a5z1R-94aHLOxl0sRrhxlh_sKvv__2R80tcVPGh3x_EDMaN-5z9rKJHRCYzT4Fa3Y_VqavYWjAw16lAqDhSYER8XcwMgYtaHkzlXCq2uHIseR6WWBFwy9wU9_mA8dL8-lTr-xN8cxWHAys6XSGRXwkUKPYYlONhLsbKvKFUbFIC43YWjQAs8gSvcbbMGIXWsuJHmQFWFP-wcXUeOeEEuEWJXccsJF-bqbVOanoH24du-Z0Paio8w9yYssPmMLpXvL18jPaLLiB8nDa9OSR-hEx4lwXkneQkMeRy3l2Asvsg9uS_GL8XDfk2TJYknD9FYqg]]></Tracking><Tracking event=\"firstQuartile\"><![CDATA[http://got.pubnative.net/video/event?t=nVmGXgKLcxOWuOHe9rUEsEuVc5dm-MAHgw_OGE6gF8Eeqwb9Heb9kuCrp3zom2R0Ubvez5_UdMeGfYk2D-cDejfWOmNzvxNcWZEG9QMWYXSNiWtvO5Z_dj-FRmB_E7lgPDPh5x96apYbZjTkT9yKx7ph9XPNCX5bpy7IbYY-EIZQnuJXDmY7vv9b-HCwkWEsWyldHFNCpm0F4s2ztEhDW1jpVPqGlx3hLf24e3DWA65Y41ZPY1ih_YawfOFKQbx0A9_hG62znn3SLUDF-iUHCXDznV5cz-sl2swDim_IeBENqRRFP0mZ4DZvy2lSMrgSviLmPin45xaJFK_1njSQEmcG8uooojDEDPqNFz6ZsfYcthQDtyrGzAxay1Kq9mp1GfzobiRW5x3hIZpzsRr8U-hhBco10M1TfNPNpewrxMXCu3__8S7vFZu0sdnIyPuXapbMAG1D-p-XaWUJjbUajtyl9euknqLoKOBJYnCa24gdWe2VZ-rCayFkKgsEQaKKTB6LtuDjbZ3VV7HjCa10y2ceL4vZiwg78Gg3dmmcyPPaHjMVsTJMzuWAVCqoqkxIjRRwUZKNtWf3B3kl63Ao3K7szNoN35xaNKYjbQqN4ZOLpm8-xA-nmdBmbV9jz64o3ZXMOTjuRXHwEPObE_kmP6KfXvi7P80ytOooZjbS2f6Zd99SSv-p7kyL7qFvukbusDje4VF9ZYGi459sVII9Rbp3xjcVrpRHn5x8l6UD91EHvcKaCBxUpgBSse7g6kFlgqk_AoTUSJf2oQxGtZ5Ugz_oJNag9f8X-f4kO6spjgo2QQIXOpcjUUjCAR5JBveTz1tkHJNI6DtsazNnJAiawJ_YGxAlKGvYB8TTWdJ5u6l3Os83ZgSIj1r95oqut5LQltZnevwP2TBiXTTDdWvD2v_OS2MmvrH54ugMmEE7ZC87MzICgbPbQwjkstGbuRNGmYx3gI3g5NOODYqHTssTpkWb_qEOSJDBWF6gzxgmoxmjydsceMA4gU5t_mRssNI0xkzv7YHDiBzPRJXASwimNolRw3_YlAjUvsSNJ_c3XuY3CIp4sSC_zgPhlOB2AHb52YKyv-95wz-DQ907]]></Tracking><Tracking event=\"thirdQuartile\"><![CDATA[http://got.pubnative.net/video/event?t=f2ZeGwv0XcX50X8duxXfRj4DoBAS3gehVXtsvAPB6n8sGGhXphxI9ArB8wkwgDN5lTWAcp8SkCGJWm3Jauayv-TixtTQN-m_XNOrl5r7jeH2vrfY2MOPhcSGoCE5fsUOtl5T51l3z6NugK2Bpr7Q_ejGRadNOSae5bl6_m9SobP2ScMv5bTTO2awr90b65Mx7kx3hlnOHPWHV52is9dINt4ZmpxeRhrfhCGHBStLZpVN7l0BT7qgN361-YRnHpGozBB6iQHc7N9cZpgteMpli-jxGO1d6NK1q-7NhH_L7btdKjY5QVGWllfgkB08zayLwcoQMO697d0sh7C4_erMwPyepYb4zDMcNYn-gn31kozQXwvJONKgND2FGpa8Xb9BDD8Erbr54JSYBw52y_XiceVARXeMO58E9PPtheTAA9ohIfnpdzjULt1Q2CTX3bU0CdTgyEhTuyaDJ2VD71Aaevd39EZOErd9Z0YQqaBNdfyv0qATLS0JYVCEsLx3_wXvoRGbLTZycqfBfckTMygyuJwLIXwe_AbTN8S3MOwrPy5oZcRaSsBrRo0bfxTTRSnG2SP5hHHQcoV60MH8_V750YTmDDR05ys0SdDTW96tDg4sZo2C-Yz-N3SfTVMv7D7FRnLJudlJTS3DmNMVo_OowMm6qGKuON7PE81XteRpYmgakF-m7A5I-c39i0xRpMe-04z-ITn7HHEc-vuXgLnB4OXsYeDYOPbS21bRVYxm3vBYFTm-rUer1uKBkjpu7_2fmC8cRjM5NXXkXLy-GARB4R4-ZEoDw6JGTD8d3EGw6jBTbf12fRcO9KutI6bblGWyX1-SUo3VC8The0H-VTjGf_qz4mGa8lvIJLbo-WAcdkvQTtD2ZuLxfxSLIzPdCV-ZOapZDKVocUE-Yv9Q4dY5aVvAcYKJJcWvQWkYoZhaWiwbWEUXie1b92Cb9rvG_eKqjtBy04k0n1Tikcxn3hK_W0uHnQMyFO29p8Ofwm087wBSLjlVfT6a8NtwYehPVZPq0YA0M7xi1QDilCdPvRjZ42xrZg4SXyIwP11kBUS-r6A_18kL5vpDq_mw8i3wmh5U_gDNEGBc1yJaTe-L]]></Tracking><Tracking event=\"complete\"><![CDATA[http://got.pubnative.net/video/event?t=RXp3hCFPq_jZ6PdM9mTmzdbM76C-zwnSF6R99C6xlSlpVLpE7Xi9zidIO5CVQ4atjP5cQ1zQ9Qz1A1OY4PRV__qWh4LP-YTOemBQ_XTUbcR6lzaFlvnOzxO_KOEpfDQUrAW7dz2QvxDCTnVhNpKcukSOQIWUIUR45ylsmP0qsYPHzCUgoYoVnWuQgBWGvCvmM1iUI9qf2rr9zxvOsmzmEUTTw7Vb9-teXBIv9rdw3X0aSMm-zwVbdqSe7w-Fooy4_CbMUVo_votJD3-r01iXDyEhqovQEDjtI4wGxQGcYlRawXV21p1TBN7dCL77PNojqVbju007WvgeIXSZRT1D6kA4QVJfywl2yi8T7atguyVSOnkjohmc2P7i5LsX_XVbRosXNGIdOc5PMmToFAySq7bWYnDGD5G3kSjePOJx_rGFYArDhbaPQzjzvaFDxorJQG1MBoELvcGk2Fa4UnnW8k2ggBA0P_nl6NQ6kHQ51DcgGoE76ZDYajnKxC-Gn68dftXJLsQjQM85GWyqnLkJ3aGtXA0mgE7v4OGrMLpP8J3CQnvt8aVFXYqXng4V7l2hSMQyxPnypDheq2pVZ8Or4XsWWEvOhyyeds3250dyUmJ1KnzIY9lttFb_R_7UdN9fj4JuP9ofTSbmlXZmRdAaA_YECj7x1Q40V8UTr6MA8Mn4Dyvo7lqDzYUhHtCigTBQ-xXif6JcSpWm557QiX7n0_dcrBoG1CyHL-sKCyyiqEXRO_7Fb0RHmlEv3Slhor2rw8mnn4dWKkOxHCR9QtDI5IiKsxb5vCS367yikTcIw7qYkXRjuFoe8ptmBeIQy3Av8t_9Aouj2nBHekduHOQlYQdx-uLBgqRaf0eJS6UEi-DfaFETC-LWGrYQ-_RVZ_d-s7TukvVwZR8npD_Zn-PROWPxyjHYJN5n3R27ubLy_r_4m5ZYFLmi7r-fAXbjVVwFFuDg5J5rvoJpBLdEaxCkkqtbuvQg6XzkwjaQ4eawKfU0rBp-U5Fm5iQHmELhOMxlyh0oApgGN-2UXiqUOr6WGliV9wW5TqTjR1AvWf3jnMBdA-lWNfHoqsT-N9vghwweLb7Xym0few]]></Tracking><Tracking event=\"mute\"><![CDATA[http://got.pubnative.net/video/event?t=5ATvk39B4WkrAUSMtN9tABJJHHDBPYl6MZniFcQyHTK9jEa5H7HYcZN1mGOPuiMY99z730z1oBV_Ynni2r-Z7RHncouufB1kA_LZOIsHUGNSgKlfVM3P2wu-D4SLFffVauuiIRoULc0E4KLct4RYycZBQ3c89wab5tY8DQErkYLo7s4W9BkprfjFp3JDP6iPD9SnjZnXLOiRfcGdHWJACjdyWR_-ONynu3C4GGNA0dtlpDcnbmW49HBf_hx_LzGkOkBu-RyaQ-sx8E2knN_w12UK57D0GKBN2ic-SpLvJPD7ab4t7iBLSXtFxSYG7ZIWt0tdPDJwvHuffIMqrTKXE6GwqU8jajjEgvFSViZoBBrknKrx7bHw6SjSGvPK-VT69_8_i3TwYmiKM2g4mL9ZKnacTqYsay_Z8Clv66iFgWtyZj9ST4j5d0tZDRhU4L6JPWuHwWIhyieCsG2chOBKjIqr_pl22fvIgl4Mx5MpmbeKE7dqDeqiM9BKsLSA7ATLL2JYn-rfDF7p9kfRm07K0HmyHFlKOzjp7U49vyzfFTiMLjLpBxnMQCDB9Qs2YvLfDuULGIZPc_UT5x1B6sS2V4291ztSv1fsZg1nfH3YaIl3VoVs3DR8I-1ulWhYK-ztw6VrcZ5uNGxKob3krA61AGgN4j99mfmhgNdwvsnVUl0z2kNQtUei649yCmusftPekyS33pJRw06CrE1tyipAVqLNVmuXmLAzCamXRzzo-sWTI0w6wgMqDw-I-_rSJrLKlHCofCBrdmi3NTCvtIieRqglwELFbNVrTQY5w_rK9NG_NG6GD4nh7Z-suRlG6O2sL-Eu8KCXlWXedOWlWIhpTVLfCFPtmZS-7e22fN3xKeAiOOEQkO8g9V_Hk2AEny3NNcDL1luZkLEwc_1kWr2n1FvcM2n39mUGri6eQQCHNKRX0ndqdqPGR4IAc79GJXJfnGmiqx9h0cFUcuCINGbHxOfekmNsrb4fqmPzWlAWre68q_xSbx86MevJNuCyywQII02GbxfvbEr4rChS_Y8UP_Sod6vhyCN1kCnhD7bR0-U0abgN4ltrIwIomco0pQe1a3I6]]></Tracking><Tracking event=\"unmute\"><![CDATA[http://got.pubnative.net/video/event?t=KyQXYWwpFKD7Ajl_npAk8TG6ZL0jON-O-93TQPzN0Z_ieB-CbRjsW_QYnXrD43V3vfIxRV35rZXeGsWuFiy9ELtZOqV-xCT5-mOI8Bd_VLMrQ8ePlZ0XsGqNuQNSxBycD82e6cEi1355E54aTcH5Kb-zr4cZcmNQWt1RTy7B6TaFs9m_YG4Z72E7kbqlU9aOn_OSXvXQE3gATsOFuJCH1J_jUR_QN-SdZkbVdTUges-HW7zMkmSvFU7kCbu9vGa2i7l0JueAdUO7TJRKCnD0L9VsxT0Tr3-Ib3dutFr527rf-Y4AFmlTf5b4jU1Y_ibUIn7HHPRirdXFRE6yqNlvQqB938QJ4K9QKQhCcMoYMQympGA653w_I88jkKGsLVWpHYWonPrEbtsufMhmqZKresvCTismWO5d-Wno4M4lTe7pFRbGiuwNHcfTBdKIEb2usaD7kvUJaVoNHQXJL2hzbyHV3Cw1CZDKJpWm3TsI5qJUr7vrGVh9nz_omZg6agc7l3ReiKNl8phJcCCVpKdFcePFozzLPU7U7zSRKk3QhnspBXHqWbJ36IHSlXSxDuBfqaVSIlRihXNUqFNqYpiGMGQSxj0uWL75PQcVYeHJZtjGfJMkQobzpiTpi6a9zXBUrJADl8G15Ne_wpwL3Gd2SATiT2Frl8kL25zMIEFsY1aktn_4pbKIh9Qzr5cjSu0rxKgQaJ8HHfgx7bwmJX4CtNAlL5WZsLGqE47m0no-o-r5kl_3_z8X2P_daomfi8MZWZntE_KCfWqBoH5w2Qf51qjuuUl8xm-u_LV1iuMA3KAiEHakMjPMMihBpgK51Sd2XRJUGax_hWr_cE0XPe23s1hY82vHykU8jTNTB52SKb-0LapP3d7t6Ofhbg88chTYoNdljJ4GhEv3nliNpy7kQ_Xp9NW97HXqOlG-PfqY03QAqwBvo4qKGXiqg0__0IuTA1bKyvZr7yuE7Tc0EMrzkTbmE4_BkcMF4RrjtmUIZ73XhSg6_e4t30-_mJX8wvZLH_jwlF40teAVRviInk3j-3rqu04aq3-kfK3QZroVblgBIo8aTukWzjBgwbYPwdJUreE6-yc]]></Tracking><Tracking event=\"pause\"><![CDATA[http://got.pubnative.net/video/event?t=Y8G45zzPRAopY90UjF9R1TssmssAsBvXmcOpNE6CUkutgvKbxyvlNDGnmRVGVIbTD0y2fXVRc8YTySvt5T193UQnSoxnnHVaUYTOvB7997-Spdoj5n9vPaqbG0kGxfilm0Q6DTwYcZBqK3qO4XHK5D3P0uo9QSgHo7gtYHNYfAUC6yM9Od834YYqPHjyCwnm79vp7s8XUqSsX-fcPSj-5J-RNEPUTKrOE0PrZRYq6-Tgsbq8Lz38dv1WfNyZATnd_uwhNXefOkcTViXza82TJfwLBVzv_embcxAryTdFxjkJnJPfmK6hbJs6GQVNlx-It0jbpEitWImg5UoQEoKhfsDZLG2VTVvdfXpVb5XuOXSst0bQ11FDIeMQbpt21y1AP6cqw-XZTejopI4nYaGLP-03xTua7hE2k0njPDF7HZBAZY4G56hnx0dN4XD8BGPAmdN9N1uOxVedQHVtm8uZm6N6rNrGLfzF9hRVaQaBuvilZwwTbcaewQraxqeGITk5dbTDqc_SH8PNxHM17iU-qRunWgwfb5ee4sqsYRUySgmx_WPC6Yj7vUBVMeRZajpmPJQK7qIFf8aWRig_3adTCVknQhemn5d44FmKCWnjtk1hzzLQEBqgaYcOTcTs5hzM4VYBcMR6_M3aSETHmfOwjf0g9zMpFbBLi8RxCu0v_iJPJ8dE7gSEjoS_eSATh0yPY5P_7pwT_s1U_hX8SXtyP8CvvD41DqtDLj3wjqR7AKQ-NAOV4VhnAGDeBTaIjo8XaQo6TM1-4_EbAnvW6W0Sv0eMl527o4GCxfm5wt9zTae-zelhuJKJMk62ygfQG4ZZPaH38eZYC9l5D918GY4DTeL32lECDq3KXvnZXFTWUVgBadfBcWMSe7oxSgWjoDCsevAvrO5_gpRmqX94ra_N9fO1twQGsz2NAR3u0LA5XyzzKvXgzyoeuHJTNGOKwEKxnaxI0BL3V7gVmuFy4Ng5x0-NyvIK3UlmZ3Ixlj0dLlU8oBicvr7OIOIuGT3j-2h1eSKX7XNSnHjAQCXWq1bU1ZwBOqoWuOydPSuKwcpRYaTTft13N8yD-gTEy0YpTdFQAzkohA]]></Tracking><Tracking event=\"rewind\"><![CDATA[http://got.pubnative.net/video/event?t=XXMy4xid1w7to9bW-Nhb2YRvWthCmVYtofFsmz9N6n8cv6JNNOr9TzJIgTJDYn-sxV0zoOKn_fR8v96QMDxARwKjh4RzyhysbclobAppvcXdUVkjWRPRC3Y0H_yeTSH4EMH8WcaYU8HkYCjE1wy7hd2pYe-fcDpnoSYhZlqLWW7hD2QlH0eq-jUZUgIa-QxdL02HLovjfc7ezaar85-eDxOPwyk2b3CAvJd_61SP7v4jcJYNkOGs9P0kDCodQJ0yRbvtEmPvZhC9_zZCC8L-WLomlS_pVp31xqw6ByTvJZgvex-sETzLu6wMH-UkbPveWGUhYMY3iwd5mOHKcOz53bdZOQEefC7CstzAllDjm-h32_sXItBjkxW0r-HXDsWWTeF-HmeJlQXO4yhJbE3GNykjP_7zIl9dNK4qhQqO_Ig_ufH4oEtqAUF3s7AbX592EVYXqEZiyMlo7N_QtAqKfs2t03HPnSRb8YJQZIT0jzSkWVHLnt3tP-T_RxCpu60To_klatPn1N_f4kjdzngxkkZtXgANuIE4b76j32oh1bX5Ml0jojrdGdxmVXzxXIceZN0MzXiaqv2CIrrRJzQi-lDyb9LlmSPyeO5CU-muT3r95IBc9Wh91l14ThJw7oeiPdLvGmV2UIZUUDQPGvJ0DvVe94YWskOXdJDdU0GKJQFYn-bWjwHV14INXy3y8zYBaBWuk9wTd6OxVaBQGJjLAlP3BQO8uRgMRTdi9EiMM04ruXYEcJly3YBcUMvo5yk7NR8LWItN6hqQzYLtVi1frSkYSM5XL-xzGQPkMOAxPo-mZ3zGb3thZWlERhPolOSGqBNDclSESSkcn0xpYxf8zwCtByVckfDx-4JDUBfzLPS8BodwkyVh_k7r6rZHZD3VL1NRN4L_hhcT0d3QWSLEJyyTfa3ivZD4rSP_hWo9vp15uD6Ttkm23_nRaYnWOpmL9hkCuqiTHtDD- -3rPgGPneNQJWr0HQJlYx9PgeOqemxjLmwXsbi8Z-olNzBDA2R4pAQ7CnRj28ougYcorxS6GKelkjuukoyrEP4ogn4zg2aYVqRuCpc2F-8f3PTBZ-q0M-pK3JA]]></Tracking><Tracking event=\"resume\"><![CDATA[http://got.pubnative.net/video/event?t=2aaEVmpM0IMbNs90xsS8NAyJspLFYoS7RavldjAEh1yT5LRuWyhBB93BarJ3HUPWw1_bSYBZTi4V9NYMuV4MnkxciqkfxmTFBourSa_q7A5BZL-GJpwmsMZA9jtMi9ucRjnablVaNhcQyg9cQacf4c4mWeKvCOFtQUjIIppe1JQqLjlrS9NDBUkj_A6E7zILE3Xe-VlNK9XH8CFatFDbKksGehbbK6FpAuRJreyL0uKZbYZUwMxu37yEEOq3fgCcze_pDkAIfsfkunZZAMMxvRpHjUD3pVpoOK5wC6LMfX6WP1WbNu8ODCjt9miMuKniCn-ltKfApSnmXdGOrWKbLj_tEAFKSFpIeWjapZ8Vtoo6XE6eFanYE4BRaogd66PtdtYJuw0ADhb2mt61PUnyJAVwdtR2XccOL0BkoQcnmjDL-s25HRxfyLItgLwDL1WgoVVsl7d-DlvlTRPwKaWUfW0mB8lNqKpxURrdZhYXpJJ5kwcBDZYrb7B_HFXeqaw8WGTxwlscwrTfklcwp8w_rrZb2OcP7CoyjTfkjRKUmQTMAKROj6xYhWCY514KrGnjp-qFMXBTLJutlWnr3d1SDhWx6kLnQzvMa0bdirxdTpIQ6OoxhbWNyj9ZblSwAaEZY_LtW8kOoHDBKTtf56xJ1v6OyZ4lEX6X5szdQSZJ_u6chAdhK6nW2_TK3Ik31h2vN75BIOAujZq-7zCn1APSbZuQzuAyCjluIoRsIDkwUlRWUiTarbcbm0usx82qy9ZbfBAQbCimR94FogpooQup6_4O29Iw7T3Z5j2UDyJ-_y6D5Bpc2w2Bp_CW1S2iKkJOPNh1S1QTkCV5MM67psFNXVkzCZqy5ypwWZzY5OPFgbgCHn7pTXKCQtFgzZKW8pAfoeGlvpsoGoJMW7LLO46HvdD6iKYAwber7yfdrJ2njtvch2Sq6-CJOB9Jqq_oRxA9h-Tgw1UNGz4F-AlQwLlEHNc3w4DWfEw0dvK4gmPbyiQvL0NwC2N0MSdLUvGxZ189gU9H96KUEHaIv0AJx-k4x1W9kKacXAzCa_o2eKgc_4FioxOxkvoqYEii1VckwblANW1fn84]]></Tracking><Tracking event=\"fullscreen\"><![CDATA[http://got.pubnative.net/video/event?t=8afzyPgBsjz7JMm0DYmnbCCGx_B0H663YSOtxE1nTajLoiSwVE70WEam6353bMWsbVWybpUjhA1Qrz51l_RWhz9mHOhylKkZRakqkTuXqBHZVHK4BWFGzgL6n0FLXRCM8jznlaWaG-qeI3IYIqivBMUrWANuIU9iFD_MTqzE82kT3sjETh2Hyd5UtrzTlNl0-rDc9HsR2d6rEBVvWQoa6X_msQB76JAgOdohffN8h98VGH6qvF8XE893ExutNNavCtBkCcbdFiXcZjaouO8GcAI1rMfWTRIqyZyQUHQ9NkNHkDu5p4tmt57jCyrnYO96n4jHs7nWz7MyXnSe7sMm7aVa3sEA2OgNp1OGBu0CYurr6OaXJBGFV53BtOTfK4Yy2hRsagTmeu6etUTV21zvIXrP1q-D7Qp7GRiMMDYT3ivL1QZUFUtkwaIot2TYpmshtvEmAVsh91UkD4IXkjJVU3-C68lhVoFqZvw_gfIYSM0zS9HzA1gKshdCEcinioV6u2usxOBQHTx5W8RSVJugy9UpDflv7Y7DmUbkkWo522xXPAgjc7aKUQshzwof0MdgEoKRB59JWeJcjhuhYpYtORAWRHAd-OIsB3GttWIwOV6VLet5rKqCBOx1zaCyBqs8v6PJ2ib115bQiO4CEX-SjTlMXj3W_i56SX0Xy7nvjpFSBKb01KP4Gi8lw0S3qqTWuAH8-6H695FD0xwUXPhCF4h1mTNYlL22KNPMastqpJKz0e6Pd-7vU-jNwd0XpIXT9FdzjFQU9nbLEZKIBAlUVoEXN5fcYjSY9q-On9uUpUu_iVjTBUv35YOvcE-JUYll2iObCzI5dHj1EfIdNcWkhYTLH6s5F5vW0yqAqizb8SgOzgu4e2KFmGVLgoD1cTYHplHUeLNPm3vSSwAAmjKUSZX-Kbe6HKKRR79lMK1yruml_HPk-az1cEP4cQ1icHCxb0K4qQ5nybYYAO1TfEzpZ6iRjfJ0m6kUpRbuYoPj2kZcD1veWRH10mfBKvOkIOEQ7iOXyxGaPiT0M9s09pFCgvEC0gOTNFDB9v2tTR9_Q-ybkPj516qZC7BWGeogo-ZOwWX50O5PnAke]]></Tracking><Tracking event=\"expand\"><![CDATA[http://got.pubnative.net/video/event?t=EDkCgqJwmc7j1HTENjrx4aK6NLZl7Fff-YNqJgUDly_XIzm1o2SH9HE-ZUEdBFDpGTwAtPRg8xL9fZndQp_OVm6UtFUxXyqH-iZY_U3tdpwq7F05uBH4783XzGCY2jplEauyE8kYKzzslOgGqPHQC0Ow5dqGvX3Lz0JH4ZuEe7etGlcmQtcz67vQb_JeVY4bvcVUqsIkO2wdLuDII2Pb946j6hXmG4Hi5lQ96b_fTvqUqvabTcUDhjGhtq6o8zrVlRU_Ga5Ic5GKei2D_i-DX6XoOkvHE_vfmTgAvHtFjLJ_8VZfolQg3aOzkor0hs-cxR1W_Dek8yCXqB0W67FXfTmg9uaa18Yhwy5QqqUx6XHKLw97P9Y9-KtW6yHhwhFcP_u6RjxMpmQXMF6zf7tLGmFEFLVFdnKB6u1eB4tqq0kb2clwLzz9KIbbITRBlsr5TY00DmGbW4-dnTQgmr_Y_XMu4TbJBCrOisjnAe79Pogx_-QfepEPeOjhJKvO6WeS32K-QL8OEvtjFxfvg6gJ3DHxqw39StXnziVsJc5OevA9VzudkJUEpaiXtMIWfPAixpjem613913imbOVjHahkO9LtfNGFGsfMZNXYxNBvPWhWHFGxPqNAoLPOSWbDs1M5GeWaGk75lxwih0_x_TbJFDkHi0Mq79vHo-I2_frQFD5UXNvfPYy09UiIWyDwWor4_ggg9PlIANdb7fUChSo8tszWyDLVock1Pjn0Bh7-qvNTwC_KXuq4-vff4XKzdEADqvnsUedKDq6t6AJP75zVFEExruHITQ2H73tdEZBUibONVlZXLE4okhEnKcc-2KaMzebP6A1vF1nQxmN-br9uBIOK3TzWIWwUhZVxn9GbYCazTwoQxcNPX3f1hGtYu-eqMDP_EOgdKiOXRrCLwYcXcgRNRu0Tqxcihjd9DUIfkzz791qOakMkVYgB4bUpqCzQkHINoyvWs6Viyx6TlKCpG9k5iZGvejD_qiGZyov4aXIqdW1LyilVqKuzBorLtrpbSlbtxvbiGDFTImLKUk4j7lKb9ixWnXPnvhgiM1hRk76ZUi27cmKEEFtgSH3LdE8n8ZM-t8]]></Tracking><Tracking event=\"collapse\"><![CDATA[http://got.pubnative.net/video/event?t=75tTdpyQxWI238CzxVt5AQI4-_hZNGC4x5RzobU7pz7L2dbUEoD5dEbgzjrjB-qbUOv1Twby0OqvRWRkQM1slgxHbUbSQIzIPmFPcWyuKMlOIYt1FENu0gy8g7kkIzAgaEppFJI9ZzOINMwZ177LwTSHPZddNrO6E6sFNXMecatXXkY93twgnT9C2ZKt31TPHf1xc8Cauf2htY7jm26bqE_re3jZMN-DBfuYLej6Q-qHHjX0L0YCLV81h22l9g-lqKgjk80RdvEc2S4VkQxYPWvjsVC1p_ZTSmusBNelORS4roI5EFYMVjpnDxUDMrP-8y0mh98LaLauXs4x4hYOS0ao9rcntmaGfVKOWe1C5GhQoDwvQ2QClUw3LbEZSLB9dWRcFvymkHP0HtAa7moQPomPK2Sthh4CmXIujG6nLEgGzo6BDVgxZFYCYGI_70krsmXAwATHYI-cWYlDfYzVPCj7KbzPjXQMCBc0O5DZsRJPufoUZB5jzEYDiR-sdlBhKj3pHBbxtKVcQBwmc1T6Rc8yeBz7yFUjC3xmOdZua3dOOU8_pmV8QDB-FNIZhsg2VW0cwI9OEFLS00OOyrZ-wSWDig5dnF58TVlIwd_COHL3ow3fmTDM-CPAxeG2zsA5fR_Q4soawo7Sy3JS1ADGywKajQ4H2NUdkbr_7DeMtyV11124iShUhyM5L2n_r_Lrl_0m4YsRLo97Hemvkpgqq0SBjtsWubiRzXY29mGuO0o989tnEqdRMtR3C6-xLh3RxJsBZ1fgs8y66eq24UaK5cOSaObGjhtZtMrYxljS-Rw4IoqsztQ2ABPXCLkMjWuupHwTJ7-zfsH7pVt1j3MNW0kUzjS9wua89VA7gcJ3383xpJMAOAuYsAMtF9DTYdvQryx0XXmeSVhydJ-LkE4AWSkOmNebqyhRhc6L2Y1cP752JepzzwJKdX3NpqqsriM0Mbx1xo1-zHVvpEEyf5GXohkJseV5CwlEEiU83yPqOXyJUUpILxXRVqnAw1xBBrZxMz_nuuUytEigMKBw8KSvdvyylttJV-u4T49CYMxay9mHMb6fUbq6pYdHeVhuoDjZSVverJfNfQ]]></Tracking><Tracking event=\"acceptInvitation\"><![CDATA[http://got.pubnative.net/video/event?t=iEzfBEXceiqiS_bIrM9TClarXTn3kWvB6C1ReyxL4RjVjd3mMMNjjzmdmIqsCVRZWWRx7dvKvzm0A1oDUSwIit08K1ca_hciC2skbSBYmG2NMgXlS3giDqEdS-UoJ68avBWAcqUS2JXBmirpcK0eBqC1Gm7FYIkNQG8AKnzfu1yKdanvnLwrlh5ekj6c2T-HCNDYxFrjmi32Swi3UkunvLAmxaEJK5nFM4NnRPUireEWP1stqiQi4CkJOpGOPo6E3ZEUrjT_Eb2m60JNU_iUD4hd2OPEV0cZjhDlYll3Fk_DSOC2vIChwxOueWuy_LoaSk6nU8hmgdXl5cb-J3LhpkSountrDBtRxtl6-kdcYvQ_BZvIL1l4SaJI6NDSRJdPF7zF_qKfGwTOtm95vBcUmp3zERwmeRSPyrNlQabaCZKzmHSdhmEM_qQFqSaj9-d-rWd5VSyy97KeR1MrZBABtOWTlUXsuAtwsYu-Svt8UPYOcW51yPx1JOp6umS13HSq-3tMoDyL8dC2TkhPWY78wYIpxyJiSfwHa-1o7TkvKAQKOyNHwje17F812ywjLGveZDX3zW3AJwzm0I-Bj6ArLgXNYet0IHQESvwk5Lo4tQDBT7A4_4Hss8Fh- - -WPcEnUjJmcUpGWnA-xMOJ36GBX2uBljLxG1NH0N3KOuNC54V487996OzKjX3MqlS7pTIzp9J1feaUYN-KSX8MmsVuCFWtAdW45ICqTavwrBpl87IuNQe_KxSJDMgHlaQ4GyjEvv3Is_D6nVs953vZA_uSkm39XqomtYdatxUL02V2J0lrHb7Agx6gaj6yOWyzBfo94PxYNr2V4ffFbjyvV79lcvAGBaYu5ObaCAg3DKxmXlWu1ydoyo9Jsi4pbgvs5nn1lNxy3GKC6p-JR55VG_NtMo4bNtjwaeb6CpidRl2rjxn3oB7X1zV2BqkRRstHtXjSf0AlSlxLnLBtG9eHuLLSq6QpWwYlD4vBxwdU8uQ1vD6FC5X7SCskKUbH8GjQatlGW8qdnUugwUz520TyJCj5ITy4U0gedtt50PSMWhVycyM4wW93uf-ykdUO02FGurIC4HXiMT-xc-IEm2A195-3]]></Tracking><Tracking event=\"close\"><![CDATA[http://got.pubnative.net/video/event?t=tUSv6QlLs7pi2B1NAhnaOscEE_tXjgXQo8yODKrHm3w_8NjaB_6gfmym0KtNIYZkfeFoWKWwF2iSrMlty87ihlPUg5drltZofls2QfiDii3nbAGcBMiJATGxkpRaZL_ttFR5Sw8W5dSnpekVAOzx4Y66yK5GyRGgXSSCSb35eaQQzpWXJSYuiuHJEp9nEctIYRoFS2MG9WDgw3cNP7-jE57du5xEsbWT5ru3Zngw8U_JOg9BtUAG6rlbino7uIdYpJpFiYHxZGcXEnLyse2gup1-Mvmwhy19qWH5aZFhJwyfqKITxf_vGHgXZYJxltLD8whKnNPtke5Q66PshEy3h3GSFjVhz5Kb2pa2vU9EFmhrKEQmOJ8XlMR_dHRi16qz4_b5P9Nw2pbsjc7slWHdybsaTfMeaKmiQsYDtq61VnX8B_oass5YWf7RS1QilrpqWRo68i2KQPGAvW_DefbllXkO_pLTp8KzXtl0GA1qzmqvf-8DodG3gza0i5Jf-_4l0Mrj8ItCeeX3ESuB7Eksp91FSyXiLoI7DOySzDgYo7ly5YYToBHa405KVK4qknHGa5VOUaZc-THpSE4pG-oW-l0PuzEducbUIU4zGODR_D8R0UzasO-FUsyuo5cj1aQdEyp7M7rBMdIlh_2mIZAHPOv4e4dS2AjR4FKSp9X-dnno6oiT9h5BhPWKXtStOh2mt3V_t2UhzAu2OQjmVztXBmXtRoFqiT7eqGrUOQtdgP5B4bBV2aT0kX_VJz_2askVfLNC-UU74qwFb5i6gAbb5JZvfJDiF3LShlzG25SQoZpPlTiuX3gZF3f3QBWIkvz-uijuPx9Fj6eySd8ElmlSomqgg0Re2IOvT2YsWSmy2HWIfMBygM9q60Y8XaugG5iK8mxY3d9qvcPxm6pqwHgIUG1Eaf3IJkVZFRQyyMLKAqfNfobsi0VAnM3pcfbUK6bH9ur54ftSTPM0jXEIRzjuSoAVW08z-HmrI1LfFm6n9IRmhyNYgxeGoK-XT3jmDOcTbTQde95luo0Tag-FdlY7I1uOYdZZF8lgn0tuUu5iByQVm5BQOD9soh67yRLzbnvR-XLE6A]]></Tracking></TrackingEvents><VideoClicks><ClickThrough><![CDATA[https://pubnative.net]]></ClickThrough><ClickTracking><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/clickTracking]]></ClickTracking><ClickTracking><![CDATA[http://backend.asia-northeast1gcp0.pubnative.net/mockdsp/v1/tracker/clickTracking2]]></ClickTracking><ClickTracking><![CDATA[http://got.pubnative.net/click/rtb?aid=1038058&t=MiO0U7Gx0gG6QClnK6a1c64cTncwyY70K4vV3UkHx11uTUoLSc_omCVKxd98L2AZzgOIIQJ04ZpbcjgB07WyHHR-izYWXcWFK4P3-DVMout3auAkNrH_hakSZGWYR6x0DTQViD7HkNBzi7ra-XlFvlaTG16ce22DHdZnmrl5SsyxkRBsvDrNzeqecLDukiIZmeeqKQ_TDrAMc53wK72aYsbEHvVcWJxFcq40leGuLpbgKTJaCRLzAsBUMsH2N2Q8uWkK6oxUhnzhL7ts-ke3eR9pU8gLjVDyG7ay06kHjH2Nn0cdMSqEzpknBPNeHdYcSabwOkHevMRtmIuXgduhlIAsHxQr8R9ObFbc2e7SD7CMrvHFh2uqn-lNw13LFo_24NuFyDSaRyjxaHkY3rq24x7o82caGQbTfOGX5M29JWgozsVBB_JQEsJi-h4xDmCxKDty969gqxyjx3CFm-MYtSXfcwyR7-8j6q233shWoKD1VHKxpGzGyGLhaCg_JoocqJ0HD6OJwWCKCTww8RE6Ume0lxOXDxNHbYdIL5bYq9V_eBoT5lXJDtxHl2wZvjoznpuJgBJgbSlE3xII4B4oC72EYaLVqJIfLaJvfBV6ZoUE6_KSFFxxsE8oOJpPwcvm0QzjYmN2Mm6FejG-LOPw6zRGw6eYy0fGML6TzBsmTX4l0LbSeDlmu-edggvrooQdliz4guaCpCaxKhxCwMKJ0e12cUkCSe1zinpo2yXXGKQrIhS_qZOK5KyqOoOz0nmiLEENJkZYIc9TB9u17AfCYYd87NnZi4z0kyU]]></ClickTracking></VideoClicks><MediaFiles><MediaFile id=\"1\" delivery=\"progressive\" type=\"video/mp4\" bitrate=\"457\" width=\"1280\" height=\"720\"><![CDATA[http://pubnative-assets.s3.amazonaws.com/static/PNVideoMockup.mp4]]></MediaFile></MediaFiles></Linear></Creative></Creatives></InLine></Ad></VAST>",
          "adomain": [
            "pubnativetestad.com"
          ],
          "cid": "10993",
          "crid": "4342184916255",
          "attr": [
            4
          ]
        }
      ]
    }
  ],
  "cur": "USD"
}
```

## 7\. Sample Device Response

```json Sample Device Object
"device": {
    "dnt": 2,
    "ua": "Mozilla/5.0 (iPhone; CPU iPhone OS 8_1_2 like Mac OS X) AppleWebKit/600.1.4 (KHTML, like Gecko) Version/8.0 Mobile/12B440 Safari/600.1.4",
    "ip": "8.8.8.8",
    "geo": {
        "lat": 0,
        "lon": 0,
        "country": "USA",
        "region": "CA",
        "city": "Mountain View",
        "zip": "94040",
        "type": 2 // 1- GPS, 2- IP address
    },
    "carrier": "Google",
    "language": "en",
    "make": "Apple",
    "model": "iphone",
    "os": "iOS",
    "osv": "8",
    "connectiontype": 2, // 0 -Unknown, 1- Ethernet, 2 - WIFI, 3 -Cellular Network – Unknown Generation
    "devicetype": 1, // 1 - Mobile/Tablet
    "ifa": "1E2DFA89-47FD-9941-DF1FC4E6484C",
    "ext": {
        "airplane": 0,
        "batterylevel": 8, // 100-85% = 8 , 84-70% = 7, 69-55% = 6, 54-40% = 5, 39-25% = 4, 21-10% = 3, 9-5% = 2, < 5% = 1  
        "batterysaver": 1,
        "bluetooth": 1,
        "charging": 0,
        "darkmode": 0,
        "dnd": 0, // 0- Do Not Disturb disabled, 1- Do Not Disturb enabled
        "headset": 0, //0- No headset connected, 1- Headset connected
        "inputLanguage": [
            "en"
        ],
        "ringmute": 0, // 0- Mute, 1- Ring
        "diskspace": 1821, //MB of data
        "totaldisk": 128000 //MB of data
    }
},
```

> 🚧 CHECKLIST BEFORE GOING LIVE
> 
> 1. Are you using the <APP-TOKEN> of your account?
> 2. Are you requesting the ad format you need? (NATIVE/STANDARD/VIDEO)
> 3. Are you replacing {AUCTION_PRICE} in the bid response when serving the ad?

## SKAdNetwork

# Register your Ad Network with Apple ([link](https://developer.apple.com/documentation/storekit/skadnetwork/registering_an_ad_network))

# Add support for processing parameters for Contextual App Targeting ([link](https://developers.verve.com/docs/contextual-app-targeting))

Find the parameters to send in your bid response on our [SKAdNewtwork documentation page](https://developers.verve.com/docs/ios14-and-skadnetwork#section-if-you-re-a-demand-partner-dsp-).

## Get Started

To get started or to receive more information, contact us at [hello@verve.com](mailto:hello@verve.com)

## Version History

| Version | Changes                            |
| :------ | :--------------------------------- |
| 1.0     | Onboarding Process                 |
| 1.1     | Support for Standard Formats       |
| 1.2     | Update for sizes and spec details. |