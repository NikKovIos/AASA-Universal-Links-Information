# AASA-Universal-Links-Information
All interesting hidden and not information about iOS deeplinks (universal links).

## Apple documentation:

- https://developer.apple.com/videos/play/wwdc2020/10098
- https://developer.apple.com/documentation/xcode/supporting-universal-links-in-your-app
- https://developer.apple.com/documentation/xcode/supporting-associated-domains
- https://developer.apple.com/documentation/bundleresources/applinks
- https://developer.apple.com/library/archive/documentation/General/Conceptual/AppSearch/UniversalLinks.html
- https://developer.apple.com/documentation/uikit/uiapplication/1648685-open
- https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623072-application
- https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_developer_associated-domains

## Test links:

To see AASA file on apple CDN:
https://app-site-association.cdn-apple.com/a/v1/YOURDOMAIN

To see AASA file on your site:
https://YOURDOMAINcom/.well-known/apple-app-site-association

## Developer mode:

https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_developer_associated-domains  
In macOS 11 and later and iOS 14 and later, apps request apple-app-site-association files from an Apple-managed content delivery network (CDN) specifically for associated domains, instead of directly from your web server. If the CDN has an old version of the file, or doesn’t already have a copy of the file, it connects to your web server to obtain the latest version.

About refreshing AASA file on apple CDN:
https://developer.apple.com/forums/thread/699401

CDN will cache approximely once a day new AASA file.   
If you trigger a sysdiagnose, in the swcutil_show.txt file you can look for your domain and find information about when the "last check" was, and when the next check will be.  
If you are iterating at a fast pace, you can use developer mode, and directly pull the AASA from your web server.  
To trigger a download you still need to delete the app and reinstall via Xcode (TF and App Store do not work for developer mode.)  

To enable Developer mode:

1)`applinks:mydomain.com?mode=developer` in entitlements. 
2) Enable setting on your device. Xcode -> Signing and.. -> Associated Domains Development.

## NOT word:

Nice question and answer https://stackoverflow.com/q/58217784/5790492

## Various

https://stackoverflow.com/a/44685218/5790492  
You are correct that the apple-app-site-association file is downloaded when the app is installed. It will be re-downloaded for updates through the App Store, which means to add new paths and ensure all users have them, you generally need to release an app update.

## Often Errors

Check that your AASA file is valid:
1) Use new apple format. `"/": ""`. "components" instead "path" and so on;
2) Validate JSON. It can be that you forget to remove comma or quotation mark;
3) Check the `"apps": []` exists;
4) Check that apple cashed your new version on CDN. Otherwise use developer mode;
5) Reinstall app or update it. AASA downloaded this time;

## Examples from big services

- https://www.ebay.co.uk/.well-known/apple-app-site-association
- https://www.kinopoisk.ru/.well-known/apple-app-site-association

## JSON and AASA Validators

- https://yurl.chayev.com/
- https://jsonlint.com/

## Example

Here is the example of AASA file where root links not opens. This is new format of AASA. With old format file didn't work and didn't refirect me.

```json
{
    "applinks": {
        "apps": [

        ],
        "details": [{
            "appIDs": [
                "XXXXXXXXXX.com.bundleId",
                "YYYYYYYYYY.com.bundleId"
            ],
            "components": [
                {
                    "/": "/test/*"
                },
                {
                    "/": "/*/type/criteria/*"
                },
                {
                    "/": "/*/news/*"
                },
                {
                    "/": "/*/some/details/*"
                },
                {
                    "/": "/*/sales/*/view/*"
                },
                {
                    "/": "/*",
                    "exclude": true
                }
            ]
        }]
    }
}
```

