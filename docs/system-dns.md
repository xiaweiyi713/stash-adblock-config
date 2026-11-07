# 可选的 iOS 系统去广告 DNS

这项设置用于 Stash 未运行时的域名过滤。系统 DNS 只能按域名过滤，无法替代路径改写，也不能清除 App 已缓存的广告。保持「自动」也可正常使用本仓库的 Stash 覆写。

- **AdGuard 公共 DNS：**从 [AdGuard 官方页面](https://adguard-dns.io/en/public-dns.html)选择默认过滤服务器的 iOS 描述文件。只在需要时安装；启用后，使用该系统解析器的查询会发给 AdGuard。
- **旧 Mullvad 描述文件：**不纳入安装包。Mullvad 已[宣布停止公共加密 DNS 服务](https://mullvad.net/en/blog/2026/9/3/shutting-down-our-public-encrypted-dns-servers-and-sponsoring-quad9-instead)，不建议恢复此前测试的公共 DNS 描述文件。

在「设置 → 通用 → VPN 与设备管理 → DNS」可以查看或切回「自动」。如果开启后加载明显变慢，可先切回自动，在同一网络、同一 App 下比较。仓库不复制旧的签名描述文件。
