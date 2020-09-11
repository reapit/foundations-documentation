---
description: >-
  Below you will find a listing of the recent changes we have made to the Developer
  Portal application. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# Developer Portal
### developer-portal_v1.1.1 - 2020-09-11
  
-----------------------------------------------------------------------------
Release: developer-portal_v1.1.1
Rollback: developer-portal_v1.0.4
Changes:
commit | author |description
  
- 97649167f013988b14d73d0da9cf2c68f82866a3 | Vu Nguyen <nphivu414@gmail.com> | feat: #2612 style documentation page to look like elements (#2672)
- 4889a007fdcd38b7f4397a13b17011a37ac5c355 | Cuong Vu <cuongvh@reapit.com> | fix: #2535 Filter invite to show only once per email (#2646)
- 562fdd1e241baf70f3000da2539b1ba7b2546438 | Cuong Vu <cuongvh@reapit.com> | fix: #2576 update direct debit flow on billing (#2608)
- a563f3c13c3c71315ee6a2dea9bbd3e6d4fc9a59 | Cuong Vu <cuongvh@reapit.com> | chore: #2572 change to notification to display error (#2598)
- 17791c8b0bb36e62e11f7d1a531548253c39b4ac | Will McVay <wmcvay@reapit.com> | fix: #2579 unprotect routes (#2605)
- bf5a1f485ab21e20b9e98b46ae68d6f5056c2d79 | Trường An <truongan106@gmail.com> | feat: #2581 Update the ‘Existing Subscription’ modal for Developer Edition(#2585)
- 1b4950c03c8004d8426bceb68f6933b3fa478d7b | Will McVay <wmcvay@reapit.com> | fix: #2579 invite flow broken on prod (#2580)
- 921428f77f1543b0dce05892da823fd89fc34651 | Vu Nguyen <nphivu414@gmail.com> | refactor: #2520 Refactor submit app modal styles + global styles (#2577)
- 808bda4e6f97643213b265fb24e9481478f0f0d0 | Cuong Vu <cuongvh@reapit.com> | chore: #2553 cleanup all sentry error (#2573)
- c124159a6193ae9b09b2003a6a9c5f3c3a1acf3c | Vu Nguyen <nphivu414@gmail.com> | refactor: #2520 Refactor Standalone App Page + terms and condition modal styles (#2571)
- b171bbe1e061d4cad3825b129a5016cd0b3818ed | Pham Hai Duong <duongph@reapit.com> | fix: pipeline deploy web-components (#2565)
- fda0533aeb1689da92eb540cde4cf49ef4c76159 | Trường An <andt@reapit.com> | fix: change url validate (#2558)
- 14126994823ac30b9e13afb3f0e31927b5c50c02 | Vu Nguyen <vunp@reapit.com> | refactor: #2520 remove unused styles + refactor app revision styles (#2554)
- 558f9489c91a9881c0dc1fa08a3ffeefcbf30486 | Vu Nguyen <nphivu414@gmail.com> | fix: #2520 - Refactor app list + analytics page styles (#2539)
- 5357bd89b757fd2ff3486ac474a50e70f25d377c | Pham Hai Duong <duongph@reapit.com> | chore: #2519 remove release:dev command (#2533)
- 8e180e732deb1fc7b90862eb4b831f58dcd20dc9 | Pham Hai Duong <duongph@reapit.com> | chore: #2519 update dev pipeline to deploy new infra (#2532)
- fce1e778df6a238310093c5ae73ceb416a19c964 | Will McVay <wmcvay@reapit.com> | fix: #2396 various tweaks for prod (#2516)* fix: #2396 various tweaks for prod* fix: fixes a test
- 594f9ccd384dd4220cd2b7b6d1a56b0a3ef1a618 | NghiaPham <nghiapn@reapit.com> | fix: #2402 tweak developer portal ui (#2513)
- e3284a1ab85b10239b58c26a8a79f4b982db8a0f | NghiaPham <nghiapn@reapit.com> | fix: #2492 disable account status checking when delisting app (#2498)
- 444be3e6d331fbbf4526d354ca67ae04fd0dcf97 | Cuong Vu <cuongvh@reapit.com> | chore: #2494 Update the modal when the account status is not confirmed (#2508)
- 1bc2046cbba518a620d651bca587a2cdab37e1fd | Trường An <andt@reapit.com> | feat: add * to require fields in organisation tab (#2503)
- 2d3e14d31835102b34f49d142987994321cf77f1 | Will McVay <wmcvay@reapit.com> | feat: #2396 prod tidy up (#2499)* fix: #2396 various prod fixes* fix: #2396 various prod fixes* fix: #2396 bumps a version number
- 9ac0998a80e037fcc750759f3241ed8be5926c48 | Pham Hai Duong <duongph@reapit.com> | fix: bug on upload images ui button (#2496)
- 52154fa4a140ab92b6d35aafa6b83909985adf71 | Khac Vy <vytk@reapit.com> | chore: #2476 identify chatlio when identity available (#2493)
- 3bd636dae893ea2351f77cedc5c60c57267c591d | Pham Hai Duong <duongph@reapit.com> | fix: #2479 upload image button error (#2489)
- 2034ec4e621008d564ac2603ba3892fd8c2b100d | Khac Vy <vytk@reapit.com> | fix: #2476 fix chatbot show multiple times on developer portal (#2487)
- a821b448bbf63db3f99e8722183ee4106cdf4cf6 | Pham Hai Duong <duongph@reapit.com> | fix: #2451 land on page not found (#2483)
- 40db9a7fbb4487d72012675aee01b7a586578c19 | Trường An <andt@reapit.com> | chore: rename SBOX client name (#2481)
- 0cf841f6cebeb9ea5953a3077130420fea2664db | Will McVay <wmcvay@reapit.com> | fix: #2467 upped the clock drift on connect session, few other small tweaks (#2474)
- 6cbe9ce6582060ab19104caefd21639d597fdb4a | Will McVay <wmcvay@reapit.com> | fix: #2467 fix CPU variance issue (#2473)* fix: #2467 fix CPU variance issue* fix: adds headers for auth
- e04da4e22e2a5141ca4653ea7236f8511d899cff | Will McVay <wmcvay@reapit.com> | feat: #1013 update prod auth flow (#2472)
- 978039a4b042068511ff3e83cce69100fa8e67c0 | Vu Nguyen <vunp@reapit.com> | fix: #2464 - Fix registration success message styles (#2466)
- 960ae53a073ac688b43a832b29ab908d8d1e0eec | NghiaPham <nghiapn@reapit.com> | chore: #2402 ui updates tweaks to the developers portal (#2441)
- e740a4b98f92782d0dc57cbf5f94a6870cd39b9c | Trường An <andt@reapit.com> | add SBOX as installation if no installation (#2470)
- 0d41e8d5e5f01326ac4e84f9db7efa8efab8bef3 | Pham Hai Duong <duongph@reapit.com> | fix: #2451 land on page not found bug (#2462)
- 9ea0c1b6b56ac2142da3dad35316328314bcaa56 | Cuong Vu <cuongvh@reapit.com> | fix: small texts fix (#2458)
- fcc73661e9a7e23f514f2465893cbf8c3811c4a2 | Trường An <andt@reapit.com> | feat: #2401 Update the 'Client' drop down to show Customer Name & Customer ID(#2446)
- 2368fd3d2efae0f6a78fccac8030d0708e59350b | Trường An <andt@reapit.com> | chore: update no company checkbox on organisation setting (#2432)
- f8d7da00752f67aa86e8e640cb7f7fd2040d391f | Trường An <andt@reapit.com> | chore: update edit app description length validate (#2437)
- a31c7004e16020e94e658c4c9d665960f13df27e | NghiaPham <nghiapn@reapit.com> | feat: #2145 expand graph ql service service for works orders entity (#2411)
- e8b00f1a65a4cad7aee537539c931c148b06709c | Pham Hai Duong <duongph@reapit.com> | chore/change-deploy-serverless-scripts (#2435)
- ed6f849fc387556b3752fac07329521d32d32780 | Trường An <andt@reapit.com> | feat: update invite again link (#2424)
- 33cdde00d03d2c348b90315cb9f0c1811736c9db | Will McVay <wmcvay@reapit.com> | feat: #2396 prod infra (#2420)* feat: initial tweaks to build script* feat: moved serverless modules to project root* feat: #2396 update slack bot (#2408)* feat: updated serverless for all go live apps* feat: #2396 deployment scripts (#2414)* feat: #2396 upload tar scripts* feat: #2396 fetch artifact scripts* feat: #2396 deployment scripts* feat: #2396 fix serverless config* chore: add deployment script by serverless* feat: #2396 add remove serverless* feat: small tweak to bucket nameCo-authored-by: Pham Hai Duong <duongph@reapit.com>
- 51ce54bf6c4e679515947ca0c045f6755508d2be | Cuong Vu <cuongvh@reapit.com> | fix: #2399 update installations table (#2415)
- ccc7b92993233a60c5cc7ad79783bf5942c69248 | Khac Vy <vytk@reapit.com> | chore: #1970 Add helper text for the 'Cost Explorer' (#2418)
- 1bf91df1c47bac23835b45900caa005ca363fb2a | Khac Vy <vytk@reapit.com> | chore: #2397 Update 'Welcome Wizard' content in Developers Portal (#2416)
- a606e37d333a6d14f80fe789bc43d03abc8d2436 | Khac Vy <vytk@reapit.com> | chore: #2385 update condition typo (#2417)
- ad5ec1feee98f23391d57f1198844f5d246493d6 | Khac Vy <vytk@reapit.com> | feat: #2385 Update ‘Disable’ link for members (#2410)
- 65272b5ff19eaba5ecfb3f896aba039678a33fed | Trường An <andt@reapit.com> | feat: #2384 Update ‘Set as Admin’ link on Organisations tab in Developers portal (#2406)
- 768f5f82069ae2a6d753846018afeebf0da88593 | Pham Hai Duong <duongph@reapit.com> | fix: #2372 sentry error type error when invite member (#2404)
- 049897d9aba35d105038d6c156568ed380b01200 | Will McVay <wmcvay@reapit.com> | fix: #2274 login bug fixed (#2392)
- 741393295a6505179314a4068913f607e557d4d3 | NghiaPham <nghiapn@reapit.com> | chore: #2329 add a helper notification on the billing page and disable fields until organisation have been complete (#2363)
- eea81089a5dcb9f0e90e11f16fe0bfe03865074f | NghiaPham <nghiapn@reapit.com> | feat: add show the about developer section developer preview page (#2365)
- 8fc557a951b48563857c37bf5a4d5c2e619e2042 | Will McVay <wmcvay@reapit.com> | fix: #2274 fixed passing state when refreshing and when query exists … (#2382)* fix: #2274 fixed passing state when refreshing and when query exists in URI* fix: #2274 handles root behaviour for developer portal
- 73af49f9711c4ec149d073275ca5133ef6e534d8 | Will McVay <wmcvay@reapit.com> | feat: #2274 verify id token (#2375)* :feat: #2274 validating id tokens WIP* feat: connect session now verifies id tokens. Needs testing and applying to apps* feat: adds and updates tests* fix: removed bug caused by console* feat: applied new Connect Session to apps* feat: tested and fixed a couple of bugs
- 440b4b73a8422c072fcb5a4d12245e297ac1fffa | Pham Hai Duong <duongph@reapit.com> | fix: #2260 show the organisation billing tab (#2368)
- 8b06e93dfb5c3e7bb69305f52fcfdc374644978e | Pham Hai Duong <duongph@reapit.com> | feat: #2331 add notification for developer after list an app (#2344)
- 1af473b58fc0950ee4cd2dbfa97a9d9378eee766 | Pham Hai Duong <duongph@reapit.com> | feat: #2346 hide transaction history if there is no transactions (#2361)
- c39a6143b40f7220fc33da40f877f1a3db893e9c | Cuong Vu <cuongvh@reapit.com> | fix: #2325 developer's profile page show wrong information (#2353)
- 8ee9b0271f55b2e725b2f6c5504afc10709992c5 | NghiaPham <nghiapn@reapit.com> | fix: #1987 hide direct debit helper text when status is pending (#2351)
- bf4964e09e8c8bc56ecb37069d0b357e9df5097c | Pham Hai Duong <duongph@reapit.com> | feat: #2328 update organisation tab ui (#2349)
- a91fb5f08d819dede3acf9dfaa8171adb1376b39 | Pham Hai Duong <duongph@reapit.com> | fix: #2346 transaction history bug (#2352)
- 6edd0c030eeaf299c0b2cf5723583fe7f9ea8ac8 | Khac Vy <vytk@reapit.com> | chore: #2330 update billing tab, add helper text (#2347)* chore: #2330 update billing tab, add helper text
- 7d5cfd82f4c44da4c56d86e77ddbef60ce65f90c | Snyk bot <snyk-bot@snyk.io> | [Snyk] Upgrade react-table from 7.2.2 to 7.3.0 (#2319)* fix: upgrade react-table from 7.2.2 to 7.3.0Snyk has created this PR to upgrade react-table from 7.2.2 to 7.3.0.See this package in npm:https://www.npmjs.com/package/react-tableSee this project in Snyk:https://app.snyk.io/org/reapit/project/fb568965-bd93-4bc6-9a64-9b23b0c87308?utm_source=github&utm_medium=upgrade-pr* fix: fixed tests and verified react-table good to merge update* fix: snapshot failed on CI* fix: small tweak to fix a configCo-authored-by: willmcvay@pm.me <wmcvay@reapit.com>
- 99b05e9dc88b2db940781e36aed153f666839a2e | Will McVay <wmcvay@reapit.com> | feat: #2248 update parameter store (#2342)* feat: WIP* feat: basic cli working - need to tidy up and fix edge cases* feat: lots of cli refinements* feat: all working, just needs testing and formatting JSON output* feat: all tested working and has docs* feat: published v2.0.1* feat: #2248 updates packages to use new config* fix: a couple of fixes for standalone mode
- c129e15f5aa6650a29e90ceed2e1337d5061c9df | Pham Hai Duong <duongph@reapit.com> | feat: #2260 change method to check role by email (#2335)
- 6810d4a0446f73d7ca29cd81f60fad14c5e49a70 | Cuong Vu <cuongvh@reapit.com> | fix: fix sentry non-error (#2318)
- d612e229a52889877861b36dc1627d6538a2a827 | Vu Nguyen <nphivu414@gmail.com> | fix: #2295: Fix create app wizard modal on close issues (#2313)
- 88d5964028ef34a9c975f39381cbfed9c815fa85 | Cuong Vu <cuongvh@reapit.com> | fix: #2294 change password error notification (#2311)
- 4c263989b455d9a7c39af7981ddf83edfeba2464 | NghiaPham <nghiapn@reapit.com> | fix: #2297 enhancement for loading of analytics pages (#2308)
- bc73744e4e2e0ec17979b7e2f7e550627c8d1d25 | Pham Hai Duong <duongph@reapit.com> | fix: #2292 bug on create new app (#2310)
- a59adec4d1f57c834ca4f286eda0e3129fd34d96 | Trường An <andt@reapit.com> | fix: Pending revision modal should loading when open #2293 (#2302)
- 59d783cad2eb551dc16930c69f39c49ea6640690 | Cuong Vu <cuongvh@reapit.com> | fix: #2287 Update App listing header for marketplace & dev (#2301)
- 80c11be0d8c765f0baea25d4e717381d86f086e1 | Pham Hai Duong <duongph@reapit.com> | feat: #22600 billing and organisation only show admin (#2299)
- 2471cc5427fc5fd7242b41aa8bbfac2cd537d4d2 | Pham Hai Duong <duongph@reapit.com> | chore: update snapshot (#2291)
- 91c7ee14c7b8ab3943dad9dafae66754b21b4ed7 | Pham Hai Duong <duongph@reapit.com> | feat: #2260 show the organisation for admin only (#2279)
- 936317a4f7d6564e833002c5445ad5e7738dc6ef | Pham Hai Duong <duongph@reapit.com> | fix: #2251 remove warningin analytics page (#2285)
- 47cc9458c128b583b1519f525c70ba39c4be3454 | Vu Nguyen <vunp@reapit.com> | refactor: #2097 clean up redux state tree for developers in dev portal (#2270)
- f61a9f2b6e9a4feb1318df90490d51383486408c | Cuong Vu <cuongvh@reapit.com> | feat: #2215 download CSV in cost explorer (#2275)
- 320e5a17b16049a35f0dff243a4cd754f880ed37 | Trường An <andt@reapit.com> | refactor: #2242 Clean up state tree for Installations (Developer Portal) (#2263)
- d189d25dd82a3afa5635700c15fb8535d71cd574 | Pham Hai Duong <duongph@reapit.com> | refactor: #2241 clean up http traffic (#2271)
- f1fa48357f384f0b71a6665c057697270b8c5316 | Khac Vy <vytk@reapit.com> | fix: #2261 Create New App wizard has double close option (#2267)
- 3a37793012e88d7cefc51529400f2cf3a5a72fae | NghiaPham <nghiapn@reapit.com> | fix: #1987 update billing page (#2262)
- ef965d35a930011c3b0273b73801dd4574c60d53 | Pham Hai Duong <duongph@reapit.com> | refactor: #2240 clean up webhoook edit (#2266)
- 82db6237319cabe7cf14f18479a74388b5cd41e3 | Vu Nguyen <vunp@reapit.com> | refactor: #2097 clean up redux state tree for revisions entity in dev portal (#2264)
- 67adc0baad8497859aaa14bc1e69fd87b35ed290 | Pham Hai Duong <duongph@reapit.com> | refactor: #2240 web hooks subscriptions (#2259)
- 631f5174b839066dcee424a5b01209a6e8a5ec8e | Pham Hai Duong <duongph@reapit.com> | refactor: #2240 refactor web hooks topics (#2245)
- 13732f86e7a0b9dfedf0afdeeb64c6bd4957b98e | Vu Nguyen <vunp@reapit.com> | refactor: #2097 Clean up redux state for Revision Detail dev portal (#2246)
- 8d20603bf891c56b77e75b19bfaf5901fb19a4ec | Vu Nguyen <vunp@reapit.com> | refactor: #2097 Refactor redux state, action, reducer, sagas for delete app flow (#2239)
- 944cc353f6980631f9db554f0d6270c5a43874e2 | Vu Nguyen <vunp@reapit.com> | refactor: #2097 Refactor redux state for submit app, categories, desktopIntegrationTypes, scopes (#2233)
- 47858ea82ae36229ad2e12f14132efbb771fcb94 | Trường An <andt@reapit.com> | feat: add a ‘login’ button the Invite ‘success’ modal (#2223)
- d9992507c332cfee5cc5011f80923bbbd1f90259 | Cuong Vu <cuongvh@reapit.com> | fix: #2204 Scrollbar in developer swagger page (#2219)
- d77cd7faa371522fe24e3d6219ddd4d9a4fdb8dc | Trường An <andt@reapit.com> | feat: #2126 Developer Portal should be refactored to use new Connect Session Auth module (#2193)
- 99117106858a3bbd883fcc5f6df628e2d12b6a0b | Cuong Vu <cuongvh@reapit.com> | feat: #2191 validation for organisation and billing tab (#2210)
- 8580b5c9a155c5cae36a44526e32479269b8ab17 | Trường An <andt@reapit.com> | chore: #2096 update modal v2 header style (#2203)
- 06e95725e307b7be6a5af8c951b5b954ca5dd75e | Vu Nguyen <vunp@reapit.com> | refactor: #2104 Refactor redux state, actions, saga, reducer for Apps entity (#2201)
- 345140ff2bb07db84b669971c903d8ecdb3d1e43 | Trường An <andt@reapit.com> | chore: #2096 update header modal style (#2176)
- e8cf6e63f9a19bbc3857837eabbcc253bb2fac58 | NghiaPham <nghiapn@reapit.com> | fix: #1987 add pending text when status pending and has reapit ref (#2170)
- 4a3c73ef5287f0c544061b1882d240b8336cc309 | NghiaPham <nghiapn@reapit.com> | fix: #1987 update reapit ref: set status when submit, disable if status not incomplete (#2165)
- f2b79c16b8904c4697f40312bcb4218b2d86b8fe | Pham Hai Duong <duongph@reapit.com> | feat: #2095 add job title field for invite modal (#2160)
- ceded1bb990ed2e030fea0bf54102659ca71a4eb | Trường An <andt@reapit.com> | feat: #2096 Create a direct route to the Developers Portal to action an Invite(#2152)
- c0df832111dfd6138a4280f03997057e7775e335 | Vu Nguyen <vunp@reapit.com> | feat: #1882 Update services chart legend layout (#2143)
- f3eba82db9857d4d4fd0d01dd441aab9720927b6 | Pham Hai Duong <duongph@reapit.com> | feat: #2095 invite new member (#2124)
- 92dffdadfcc36ecf240e9363deb3c63faceadda5 | Trường An <andt@reapit.com> | feat: #2094 Update ‘Members’ section to endpoints (#2110)
- b4a490b59b1ebb60c515fbf00ba87a57098d6c93 | Will McVay <wmcvay@reapit.com> | fix: #2111 fixes app preview (#2113)
- 117099f5e902da05529d3d05bddd37a9161705ba | willmcvay@pm.me <wmcvay@reapit.com> | fix: #2111 fixes app preview
- 11923e7c284b72240d9e87307c796dbc29725e0f | Cuong Vu <cuongvh@reapit.com> | feat: #2011 Add Modal responsive variant & apply to billing debit modal (#2106)
- 71c29a7230caca6e2e74fcf7dee7601f91c9538b | NghiaPham <nghiapn@reapit.com> | fix: #1987 update billing page (#2082)
- 55612ba81f878cd2fe7c3ea3f9948de5bed29dbb | Trường An <andt@reapit.com> | feat: #2025 update billing page admin portal (#2080)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
-----------------------------------------------------------------------------

    
### developer-portal_v1.0.4 - 2020-07-20
  
-----------------------------------------------------------------------------
Release: developer-portal_v1.0.4
Rollback: developer-portal_v1.0.3
Changes:
commit | author |description
  
- 117099f5e902da05529d3d05bddd37a9161705ba | willmcvay@pm.me <wmcvay@reapit.com> | fix: #2111 fixes app preview

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
-----------------------------------------------------------------------------

    

