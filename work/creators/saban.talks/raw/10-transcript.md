# saban.talks · post 10 · WINNER

```
date        9 Aug 2026
engagement  3,227
outlier     2.25x  against a median of 1,432
maturity    settled
```

source      https://www.instagram.com/p/Db02G_svmNr/
frames      work/creators/saban.talks/raw/frames/post-10/
collected   Day 26, 31 Aug 2026 · by hand, via the Reel Intake artifact (Copy-everything export)

---

## FULL CAPTION

```
Ever noticed an app's UI changing without downloading an update from the App Store? It isn't always because of OTA. 👀

Sometimes it's Remote Config, sometimes Server-Driven UI, and in React Native apps, compatible JavaScript and assets can be delivered through OTA updates.

React Native OTA doesn't replace the entire app. It downloads, verifies, and caches a new bundle. On the next reload, the existing native runtime runs that bundle.

But if you change Kotlin, Swift, native SDKs, permissions, manifests, or entitlements, you need a new store build.

Save this reel for your next mobile-development interview or app release—and share it with a fellow app developer. 📱
```

## TRANSCRIPT

तो यह सोचा है तुम्हारे Netflix, Blinkit, Instagram जैसे apps पर बिना update किये UI change कैसे हो जाता है? अगर तुम खुद का mobile app wipe code करने जा रहे हो, तो कैसे बिना app review करवाए अपने changes user के device पर push कर सकते हो? तो बहुत सारे तरीकों मेंसे एक तरीका होता है OTA updates. OTA का मतलब होता है over the air. तो OTA updates के थ्रू ही तुम्हारे app के UI changes बिना update करे हो जाते हैं. For example, तुमने सुना होगा कि लोग React Native में app बनाते हैं उसके दो लेयर्स होते हैं एक तो तुम्हारा जावास्क्रिप्ट लेयर और एक होती है नीचे की लेयर देट इस बाइनरी लेयर जहां पे तुम परमिशन्स एक्सेस करते हो जो नेटिव लाइब्रेरी होती हैं वो एक्सेस करते हो अब जो तुम्हारी टॉप लेयर है जावास्क्रिप्ट बंडल्स या एसेट जो तुम्हारे फॉन्ट्स है इमेजेज है स्टाइलिंग है वो सारी चीज़े तुम पुश कर सकते हो OTA के थ्रू

मान लो तुम्हारे ऐप में कोई एक बटन था जिस पर क्लिक करने पर दूसरी स्क्रीन खुलनी चाहिए थी पर वह वर्क नहीं कर रहा है तो तुम उसको OTA अपडेट के थ्रू बग फिक्स करा सकते हो। अगर वही बटन इंटरैक्ट कर रहा होता है नेटिव चीजों से — फॉर एक्जांपल वह बटन क्लिक करने पर तुम्हारा कैमरा खुलना चाहिए था बट कैमरा नहीं खुल रहा है, या फिर उस बटन पर क्लिक करके तुम्हारा ऑडियो रिकॉर्ड होना चाहिए — तो उसके लिए तुम्हें एक नया build बनाना पड़ता है जिसको app store review करता है।

ये OTA update कैसे काम करता है: मान लो किसी developer ने कोई fix निकाला और OTA update publish किया तो server पर नया javascript bundle बनता है, manifest file बनती है, और जब user वो app अपने phone पर launch करता है उसी टाइम पर server से check होता है manifest file और जो नया javascript update file है bundle file है वो download हो जाता है, cache में locally verify हो जाता है, next time जब वो app reboot होता है तो नया update user को show हो जाता है।

और भी तरीके होते हैं app पे updates push करने के — जैसे server driven UI होता है, feature flagging होती है, remote configs होते हैं जिसके through updates push करे जा सकते हैं। तो तुम्हारे दिमाग में खुराफाती idea है कि मैं पूरा का पूरा app ही क्यों ना OTA update करा दूँ — but please avoid that, क्योंकि अगर तुमने कुछ गलत bug वगेरा push कर दिया OTA update में तो वो next time तुम्हारा user जब भी app खोलने वाला है तो सब affect होने वाले हैं। तो only try to ship small bugs and fixes जो बहुत important है over the air updates में।

इस वीडियो को save कर लो future के लिए और अपने दोस्त के साथ भी share कर दो। page को follow नहीं किया है तो ऐसी ही वीडियो के लिए page को follow कर लो। I'll see you in the next one.
