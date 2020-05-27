---
description: >-
  Below you will find a listing of the recent changes we have made to Web
  Components. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# Web Components

### web-components_v0.0.6 - 2020-05-18
  
Release: web-components_v0.0.6
Rollback: web-components_v0.0.5
Changes:
commit | author |description
  
- 4f336dcda2f9565c057a376f4bda49b60dd6472e | NghiaPham <nghiapn@reapit.com> | feat: #1107 web components should be deployed to NPM (#1179)
- 5033678d1d9efcf572af3499580c79a1d8b0d34a | Cuong Vu <cuongvh@reapit.com> | fix: fix web component cors headers (#1251)
- 63ae65d6ef2f18f2d5c3fe52915c711447b7eebc | Pham Hai Duong <duongph@reapit.com> | fix: #1145 minor fix for Y axis's legend of bar chart and change to netAmount instead of grossAmount (#1216)Resolve #1145Changes- Minor fix for bar chart Y legend- Change grossAmount to netAmount- Fix test
- be44eaf818a96e3f14af69b74e60369e68953353 | Khac Vy <vytk@reapit.com> | feat: create property-detail widget (#1182)* feat: create property-detail widget
- 71913c79f734735981313d27ebb470153faafeac | Trường An <andt@reapit.com> | fix: #1138 Search widget is not returning results on Demo Site (#1184)
- 403e4cf9bd73dff04adbc167e5a378b3f9203399 | Khac Vy <vytk@reapit.com> | feat: #1150 Served web component themes over CDN (#1158)
- 80af469115b0b2a8bf13a5495a4cb58fe69caae6 | Cuong Vu <cuongvh@reapit.com> | feat: #1106 web component config update (#1157)* feat: #1106 Web components update config* feat: #1106 Fixing customerId not included
- 991ee1e474f0ae622a16cc1060e6260da0de1db7 | Khac Vy <vytk@reapit.com> | chore: update search form (#1155)
- d856abc588f74e57e47aa1563b00321c4d805dae | Khac Vy <vytk@reapit.com> | feat: #1086 Property detail page (#1149)* feat: #1086 Property detail page
- d076b3d062653f95e7e82b6d8bb04a785396a6b5 | NghiaPham <nghiapn@reapit.com> | fix #1052: both select appointment on demo-site opens books a valuation (#1137)
- 0fad21d6bc05d78b2ab81cac69d000877d22406c | Khac Vy <vytk@reapit.com> | chore: Hide loader after search in search widget (#1114)
- c429b1f8c86912b81b9b7668e7d1e848b0a2b3b3 | Cuong Vu <cuongvh@reapit.com> | fix: #1046 update form step 1 book a valuation (#1099)
- f6d395afc5f1476e09d4c33761fe347ec1872859 | NghiaPham <nghiapn@reapit.com> | fix: #693 - increase webhooks page dropdown size, and load developer apps data (#1095)
- 6696946edd49c0c01afc0415361c22f7147028a3 | Khac Vy <vytk@reapit.com> | chore: #1085 update search widget query (#1094)* chore: #1039 Update search widget: result message, placeholder and enter button
- fd52c8520f1d8765c727edd4f041da1335408295 | Pham Hai Duong <duongph@reapit.com> | feat: #1068 updatecalculation total cost table in term and condition (#1080)* feat: #1068 updatecalculation total cost table in term and condition* chore: set up test for web-components
- 16c92eb246e4c2500fd5fe374bec149d79448e7a | Pham Hai Duong <duongph@reapit.com> | feat: #1009 serverless deployment for cloud apps (#1061)Changes- Clone serverless.yml for cloud apps
- 81769360e3a76575594ea15f980199aa893fc38f | Vu Nguyen <vunp@reapit.com> | fix: Appointment booking modal styles (#1004)* fix: appointment booking modal styles* Update snapshot testing for appointment booking
- 55aed3488e24b68f849be67fa23c3490869376e6 | Khac Vy <vytk@reapit.com> | feat: #904 Search properties filter form (#942)* feat: #904 Search properties filter form
- 341ef126b59fb1cd784c0f64820b2eca60e41897 | Vu Nguyen <vunp@reapit.com> | Feat: #938 render appointment booking widgets in demo site (#958)* feat: #938: Add appointment booking to search widget
- 6319406aa6db5c219bbe2fe3876496be7ae3774f | Pham Hai Duong <duongph@reapit.com> | Fix: serverless headers when request go through authorizer (#961)Changes-Add parse headers for requestContext-Parse headers to correct one
- 261ac7ccf3d063d81c481bcb32f32b687447a830 | Trường An <truongan106@gmail.com> | fix: revert web-component common modal (#960)* feat: #781 I want to click button to arrange a viewing with Estate Agent* chore: #781 update style* chore: add some test* chore: #781 update theme class* chore: #781 update styles* fix: revert common modal web-componentCo-authored-by: andt <andt@dwarvesv.com>
- 629fb15861d4d28fc52777c18e025a8bc22c7e66 | Trường An <truongan106@gmail.com> | feat: #781 Book a viewing (#931)* feat: #781 I want to click button to arrange a viewing with Estate Agent* chore: #781 update style* chore: add some test* chore: #781 update theme class* chore: #781 update stylesCo-authored-by: andt <andt@dwarvesv.com>
- 3e7b260760cd8a727704b3b992da173dcaab558d | Pham Hai Duong <duongph@reapit.com> | chore: revert back to correct bucket of web-components (#948)
- 0d035775630344bb7bc3f6109699bd60b505d241 | Pham Hai Duong <duongph@reapit.com> | chore: add env SLS_DEBUG for serverless debugging (#947)* chore: add logger for searchwidget api to '*'* chore: fix change deployment bucket to new one for web-components
- e0d7696e4be8468c968bb71bb33c205537add395 | Pham Hai Duong <duongph@reapit.com> | chore: add logger for searchwidget api (#944)
- 95ff51b66c5681821335a75ef8e7295a8a572e3f | NghiaPham <nghiapn@reapit.com> | feat: #863 - lightbox component for search widget (#937)
- 1e001c235eed9b72a2184d6836fab67d6166cf22 | Pham Hai Duong <duongph@reapit.com> | chore: deploy search widget behind gateway (#936)
- bd47ff94d45ae196d6ca7c11c99f82cf4fd7e007 | Pham Hai Duong <duongph@reapit.com> | fix: deploy behind api gateway for demo-site (#927)
- c23aa2776ebc744e7108265fc11a340c9ba55c0e | Pham Hai Duong <duongph@reapit.com> | fix: serverless deploy behind gateway for web-components (#925)
- 9a434f7a21157b7faaafc9692409c7c01abe40f2 | Pham Hai Duong <duongph@reapit.com> | fix: add api-version to earch widget components headers (#919)
- 5eb042a1cc3af4b5e5f296fb4aff8cdcba28876d | Pham Hai Duong <duongph@reapit.com> | fix: deploy pipeline release prod for web-components (#906)
- f782a08a791651459fb35bbd4e96216ea0c2f619 | Vu Nguyen <vunp@reapit.com> | Feat 631 create an interactive planner component (#899)* feat: #634:Appointment confirmation form

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

### web-components_v0.0.5 - 2020-04-14
  
Release: web-components_v0.0.5
Rollback: web-components_v0.0.4
Changes:
commit | author |description
  
- 985ca60248fe24245b1e9127d4b9db2793b02a6f | Pham Hai Duong <duongph@reapit.com> | chore: bump version for demo site and search widget (#898)
- b069775bb9138e362e3cd756340e9bd0fdd48428 | Pham Hai Duong <duongph@reapit.com> | feat: #864 pagination for search widget (#887)feat: #864 pagination for search widget (#887)
- 72144c0f785fad25b62670e3bcbf688349ba48f2 | Will McVay <wmcvay@reapit.com> | feat: map slider (#891)* feat: wip* feat: google maps slider complete

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
    
### web-components_v0.0.4 - 2020-04-13
  
Release: web-components_v0.0.4
Rollback: web-components_v0.0.4
Changes:
commit | author |description
  

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
    
