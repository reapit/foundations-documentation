# Elements

description: &gt;- Below you will find a listing of the recent changes we have made to the Elements package. This includes details of any bugs that have been fixed or

### features/enhancements that have been added.

## Elements

### elements_v0.5.56 - 2020-05-12
  
Release: elements_v0.5.56
Rollback: elements_v0.5.53
Changes:
commit | author |description
  
- 2c8346824813966245a4ab567e8ae43892396472 | Cuong Vu <cuongvh@reapit.com> | fix: #1160 fix placeholder color, change H6 to H5 (#1194)* fix: #1160 fix placeholder color* fix: #1160 change h6 to h5 in desciption
- 1d30c8b526b6b6c5abf054b45948e9d7325a69a6 | Khac Vy <vytk@reapit.com> | chore: bump elements version 0.5.56 (#1213)
- a2106bf468c233be83b5621358414f97eb00faeb | Khac Vy <vytk@reapit.com> | fix: #1189 fix desktop integration type dropdown spacing (#1190)
- 0f66915923551cff8440344ee013a627a78b9d80 | Cuong Vu <cuongvh@reapit.com> | fix: #1160 HTML Description fields fixes (#1181)* fix #1160 WIP fixing <Editor> and <HTMLRender>* fix #1160 fixing <Editor> and <HTMLRender>* fix: #1160 rem instead of em
- 91fe077d165bd41afacbd3b5a5cb1fa1f7cf7d0e | Trường An <andt@reapit.com> | feat: #1006 #979 create/edit webhook modal (#1140)* feat: #1006 #979 create/edit webhook modal* feat: #1006 update list webhooks* chore: #1006 update content type of header API call* chore: #1006 add type for variable* chore: #1006 add open webhook modal
- e503f3a3a269e9006b676f32028ffb41cfe1bc6b | Pham Hai Duong <duongph@reapit.com> | feat: #1123 render text editor instead of text area submit app (#1151)feat: #1123 render text editor instead of text area submit app (#1151)
- 349e86a308951fc723a519521e21468297c686c7 | Pham Hai Duong <duongph@reapit.com> | feat: #1123 render renderHTML for diff compare of approval modal (#1153)Changes- Add diff viewer for RenderHTML component
- d9182462a1a90ed1b0414b2c715d32687d39c10b | Cuong Vu <cuongvh@reapit.com> | feat: #1120 elements heading font default roboto (#1132)
- ea009069bb4e5153a9d51ca94ff6986fe5506959 | Vu Nguyen <vunp@reapit.com> | Feat/1078 create cost explorer section on billing tab (#1115)* feat: #1078 - Add cost explorer section to billing tab
- 6cfa6953b45c16f86ff15f8a98edf1b6d7c4c9a7 | Cuong Vu <cuongvh@reapit.com> | fix: #1067 fix double scroll bar issue (#1111)
- 78e0c0052c004470a578a168e2e02902b632bfb6 | NghiaPham <nghiapn@reapit.com> | fix: #639 - selectbox styles (#1108)
- f6d395afc5f1476e09d4c33761fe347ec1872859 | NghiaPham <nghiapn@reapit.com> | fix: #693 - increase webhooks page dropdown size, and load developer apps data (#1095)
- 579d2c515ed2df63277cd77fcbc08a45a6c5c67e | NghiaPham <nghiapn@reapit.com> | fix: #1065 fix loading chunk fail (#1092)
- 7fed969c082458b3ca44628e9573143d7110a248 | Vu Nguyen <vunp@reapit.com> | Feat: #714 - Create cost calculator on analytics billing tab (#1079)* feat: #714 - Add cost calculator to billing tab
- 16c92eb246e4c2500fd5fe374bec149d79448e7a | Pham Hai Duong <duongph@reapit.com> | feat: #1009 serverless deployment for cloud apps (#1061)Changes- Clone serverless.yml for cloud apps
- 1d307dad916b497ef3d6eb3e35510e5bafb3acfb | NghiaPham <nghiapn@reapit.com> | Feat #963: Implement Developer Webhooks page (#1049)
- e02fba2817092224554006d4eae2bb104f147c05 | Vu Nguyen <vunp@reapit.com> | Feat/956 search developer registrations by date (#1044)* feat: #956 - Search developer registrations by date
- aea4ce8c2597c96cac1b8350cff6b75628ebc737 | Cuong Vu <cuongvh@reapit.com> | feat: #939 Web apps should have their own dev and prod cookie identifier (#972)- Web Apps now have three different cookie identifiers `local`,`developement` , `production`, based on `config.json`- Some methods in `cognito-auth` now have an additional `appEnv?: string` param to work with cookie for different environments- Default `refreshSession` state in `redux store` now will be set after fetch `config.json`- Fix e2e tests login after changing cookie identifiers
- edb6794755d257ebcdc77e24aec29ba6898314d7 | Khac Vy <vytk@reapit.com> | chore: #830 Update description text (#976)
- f11d41b283f096b00de498f1f6149622a71e1a75 | Khac Vy <vytk@reapit.com> | chore: #830 Add space between texts in tag component (#955)
- 6c35f507941d05ce42efa6a262ca5261220f03ce | Khac Vy <vytk@reapit.com> | chore: #830 Update tag link component and option font size (#928)* chore: #830 Update tag link component and option font size

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/

### elements_v0.5.53 - 2020-04-15
  
Release: elements_v0.5.53
Rollback: elements_v0.5.52
Changes:
commit | author |description
  
- 6a31636011bae975400fdb2719322c74a5320b00 | Khac Vy <vytk@reapit.com> | chore: bump @reapit/elements version 0.5.53 (#915)
- 8648895ff351105096069d8a1df4fcffa3195bd8 | Khac Vy <vytk@reapit.com> | feat: #890 display html version of elements components (#912)

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
    
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

