
## Install

[Renegade Project | Renegade Project](https://renegade-project.tech/zh/home)

[MSDN系统库](https://www.xitongku.com/) | [HelloWindows.cn](https://hellowindows.cn/) | [山己几子木](https://msdn.sjjzm.com/) | [NEXT, ITELLYOU](https://next.itellyou.cn/)

## Activation

> [YerongAI/Office-Tool](https://github.com/YerongAI/Office-Tool)

[沧水的KMS服务](https://kms.cangshui.net/) | [KMS 列表](https://www.coolhub.top/tech-articles/kms_list.html)

[zbezj/HEU_KMS_Activator](https://github.com/zbezj/HEU_KMS_Activator)

[Microsoft KMS Activation | vlmcsd](http://wind4.github.io/vlmcsd/) | [Wind4/vlmcsd: KMS Emulator in C](https://github.com/Wind4/vlmcsd)
    
1. 运行`floppy`文件夹内虚拟机文件

> VMware 17 Keys [VMware Workstation Pro 17 full license keys](https://gist.github.com/hegdepavankumar/e1c4c2d58d8698f69792d664d39bc402)
>
> `MC60H-DWHD5-H80U9-6V85M-8280D`

2. 记录 IPv4 address: `10.181.33.249`（根据实际IP修改此内容，只记录斜杠前面的数值）

3. 以管理员方式打开`PoweShell`

4. 输入 `slmgr -skms 10.181.33.249`

5. （更新激活时无需进行）输入 `slmgr -upk`

6. （更新激活时无需进行）输入 `slmgr -ipk NW6C2-QMPVW-D7KKK-3GKT6-VCFB2`（以Win10教育版GVLK为例）

7. 输入 `slmgr -ato`

8. 输入 `slmgr -dlv` 查看结果

9.  Office需要先清除许可证，后选择批量许可证，输入相同IP

10. 可全程断网激活，如使用手机作为热点连接但不联网，此时也会出现需要的IP

11. 虚拟机仅有IPv6时，修改`虚拟机设置→网络适配器→NAT模式`

------

[lightningwar/Self-built-KMS-Server-for-Android: An Android program that can be used as a KMS server to activate Windows or Office. (github.com)](https://github.com/lightningwar/Self-built-KMS-Server-for-Android)

## Configuration

[Windows11轻松设置](https://www.bilibili.com/opus/904672369138729017)

[DoNotSpy11 » pXc-coding](https://pxc-coding.com/donotspy11/)

[Windows Firewall Control](https://www.binisoft.org/wfc) | Install Cracked Software Use, Like ArcGIS

## Uninstall

[Bulk Crap Uninstaller - Remove large amounts of unwanted applications](https://www.bcuninstaller.com/) | [Klocman/Bulk-Crap-Uninstaller](https://github.com/Klocman/Bulk-Crap-Uninstaller)

## Info

[HWiNFO - Free System Information, Monitoring and Diagnostics](https://www.hwinfo.com)

## Restore

[易数一键还原](https://www.onekeyrestore.cn/)

[微PE工具箱 - 超好用的装机维护工具](https://www.wepe.com.cn/) | ♥

## Proxy

[GitHub - MetaCubeX/mihomo](https://github.com/MetaCubeX/mihomo)

> [GitHub - libnyanpasu/clash-nyanpasu： Clash Nyanpasu~（∠・ω< ）⌒☆](https://github.com/LibNyanpasu/clash-nyanpasu) | [Clash Nyanpasu](https://nyanpasu.elaina.moe/)
>
> [GitHub - GUI-for-Cores/GUI.for.Clash: A GUI program developed by vue3 + wails.](https://github.com/GUI-for-Cores/GUI.for.Clash)

```shell
$env:HTTP_PROXY="http://127.0.0.1:10809/"
$env:HTTPS_PROXY="http://127.0.0.1:10809/"
curl.exe -vv http://www.google.com/
# 在PowerShell中使用代理
```

## WSL

[旧版 WSL 的手动安装步骤 | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows/wsl/install-manual)

[WSL 的基本命令 | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows/wsl/basic-commands)

## Desktop

[Cairo Desktop Environment](https://cairodesktop.com/)

## Setting

[电脑常见问题汇总解答（病毒吧）](https://docs.qq.com/doc/DSU9mbmt5SHp2YmFS)

关闭 CompatTelRunner.exe

- 方法1：`taskschd.msc` → 任务计划程序库 → Microsoft → Windows → Application Experience → Microsoft Compatibility Appraiser → 禁用
- 方法2：`gpedit.msc` → 计算机配置 → 管理模板 → Windows组件 → 数据收集和预览版 → 允许遥测 → 策略设置 → 已禁用

关闭休眠

- 使用`powercfg -h off`关闭Windows休眠

仅登录Edge不登录系统

- `Windows管理工具→本地安全策略→本地策略→安全选项→账户：阻止Microsoft账户`，设置为第三个选项

命令行安装kaspersky

- `.\kav21.3.10.391abzh-Hans_26151.exe /pPRODUCTTYPE=kfa`
- KFA 激活码 `3SXCM-M9RJM-6985N-PWKP7` | `A23B5-44EXM-85MVF-KM2GQ`

硬件的最大内存容量

- `wmic memphysical get maxcapacity`

重新启用Internet Explorer 11

- `dism /online /Add-Capability /CapabilityName:Browser.InternetExplorer~~~~0.0.11.0`