# AASA-Universal-Links-Information
All interesting hidden and not information about iOS deeplinks (universal links).

## Apple documentation:

https://developer.apple.com/videos/play/wwdc2020/10098
https://developer.apple.com/documentation/xcode/supporting-universal-links-in-your-app
https://developer.apple.com/documentation/xcode/supporting-associated-domains
https://developer.apple.com/documentation/bundleresources/applinks
https://developer.apple.com/library/archive/documentation/General/Conceptual/AppSearch/UniversalLinks.html
https://developer.apple.com/documentation/uikit/uiapplication/1648685-open
https://developer.apple.com/documentation/uikit/uiapplicationdelegate/1623072-application
https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_developer_associated-domains

## Test links:

To see AASA file on apple CDN:
https://app-site-association.cdn-apple.com/a/v1/YOURDOMAIN

To see AASA file on your site:
https://YOURDOMAINcom/.well-known/apple-app-site-association

## Developer mode:

About refreshing AASA file on apple CDN:
https://developer.apple.com/forums/thread/699401

The system will check approximately once a week for an updated AASA. Other sources tell - ones a day.  
If you trigger a sysdiagnose, in the swcutil_show.txt file you can look for your domain and find information about when the "last check" was, and when the next check will be.  
If you are iterating at a fast pace, you can use developer mode, and directly pull the AASA from your web server.  
To trigger a download you still need to delete the app and reinstall via Xcode (TF and App Store do not work for developer mode.)  

Developer mode example: `applinks:mydomain.com?mode=developer` in entitlements. Xcode -> Signing and.. -> Associated Domains.

Make sure you enable Associated Domains Development on Developer menu in iOS Settings.


https://developer.apple.com/documentation/bundleresources/entitlements/com_apple_developer_associated-domains  
In macOS 11 and later and iOS 14 and later, apps request apple-app-site-association files from an Apple-managed content delivery network (CDN) specifically for associated domains, instead of directly from your web server. If the CDN has an old version of the file, or doesn’t already have a copy of the file, it connects to your web server to obtain the latest version.

## NOT word:

Nice question and answer https://stackoverflow.com/q/58217784/5790492



