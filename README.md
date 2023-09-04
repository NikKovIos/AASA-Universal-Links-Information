# AASA-Universal-Links-Information
All interesting hidden and not information about iOS deeplinks (universal links).

## Apple documentation:

https://developer.apple.com/videos/play/wwdc2020/10098
https://developer.apple.com/documentation/xcode/supporting-associated-domains
https://developer.apple.com/documentation/bundleresources/applinks
https://developer.apple.com/library/archive/documentation/General/Conceptual/AppSearch/UniversalLinks.html

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

Developer mode example: `applinks:mydomain.com?mode=developer`

---



