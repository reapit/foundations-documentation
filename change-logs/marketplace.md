---
description: >-
  Below you will find a listing of the recent changes we have made to
  Marketplace. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# Marketplace
### marketplace_v1.0.24 - 2020-05-22
  
Release: marketplace_v1.0.24
Rollback: marketplace_v1.0.24
Changes:
commit | author |description

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

### marketplace_v1.0.23 - 2020-05-22
  
Release: marketplace_v1.0.23
Rollback: marketplace_v1.0.22
Changes:
commit | author |description
  
- 3d0fea7176d4e2993965192db6cff75f440af973 | Vu Nguyen <nphivu414@gmail.com> | refactor: #1174 Refactor register page using new react-redux hooks (#1314)* feat: #1174 Refactor register page to use new react-redux hooks
- a7122b92a0936b5d48291e9284dc64c54924c20d | NghiaPham <nghiapn@reapit.com> | feat: #1210 #1026 ui for developer/client side standalone (#1304)
- 394f5f26073eeb0f5c58c843c02c18ac11af0d47 | Khac Vy <vytk@reapit.com> | fix: #1292 fix Toast should be full width in desktop mode (#1306)
- 497b5eb924943859b3bde6db9cc15ebd64e4528f | Vu Nguyen <nphivu414@gmail.com> | fix: #1290 Update login link in case clientId is existed (#1312)* feat: #1290 Update login route in register page when clientId is existed
- 478179cd87d21b9f2e6339e4f1e54397b705be27 | Vu Nguyen <nphivu414@gmail.com> | fix: #1300 Update text and links on developer webhooks page (#1311)* feat: #1300 Update text and links on developer webhooks page
- a35834aa73d5c92490913a73acc56960ab43f6a2 | Vu Nguyen <nphivu414@gmail.com> | feat: #1290 Fix issues with logging into dev and client portal (#1301)
- e47980631cb27489a920c4e1715b87fe6203106f | Vu Nguyen <nphivu414@gmail.com> | fix: #1300 Update text and links on developer webhooks page (#1302)* feat: #1300 Update text and links on developer webhooks page* feat: #1300 Fix lint errors
- 725f31eb4314f7380086f410257a94c8ce5e130c | Vu Nguyen <nphivu414@gmail.com> | feat: #1174 Refactor login page to use useSelector instead of mapStateToProps (#1293)* feat: #1174 Refactor login page to use useSelector instead of mapStateToProps
- 35b0cede2867318b0f72f64e78e64f7a212688ff | NghiaPham <nghiapn@reapit.com> | fix: #1225 ui for mobile client side app (#1271)
- 13ce3e5760d5efc56df85af0d1ab3823c157b410 | Vu Nguyen <nphivu414@gmail.com> | feat: #101 Developers should be directed to information if trying to access the marketplace without a client Id (#1270)* feat: #101 Developers should be directed to information if trying to access the marketplace without a client Id* feat: #99 As a ‘Client’, I want to use my existing email address to also register as a ‘Developer’ so that I can use the same email address
- cc171c88234195b5c1694bb151aa72c4ed83e2c8 | Trường An <andt@reapit.com> | chore: #1012 hide install app button in app detail standalone page (#1280)
- db13c2d88903a5a4c359c3b8be0d688d242b03aa | Cuong Vu <cuongvh@reapit.com> | fix: #1276 fix type definitions in ErrorBoundary (#1285)
- dacb9af3ccf53658daa42a610394c73914867523 | Khac Vy <vytk@reapit.com> | chore: #1277 Update wording on the Webhooks page in the Developers Portal (#1279)
- 7d6f7574ad5c267afc7d87170e2d46730bfacc88 | Trường An <andt@reapit.com> | chore: bump cognito-auth 2.1.5 (#1281)
- bb22c7a21766c1d13c308433a0529e693a6c1ad3 | Pham Hai Duong <duongph@reapit.com> | feat: #1221 add cloud alert for production env web apps (#1273)
- 8c4c54632eb5a2057f6ad06bdc85abc30f240f18 | Cuong Vu <cuongvh@reapit.com> | refactor: #1173 Step 1 - Move API calls to services folders (#1265)
- f8e1c37affcd2d4cf688c937bad3572745e4a5d5 | Trường An <andt@reapit.com> | feat: #1118 Client should see permission appropriate welcome on 1stlogin (#1269)
- 0faa38e441e4e81e7728d0e47a22b7deb690e09e | Trường An <andt@reapit.com> | feat: #1012 Client without admin permissions should not install app (#1268)* feat: #1012 Client without admin permissions should not install app* chore: #1012 update variable name
- 73296981d70de416f5eb9b49c9901fda0befaf83 | Trường An <andt@reapit.com> | feat: #1011 As a client who is not an admin, I should not see certain tabs in the marketplace (#1261)* feat: #1262 Get the current user logged in phone number
- 1ffdc6c79895aaf95763f3bbc94a768da7ddbd82 | Khac Vy <vytk@reapit.com> | chore: #1223 Update T&C developer register (#1255)
- d06476c459131910d2d89c122c9ae1da211db4f0 | Khac Vy <vytk@reapit.com> | feat: #1248 Remove submit app menu item. Create new app button in my … (#1253)* feat: #1248 Remove submit app menu item. Create new app button in my apps page
- b6cba8e8da7886b868f4a3faf824c4317931c228 | Khac Vy <vytk@reapit.com> | feat: #1231 Add pagination for transaction history (#1252)
- 8cf9f28f23a04ab4e71dd68ddfb014cc4c9b3935 | Cuong Vu <cuongvh@reapit.com> | fix: update placcholder html description (#1254)
- 12cc29df7b22d6e0b23564aedba14109939572db | Vu Nguyen <nphivu414@gmail.com> | feat: #1125 Standalone app page (#1240)* feat: #1125: Create app details standalone page
- 318c19bb3fa08f9292c839ea48fbf424c1ce0403 | Trường An <andt@reapit.com> | chore: #1185 update "Ping" as hiperlink (#1250)
- 4e0bd6ce1a5a5a25ba0d2534e44a8edb6ab5c184 | NghiaPham <nghiapn@reapit.com> | fix: #1143 transaction history billing csv download link format is incorrect (#1244)* fix: #1143 transaction history billing csv download link format is incorrect* update typos
- 433aee1b898611dac3267fbbacfbcc8889adb897 | Cuong Vu <cuongvh@reapit.com> | fix: #1160 strip out HTML when pasting (#1247)
- a83fc0132e5dd6a7d8104c0dbc6a422e8b0f3f07 | Cuong Vu <cuongvh@reapit.com> | fix: css issue manage app (#1241)
- 8338fa8a7848fb8b0de658d3d03fffa390352307 | Pham Hai Duong <duongph@reapit.com> | chore: #1232 add line text to cost explorer (#1237)resolve #1232Changes- Add line text "** As our chargers are calculated in fractions of pence per transaction, very occasionally you may see a rounding discrepancy of more than £0.01 in the Cost Explorer."- Update snapshot
- 15442458c229092e9a5c33003c1a5cb5d27049e8 | Trường An <andt@reapit.com> | feat: #1185 Add a 'Ping' feature to the Webhook Subscriptions (#1235)
- ebe967eb25687f2507a431e51f1afff37df112b8 | Trường An <andt@reapit.com> | chore: #1159 add URL validate before submit webhook edit form (#1236)
- c0a25c6ef8eebb0fbf61a9417782e2e56b4b973c | Khac Vy <vytk@reapit.com> | fix: Error when loading the billings page in the Developers Portal(#1233)
- c007ed6468639fec14e5c07d71b938f1684cee36 | Cuong Vu <cuongvh@reapit.com> | fix: #1160 update validation of textareaeditor (#1227)
- 63ae65d6ef2f18f2d5c3fe52915c711447b7eebc | Pham Hai Duong <duongph@reapit.com> | fix: #1145 minor fix for Y axis's legend of bar chart and change to netAmount instead of grossAmount (#1216)Resolve #1145Changes- Minor fix for bar chart Y legend- Change grossAmount to netAmount- Fix test
- 3e0d0c78e3e736d57e8bad8339b28ee206fdf1c6 | NghiaPham <nghiapn@reapit.com> | feat: #143 - Transaction History Update (Billing/Analytics) (#1167)feat: #143 - Transaction History Update (Billing/Analytics) (#1167)
- 2c8346824813966245a4ab567e8ae43892396472 | Cuong Vu <cuongvh@reapit.com> | fix: #1160 fix placeholder color, change H6 to H5 (#1194)* fix: #1160 fix placeholder color* fix: #1160 change h6 to h5 in desciption
- 142fe4bce1f49cc16156465d5a639d314c2cf191 | Trường An <andt@reapit.com> | chore: #1159 update webhook page (#1191)
- 0f66915923551cff8440344ee013a627a78b9d80 | Cuong Vu <cuongvh@reapit.com> | fix: #1160 HTML Description fields fixes (#1181)* fix #1160 WIP fixing <Editor> and <HTMLRender>* fix #1160 fixing <Editor> and <HTMLRender>* fix: #1160 rem instead of em
- c20bb78efd587d96a78d1d6c545f6ce1d87c9ba9 | Trường An <andt@reapit.com> | feat: #1166 Cost Explorer (Usage and Cost) update (#1180)* feat: #1166 Cost Explorer (Usage and Cost) update* chore: #1166 update actionType name* chore: #1166 update follow PR comment* chore: #1166 update file name
- 1568f527794bc8976fc8d9f6d8b0ae5d4b6c7cae | Cuong Vu <cuongvh@reapit.com> | fix: #1171 pagnination rps issue (#1187)
- d7da78f6d3c41b05800692872944f4a228446059 | Trường An <andt@reapit.com> | feat: #1159 Updates required to the Webhooks page in the Developers Portal (#1169)* feat: #1159 Updates required to Webhooks page in the Developers Portal* chore: #1159 update webhook table render* chore: #1159 update reducer loading, add call api func as a service* chore: #1159 update route dispatcher webhook
- ac134898d1fe5d6f26e45a0918e9ae606c65e6ba | Pham Hai Duong <duongph@reapit.com> | feat: #1164 add SBOX to customer of subscription drop down (#1172)feat: #1164 add SBOX to customer of subscription drop down (#1172)Changes- modify generateCustomerOptions for return correct value
- 533632f4e57d39a9ae17ab798573516416f1fa3a | Pham Hai Duong <duongph@reapit.com> | feat:integrate api for billing bar chart (#1168)Changes- Integrate api for billing bar chart- Write test- Refactor some places
- faaa7986543e32197ef0919e8b26ba737eb47790 | Trường An <andt@reapit.com> | feat: #1122 redirect to the browse apps page if I have no installations (#1156)
- 91fe077d165bd41afacbd3b5a5cb1fa1f7cf7d0e | Trường An <andt@reapit.com> | feat: #1006 #979 create/edit webhook modal (#1140)* feat: #1006 #979 create/edit webhook modal* feat: #1006 update list webhooks* chore: #1006 update content type of header API call* chore: #1006 add type for variable* chore: #1006 add open webhook modal
- c9a2dac512ee7d90833f655c46bf71296f09735a | Pham Hai Duong <duongph@reapit.com> | refactor: #1145 refactor billing bar chart (#1154)refactor: #1145 refactor billing bar chart (#1154)
- e503f3a3a269e9006b676f32028ffb41cfe1bc6b | Pham Hai Duong <duongph@reapit.com> | feat: #1123 render text editor instead of text area submit app (#1151)feat: #1123 render text editor instead of text area submit app (#1151)
- 6cb9322c4d238377b98f41c9729a820f014fcf27 | NghiaPham <nghiapn@reapit.com> | fix #1065: re-instating purge unused s3 assets cronjob (#1134)fix #1065: re-instating purge unused s3 assets cronjob (#1134)
- 349e86a308951fc723a519521e21468297c686c7 | Pham Hai Duong <duongph@reapit.com> | feat: #1123 render renderHTML for diff compare of approval modal (#1153)Changes- Add diff viewer for RenderHTML component
- ee76c1a2bde4981b580e949730869c95ae8686aa | Pham Hai Duong <duongph@reapit.com> | feat: #1123 render html for app detail (#1152)feat: #1123 render html for app detail (#1152)
- 0669a9350761bca3723fa279e9b27c979d3ef587 | Trường An <andt@reapit.com> | feat: #1062 Include date Created as a column on the Apps and Devs (#1147)
- 897ee1ec8c9618555613f8d73670e0513184ee89 | Trường An <andt@reapit.com> | feat: #1069 Update wording on the Analytics Dashboard (#1146)
- cdb0a9c0b29ad10ccae29cb678e65487e3de1a14 | Pham Hai Duong <duongph@reapit.com> | chore: add sentry cli to push source map to sentry.io (#1136)* chore: add sentry cli to push source map to rsentry.io* chore: add IS_RELEAASE env for sentry source map upload
- 40996bc76d4a829d4e623398076ec6bf89cc20f2 | NghiaPham <nghiapn@reapit.com> | fix: #1121 remove login type tab from marketplace's login page (#1135)
- e3b5cdf3c889e5be9b1d3efdd67e09236617c865 | Vu Nguyen <nphivu414@gmail.com> | Feat: #1104 - Update billing tab UI (#1141)* feat: #1104: Update billing tab UI
- ea009069bb4e5153a9d51ca94ff6986fe5506959 | Vu Nguyen <vunp@reapit.com> | Feat/1078 create cost explorer section on billing tab (#1115)* feat: #1078 - Add cost explorer section to billing tab
- 2001628ce1ea9be4f4b27a3c6ad22058075357a2 | Pham Hai Duong <duongph@reapit.com> | fix: #1066 show image 5 for app revision submit (#1101)Changes- Add upload helpers for image5- Fix test
- f6d395afc5f1476e09d4c33761fe347ec1872859 | NghiaPham <nghiapn@reapit.com> | fix: #693 - increase webhooks page dropdown size, and load developer apps data (#1095)
- 579d2c515ed2df63277cd77fcbc08a45a6c5c67e | NghiaPham <nghiapn@reapit.com> | fix: #1065 fix loading chunk fail (#1092)
- 8c36f7ec52fa78ed66194387647f2cf97152a808 | Vu Nguyen <vunp@reapit.com> | feat: #1089 Update cost calculator table UI (#1096)* feat: #1089 - Update total calculator table layout
- e066a95a96d0b11757156228788bdfddb20c97a6 | Khac Vy <vytk@reapit.com> | feat: #973 implement developer list webhooks (#1081)* feat: #973 implement developer list webhooks
- 3d2a2e09802fe9ea75232ec22b6402e57de14575 | Pham Hai Duong <duongph@reapit.com> | feat: #1073 add axis label for service chart (#1093)
- 78d9288bf4719e1e233966c12a985c821406b86d | Vu Nguyen <vunp@reapit.com> | feat: #1077 - Add Transaction History section to billing tab (#1087)* feat: #1077 - Add Transaction History section to billing tab
- 5bb909159d8464ba2dde328cee22d94db06be701 | Pham Hai Duong <duongph@reapit.com> | feat: #1073 create bar chart developer portal (#1090)
- 7fed969c082458b3ca44628e9573143d7110a248 | Vu Nguyen <vunp@reapit.com> | Feat: #714 - Create cost calculator on analytics billing tab (#1079)* feat: #714 - Add cost calculator to billing tab
- fd52c8520f1d8765c727edd4f041da1335408295 | Pham Hai Duong <duongph@reapit.com> | feat: #1068 updatecalculation total cost table in term and condition (#1080)* feat: #1068 updatecalculation total cost table in term and condition* chore: set up test for web-components
- 32c244d40e83402b1443f61c04646e47ba8e1d64 | Khac Vy <vytk@reapit.com> | chore: #1055 Temporary hide client T&C modal (#1058)* chore: #1055 Temporary hide client T&C modal* chore: update navigate route
- 16c92eb246e4c2500fd5fe374bec149d79448e7a | Pham Hai Duong <duongph@reapit.com> | feat: #1009 serverless deployment for cloud apps (#1061)Changes- Clone serverless.yml for cloud apps
- 1d307dad916b497ef3d6eb3e35510e5bafb3acfb | NghiaPham <nghiapn@reapit.com> | Feat #963: Implement Developer Webhooks page (#1049)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

### marketplace_v1.0.22 - 2020-04-23
  
Release: marketplace_v1.0.22
Rollback: marketplace_v1.0.21
Changes:
commit | author |description
  
- 5e282514b01ca338f0b7b9f1d467f509abadb881 | Cuong Vu <cuongvh@reapit.com> | fix: #1040 fix pending revision image missing (#1060)
- d546c17255e322524c78deffc311aca2120a612d | Khac Vy <vytk@reapit.com> | chore: Update agency integration type section text (#1047)* chore: Update agency integration type section text* chore: bump version cognito-auth 2.1.4
- 02b78b007c56ee2cfb5b25c2ddf1f026b444f0d2 | Vu Nguyen <vunp@reapit.com> | Feat/956 search developer registrations by date (#1044)* feat: #956 - Search developer registrations by date
- add5f492bd8998789fc2688f9ba2879c551341c4 | Trường An <andt@reapit.com> | chore: #957 can search just with date range (#1041)
- 7324a2c675932d93f43d5b7978b2d13d0a705768 | Cuong Vu <cuongvh@reapit.com> | fix: #1035 swagger link color (#1045)
- fbfbe35221e217714a5d419f9d689f4c15ed6bc8 | Cuong Vu <cuongvh@reapit.com> | fix: #939 fix e2e tests (#1048)
- 7fb4663aa09063dc790169191277efc42523d2ec | Cuong Vu <cuongvh@reapit.com> | feat: #939 Web apps should have their own dev and prod cookie identifier (#972)- Web Apps now have three different cookie identifiers `local`,`developement` , `production`, based on `config.json`- Some methods in `cognito-auth` now have an additional `appEnv?: string` param to work with cookie for different environments- Default `refreshSession` state in `redux store` now will be set after fetch `config.json`- Fix e2e tests login after changing cookie identifiers
- 220ffdd6fc928be16774ae046d391ecb3416de90 | Trường An <andt@reapit.com> | feat: #957search App Registrations by date in the Admin Portal (#1007)* feat: #957 As an ‘Admin’, I want to search for App Registrations by date in the Admin Portal* chore: #957update variable name
- 623453eacf3ddf616c5b7bbdf5c3287c415ef1e4 | Trường An <andt@reapit.com> | fix: #932 Client ID not displaying on first page load - Client Portal (#967)
- e60f9279bbc58cb6957dc5b14e64f23ea03014c5 | Cuong Vu <cuongvh@reapit.com> | fix: fix filter app flow add delay (#949)
- d18a36a985a4c13bf0939f1eb375dd0efc9c86a5 | Cuong Vu <cuongvh@reapit.com> | fix: #122 Fix admin login e2e test (#946)
- 3d680814746fb5c62f83cc6acdd91ef164c98cfb | Cuong Vu <cuongvh@reapit.com> | feat: #917 Desktop Integration in revision modal & Stabilize E2E tests (#941)
- 88070783a538ef4bb2e5ad3c9983791b13db71ef | Cuong Vu <cuongvh@reapit.com> | fix: fix e2e test fail (#940)
- 7538c11bda998f6ceed67153065eed10c29ffefa | Cuong Vu <cuongvh@reapit.com> | chore: #122Integrate E2E tests (#924)
- 83ff778d60ed33b8753dbc58bbaf53efdcced1f8 | Vu Nguyen <vunp@reapit.com> | feat: #910: Fix whats new link in Help page (#926)
- f5ec3ab4183ac308dc768b8e84a3b6fb29c75837 | Vu Nguyen <vunp@reapit.com> | feat: #923: Fix analytic filter date params (#929)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

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
