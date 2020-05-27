---
description: >-
  Below you will find a listing of the recent changes we have made to the GEO
  Diary App. This includes details of any bugs that have been fixed or
  features/enhancements that have been added.
---

# GEO Diary
### geo-diary_v1.0.1 - 2020-04-24
  
Release: geo-diary_v1.0.1
Rollback: geo-diary_v1.0.0
Changes:
commit | author |description
  
- 7fb4663aa09063dc790169191277efc42523d2ec | Cuong Vu <cuongvh@reapit.com> | feat: #939 Web apps should have their own dev and prod cookie identifier (#972)- Web Apps now have three different cookie identifiers `local`,`developement` , `production`, based on `config.json`- Some methods in `cognito-auth` now have an additional `appEnv?: string` param to work with cookie for different environments- Default `refreshSession` state in `redux store` now will be set after fetch `config.json`- Fix e2e tests login after changing cookie identifiers
- a9c8c8d84d753f6b0db8a635aa377df0bafd5f49 | Cuong Vu <cuongvh@reapit.com> | fix: #965 fix geo-diary cannot refresh token (#1005)
- 8d3bd81c139e1a7f5e3e903f182faf1d156e54c5 | Cuong Vu <cuongvh@reapit.com> | feat: #739 The Cloud Apps should be testable in "Desktop Mode" (#784)* feat: #739 cloud apps now testable in desktop mode
- c2dc732b60516096c3310e2060b794dfb0fc6523 | Pham Hai Duong <duongph@reapit.com> | fix: #issue appointment does not have propertyId (#724)
- 0fb24fbe92ca4b2c71264b28a9e3cc2bf9102627 | Pham Hai Duong <duongph@reapit.com> | fix: #568 react scaffold after migration to config.json (#693)Changes- Add export default app.tsx- Change index.tsx to remove import index.scss
- e32f8fa0809b80dd153a548b13ab77ac0d6c43ed | Pham Hai Duong <duongph@reapit.com> | chore: #629 migrate config of apps to config.json (#644)chore: #629 migrate config of apps to config.json (#644)
- 1a717294fb88558f47951bbedd1bbab12f3b38b0 | Cuong Vu <cuongvh@reapit.com> | fix: #601 invalidate chunk when deploying to dev/prod (#624)
- 732627537a29c4f32585dae3165baef4ad1725c0 | Pham Hai Duong <duongph@reapit.com> | feature: #550 add app version to login page (#553)* feat: #550 add app version to login page* feat: add app version to elements story-book
- 241590e07280434cd0bf8f6ab65a3e7e7d322279 | Cuong Vu <cuongvh@reapit.com> | chore: #473 GraphQL Server Refactor (#548)* chore: #473 refactor graphql server
- cfa5635aa0ea5d1c9ee4da83c548213eef47c0f6 | Cuong Vu <cuongvh@reapit.com> | fix: fix failing pipeline (#521)* fix: reconstruct packages depedencies, fix webpack.sass not throw errors* fix: add todo comment, remove unused config, add sentry_log_level* fix: remove SENTRY_LOG_LEVELS env, add to sentry webpack plugin instead
- 8e0080b8b62a04db3ea810bfad77daa03db7fa0c | NghiaPham <nghiapn@dwarvesv.com> | chore: #368 Add resolver for graphql server to call appointment services (#389)
- c6a4c531dca8e4b6f2b1dff6669c73dba1f7c9bc | Pham Hai Duong <tanphamhaiduong@gmail.com> | chore: #128 remove redundant and restructure dependencies (#451)* chore: #128 remove redundant and restructure dependencies* chore: resolve all warning on build console* chore: resolve warning peer dependencies for install by yarn* fix: resolve package cognito-auth in cognito package* chore: remove query-string dependency
- 64d096cbb85ef4bc98f86ad6964e8c4527579479 | Cuong Vu <vuhuucuong1310@gmail.com> | chore: #125 improve webpack bundling performance (#445)* chore: #125 (POC) improve webpack bundling performance locally* chore: #125 add mode for webpack dev* chore: #125 resolve conflicts* chore: #125 graphql-server add tsconfig path to cognito-auth* chore: #125 update pullrequest pipeline to include cache build* chore: #125 update pullrequest pipeline to include marketplace cache* chore: #125 correct cache keys* chore: #125 first build test (expected to take long time)* chore: #125 concurrently build in elements* chore: #125 second test* chore: #125 remove duplicated --parallel flag* chore: #125 ignore .temp folder* chore: #125 remove babel-loader built-in cache* chore: #125 finish pipeline* chore: #125 test pipeline* chore: #125 readd sass temp* chore: #125 add jest cache* chore: #125 refactor & finish* chore: #125 finish both ci/local cache settings* chore: #125 fix hooks not run* chore: #125 fix echo & cp not working in windows
- c2e6fec90054d915dbf75e03d81b2a2d689761d1 | Pham Hai Duong <tanphamhaiduong@gmail.com> | chore: #337 update readme of packages (#340)* chore(readme): #337 update readme of packages* chore: bump version for react-app-scaffolder
- f86d9bd6d313dac39946852987c4118b69dee7d2 | Will McVay <wmcvay@reapit.com> | fix: ts definitions deploy (#295)* fix: dead link in definitons deploy* fix: revert deploy from master for ts-definitions cron* fix: geo-diary build fail
- 03e2db4695cd870e4e98ddd851ee656ed4206777 | NghiaPham <nghiapn@dwarvesv.com> | [WIP]Chore/33 update react scalfolder (#224)* temp* temp* chore: #33 update marketplace-api-schema.ts file* chore: #230 Update scaffolder styles solutions (#259)* temp* temp* chore: #230 Update scaffolder styles solutions* chore: #230 Update .gitignore* chore: #230 update types fileCo-authored-by: NghiaPham <nghiapn@dwarvesv.com>* chore: #227: scaffolder option no redux (#268)* chore: #244 Update base files of the scaffolder* fix .gitignore* update schema file* update snapshotCo-authored-by: Khac Vy <khacvy93@gmail.com>Co-authored-by: Dan Nguyen <45675930+danndz@users.noreply.github.com>
- 7c49b93a1ebfaa659e8a4c81245abee445b3ab39 | NghiaPham <nghiapn@dwarvesv.com> | chore: #116 #117 update ts-definition pipeline, scripts (#226)* chore: #116 #117 update ts-definition pipeline, scripts* chore: lock version of package "foundation-ts-definition" for all apps. update PR comment* fix* update elements package to include foundation definition* remove password param from test

approver: @willmcvay
monitor: https://sentry.io/organizations/reapit-ltd/projects/
    

