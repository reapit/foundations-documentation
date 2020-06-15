---
description: >-
  Below you will find a listing of the recent changes we have made to
  Marketplace. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# Marketplace
### marketplace_v1.0.32 - 2020-06-15
  
-----------------------------------------------------------------------------
Release: marketplace_v1.0.32
Rollback: marketplace_v1.0.27
Changes:
commit | author |description
  
- b145a3be9fa5abeb6b37f04867b089bca3b0bd05 | Vu Nguyen <vunp@reapit.com> | fix: #1657 Fix standalone apps page container position on IE1 (#1723)
- b969cfc95e30c58462508a2507d7c634b94e1888 | Will McVay <wmcvay@reapit.com> | fix: #1565 tiny css tweak (#1692)* fix: tiny css tweak* fix: page tweaks for app page release
- 41010f40faa20a79292d0e837890b89be2ac18c0 | Pham Hai Duong <duongph@reapit.com> | fix: #1393 linaria issue on cx (#1713)
- 059c919d20a5272f3d70be6ab15ad388ff6d8df4 | Cuong Vu <cuongvh@reapit.com> | fix: #1683 & #1684[Marketplace]- [Client] Browse App Search validation (#1709)
- 88e116758d45ccec639a354e031422610ce31f2e | NghiaPham <nghiapn@reapit.com> | fix: #1340 temp fix for developer billing and organisation page navbar type (#1654)
- 65eb0dca10dfdd00aa53e711f1ae903e309ec8ae | Will McVay <wmcvay@reapit.com> | fix: #1393 ie linaria bug (#1691)* fix: ie linaraia bug* fix: re-add storybook build* fix: iframe url
- 71ce99ac7ccdc763ecce4816bca5ced351e0b47b | Pham Hai Duong <duongph@reapit.com> | fix: #1528 add more description for customer id field (#1689)
- ca1e38f1ba5af15f41de2bb0d230685a3ea07da7 | NghiaPham <nghiapn@reapit.com> | feat: #1383 create a new section in the admin portal billing (#1636)
- 2addf0c6b2096bb06a63aac331ea0d39bd7397cc | NghiaPham <nghiapn@reapit.com> | fix: #1555 - input space at first and last position when searching on marketplace (#1677)
- 817133257c26d3fd8fa2595ede39a7c187e084ba | Vu Nguyen <vunp@reapit.com> | fix: #1591 Upload file button issues in AML checklist (#1674)
- d84ac80a7816946cc3b3e4509f7530a6420f7f68 | Pham Hai Duong <duongph@reapit.com> | fix: #1580 remove validate required for category field in submit app (#1688)
- 4987326f9d2cdb12d980ff5d88ce124dc71b6c4a | Pham Hai Duong <duongph@reapit.com> | fix: #1628 should not allow fill text in telephone field (#1675)
- 6a3c6518d83722e805fca5de6e78ac8de28bb484 | Trường An <andt@reapit.com> | chore: #1646 admin portal update (#1648)
- dfca199d9622d993bd50d88475015505094b7ad8 | Vu Nguyen <vunp@reapit.com> | fix: #1657 Standalone apps pages ui broken on ie11 (#1671)
- 520ca1233f6091dee0ea04b080aeb161bc149fda | Khac Vy <vytk@reapit.com> | fix: #1421 fix logout button doesnot display in IE (#1659)
- b9519eff9a0728cd3af8e9c9d93c852427251603 | Trường An <andt@reapit.com> | fix: #1649 avoid click outside label to focus input (#1664)
- 6fb212b394351fb775933a57d6ae48e3ae328a7d | NghiaPham <nghiapn@reapit.com> | fix: #1384 - when an app is pending we should prevent access to edit (#1642)
- dc1825b89f40f1b42f248a943ef7c965479f1708 | Cuong Vu <cuongvh@reapit.com> | fix: #1640 should show warning when input spaces in admin app rejection (#1662)
- 431233fb022091a1b21a7beac5ddc2fe0a3d5dc9 | Trường An <andt@reapit.com> | fix: #1649 App preview should have default placeholder for App Icon (#1658)
- 95b64d7277a4add46e116f7f31d11ab8fb81c23c | Pham Hai Duong <duongph@reapit.com> | fix: #1580 submit app should have asterisk required field (#1656)
- 86556a475ee81a956988cdd100c61ef406c6875a | Pham Hai Duong <duongph@reapit.com> | fix: #1580 add required label for text area and text description (#1655)
- 39f88ac08c83af5b46bcd02eaef36f2d83bfb12a | Pham Hai Duong <duongph@reapit.com> | fix: #1528unable to submit private app without customer id (#1650)
- c93ae1cbfa8bce9964fce586b0b23258f87373a4 | Pham Hai Duong <duongph@reapit.com> | fix: #1628 validate telephone number for developer register form (#1651)
- 866edfa39bbdc3ddb28abd1a8be2ba2896612fd1 | Trường An <andt@reapit.com> | fix: #1641 display all apps infomation in admin apps (#1647)
- e261e239a7260b59a828cc08a71b4076de59452d | Khac Vy <vytk@reapit.com> | fix: #1421 Developer Portal Browser Testing (#1643)* fix: #1421 Update component name. Fix style error
- d91141b689f2dcd20b5639c1eb3ac919d1da5d89 | Pham Hai Duong <duongph@reapit.com> | fix: #1554 app name missing on delete modal (#1639)
- ae5e0a18209ba04781bff8937be810ab41278903 | Cuong Vu <cuongvh@reapit.com> | fix: #1585 fixed integration types (#1638)
- 6edd90d124871a314d28825f9a88768dff8d4f22 | NghiaPham <nghiapn@reapit.com> | fix: #1627 - trim text before validate empty for fields company name and telephone (#1634)
- 952ccccf568eea39df8aebc452513e15fece5178 | Trường An <andt@reapit.com> | fix: #1243 Show email address has already been registered on register page (#1637)
- aa330d323f2db857bf67cc09afbef2e6d27d9896 | Khac Vy <vytk@reapit.com> | fix: #1421 update unsupported brower popup (#1635)
- 891f9b76c8d3744f8eb60d3142337c16165696b5 | NghiaPham <nghiapn@reapit.com> | fix: #1520 - field value overflow on marketplace diff viewer (#1630)
- 0898540ba918805242b91014580a98dd4cd56127 | Vu Nguyen <nphivu414@gmail.com> | fix: #1579 Desktop bugs on standalone app page (#1620)* fix: #1579 Desktop bugs on standalone app page
- bce2f7fcfa62994312c201a76a1e49e072db1f8a | Trường An <andt@reapit.com> | fix: #1595 #1526 Should be limiting the size of the input value in fields (#1609)
- 8ba2cc21ce2984a70ad3aaa0ad0f48dee3d91b3c | Trường An <andt@reapit.com> | fix: #1517 #1495 Should be displayed warning message when enters the space in all search fields (#1581)
- 8bb4e905f12ab5067e508ca33463ff04e6f57f21 | NghiaPham <nghiapn@reapit.com> | fix: #1385 apply manage route to client standalone page opened by client manage apps (#1614)
- 5a56e42074fbe9a68b70bf64889a5680c11a3258 | Will McVay <wmcvay@reapit.com> | feat: #1565 standalone apps prod fixes (#1626)
- 2e362a2b7a41fd3b8edef31cdcb11709719df989 | Trường An <andt@reapit.com> | fix: #1127 enable preview button from submit app page (#1619)* chore: #1127 enable preview button from submit app page* chore: #1127 update image preview app* chore: #1127 update image preview app
- 4c44e469d5e8fa7f68171c5e14b0fac95a666cd1 | NghiaPham <nghiapn@reapit.com> | fix: #1587 - add diff render class to purify css white list (#1622)
- a794718ad077e80f04225cc693a5e951e7572e9d | Cuong Vu <cuongvh@reapit.com> | chore: #1343 update subtitle (#1618)
- e83f9580ff1ec147ec8a9188094f08872c5c90d0 | Khac Vy <vytk@reapit.com> | fix: #1593 register full name should be filter input values (#1617)
- fbd560e567be54b142b81d6abfd95d719b397199 | NghiaPham <nghiapn@reapit.com> | fix: #1595 - bug select field type integration page app submit developer (#1615)
- 8846014a84f82a5ceee92984b32b423d377cf1ff | Vu Nguyen <nphivu414@gmail.com> | fix: #1579 Desktop bugs on standalone app page (#1612)* fix: #1579 Fix desktop bugs on the standalone app page
- 476c06f70deef67f117b7d6d089318202b2e0fd4 | Khac Vy <vytk@reapit.com> | chore: #1553 number order column should display on one line (#1613)
- 719c06ff548f4fe13f246d2da598cba01083c60d | NghiaPham <nghiapn@reapit.com> | fix: #1516 - description field in diff editor (#1587)
- 78b4646360d32e0917d0136863799745c6b8d846 | Khac Vy <vytk@reapit.com> | chore: #1496 validate telephone field (#1611)
- 298a00fd9208e22caa2dec2f1e18b08ab63e2b0d | NghiaPham <nghiapn@reapit.com> | fix: #1592 - page register on field fullname validate (#1607)
- 0c814a931303644a2007e5072b046b7f9f0e2dd9 | Trường An <andt@reapit.com> | chore: #1127 add categories data to preview (#1610)
- 6cdf68fe48b246d8dc36ff9da524dc875e7679f4 | Pham Hai Duong <duongph@reapit.com> | fix: #1554 app name missing on delete modal (#1583)
- e49a036e3d1e28358dbeda8def2a09d53acfe539 | Cuong Vu <cuongvh@reapit.com> | fix: #1518 fix stretched desciption when inputing long text (#1589)
- 2f8c0f8c58d44d484b69a911ef5eb415bbb223f6 | Khac Vy <vytk@reapit.com> | chore: #1499 Move contact developer button above back to apps button (#1572)
- ac3be56e33db64e7cd2ee12651e9c75c3b395e48 | Vu Nguyen <nphivu414@gmail.com> | fix: #1468 Fix client standalone app page title issues
- bd2063d113a829bfc527e9264203b07703372a42 | Cuong Vu <cuongvh@reapit.com> | fix: #1343 integrate ui into developr setting tab (#1574)
- 689fc8f504504e235fdb53b693fa5b69b38cec4b | Trường An <andt@reapit.com> | feat: #1127 preview app from app details page (#1573)
- 141b67fe4fc997c075e817a454cf852adafe8c3e | Trường An <andt@reapit.com> | fix: #1509 pagination problem on developer app page (#1567)
- cc41c4e5b097789789bd61017c02337f34d817b8 | Vu Nguyen <nphivu414@gmail.com> | fix: #1467 Update standalone apps mobile layout for developer and client portal (#1571)* fix: #1467 Update standalone app mobile layout for client and developer
- 670a0a37d8bd82e2023c185603c98f752826a8d8 | Trường An <andt@reapit.com> | chore: #1504 update T&C text (#1566)
- bf194b36507bcae7ace1ecc96f06b853b64b16e3 | Trường An <andt@reapit.com> | chore: #1033 hide web-component config button (#1568)
- 171c82a612979b810e4368867ae7236b90a68e13 | Will McVay <wmcvay@reapit.com> | fix: ties swagger ui to 3.24.3 to fix broken dev (#1563)
- 12a2c561862b1d097c5026c53ffcc2fc2e3f90fd | Cuong Vu <cuongvh@reapit.com> | fix: #1468 client standalone ui update (#1560)
- 2b49b19bfcfa6530224da46a3b3a99fe237048a4 | Khac Vy <vytk@reapit.com> | fix: #1421 fix developer portal UI bugs (#1559)
- f1aaad7da63a30e7f289d03b9a195e2a785ac866 | Vu Nguyen <nphivu414@gmail.com> | fix: #1467 Developer standalone apps should be mobile responsive (#1558)* fix: #1467 Update UI on mobile screens for developer app detail page
- a7c012085e72ac0097513a6f8d04e0389a3142f4 | NghiaPham <nghiapn@reapit.com> | fix: #1340 add tabs and rename settings page (#1551)
- 29c1808aacb35165e40a830ce50530ced6a33878 | Trường An <andt@reapit.com> | feat: #1509 Remove params on pagination (#1556)
- dd9e470a502aa2f4e13d79f157afa13f3e907317 | Will McVay <wmcvay@reapit.com> | chore: #1414 #1488 #1413 #1412tidy app errors (#1535)* fix: tidied up Geo Diary* fix: reduces noise when running tests in AML, Marketplace and Elements
- 6e294533bff47ecb20953a6ddfd55264d62f28ac | Khac Vy <vytk@reapit.com> | feat: #1463 Create modal to display App contact details (#1525)* feat: #1463 Create modal to display App contact details
- c9b0ba4f7d86212e7c07fde3999dd5e3d67a944a | Trường An <andt@reapit.com> | chore: #1127 disabled preview button when submit new app (#1548)
- f95ee94acc32a53af4f1c564ed0928e4c98697cc | Trường An <andt@reapit.com> | chore: #1504 Update the T&C’s on Developer Registration (#1524)
- f692932f99d7b20f9ed93fe06b337263495012db | Trường An <andt@reapit.com> | fix: #1491 Should have a clear message when cannot create a new app (#1515)
- ffc7b2cbc8dd74d8695b528a4d46ecd51e343d7b | Trường An <andt@reapit.com> | fix: #1494 #1497 fix some validate bugs on submit app page (#1521)
- 99d8c3e77fbfb8c609fd36aed625e5ae8e36993b | Will McVay <wmcvay@reapit.com> | chore: bump elements version to release (#1530)
- 96c000ea77388fcc0d8d5895de40e1bf40acbe99 | Snyk bot <snyk-bot@snyk.io> | fix: packages/marketplace/package.json & packages/marketplace/.snyk to reduce vulnerabilities (#1531)The following vulnerabilities are fixed with a Snyk patch:- https://snyk.io/vuln/SNYK-JS-LODASH-567746
- 2b64260f4f2ceadc607f83278092b095bb77e0c2 | Cuong Vu <cuongvh@reapit.com> | fix: #1425 aml mobile and ie fixing (#1522)
- 9f497f26b58f29d6eeef8dd44a4b44611ed3d6e7 | Trường An <andt@reapit.com> | fix: #1493 All apps are duplicated in many pages (#1510)
- dcc0d7a186b82c556e2e882f8b6f16173ae061a2 | Vu Nguyen <nphivu414@gmail.com> | feat: #1126 Remove old app detail modal code (#1498)* feat: #1126 Routing to the new standalone app page + Remove old app detail modal code
- 705a74751960a76c5e3faa924a751e9523574456 | Trường An <andt@reapit.com> | feat: #1127 As a developer, I should be able to see a preview of my app (#1431)
- 59dbffa11ef2299f2032530ab799ccd02fa17bd3 | Pham Hai Duong <duongph@reapit.com> | fix: #1506 paginationfor developer management (#1513)
- 3a535c389b52678301538d94a2642236bd6064b1 | Trường An <andt@reapit.com> | refactor: #1327 refactor Admin Stats using new react-redux hooks (#1442)
- c34cfd57d6926014356a10412732ccb074cdce3c | Vu Nguyen <nphivu414@gmail.com> | feat: #1126 Route to the new standalone app page (#1368)* feat: #1126 Route to the new standalone app page
- 64f555f40c3b035ed1b3ba208fbd5065e778eb04 | Khac Vy <vytk@reapit.com> | chore: #1343 Update confirm uninstall modal style (#1478)
- b903fb8fa55f18e614c5dc3d328bc660ef664a83 | Trường An <andt@reapit.com> | fix: #1474 fix Route Fetcher not fetch when switch page (#1484)
- 0d0d02906714f7f591dd53cc411632c73472a13b | Cuong Vu <cuongvh@reapit.com> | feat: #1343 invite member via email UI (#1407)
- 62fb2561486eb9a05e2e0fd19a6d0677c8fd9870 | Pham Hai Duong <duongph@reapit.com> | ci: #1333 add deployment pipeline for new process (#1479)
- 4267c156525a927e321e61d5fd468ddd3737297e | Cuong Vu <cuongvh@reapit.com> | fix: #1422 IE bug fixed (#1471)
- b0b3db9ff3435e8b14bbad03ceaaf86e883391db | NghiaPham <nghiapn@reapit.com> | fix: #1371 filtering-mobile-and-ui-issues-on-browse-apps (#1433)
- c34899b910fa019e76abafc8ae5081e2d0891340 | Trường An <andt@reapit.com> | refactor: #1327 Refactor Admin Dev Management using react-redux hooks (#1386)
- fdef34b02b931a8d61cf54f619e69371a4dcdc14 | Khac Vy <vytk@reapit.com> | chore: #1354 Update the confirm uninstall modal style (#1470)
- 4d22d2b3db6a0133c12219faf577a07c6f3f8d99 | Khac Vy <vytk@reapit.com> | Fix marketplace warning error (#1406)
- 6e6e9db3c8c4e9bcd355c7944415294a9584c69b | Vu Nguyen <nphivu414@gmail.com> | refactor: #1325 Refactor developer web hooks page using new react-redux hooks (#1399)* feat: #1325 Refactor developer web hooks page using new react-redux hooks
- a0107a92e7968a43e7d00df008cee42278752700 | Trường An <andt@reapit.com> | chore: #1412 clean up jest error, wearning (#1460)
- 84058bd65e254a3c12957d7e7edb11c2cccb3988 | Pham Hai Duong <duongph@reapit.com> | fix: #1217 apply fix chunk errors for entire apps (#1459)
- ca4480840cb476a5d4af57d8c511e200ac3b2370 | NghiaPham <nghiapn@reapit.com> | fix: #1424 Admin Portal landing page issue (#1445)
- 9154ced037dd127eae9f52965f85085c86dd4278 | Will McVay <wmcvay@reapit.com> | fix: hotfix on admin routing (#1449)
- 45e87bb5d66bde71aed4bf484d21165acbf762fd | willmcvay@pm.me <wmcvay@reapit.com> | fix: hotfix on admin routing
- 4fab6e547b0d2d9d0b098d69c8eb8285510372be | NghiaPham <nghiapn@reapit.com> | fix: #1210 #1206 - update render 'category', 'Desktop Integration Types', 'Private App' (#1366)
- 20a3017da674df18ca98bd93c657d57f7dad8a97 | Trường An <andt@reapit.com> | refactor: #1326 refactor Client Settings page using react-redux hooks (#1362)* refactor: #1326 refactor Client Settings page using react-redux hooks
- b7985c934b11410e3071430180f17ca96648a525 | Khac Vy <vytk@reapit.com> | fix: #1391 Fix warning error which display in marketplace (#1405)
- 469908c8b7bb0818880fb24b63d0f3ae865d4034 | Vu Nguyen <nphivu414@gmail.com> | fix: #1392 endless loading spinner on cost explorer page (#1404)* fix: #1392 Fix service chart loading issues
- 1109cc4a89dbcc242b13e216498d8784287dae49 | Cuong Vu <cuongvh@reapit.com> | fix: #1389 dead link search widget in elements (#1400)
- 1cb0e425c08e8e8caf5f5fa8e1eecc7dea29bf59 | Vu Nguyen <nphivu414@gmail.com> | fix: #1392 Hide loader after finishing fetching data in analytics page (#1398)
- ab31bf0793df083d6782a30a5d6fe6b9442eb328 | Pham Hai Duong <duongph@reapit.com> | fix: hot fix for private route (#1381)
- 317d47d5e7ceb6477e99ffdb16299793b3465aa1 | Pham Hai Duong <duongph@reapit.com> | refactor: #1327 refactor admin apps page (#1361)
- 75bd498a445ebb2baa0cb72594e99f5cb2b699cc | Pham Hai Duong <duongph@reapit.com> | fix: hot fix for private route (#1381)
- 195c0994cc242ac6b5fe5c2111039393a3988373 | Cuong Vu <cuongvh@reapit.com> | refactor: #1336 refactor private-route-wrapper (#1363)
- 11be3122b0e6d86f3786f920adfe1ff8040c558b | Trường An <andt@reapit.com> | refactor: #1326 refactor Client MyApps page using new redux-react hooks (#1358)
- bcbabc8b6f83a41129259bde15779599da5955b7 | Trường An <andt@reapit.com> | fix: #1033 update config button (#1365)
- cc3b7b34d8f595bebeb140ef7b1a25fd1697cbef | Vu Nguyen <nphivu414@gmail.com> | refactor:#1325 Refactor developer submit app page using react-redux hooks (#1356)
- f532998c12ccd65b09015189bf092e98428f5c8a | NghiaPham <nghiapn@reapit.com> | fix #1206: install uninstall button (#1364)
- e5405a58b7df1c9118c0c61416bde230a4250532 | NghiaPham <nghiapn@reapit.com> | chore: remove offline plugin + offline service worker of marketplace (#1360)
- 9e834432f1d1271d4c83014b2683059fe0af9aa5 | Cuong Vu <cuongvh@reapit.com> | fix: fix cypress auth (#1357)
- ce6ef75fe73a7b635d1f78ad2a1a450f141e6465 | Pham Hai Duong <duongph@reapit.com> | fix: 1217 chunk cache error (#1352)
- d9bcf325c0d1e9f3e87c9f1794d4feddbf65b0bc | Trường An <andt@reapit.com> | refactor: #1326 refactor client installed apps page using new react-redux hooks(#1338)
- 663bb21ebe2aa0fd4f367d9a18eaa9782805c42c | Trường An <andt@reapit.com> | feat: #1033 configure my web component installations in the Marketplace (#1313)* feat: #1033 configure my web component installations in the Marketplace* chore: #1033 add negotiators dropdown* chore: #1033 update app header, update snapshot* chore: #1033 fetch negotiators list* chore: #1033 update api* chore: #1033 update follow PR cmts* chore: #1033 fix test fail
- ef3291751489f1191063953ed16346fbc40bec50 | Cuong Vu <cuongvh@reapit.com> | chore: update snapshot to fix CI (#1348)
- 1a705580bf9f1d620479c642b42840f18b2b3830 | Cuong Vu <cuongvh@reapit.com> | fix: fix element page on mobile (#1345)
- 5ff9bd87dd0d5412774feab08aad7640d1db6933 | Trường An <andt@reapit.com> | refactor: #1326 Refactor client apps page using new react-redux hooks (#1334)* refactor: #1326 use useSelector, useDispatch in client page* chore: #1326 use useHistory, useLocation instead withRouter* chore: move page to specific folder* chore: update var name
- 3ef00944980db847f4f0d559086004230503ab32 | Pham Hai Duong <duongph@reapit.com> | refactor: #1328 remove mapStateToProps and change to hooks (#1337)
- 09f7cadd3c627d6f0ece0a54e58eb072957d5cd7 | NghiaPham <nghiapn@reapit.com> | fix: #1206 #1210 tweak standalone page css (#1335)
- 65c973a0173565bf0ddb129d18964db672866e5f | Cuong Vu <cuongvh@reapit.com> | fix: #1275 layout issue on mobile (#1332)
- 22020d39be7ee6f4304a7f519657b283c40c7199 | Vu Nguyen <nphivu414@gmail.com> | refactor: #1325 Refactor developer help page using react-redux hooks (#1329)* feat: #1325 Refactor developer help page using new react-redux hooks
- 4f7198062aedbdd38cec2b1b471593da613c4fab | Vu Nguyen <nphivu414@gmail.com> | refactor: #1174 Refactor developer home page using new react-redux hooks (#1321)* feat: #1174 Refactor developer home page using new react-redux hooks

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
-----------------------------------------------------------------------------

    

# Marketplace
### marketplace_v1.0.27 - 2020-05-29
  
Release: marketplace_v1.0.27
Rollback: marketplace_v1.0.26
Changes:
commit | author |description
  
- 45e87bb5d66bde71aed4bf484d21165acbf762fd | willmcvay@pm.me <wmcvay@reapit.com> | fix: hotfix on admin routing

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

## marketplace\_v1.0.26 - 2020-05-28

Release: marketplace\_v1.0.26 Rollback: marketplace\_v1.0.25 Changes: commit \| author \|description

* ab31bf0793df083d6782a30a5d6fe6b9442eb328 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: hot fix for private route \(\#1381\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.24 - 2020-05-22

Release: marketplace\_v1.0.24 Rollback: marketplace\_v1.0.24 Changes: commit \| author \|description

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.23 - 2020-05-22

Release: marketplace\_v1.0.23 Rollback: marketplace\_v1.0.22 Changes: commit \| author \|description

* 3d0fea7176d4e2993965192db6cff75f440af973 \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| refactor: \#1174 Refactor register page using new react-redux hooks \(\#1314\)\* feat: \#1174 Refactor register page to use new react-redux hooks
* a7122b92a0936b5d48291e9284dc64c54924c20d \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| feat: \#1210 \#1026 ui for developer/client side standalone \(\#1304\)
* 394f5f26073eeb0f5c58c843c02c18ac11af0d47 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| fix: \#1292 fix Toast should be full width in desktop mode \(\#1306\)
* 497b5eb924943859b3bde6db9cc15ebd64e4528f \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| fix: \#1290 Update login link in case clientId is existed \(\#1312\)\* feat: \#1290 Update login route in register page when clientId is existed
* 478179cd87d21b9f2e6339e4f1e54397b705be27 \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| fix: \#1300 Update text and links on developer webhooks page \(\#1311\)\* feat: \#1300 Update text and links on developer webhooks page
* a35834aa73d5c92490913a73acc56960ab43f6a2 \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| feat: \#1290 Fix issues with logging into dev and client portal \(\#1301\)
* e47980631cb27489a920c4e1715b87fe6203106f \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| fix: \#1300 Update text and links on developer webhooks page \(\#1302\) _feat: \#1300 Update text and links on developer webhooks page_ feat: \#1300 Fix lint errors
* 725f31eb4314f7380086f410257a94c8ce5e130c \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| feat: \#1174 Refactor login page to use useSelector instead of mapStateToProps \(\#1293\)\* feat: \#1174 Refactor login page to use useSelector instead of mapStateToProps
* 35b0cede2867318b0f72f64e78e64f7a212688ff \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1225 ui for mobile client side app \(\#1271\)
* 13ce3e5760d5efc56df85af0d1ab3823c157b410 \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| feat: \#101 Developers should be directed to information if trying to access the marketplace without a client Id \(\#1270\) _feat: \#101 Developers should be directed to information if trying to access the marketplace without a client Id_ feat: \#99 As a ‘Client’, I want to use my existing email address to also register as a ‘Developer’ so that I can use the same email address
* cc171c88234195b5c1694bb151aa72c4ed83e2c8 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: \#1012 hide install app button in app detail standalone page \(\#1280\)
* db13c2d88903a5a4c359c3b8be0d688d242b03aa \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1276 fix type definitions in ErrorBoundary \(\#1285\)
* dacb9af3ccf53658daa42a610394c73914867523 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: \#1277 Update wording on the Webhooks page in the Developers Portal \(\#1279\)
* 7d6f7574ad5c267afc7d87170e2d46730bfacc88 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: bump cognito-auth 2.1.5 \(\#1281\)
* bb22c7a21766c1d13c308433a0529e693a6c1ad3 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1221 add cloud alert for production env web apps \(\#1273\)
* 8c4c54632eb5a2057f6ad06bdc85abc30f240f18 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| refactor: \#1173 Step 1 - Move API calls to services folders \(\#1265\)
* f8e1c37affcd2d4cf688c937bad3572745e4a5d5 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1118 Client should see permission appropriate welcome on 1stlogin \(\#1269\)
* 0faa38e441e4e81e7728d0e47a22b7deb690e09e \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1012 Client without admin permissions should not install app \(\#1268\) _feat: \#1012 Client without admin permissions should not install app_ chore: \#1012 update variable name
* 73296981d70de416f5eb9b49c9901fda0befaf83 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1011 As a client who is not an admin, I should not see certain tabs in the marketplace \(\#1261\)\* feat: \#1262 Get the current user logged in phone number
* 1ffdc6c79895aaf95763f3bbc94a768da7ddbd82 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: \#1223 Update T&C developer register \(\#1255\)
* d06476c459131910d2d89c122c9ae1da211db4f0 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#1248 Remove submit app menu item. Create new app button in my … \(\#1253\)\* feat: \#1248 Remove submit app menu item. Create new app button in my apps page
* b6cba8e8da7886b868f4a3faf824c4317931c228 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#1231 Add pagination for transaction history \(\#1252\)
* 8cf9f28f23a04ab4e71dd68ddfb014cc4c9b3935 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: update placcholder html description \(\#1254\)
* 12cc29df7b22d6e0b23564aedba14109939572db \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| feat: \#1125 Standalone app page \(\#1240\)\* feat: \#1125: Create app details standalone page
* 318c19bb3fa08f9292c839ea48fbf424c1ce0403 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: \#1185 update "Ping" as hiperlink \(\#1250\)
* 4e0bd6ce1a5a5a25ba0d2534e44a8edb6ab5c184 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1143 transaction history billing csv download link format is incorrect \(\#1244\) _fix: \#1143 transaction history billing csv download link format is incorrect_ update typos
* 433aee1b898611dac3267fbbacfbcc8889adb897 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 strip out HTML when pasting \(\#1247\)
* a83fc0132e5dd6a7d8104c0dbc6a422e8b0f3f07 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: css issue manage app \(\#1241\)
* 8338fa8a7848fb8b0de658d3d03fffa390352307 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| chore: \#1232 add line text to cost explorer \(\#1237\)resolve \#1232Changes- Add line text "\*\* As our chargers are calculated in fractions of pence per transaction, very occasionally you may see a rounding discrepancy of more than £0.01 in the Cost Explorer."- Update snapshot
* 15442458c229092e9a5c33003c1a5cb5d27049e8 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1185 Add a 'Ping' feature to the Webhook Subscriptions \(\#1235\)
* ebe967eb25687f2507a431e51f1afff37df112b8 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: \#1159 add URL validate before submit webhook edit form \(\#1236\)
* c0a25c6ef8eebb0fbf61a9417782e2e56b4b973c \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| fix: Error when loading the billings page in the Developers Portal\(\#1233\)
* c007ed6468639fec14e5c07d71b938f1684cee36 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 update validation of textareaeditor \(\#1227\)
* 63ae65d6ef2f18f2d5c3fe52915c711447b7eebc \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: \#1145 minor fix for Y axis's legend of bar chart and change to netAmount instead of grossAmount \(\#1216\)Resolve \#1145Changes- Minor fix for bar chart Y legend- Change grossAmount to netAmount- Fix test
* 3e0d0c78e3e736d57e8bad8339b28ee206fdf1c6 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| feat: \#143 - Transaction History Update \(Billing/Analytics\) \(\#1167\)feat: \#143 - Transaction History Update \(Billing/Analytics\) \(\#1167\)
* 2c8346824813966245a4ab567e8ae43892396472 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 fix placeholder color, change H6 to H5 \(\#1194\) _fix: \#1160 fix placeholder color_ fix: \#1160 change h6 to h5 in desciption
* 142fe4bce1f49cc16156465d5a639d314c2cf191 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: \#1159 update webhook page \(\#1191\)
* 0f66915923551cff8440344ee013a627a78b9d80 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 HTML Description fields fixes \(\#1181\) _fix \#1160 WIP fixing  and_  fix \#1160 fixing  and \* fix: \#1160 rem instead of em
* c20bb78efd587d96a78d1d6c545f6ce1d87c9ba9 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1166 Cost Explorer \(Usage and Cost\) update \(\#1180\) _feat: \#1166 Cost Explorer \(Usage and Cost\) update_ chore: \#1166 update actionType name _chore: \#1166 update follow PR comment_ chore: \#1166 update file name
* 1568f527794bc8976fc8d9f6d8b0ae5d4b6c7cae \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1171 pagnination rps issue \(\#1187\)
* d7da78f6d3c41b05800692872944f4a228446059 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1159 Updates required to the Webhooks page in the Developers Portal \(\#1169\) _feat: \#1159 Updates required to Webhooks page in the Developers Portal_ chore: \#1159 update webhook table render _chore: \#1159 update reducer loading, add call api func as a service_ chore: \#1159 update route dispatcher webhook
* ac134898d1fe5d6f26e45a0918e9ae606c65e6ba \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1164 add SBOX to customer of subscription drop down \(\#1172\)feat: \#1164 add SBOX to customer of subscription drop down \(\#1172\)Changes- modify generateCustomerOptions for return correct value
* 533632f4e57d39a9ae17ab798573516416f1fa3a \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat:integrate api for billing bar chart \(\#1168\)Changes- Integrate api for billing bar chart- Write test- Refactor some places
* faaa7986543e32197ef0919e8b26ba737eb47790 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1122 redirect to the browse apps page if I have no installations \(\#1156\)
* 91fe077d165bd41afacbd3b5a5cb1fa1f7cf7d0e \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1006 \#979 create/edit webhook modal \(\#1140\) _feat: \#1006 \#979 create/edit webhook modal_ feat: \#1006 update list webhooks _chore: \#1006 update content type of header API call_ chore: \#1006 add type for variable\* chore: \#1006 add open webhook modal
* c9a2dac512ee7d90833f655c46bf71296f09735a \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| refactor: \#1145 refactor billing bar chart \(\#1154\)refactor: \#1145 refactor billing bar chart \(\#1154\)
* e503f3a3a269e9006b676f32028ffb41cfe1bc6b \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1123 render text editor instead of text area submit app \(\#1151\)feat: \#1123 render text editor instead of text area submit app \(\#1151\)
* 6cb9322c4d238377b98f41c9729a820f014fcf27 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix \#1065: re-instating purge unused s3 assets cronjob \(\#1134\)fix \#1065: re-instating purge unused s3 assets cronjob \(\#1134\)
* 349e86a308951fc723a519521e21468297c686c7 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1123 render renderHTML for diff compare of approval modal \(\#1153\)Changes- Add diff viewer for RenderHTML component
* ee76c1a2bde4981b580e949730869c95ae8686aa \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1123 render html for app detail \(\#1152\)feat: \#1123 render html for app detail \(\#1152\)
* 0669a9350761bca3723fa279e9b27c979d3ef587 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1062 Include date Created as a column on the Apps and Devs \(\#1147\)
* 897ee1ec8c9618555613f8d73670e0513184ee89 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1069 Update wording on the Analytics Dashboard \(\#1146\)
* cdb0a9c0b29ad10ccae29cb678e65487e3de1a14 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| chore: add sentry cli to push source map to sentry.io \(\#1136\) _chore: add sentry cli to push source map to rsentry.io_ chore: add IS\_RELEAASE env for sentry source map upload
* 40996bc76d4a829d4e623398076ec6bf89cc20f2 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1121 remove login type tab from marketplace's login page \(\#1135\)
* e3b5cdf3c889e5be9b1d3efdd67e09236617c865 \| Vu Nguyen [nphivu414@gmail.com](mailto:nphivu414@gmail.com) \| Feat: \#1104 - Update billing tab UI \(\#1141\)\* feat: \#1104: Update billing tab UI
* ea009069bb4e5153a9d51ca94ff6986fe5506959 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/1078 create cost explorer section on billing tab \(\#1115\)\* feat: \#1078 - Add cost explorer section to billing tab
* 2001628ce1ea9be4f4b27a3c6ad22058075357a2 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: \#1066 show image 5 for app revision submit \(\#1101\)Changes- Add upload helpers for image5- Fix test
* f6d395afc5f1476e09d4c33761fe347ec1872859 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#693 - increase webhooks page dropdown size, and load developer apps data \(\#1095\)
* 579d2c515ed2df63277cd77fcbc08a45a6c5c67e \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1065 fix loading chunk fail \(\#1092\)
* 8c36f7ec52fa78ed66194387647f2cf97152a808 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#1089 Update cost calculator table UI \(\#1096\)\* feat: \#1089 - Update total calculator table layout
* e066a95a96d0b11757156228788bdfddb20c97a6 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#973 implement developer list webhooks \(\#1081\)\* feat: \#973 implement developer list webhooks
* 3d2a2e09802fe9ea75232ec22b6402e57de14575 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1073 add axis label for service chart \(\#1093\)
* 78d9288bf4719e1e233966c12a985c821406b86d \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#1077 - Add Transaction History section to billing tab \(\#1087\)\* feat: \#1077 - Add Transaction History section to billing tab
* 5bb909159d8464ba2dde328cee22d94db06be701 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1073 create bar chart developer portal \(\#1090\)
* 7fed969c082458b3ca44628e9573143d7110a248 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat: \#714 - Create cost calculator on analytics billing tab \(\#1079\)\* feat: \#714 - Add cost calculator to billing tab
* fd52c8520f1d8765c727edd4f041da1335408295 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1068 updatecalculation total cost table in term and condition \(\#1080\) _feat: \#1068 updatecalculation total cost table in term and condition_ chore: set up test for web-components
* 32c244d40e83402b1443f61c04646e47ba8e1d64 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: \#1055 Temporary hide client T&C modal \(\#1058\) _chore: \#1055 Temporary hide client T&C modal_ chore: update navigate route
* 16c92eb246e4c2500fd5fe374bec149d79448e7a \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1009 serverless deployment for cloud apps \(\#1061\)Changes- Clone serverless.yml for cloud apps
* 1d307dad916b497ef3d6eb3e35510e5bafb3acfb \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| Feat \#963: Implement Developer Webhooks page \(\#1049\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.22 - 2020-04-23

Release: marketplace\_v1.0.22 Rollback: marketplace\_v1.0.21 Changes: commit \| author \|description

* 5e282514b01ca338f0b7b9f1d467f509abadb881 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1040 fix pending revision image missing \(\#1060\)
* d546c17255e322524c78deffc311aca2120a612d \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: Update agency integration type section text \(\#1047\) _chore: Update agency integration type section text_ chore: bump version cognito-auth 2.1.4
* 02b78b007c56ee2cfb5b25c2ddf1f026b444f0d2 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/956 search developer registrations by date \(\#1044\)\* feat: \#956 - Search developer registrations by date
* add5f492bd8998789fc2688f9ba2879c551341c4 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: \#957 can search just with date range \(\#1041\)
* 7324a2c675932d93f43d5b7978b2d13d0a705768 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1035 swagger link color \(\#1045\)
* fbfbe35221e217714a5d419f9d689f4c15ed6bc8 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#939 fix e2e tests \(\#1048\)
* 7fb4663aa09063dc790169191277efc42523d2ec \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#939 Web apps should have their own dev and prod cookie identifier \(\#972\)- Web Apps now have three different cookie identifiers `local`,`developement` , `production`, based on `config.json`- Some methods in `cognito-auth` now have an additional `appEnv?: string` param to work with cookie for different environments- Default `refreshSession` state in `redux store` now will be set after fetch `config.json`- Fix e2e tests login after changing cookie identifiers
* 220ffdd6fc928be16774ae046d391ecb3416de90 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#957search App Registrations by date in the Admin Portal \(\#1007\) _feat: \#957 As an ‘Admin’, I want to search for App Registrations by date in the Admin Portal_ chore: \#957update variable name
* 623453eacf3ddf616c5b7bbdf5c3287c415ef1e4 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| fix: \#932 Client ID not displaying on first page load - Client Portal \(\#967\)
* e60f9279bbc58cb6957dc5b14e64f23ea03014c5 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: fix filter app flow add delay \(\#949\)
* d18a36a985a4c13bf0939f1eb375dd0efc9c86a5 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#122 Fix admin login e2e test \(\#946\)
* 3d680814746fb5c62f83cc6acdd91ef164c98cfb \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#917 Desktop Integration in revision modal & Stabilize E2E tests \(\#941\)
* 88070783a538ef4bb2e5ad3c9983791b13db71ef \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: fix e2e test fail \(\#940\)
* 7538c11bda998f6ceed67153065eed10c29ffefa \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: \#122Integrate E2E tests \(\#924\)
* 83ff778d60ed33b8753dbc58bbaf53efdcced1f8 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#910: Fix whats new link in Help page \(\#926\)
* f5ec3ab4183ac308dc768b8e84a3b6fb29c75837 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#923: Fix analytic filter date params \(\#929\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.21 - 2020-04-15

Release: marketplace\_v1.0.21 Rollback: marketplace\_v1.0.20 Changes: commit \| author \|description

* d14b33d755b1d8a56d225f1a0a6c0cdc87f1c4e8 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Fix/905 update date filtering in analytics page \(\#914\)\* feat: \#905: Update date filtering in analytics page
* e9c804b5b5352a5ca3605f1e02eb83a98f23eec5 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#908 - Fix analytics page filter issues \(\#913\)
* 1eca438da329598593bed4755eb18c448c606deb \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#830 submit app with desktop integration types \(\#895\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.20 - 2020-04-14

Release: marketplace\_v1.0.20 Rollback: marketplace\_v1.0.19 Changes: commit \| author \|description

* c46b2f0dea3da7e6dc69667de1680fede5379f15 \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| fix: t and c update \(\#907\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.19 - 2020-04-14

Release: marketplace\_v1.0.19 Rollback: marketplace\_v1.0.18 Changes: commit \| author \|description

* f9c18b620fd39f9bcef20656f9ffc1aa15c6d48b \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#902 Issue with text on after registering as a Developer \(\#903\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## marketplace\_v1.0.18 - 2020-04-14

Release: marketplace\_v1.0.18 Rollback: marketplace\_v1.0.17 Changes: commit \| author \|description

* 75725d886427d0ce17aac4674724c9d60fe7a8f6 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: \#889 markerplace login button is misaligned \(\#894\)
* 0cc5a75de47265219216ced6c425357be0faadd1 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#792 remove developer term and condition from private-router-wrapper \(\#897\)
* 63a04c134a7ee04c726dceee7e435e765eff7334 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: \#883 remove text from submit & edit form \(\#885\)
* 10ab176102e609f7e63b0a33d937f8d9ff6bd8e5 \| Trường An [duongtruongan@outlook.com](mailto:duongtruongan@outlook.com) \| fix: \#732 Filtering should apply to all apps not just those on curr page \(\#882\)Co-authored-by: andt [andt@dwarvesv.com](mailto:andt@dwarvesv.com)
* bdf01a134a3aad4c3eb97088b3050d003965d30c \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#792 update snapshot \(\#880\)
* 9414fe4d4918751e10975d8dc11aa7d51093f509 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| feat: \#792 terms and conditions acceptance should be confirmed by developer API \(\#874\)feat: \#792 terms and conditions acceptance should be confirmed by developer API
* 1e494987f890526232bfa53a52cb2f36c739fa84 \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| fix: adds sandbox as filter to analytics \(\#878\)
* bb0df0a0a145573feb9aebbd8e1fea4c5920ca7e \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#849 link valid foundations-doc url via the iframe \(\#860\)\* feat: \#849 link valid foundations-doc url via the iframe
* 60de4013a36bf0fdc528b990eb5b6c106f64320d \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Fix: \#840 updates required to analytics tab \(\#861\)\* feat: \#840: Updates required to analytics tab
* c2beee62eda02b3e16eab41cdaf195ab17cb5b9a \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| feat: add question template \(\#857\) _feat: add question template_ feat: enforce template\* feat: enforces templates, updates template links
* 66c5d08b69f9d9b057dec1aa5a4c35bf682f9c35 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#838: Fix private apps validation \(\#839\)
* ef2f7f2eadd6f6923d45edc2ce2b5616a57c8c1d \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat \#712 + \#711 : Developer can see a list of enpoints and a graph showing my ‘Hits per Day’ \(\#836\) _mock redux_ mock redux _feat: \#712: Add traffic event table component_ feat: \#712: Upgrade react-table to stable version - Add Footer for table element _fixing typescript_ feat: \#712: Update developer endpoint list + chart _feat: \#712: Fix typo issues_ feat: \#712: Fix linting issues _feat: \#712: Fix linting issues_ feat: \#712: Update snapshot testCo-authored-by: nhalx [nhalx@reapit.com](mailto:nhalx@reapit.com)
* 127de142361e4490dfd750c64992566832eec8aa \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/755 developers can specify who can see their apps \(\#832\)\* feat: \#755: Fix private app title typo
* c382ab36061ebc22223bae497da7cb053b9e85e9 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/755 developers can specify who can see their apps \(\#827\) _feat: \#755: Add private apps section to submit app form_ feat: \#755: Devs can specify who can see their apps _feat: \#755: Update snapshot testing_ feat: \#755: Reword the validation - Fix submit app issues with whitespaces
* dfbdf4b5590d3b3387c7caa108536f5e0550d9f9 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#741 integrate api for view api key when app installed \(\#824\)Changes- Add fetchApiKey for installtion apps- Add test for fetchApiKey sagas
* 7788e9539ac58a936f38db74a13bcb37102f31c6 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#745 Add Settings menu for client \(\#793\)
* b424747713096bb293a257d7ce40749f12f15beb \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#741 ui for view api key of web componentts \(\#813\)Changes- UI for view api key of web components and tests
* f6501109cefc3140f2f928747990dd1e420d00a3 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat/755 developers can specify who can see their apps \(\#808\) _feat: \#755: Add private apps section to submit app form_ feat: \#755: Devs can specify who can see their apps\* feat: \#755: Update snapshot testing
* 490f0b13c8e6200cd7ba98810f15af74c6372e3b \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#739 cannot assign to readonly window.**REAPIT\_MARKETPLACE\_GLOBALS** \(\#800\)
* 8d3bd81c139e1a7f5e3e903f182faf1d156e54c5 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#739 The Cloud Apps should be testable in "Desktop Mode" \(\#784\)\* feat: \#739 cloud apps now testable in desktop mode
* f229847a63f34993c3c1e6b1c134b97cb3f0ca87 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| Feat: \#725 developer can filter detailed page to customize results \(\#777\) _feat: \#725: Refactor detailed tab_ feat: \#725: Update analytics filter form _feat: \#725: Update analytics page to use react redux hooks_ feat: \#725: Update detail tab test _feat: \#725: Update test for filter bar + filter form_ feat: \#725: Pump elements version _feat: \#725: Fix lint error_ feat: \#725: Fix naming convention
* f8cbc43b89b90594fb3c0a9b5f3c7b452e29500f \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#701 use window.location.href instead of navigateDynamicApp \(\#763\)
* 5037c84ce5c2ee3d1aecbc3be37a146366086dc9 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#701 refresh link incorrect, add param in navigateDynamicApp \(\#758\)
* b91719552a2da0fc5e69e2be92fc895ffa0dbef2 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#652 Upload CSV should validate before submit \(\#750\)\* feat: \#652 upload CSV should validate before submit
* 05f0e8d0898d6e7142b0acf3ffe925aa74bf57c0 \| Vu Nguyen [vunp@reapit.com](mailto:vunp@reapit.com) \| feat: \#710: Add additional tab option on analytics page \(\#748\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

