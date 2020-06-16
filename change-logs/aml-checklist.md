---
description: >-
  Below you will find a listing of the recent changes we have made to the AML
  Checklist App. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# AML Checklist
### aml-checklist_v1.0.5 - 2020-06-16
  
-----------------------------------------------------------------------------
Release: aml-checklist_v1.0.5
Rollback: aml-checklist_v1.0.4
Changes:
commit | author |description
  
- b2d19a5db019e8926dd358fb47f397fb9fd3441c | Khac Vy <vytk@reapit.com> | fix: #1727 fix birthday field validation (#1738)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
-----------------------------------------------------------------------------

    

## aml-checklist\_v1.0.2 - 2020-05-28

Release: aml-checklist\_v1.0.2 Rollback: aml-checklist\_v1.0.1 Changes: commit \| author \|description

* 663bb21ebe2aa0fd4f367d9a18eaa9782805c42c \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1033 configure my web component installations in the Marketplace \(\#1313\) _feat: \#1033 configure my web component installations in the Marketplace_ chore: \#1033 add negotiators dropdown _chore: \#1033 update app header, update snapshot_ chore: \#1033 fetch negotiators list _chore: \#1033 update api_ chore: \#1033 update follow PR cmts\* chore: \#1033 fix test fail
* 65c973a0173565bf0ddb129d18964db672866e5f \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1275 layout issue on mobile \(\#1332\)
* 03d6a705d505f45d5b269769fa4a4b6396c75d9b \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| fix: \#964 add extension for download file \(\#1318\)\* fix: \#964 add extension for download file
* 207be384959f958fd73562b123ee81c606583849 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| fix: \#964 fix unable to view an uploaded file in AML \(\#1286\)
* db13c2d88903a5a4c359c3b8be0d688d242b03aa \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1276 fix type definitions in ErrorBoundary \(\#1285\)
* bb22c7a21766c1d13c308433a0529e693a6c1ad3 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1221 add cloud alert for production env web apps \(\#1273\)
* 0f66915923551cff8440344ee013a627a78b9d80 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 HTML Description fields fixes \(\#1181\) _fix \#1160 WIP fixing  and_  fix \#1160 fixing  and \* fix: \#1160 rem instead of em
* 6cb9322c4d238377b98f41c9729a820f014fcf27 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix \#1065: re-instating purge unused s3 assets cronjob \(\#1134\)fix \#1065: re-instating purge unused s3 assets cronjob \(\#1134\)
* cdb0a9c0b29ad10ccae29cb678e65487e3de1a14 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| chore: add sentry cli to push source map to sentry.io \(\#1136\) _chore: add sentry cli to push source map to rsentry.io_ chore: add IS\_RELEAASE env for sentry source map upload
* 579d2c515ed2df63277cd77fcbc08a45a6c5c67e \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1065 fix loading chunk fail \(\#1092\)
* 16c92eb246e4c2500fd5fe374bec149d79448e7a \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1009 serverless deployment for cloud apps \(\#1061\)Changes- Clone serverless.yml for cloud apps
* aea4ce8c2597c96cac1b8350cff6b75628ebc737 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#939 Web apps should have their own dev and prod cookie identifier \(\#972\)- Web Apps now have three different cookie identifiers `local`,`developement` , `production`, based on `config.json`- Some methods in `cognito-auth` now have an additional `appEnv?: string` param to work with cookie for different environments- Default `refreshSession` state in `redux store` now will be set after fetch `config.json`- Fix e2e tests login after changing cookie identifiers
* 55121f4404e422b4c32eb5caa6dc6d2ead7c734b \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#739 cannot assign to readonly window.**REAPIT\_MARKETPLACE\_GLOBALS** \(\#800\)
* 4640dfc24649fabd6e1552ec4d2f385996c06c0b \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| feat: \#739 The Cloud Apps should be testable in "Desktop Mode" \(\#784\)\* feat: \#739 cloud apps now testable in desktop mode
* c8c3fb21ec515a2448f6fcab11b0bb7b937a793c \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| fix: aml app should not redirect if already on correct route \(\#789\)
* ebdbabcf922f4ae405ede602f208390b7eff9a31 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#700 - Update the 'Desktop Search' URL to use the correct App ID \(\#727\)\* fix: \#700 - Update the 'Desktop Search' URL to use the correct App ID
* 47f00e3f6c4027f2f31a97217ab1723e750cab49 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: \#568 react scaffold after migration to config.json \(\#693\)Changes- Add export default app.tsx- Change index.tsx to remove import index.scss
* ee97cdcf89809d86520c9167f9ca361c0c2d040a \| leXuanNha [xuannhak13@gmail.com](mailto:xuannhak13@gmail.com) \| fix: \#596 condition to check completed status \(\#672\) _fix: condition to check completed status \(\#596\)_ chore:\#596 add more test casesCo-authored-by: Duong Pham [duongph@reapit.com](mailto:duongph@reapit.com)
* 8cb838c1debdde691158f4cf37a4f9a723561918 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| chore: \#629 migrate config of apps to config.json \(\#644\)chore: \#629 migrate config of apps to config.json \(\#644\)
* dd5698ca3c621824a2fd2f87838902bfdefeda65 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#597 updates to desktop interaction for cloud apps \(\#646\)\* fix: \#597 updates to desktop interaction for cloud apps
* 356af658d03bf57fa614417508c1de4f73bdd898 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#601 invalidate chunk when deploying to dev/prod \(\#624\)
* 3b061ac760ec179629c7442a3b984de50d5ba6a3 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#573 - Update the CSS to address header issue in AML \(\#621\)
* 107a01e239753ef5c6df6186ad1760a087394da1 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#572 Incorrectly sending the DOB when updating the Address History \(\#620\)
* 475a30042f49816aea761f5f203a45a5ad0d31ec \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feature: \#550 add app version to login page \(\#553\) _feat: \#550 add app version to login page_ feat: add app version to elements story-book
* 332f9117afa16897e23bd9456f3e1f3093c69eee \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: \#473 GraphQL Server Refactor \(\#548\)\* chore: \#473 refactor graphql server
* 61089130421ebd98571fd267394df9f296879d90 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: fix failing pipeline \(\#521\) _fix: reconstruct packages depedencies, fix webpack.sass not throw errors_ fix: add todo comment, remove unused config, add sentry\_log\_level\* fix: remove SENTRY\_LOG\_LEVELS env, add to sentry webpack plugin instead
* 3f2f1550f55d5e855545958d55b2a2a8b0b83c91 \| NghiaPham [nghiapn@dwarvesv.com](mailto:nghiapn@dwarvesv.com) \| chore: \#368 Add resolver for graphql server to call appointment services \(\#389\)
* c981027bedb5e4f8ebb8431f1523016ba52fcc87 \| Pham Hai Duong [tanphamhaiduong@gmail.com](mailto:tanphamhaiduong@gmail.com) \| chore: \#128 remove redundant and restructure dependencies \(\#451\) _chore: \#128 remove redundant and restructure dependencies_ chore: resolve all warning on build console _chore: resolve warning peer dependencies for install by yarn_ fix: resolve package cognito-auth in cognito package\* chore: remove query-string dependency
* a4ce3139f4e52e17bc6aa8d0671e77c883b6cef5 \| Cuong Vu [vuhuucuong1310@gmail.com](mailto:vuhuucuong1310@gmail.com) \| chore: \#125 improve webpack bundling performance \(\#445\) _chore: \#125 \(POC\) improve webpack bundling performance locally_ chore: \#125 add mode for webpack dev _chore: \#125 resolve conflicts_ chore: \#125 graphql-server add tsconfig path to cognito-auth _chore: \#125 update pullrequest pipeline to include cache build_ chore: \#125 update pullrequest pipeline to include marketplace cache _chore: \#125 correct cache keys_ chore: \#125 first build test \(expected to take long time\) _chore: \#125 concurrently build in elements_ chore: \#125 second test _chore: \#125 remove duplicated --parallel flag_ chore: \#125 ignore .temp folder _chore: \#125 remove babel-loader built-in cache_ chore: \#125 finish pipeline _chore: \#125 test pipeline_ chore: \#125 readd sass temp _chore: \#125 add jest cache_ chore: \#125 refactor & finish _chore: \#125 finish both ci/local cache settings_ chore: \#125 fix hooks not run\* chore: \#125 fix echo & cp not working in windows
* 8774e3a2d5a5b499468fb5f291e86c971fc50431 \| Pham Hai Duong [tanphamhaiduong@gmail.com](mailto:tanphamhaiduong@gmail.com) \| chore: \#337 update readme of packages \(\#340\) _chore\(readme\): \#337 update readme of packages_ chore: bump version for react-app-scaffolder
* f90cefee831f12221e9a753da107f5c7c74f1284 \| NghiaPham [nghiapn@dwarvesv.com](mailto:nghiapn@dwarvesv.com) \| \[WIP\]Chore/33 update react scalfolder \(\#224\) _temp_ temp _chore: \#33 update marketplace-api-schema.ts file_ chore: \#230 Update scaffolder styles solutions \(\#259\) _temp_ temp _chore: \#230 Update scaffolder styles solutions_ chore: \#230 Update .gitignore _chore: \#230 update types fileCo-authored-by: NghiaPham_ [nghiapn@dwarvesv.com](mailto:nghiapn@dwarvesv.com) chore: \#227: scaffolder option no redux \(\#268\) _chore: \#244 Update base files of the scaffolder_ fix .gitignore _update schema file_ update snapshotCo-authored-by: Khac Vy [khacvy93@gmail.com](mailto:khacvy93@gmail.com)Co-authored-by: Dan Nguyen [45675930+danndz@users.noreply.github.com](mailto:45675930+danndz@users.noreply.github.com)
* dae085a119d5816b7ad65819fdf62d4d762589f6 \| Cuong Vu [vuhuucuong1310@gmail.com](mailto:vuhuucuong1310@gmail.com) \| fix: \#262 date of birth correct format YYYY-MM-DD \(\#269\)
* a97fc457b901c99d4420fd5cbcf4611f13b0ca5b \| NghiaPham [nghiapn@dwarvesv.com](mailto:nghiapn@dwarvesv.com) \| chore: \#116 \#117 update ts-definition pipeline, scripts \(\#226\) _chore: \#116 \#117 update ts-definition pipeline, scripts_ chore: lock version of package "foundation-ts-definition" for all apps. update PR comment _fix_ update elements package to include foundation definition\* remove password param from test

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

