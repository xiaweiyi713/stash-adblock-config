# Stash 开屏去广告配置

适用于 iPhone 和 iPad。保留现有 Stash 主配置，把这里的文件作为**覆写**导入。合并版包含 669 条分流规则、8 条 URL 改写，以及 3 个指定的 HTTPS 检查主机。

虎扑和菜鸟在 iPhone 实测中已观察到开屏减少。百度和百度网盘仍有开屏残留，详见[验证记录](docs/verification.md)。

## 导入方式

**整套导入：**下载 [Stash-Adblock.stoverride](stash/Stash-Adblock.stoverride)，在 iPhone 或 iPad 的「文件」中打开，或通过分享菜单交给 Stash。若系统未关联此扩展名，可在 Stash「覆写 → 新建覆写 → {}」中粘贴文件内容并保存。

**分开导入：**按下表从上到下的顺序导入，便于单独启用和排查。只需要域名拦截时，使用前两份即可，无需配置 HTTPS 检查。

| 模块 | 用途 |
| --- | --- |
| [01 秋风纯广告](stash/01-awavenue-ads.stoverride) | 665 条广告域名分流 |
| [02 域名补充](stash/02-extra-domains.stoverride) | 2 条精确域名拦截 |
| [03 开屏路径](stash/03-splash-paths.stoverride) | 菜鸟、虎扑和百度网盘的 4 条路径改写 |
| [04 百度补充](stash/04-baidu-partial.stoverride) | 2 条分流与 4 条改写，部分请求已验证命中 |

合并版与四份模块二选一。已经安装这四份覆写的设备可以继续使用现有版本。私有仓库需登录 GitHub 下载，可在 Mac 下载后隔空投送；无需在 Stash 中保存 GitHub 访问令牌。

## 生效与回退

- 在 iOS 上开启 Stash，并使用规则模式。要让路径规则工作，开启「覆写」「改写」和「MitM」，按 [Stash 官方指南](https://stash.wiki/en/http-engine/mitm) 在该设备生成并信任自己的 CA。证书与私钥留在设备上。
- 路径规则只检查 `cn-acs.m.cainiao.com`、`goblin.hupu.com`、`pan.baidu.com` 三个主机；不需要安装远程脚本。
- 遇到误拦时，关闭合并版或相关独立覆写再复测。主配置、节点订阅和 DNS 可继续沿用。
- [系统 DNS 说明](docs/system-dns.md)是可选项。系统 DNS 的域名过滤无法替代 Stash 的 HTTPS 路径规则。

[停用的百度两主机测试](experimental/disabled-baidu-app-two-hosts.stoverride)只作记录，日常导入时跳过。仓库只保存规则与说明，不保存主代理配置、机场订阅、节点凭据、设备证书或原始请求日志。

规则来源和许可见 [THIRD_PARTY.md](THIRD_PARTY.md)。合并依据 [Stash 的覆写顺序和数组合并规则](https://stash.wiki/en/configuration/override)。
