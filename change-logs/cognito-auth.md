---
description: >-
  Below you will find a listing of the recent changes we have made to the
  Cognito Auth package. This includes details of any bugs that have been fixed
  or features/enhancements that have been added.
---

# Cognito Auth
### cognito-auth_v3.0.0 - 2020-07-31
  
-----------------------------------------------------------------------------
Release: cognito-auth_v3.0.0
Rollback: cognito-auth_v2.1.10
Changes:
commit | author |description
  
- 8afc7aba66d4f588f7ccea40c44d6ca4b4c579d9 | Will McVay <wmcvay@reapit.com> | fix: #2023 tweaks to go live with NPM (#2244)* fix: tweaks to go live with NPM* fix: fixed defintions
- 21944479c9e26dfe143709e22456d75e54629248 | Will McVay <wmcvay@reapit.com> | feat: #2023 NPM packages v1.0.0 (#2234)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
-----------------------------------------------------------------------------

    

### cognito-auth\_v2.1.10 - 2020-07-27

Release: cognito-auth\_v2.1.10 Rollback: cognito-auth\_v2.1.7 Changes: commit \| author \|description

* 7493826dbe7b0eeab3192a8549b89abe05f62c0a \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: bump cognito-auth 2.1.10 \(\#2181\)
* e5bc1b73bf172a357f42d520c31fcb15d0e236cc \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: \#2032 NPM broken badges, use absolute paths instead \(\#2179\)
* 75025e7dc36f24ddcd81497d34e6c8a0c164f1ed \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| chore: \#2032 elements & cognito-auth & connect-session badges broken \(\#2171\)
* 300e3790d2f6e9ec4407d897c198a2f282456723 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: \#2026 scroll bar at element level \(\#2060\)
* e9c775e794cd380746fc6a3de9dc6c942b59e3a1 \| NghiaPham [nghiapn@reapit.com](mailto:nghiapn@reapit.com) \| fix: \#1978 elements production issue cant resolve reapit utils \(\#1979\)
* 7ef6d33f9e06a9c5239fa9bb7fd35b61bcba67bd \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: update the helper notification message \(\#1883\)
* 28d03c6d9ec400f168a27f6c88b0f15efc2fb3e3 \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| feat: \#1848 filter app lists when using the marketplace in Developer Edition \(\#1851\)\* feat: \#1848 filter app lists when using the marketplace in Developer Edition
* 4dad8c47bd6c2b15cc973d9714a5b445edc908a2 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: \#1748 remove unuse dependencies and add use dependencies to package.json \(\#1775\)
* 864c59f05c75ff65a4670a76f4876896e30b7ec8 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| ci: \#1748 improve speed for pipeline \(\#1764\)

approver: @willmcvay

## monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

### cognito-auth\_v2.1.7 - 2020-06-15

Release: cognito-auth\_v2.1.7 Rollback: cognito-auth\_v2.1.6 Changes: commit \| author \|description

* 3a8e389e21df9639c13d15dd75cdc5960b990318 \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| chore: \#1393bump version numbers of NPM packages to release \(\#1667\)
* 8dc9b71908ebaf6d582975d4e19226e9c0faac07 \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| fix: \#1393 linaria elements build \(\#1645\) _fix: fixes elements rollup dist_ fix: adds comments _fix: fixes elements build, now outputs types_ fix: fixes test run by splitting tsconfigs\* fix: fixes lockfile issue
* 11b7e44040816b6e22193ccb9f8580c2feb5cb29 \| Snyk bot [snyk-bot@snyk.io](mailto:snyk-bot@snyk.io) \| fix: packages/cognito-auth/package.json & packages/cognito-auth/.snyk to reduce vulnerabilities \(\#1537\)The following vulnerabilities are fixed with a Snyk patch:- [https://snyk.io/vuln/SNYK-JS-LODASH-567746](https://snyk.io/vuln/SNYK-JS-LODASH-567746)
* 22f53f3e4b72b4e6964739940c14ef32cea4b427 \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| fix: \#1393 fixes rollup config for elements so linaria styles are exported \(\#1501\) _fix: resolves linaria styles bundle issue_ fix: adds a couple of comments _fix: add comment_ fix: fixes tests by handling sass in Jest properly\* fix: re-generate lock file after merge
* 62fb2561486eb9a05e2e0fd19a6d0677c8fd9870 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| ci: \#1333 add deployment pipeline for new process \(\#1479\)
* 1109cc4a89dbcc242b13e216498d8784287dae49 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1389 dead link search widget in elements \(\#1400\)

approver: @willmcvay

## monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## cognito-auth\_v2.1.6 - 2020-05-28

Release: cognito-auth\_v2.1.6 Rollback: cognito-auth\_v2.1.5 Changes: commit \| author \|description

* 3dc87f4250c21bcee7715451abbbac7ed5a6ebd0 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| chore: bump version cognito auth \(\#1394\)
* 75bd498a445ebb2baa0cb72594e99f5cb2b699cc \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| fix: hot fix for private route \(\#1381\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## cognito-auth\_v2.1.5 - 2020-05-19

Release: cognito-auth\_v2.1.5 Rollback: cognito-auth\_v2.1.4 Changes: commit \| author \|description

* 7d6f7574ad5c267afc7d87170e2d46730bfacc88 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| chore: bump cognito-auth 2.1.5 \(\#1281\)
* 73296981d70de416f5eb9b49c9901fda0befaf83 \| Trường An [andt@reapit.com](mailto:andt@reapit.com) \| feat: \#1011 As a client who is not an admin, I should not see certain tabs in the marketplace \(\#1261\)\* feat: \#1262 Get the current user logged in phone number
* 0f66915923551cff8440344ee013a627a78b9d80 \| Cuong Vu [cuongvh@reapit.com](mailto:cuongvh@reapit.com) \| fix: \#1160 HTML Description fields fixes \(\#1181\) _fix \#1160 WIP fixing  and_  fix \#1160 fixing  and \* fix: \#1160 rem instead of em
* 349e86a308951fc723a519521e21468297c686c7 \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1123 render renderHTML for diff compare of approval modal \(\#1153\)Changes- Add diff viewer for RenderHTML component
* 16c92eb246e4c2500fd5fe374bec149d79448e7a \| Pham Hai Duong [duongph@reapit.com](mailto:duongph@reapit.com) \| feat: \#1009 serverless deployment for cloud apps \(\#1061\)Changes- Clone serverless.yml for cloud apps

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## cognito-auth\_v2.1.4 - 2020-04-23

Release: cognito-auth\_v2.1.4 Rollback: cognito-auth\_v2.1.3 Changes: commit \| author \|description

* d546c17255e322524c78deffc311aca2120a612d \| Khac Vy [vytk@reapit.com](mailto:vytk@reapit.com) \| chore: Update agency integration type section text \(\#1047\) _chore: Update agency integration type section text_ chore: bump version cognito-auth 2.1.4

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

## cognito-auth\_v2.1.2 - 2020-04-14

Release: cognito-auth\_v2.1.2 Rollback: cognito-auth\_v2.1.1 Changes: commit \| author \|description

* 0c2c895f25d0c10bd929f792ac3f7903220b7db1 \| Will McVay [wmcvay@reapit.com](mailto:wmcvay@reapit.com) \| fix: bump version number \(\#911\)

approver: @willmcvay monitor: [https://sentry.io/organizations/reapit-ltd/projects/](https://sentry.io/organizations/reapit-ltd/projects/)

