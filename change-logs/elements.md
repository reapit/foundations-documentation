# Elements

description: &gt;- Below you will find a listing of the recent changes we have made to the Elements package. This includes details of any bugs that have been fixed or

### features/enhancements that have been added.

## Elements

### elements_v0.5.59-beta.1 - 2020-06-10
  
-----------------------------------------------------------------------------
Release: elements_v0.5.59-beta.1
Rollback: elements_v0.5.57
Changes:
commit | author |description
  
- 8dc9b71908ebaf6d582975d4e19226e9c0faac07 | Will McVay <wmcvay@reapit.com> | fix: #1393 linaria elements build (#1645)* fix: fixes elements rollup dist* fix: adds comments* fix: fixes elements build, now outputs types* fix: fixes test run by splitting tsconfigs* fix: fixes lockfile issue
- 86556a475ee81a956988cdd100c61ef406c6875a | Pham Hai Duong <duongph@reapit.com> | fix: #1580 add required label for text area and text description (#1655)
- ae5e0a18209ba04781bff8937be810ab41278903 | Cuong Vu <cuongvh@reapit.com> | fix: #1585 fixed integration types (#1638)
- dba71118fb6f2cd4fe32335a842d23c15e7010f3 | Pham Hai Duong <duongph@reapit.com> | fix: #1393 resolve problem on elements (#1633)
- 62ea69ff21ade7db8e1a9a9429a52290a35ec9cf | Khac Vy <vytk@reapit.com> | fix: #1632 Toast doesn't display on IE (#1631)
- bce2f7fcfa62994312c201a76a1e49e072db1f8a | Trường An <andt@reapit.com> | fix: #1595 #1526 Should be limiting the size of the input value in fields (#1609)
- 5a56e42074fbe9a68b70bf64889a5680c11a3258 | Will McVay <wmcvay@reapit.com> | feat: #1565 standalone apps prod fixes (#1626)
- 4c44e469d5e8fa7f68171c5e14b0fac95a666cd1 | NghiaPham <nghiapn@reapit.com> | fix: #1587 - add diff render class to purify css white list (#1622)
- fbd560e567be54b142b81d6abfd95d719b397199 | NghiaPham <nghiapn@reapit.com> | fix: #1595 - bug select field type integration page app submit developer (#1615)
- e49a036e3d1e28358dbeda8def2a09d53acfe539 | Cuong Vu <cuongvh@reapit.com> | fix: #1518 fix stretched desciption when inputing long text (#1589)
- 2b49b19bfcfa6530224da46a3b3a99fe237048a4 | Khac Vy <vytk@reapit.com> | fix: #1421 fix developer portal UI bugs (#1559)
- dd9e470a502aa2f4e13d79f157afa13f3e907317 | Will McVay <wmcvay@reapit.com> | chore: #1414 #1488 #1413 #1412tidy app errors (#1535)* fix: tidied up Geo Diary* fix: reduces noise when running tests in AML, Marketplace and Elements
- ffc7b2cbc8dd74d8695b528a4d46ecd51e343d7b | Trường An <andt@reapit.com> | fix: #1494 #1497 fix some validate bugs on submit app page (#1521)
- bf1e25be58832cfd42c482d6f4706eda56776903 | Snyk bot <snyk-bot@snyk.io> | fix: packages/elements/package.json & packages/elements/.snyk to reduce vulnerabilities (#1538)The following vulnerabilities are fixed with a Snyk patch:- https://snyk.io/vuln/SNYK-JS-LODASH-567746
- 99d8c3e77fbfb8c609fd36aed625e5ae8e36993b | Will McVay <wmcvay@reapit.com> | chore: bump elements version to release (#1530)
- 3b7d043894ec3029099224e1fdf3763f350003cc | NghiaPham <nghiapn@reapit.com> | fix: #1316 Update to Demo Site Search Widget (#1461)
- 2b64260f4f2ceadc607f83278092b095bb77e0c2 | Cuong Vu <cuongvh@reapit.com> | fix: #1425 aml mobile and ie fixing (#1522)
- 22f53f3e4b72b4e6964739940c14ef32cea4b427 | Will McVay <wmcvay@reapit.com> | fix: #1393 fixes rollup config for elements so linaria styles are exported (#1501)* fix: resolves linaria styles bundle issue* fix: adds a couple of comments* fix: add comment* fix: fixes tests by handling sass in Jest properly* fix: re-generate lock file after merge
- dcc0d7a186b82c556e2e882f8b6f16173ae061a2 | Vu Nguyen <nphivu414@gmail.com> | feat: #1126 Remove old app detail modal code (#1498)* feat: #1126 Routing to the new standalone app page + Remove old app detail modal code
- 0e831e5ec742dd60148a3acac1137b12365bcc77 | Vu Nguyen <nphivu414@gmail.com> | fix: #1422 Fix IE crashing issues due to google-maps-loader (#1519)
- 62fb2561486eb9a05e2e0fd19a6d0677c8fd9870 | Pham Hai Duong <duongph@reapit.com> | ci: #1333 add deployment pipeline for new process (#1479)
- 4267c156525a927e321e61d5fd468ddd3737297e | Cuong Vu <cuongvh@reapit.com> | fix: #1422 IE bug fixed (#1471)
- c34899b910fa019e76abafc8ae5081e2d0891340 | Trường An <andt@reapit.com> | refactor: #1327 Refactor Admin Dev Management using react-redux hooks (#1386)
- b7985c934b11410e3071430180f17ca96648a525 | Khac Vy <vytk@reapit.com> | fix: #1391 Fix warning error which display in marketplace (#1405)
- 78db4a6fe056181b77a49c3dbf34cda296f5b5aa | NghiaPham <nghiapn@reapit.com> | chore: remove offline plugin (#1387)
- 1109cc4a89dbcc242b13e216498d8784287dae49 | Cuong Vu <cuongvh@reapit.com> | fix: #1389 dead link search widget in elements (#1400)
- 9373540a37132518e18045d76213c221de773293 | Pham Hai Duong <duongph@reapit.com> | fix: breadcrumb style in elements storybook (#1351)
- 663bb21ebe2aa0fd4f367d9a18eaa9782805c42c | Trường An <andt@reapit.com> | feat: #1033 configure my web component installations in the Marketplace (#1313)* feat: #1033 configure my web component installations in the Marketplace* chore: #1033 add negotiators dropdown* chore: #1033 update app header, update snapshot* chore: #1033 fetch negotiators list* chore: #1033 update api* chore: #1033 update follow PR cmts* chore: #1033 fix test fail
- 1a705580bf9f1d620479c642b42840f18b2b3830 | Cuong Vu <cuongvh@reapit.com> | fix: fix element page on mobile (#1345)
- c475f3c0f9638e18664c50bc005ce22ed332448a | Cuong Vu <cuongvh@reapit.com> | fix: fix client app page css issue (#1339)
- 09f7cadd3c627d6f0ece0a54e58eb072957d5cd7 | NghiaPham <nghiapn@reapit.com> | fix: #1206 #1210 tweak standalone page css (#1335)
- 65c973a0173565bf0ddb129d18964db672866e5f | Cuong Vu <cuongvh@reapit.com> | fix: #1275 layout issue on mobile (#1332)
- 906512f589cc326c3299d5446f304dcf2c41c68a | Pham Hai Duong <duongph@reapit.com> | chore: add MiniCssExtractPlugin to prod and dev webpack (#1324)
- d15a9d9ed50ba9b51acceffb9ad829218f59cf16 | Pham Hai Duong <duongph@reapit.com> | feat: #1274 create breadcrumb components (#1303)
- a35834aa73d5c92490913a73acc56960ab43f6a2 | Vu Nguyen <nphivu414@gmail.com> | feat: #1290 Fix issues with logging into dev and client portal (#1301)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
-----------------------------------------------------------------------------

    
### elements\_v0.5.56 - 2020-05-12

Release: elements\_v0.5.56 Rollback: elements\_v0.5.53 Changes: commit \| author \|description

* 2c8346824813966245a4ab567e8ae43892396472 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 fix placeholder color, change H6 to H5 \(\#1194\) _fix: \#1160 fix placeholder color_ fix: \#1160 change h6 to h5 in desciption
* 1d30c8b526b6b6c5abf054b45948e9d7325a69a6 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: bump elements version 0.5.56 \(\#1213\)
* a2106bf468c233be83b5621358414f97eb00faeb \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| fix: \#1189 fix desktop integration type dropdown spacing \(\#1190\)
* 0f66915923551cff8440344ee013a627a78b9d80 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 HTML Description fields fixes \(\#1181\) _fix \#1160 WIP fixing  and_  fix \#1160 fixing  and \* fix: \#1160 rem instead of em
* 91fe077d165bd41afacbd3b5a5cb1fa1f7cf7d0e \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1006 \#979 create/edit webhook modal \(\#1140\) _feat: \#1006 \#979 create/edit webhook modal_ feat: \#1006 update list webhooks _chore: \#1006 update content type of header API call_ chore: \#1006 add type for variable\* chore: \#1006 add open webhook modal
* e503f3a3a269e9006b676f32028ffb41cfe1bc6b \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1123 render text editor instead of text area submit app \(\#1151\)feat: \#1123 render text editor instead of text area submit app \(\#1151\)
* 349e86a308951fc723a519521e21468297c686c7 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1123 render renderHTML for diff compare of approval modal \(\#1153\)Changes- Add diff viewer for RenderHTML component
* d9182462a1a90ed1b0414b2c715d32687d39c10b \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#1120 elements heading font default roboto \(\#1132\)
* ea009069bb4e5153a9d51ca94ff6986fe5506959 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/1078 create cost explorer section on billing tab \(\#1115\)\* feat: \#1078 - Add cost explorer section to billing tab
* 6cfa6953b45c16f86ff15f8a98edf1b6d7c4c9a7 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1067 fix double scroll bar issue \(\#1111\)
* 78e0c0052c004470a578a168e2e02902b632bfb6 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#639 - selectbox styles \(\#1108\)
* f6d395afc5f1476e09d4c33761fe347ec1872859 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#693 - increase webhooks page dropdown size, and load developer apps data \(\#1095\)
* 579d2c515ed2df63277cd77fcbc08a45a6c5c67e \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1065 fix loading chunk fail \(\#1092\)
* 7fed969c082458b3ca44628e9573143d7110a248 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat: \#714 - Create cost calculator on analytics billing tab \(\#1079\)\* feat: \#714 - Add cost calculator to billing tab
* 16c92eb246e4c2500fd5fe374bec149d79448e7a \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1009 serverless deployment for cloud apps \(\#1061\)Changes- Clone serverless.yml for cloud apps
* 1d307dad916b497ef3d6eb3e35510e5bafb3acfb \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| Feat \#963: Implement Developer Webhooks page \(\#1049\)
* e02fba2817092224554006d4eae2bb104f147c05 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/956 search developer registrations by date \(\#1044\)\* feat: \#956 - Search developer registrations by date
* aea4ce8c2597c96cac1b8350cff6b75628ebc737 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#939 Web apps should have their own dev and prod cookie identifier \(\#972\)- Web Apps now have three different cookie identifiers `local`,`developement` , `production`, based on `config.json`- Some methods in `cognito-auth` now have an additional `appEnv?: string` param to work with cookie for different environments- Default `refreshSession` state in `redux store` now will be set after fetch `config.json`- Fix e2e tests login after changing cookie identifiers
* edb6794755d257ebcdc77e24aec29ba6898314d7 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: \#830 Update description text \(\#976\)
* f11d41b283f096b00de498f1f6149622a71e1a75 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: \#830 Add space between texts in tag component \(\#955\)
* 6c35f507941d05ce42efa6a262ca5261220f03ce \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: \#830 Update tag link component and option font size \(\#928\)\* chore: \#830 Update tag link component and option font size

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

### elements\_v0.5.53 - 2020-04-15

Release: elements\_v0.5.53 Rollback: elements\_v0.5.52 Changes: commit \| author \|description

* 6a31636011bae975400fdb2719322c74a5320b00 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: bump @reapit/elements version 0.5.53 \(\#915\)
* 8648895ff351105096069d8a1df4fcffa3195bd8 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#890 display html version of elements components \(\#912\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

### elements\_v0.5.52 - 2020-04-14

Release: elements\_v0.5.52 Rollback: elements\_v0.5.51 Changes: commit \| author \|description

* 779c691f5e095e497789a126a50b8c46c5e0809a \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| bump @reapit/elements version 0.5.52 \(\#893\)
* a339d89e98f6dc7b5bcc5849de9f9ae19f792394 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: Update dropdown select component \(\#892\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

### elements\_v0.5.51 - 2020-04-13

Release: elements\_v0.5.51 Rollback: elements\_v0.5.49 Changes: commit \| author \|description

* 15e849ac35b1ab8e58ab0652a3a5e2d52d286926 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: bump elements version 0.5.51 \(\#886\)
* 4a1bfeacd2304a5000f567ac39cb55eadbd1f6c5 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: Add tooltip which display when user hover in tag \(\#879\)\* chore: Add tooltip which display when user hover in tag
* aeac1e83a85a99c1bd72c7088ec5e3ef2995536b \| leXuanNha [nhalx@reapit.com](mailto:nhalx@reapit.com) \| Feat/828 create tag component in elements \(\#866\) _feat: \#828 Add dropdown select component using rc-select_ put tag component into formik and testing\* fix lintCo-authored-by: Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com)
* 60de4013a36bf0fdc528b990eb5b6c106f64320d \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Fix: \#840 updates required to analytics tab \(\#861\)\* feat: \#840: Updates required to analytics tab
* ef2f7f2eadd6f6923d45edc2ce2b5616a57c8c1d \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat \#712 + \#711 : Developer can see a list of enpoints and a graph showing my ‘Hits per Day’ \(\#836\) _mock redux_ mock redux _feat: \#712: Add traffic event table component_ feat: \#712: Upgrade react-table to stable version - Add Footer for table element _fixing typescript_ feat: \#712: Update developer endpoint list + chart _feat: \#712: Fix typo issues_ feat: \#712: Fix linting issues _feat: \#712: Fix linting issues_ feat: \#712: Update snapshot testCo-authored-by: nhalx [nhalx@reapit.com](mailto:nhalx@reapit.com)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

#### elements\_v0.5.49 - 2020-04-03

Release: elements\_v0.5.49 Rollback: elements\_v0.5.48 Changes: commit \| author \|description

* fc33827dd41ae1f68171f73ad1346c4c709ae490 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: bump elements version 0.5.49 \(\#810\)
* f9d7f3a34a89e5c1a2e5ab748562dba149093b3c \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#739 correcr logic before restorewindow.**REAPIT\_MARKETPLACE\_GLOBALS** \(\#809\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

#### elements\_v0.5.48 - 2020-04-03

Release: elements\_v0.5.48 Rollback: elements\_v0.5.47 Changes: commit \| author \|description

* 490f0b13c8e6200cd7ba98810f15af74c6372e3b \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#739 cannot assign to readonly window.**REAPIT\_MARKETPLACE\_GLOBALS** \(\#800\)
* 8d3bd81c139e1a7f5e3e903f182faf1d156e54c5 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#739 The Cloud Apps should be testable in "Desktop Mode" \(\#784\)\* feat: \#739 cloud apps now testable in desktop mode

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

#### elements\_v0.5.47 - 2020-04-01

Release: elements\_v0.5.47 Rollback: elements\_v0.5.46 Changes: commit \| author \|description

* d09c020aa042f59d08e36f086ea8401426ffab94 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: export upload progress component \(\#780\)
* f229847a63f34993c3c1e6b1c134b97cb3f0ca87 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat: \#725 developer can filter detailed page to customize results \(\#777\) _feat: \#725: Refactor detailed tab_ feat: \#725: Update analytics filter form _feat: \#725: Update analytics page to use react redux hooks_ feat: \#725: Update detail tab test _feat: \#725: Update test for filter bar + filter form_ feat: \#725: Pump elements version _feat: \#725: Fix lint error_ feat: \#725: Fix naming convention
* d9d081b79190cd5ff1277bbeca6af75e0af76c12 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: fix edit release not trigger github action \(\#762\) _chore: fix edit release not trigger github action_ chore: avoid duplicated \_released when release:npm && relase:prod

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

#### elements\_v0.5.46 - 2020-03-30

Release: elements\_v0.5.46 Rollback: elements\_v0.5.45 Changes: commit \| author \|description

* 5037c84ce5c2ee3d1aecbc3be37a146366086dc9 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#701 refresh link incorrect, add param in navigateDynamicApp \(\#758\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

