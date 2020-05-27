---
description: >-
  Below you will find a listing of the recent changes we have made to
  Marketplace. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# Marketplace

### marketplace_v1.0.21 - 2020-04-15
  
Release: marketplace_v1.0.21
Rollback: marketplace_v1.0.20
Changes:
commit | author |description
  
- d14b33d755b1d8a56d225f1a0a6c0cdc87f1c4e8 | Vu Nguyen <vunp@reapit.com> | Fix/905 update date filtering in analytics page (#914)* feat: #905: Update date filtering in analytics page
- e9c804b5b5352a5ca3605f1e02eb83a98f23eec5 | Vu Nguyen <vunp@reapit.com> | feat: #908 - Fix analytics page filter issues (#913)
- 1eca438da329598593bed4755eb18c448c606deb | Khac Vy <vytk@reapit.com> | feat: #830 submit app with desktop integration types (#895)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

### marketplace_v1.0.20 - 2020-04-14
  
Release: marketplace_v1.0.20
Rollback: marketplace_v1.0.19
Changes:
commit | author |description
  
- c46b2f0dea3da7e6dc69667de1680fede5379f15 | Will McVay <wmcvay@reapit.com> | fix: t and c update (#907)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

### marketplace_v1.0.19 - 2020-04-14
  
Release: marketplace_v1.0.19
Rollback: marketplace_v1.0.18
Changes:
commit | author |description
  
- f9c18b620fd39f9bcef20656f9ffc1aa15c6d48b | NghiaPham <nghiapn@reapit.com> | fix: #902 Issue with text on after registering as a Developer (#903)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
    
### marketplace_v1.0.18 - 2020-04-14
  
Release: marketplace_v1.0.18
Rollback: marketplace_v1.0.17
Changes:
commit | author |description
  
- 75725d886427d0ce17aac4674724c9d60fe7a8f6 | Cuong Vu <cuongvh@reapit.com> | chore: #889 markerplace login button is misaligned (#894)
- 0cc5a75de47265219216ced6c425357be0faadd1 | NghiaPham <nghiapn@reapit.com> | fix: #792 remove developer term and condition from private-router-wrapper (#897)
- 63a04c134a7ee04c726dceee7e435e765eff7334 | Cuong Vu <cuongvh@reapit.com> | chore: #883 remove text from submit & edit form (#885)
- 10ab176102e609f7e63b0a33d937f8d9ff6bd8e5 | Trường An <duongtruongan@outlook.com> | fix: #732 Filtering should apply to all apps not just those on curr page (#882)Co-authored-by: andt <andt@dwarvesv.com>
- bdf01a134a3aad4c3eb97088b3050d003965d30c | NghiaPham <nghiapn@reapit.com> | fix: #792 update snapshot (#880)
- 9414fe4d4918751e10975d8dc11aa7d51093f509 | NghiaPham <nghiapn@reapit.com> | feat: #792 terms and conditions acceptance should be confirmed by developer API (#874)feat: #792 terms and conditions acceptance should be confirmed by developer API
- 1e494987f890526232bfa53a52cb2f36c739fa84 | Will McVay <wmcvay@reapit.com> | fix: adds sandbox as filter to analytics (#878)
- bb0df0a0a145573feb9aebbd8e1fea4c5920ca7e | Khac Vy <vytk@reapit.com> | feat: #849 link valid foundations-doc url via the iframe (#860)* feat: #849 link valid foundations-doc url via the iframe
- 60de4013a36bf0fdc528b990eb5b6c106f64320d | Vu Nguyen <vunp@reapit.com> | Fix: #840 updates required to analytics tab (#861)* feat: #840: Updates required to analytics tab
- c2beee62eda02b3e16eab41cdaf195ab17cb5b9a | Will McVay <wmcvay@reapit.com> | feat: add question template (#857)* feat: add question template* feat: enforce template* feat: enforces templates, updates template links
- 66c5d08b69f9d9b057dec1aa5a4c35bf682f9c35 | Vu Nguyen <vunp@reapit.com> | feat: #838: Fix private apps validation (#839)
- ef2f7f2eadd6f6923d45edc2ce2b5616a57c8c1d | Vu Nguyen <vunp@reapit.com> | Feat #712 + #711 : Developer can see a list of enpoints and a graph showing my ‘Hits per Day’ (#836)* mock redux* mock redux* feat: #712: Add traffic event table component* feat: #712: Upgrade react-table to stable version - Add Footer for table element* fixing typescript* feat: #712: Update developer endpoint list + chart* feat: #712: Fix typo issues* feat: #712: Fix linting issues* feat: #712: Fix linting issues* feat: #712: Update snapshot testCo-authored-by: nhalx <nhalx@reapit.com>
- 127de142361e4490dfd750c64992566832eec8aa | Vu Nguyen <vunp@reapit.com> | Feat/755 developers can specify who can see their apps (#832)* feat: #755: Fix private app title typo
- c382ab36061ebc22223bae497da7cb053b9e85e9 | Vu Nguyen <vunp@reapit.com> | Feat/755 developers can specify who can see their apps (#827)* feat: #755: Add private apps section to submit app form* feat: #755: Devs can specify who can see their apps* feat: #755: Update snapshot testing* feat: #755: Reword the validation - Fix submit app issues with whitespaces
- dfbdf4b5590d3b3387c7caa108536f5e0550d9f9 | Pham Hai Duong <duongph@reapit.com> | feat: #741 integrate api for view api key when app installed (#824)Changes- Add fetchApiKey for installtion apps- Add test for fetchApiKey sagas
- 7788e9539ac58a936f38db74a13bcb37102f31c6 | Khac Vy <vytk@reapit.com> | feat: #745 Add Settings menu for client (#793)
- b424747713096bb293a257d7ce40749f12f15beb | Pham Hai Duong <duongph@reapit.com> | feat: #741 ui for view api key of web componentts (#813)Changes- UI for view api key of web components and tests
- f6501109cefc3140f2f928747990dd1e420d00a3 | Vu Nguyen <vunp@reapit.com> | Feat/755 developers can specify who can see their apps (#808)* feat: #755: Add private apps section to submit app form* feat: #755: Devs can specify who can see their apps* feat: #755: Update snapshot testing
- 490f0b13c8e6200cd7ba98810f15af74c6372e3b | Cuong Vu <cuongvh@reapit.com> | fix: #739 cannot assign to readonly window.__REAPIT_MARKETPLACE_GLOBALS__ (#800)
- 8d3bd81c139e1a7f5e3e903f182faf1d156e54c5 | Cuong Vu <cuongvh@reapit.com> | feat: #739 The Cloud Apps should be testable in "Desktop Mode" (#784)* feat: #739 cloud apps now testable in desktop mode
- f229847a63f34993c3c1e6b1c134b97cb3f0ca87 | Vu Nguyen <vunp@reapit.com> | Feat: #725 developer can filter detailed page to customize results (#777)* feat: #725: Refactor detailed tab* feat: #725: Update analytics filter form* feat: #725: Update analytics page to use react redux hooks* feat: #725: Update detail tab test* feat: #725: Update test for filter bar + filter form* feat: #725: Pump elements version* feat: #725: Fix lint error* feat: #725: Fix naming convention
- f8cbc43b89b90594fb3c0a9b5f3c7b452e29500f | Cuong Vu <cuongvh@reapit.com> | fix: #701 use window.location.href instead of navigateDynamicApp (#763)
- 5037c84ce5c2ee3d1aecbc3be37a146366086dc9 | Cuong Vu <cuongvh@reapit.com> | fix: #701 refresh link incorrect, add param in navigateDynamicApp (#758)
- b91719552a2da0fc5e69e2be92fc895ffa0dbef2 | Cuong Vu <cuongvh@reapit.com> | feat: #652 Upload CSV should validate before submit (#750)* feat: #652 upload CSV should validate before submit
- 05f0e8d0898d6e7142b0acf3ffe925aa74bf57c0 | Vu Nguyen <vunp@reapit.com> | feat: #710: Add additional tab option on analytics page (#748)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
