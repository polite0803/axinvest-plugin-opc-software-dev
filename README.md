# opc-software-dev

本目录由 `scripts/generate-plugin-independent-repos.mjs` 从 AxInvest 主仓非破坏性生成。

- 插件名：opc-software-dev
- Cargo 包：axagent-plugin-opc-software-dev
- SDK 依赖：副本 plugin-proto、plugin-opc-core、plugin-testkit
- CI：`.github/workflows/plugin-ci.yml`
- 发布：推送与 `plugin.json` 版本一致的 `v*` tag，由 `.github/workflows/release-plugin.yml` 生成 GitHub Release
- 主应用发布地址：`https://github.com/polite0803/axinvest-plugin-opc-software-dev/releases/latest/download/release.json`
- 打包：`node scripts/build-plugin-bundle.mjs --plugin opc-software-dev --check`
- 单平台发布清单：`node generate-plugin-release-manifest.mjs --bundle dist/plugins/opc-software-dev --artifact-url https://example.com/opc-software-dev-linux-x86_64.tar.gz --os linux --arch x86_64`
- 正式发布：`release-plugin.yml` 在六个平台分别生成清单，再由 `--merge --require-platform` 汇总为唯一 `release.json` 和全部平台包。
- SDK：`sdk/` 是生成器从主仓同步的最小源码快照，所有依赖都留在本仓内；无需预先发布 crates.io。
