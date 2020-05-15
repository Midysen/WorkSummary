# 2020-03-16 ~ 2020-03-20周报
## 董鹏
- 搭建window 开发环境
- 添加volume点击事件接口

# 2019-12-30 ~ 2020-01-03周报
## 董鹏
- systemui 底部任务栏ui替换，完成度90%，目前存在切换屏幕密度后，分辨率（12月9日开始）
- wifi、电池、音量、输入法的弹窗和逻辑，完成度0% （12月23日开始）

## 王之旭
- 完成文件管理器用正常途径解决图片管理器打开文件显示错误的BUG
- 完成Openthos 8.0 壁纸缩放不正确的bug
- 编写本周总结文档-Wallpaper的显示 https://github.com/potatomagic/DevelopmentMaterials/blob/master/Android/WallPaper%E7%9A%84%E6%98%BE%E7%A4%BA.md
- SystemUI新UI的讨论与开发，Review董鹏补丁

# 2019-12-23 ~ 2019-12-27周报
## 董鹏
- systemui 底部任务栏ui替换，完成度60% （12月9日开始）
- wifi、电池、音量、输入法、日历的弹窗和逻辑，完成度0% （12月23日开始）
- 下周计划
  - 完成systemui ui 底部任务栏替换
  - 完成wifi、电池、音量、输入法的弹窗和逻辑
  
## 王之旭
- 修复多次创建桌面的BUG
- 修复图片管理器打开文件显示错误的BUG，后期会更加完美的解决该问题（目前是在frameworks层解决，后期会更换到应用层来解决，工作量较大）
- 优化文件管理器代码
- 编写本周总结-FileProvider的使用（https://github.com/potatomagic/DevelopmentMaterials/blob/master/Android/FileProvider%E7%9A%84%E4%BD%BF%E7%94%A8.md ）

# 2019-12-16 ~ 2019-12-20周报
## 董鹏
- systemui 底部任务栏ui替换，完成度80%
- 下周计划
  - 完成systemui ui 底部任务栏替换
  - 两周时间完成wifi、电池、音量、输入法的弹窗和逻辑，截止时间2020-1-3
  
## 王之旭
- 测试OneDrive和Seafile对异常操作的处理
- 云服务概要设计
- 测试Deepin Cloud Sync，并给出相应的报告
- 阅读高斯模糊补丁 40%

# 2019-12-09 ~ 2019-12-13周报
## 董鹏
- systemui 底部任务栏ui替换，完成度60%
- 下周计划
  - 完成systemui ui 底部任务栏替换

## 王之旭
- 编写多窗口文档
- 测试并调试Android-x86 9.0
- 参加开源操作系统年度技术会议
- 下周计划
  - onedrive 概要设计
  - 学习高斯模糊
  - 调研浏览器

# 2019-12-02 ~ 2019-12-06周报
## 董鹏
- 完成onedrive、坚果云、iCloud需求分析报告
- 完成openthos云手机版需求文档
- 下周计划
  - systemui 底部任务栏ui替换

## 王之旭
- 编写多窗口文档
- 编写云服务桌面版需求分析
- 下周计划
   - 完成多窗口文档
   - 研究9.0多窗口

# 2019-11-25 ~ 2019-11-29周报
## 董鹏
- 完成openthos云手机版最新登陆页面功能
- openthos云手机版添加设置页面功能
- 下周计划：
 - 完成坚果云，Cloud，OneDrive，Seafile横向对比分析报告
 - 完成Openthos 云需求分析
## 王之旭
- 编写多窗口文档，涉及的面比较多，目前完成度80%
- 下周计划
   - 完成多窗口文档，目标有效的协助新人理解多窗口
   - 研究Android 10补丁

# 2019-11-18 ~ 2019-11-22周报
## 董鹏
- 调研 坚果云，seafile windows版，dropbox
- 下周计划
   - seafile手机模式最近，传输，我的功能模块的开发
## 王之旭
- android 9 移植并调试桌面和文件管理器
- android 9 增加记住窗口打开位置功能（40%）
- 攥写基于Android9和10的多窗口文档（10%）

# 2019-11-11 ~ 2019-11-15周报
## 董鹏
- 调研iclound，oneDrive
- 下周计划
   - 调研坚果云，seafile windows版，dropbox
## 王之旭
- 对比android 10 和android 9多窗口的差异性 60%
- 窗口最大化后无法还原回窗口 50%

# 2019-11-04 ~ 2019-11-08周报
## 董鹏
- 修复传输列表开始暂停线程阻塞问题
- 修复传输列表暂停和开始按钮在断开网络时没有更新状态问题
- 优化左侧文件选中状态
- 修复横屏点击Esc崩溃问题
- 修复云空间大小在点击上传，下载，删除时候没有及时更新的问题
- 修复在重命名时没有及时更新问题
- 修正openthos about URL
- 下周计划
   - 修复桌面版本bug
## 王之旭
- freeform启动应用 100%
- 修复exitFreeform后黑边的bug 100%
- 调研oem-Lock，待完成 50%
- 完成最大化还原按钮，待完成 20%

# 2019-10-28 ~ 2019-11-01周报
## 董鹏
功能:
- 完成文件列表多选功能
- 添加多个文件下载功能
- 添加多个删除功能（当点击ctrl时）
- 优化下载 删除按钮状态的展示
- 修复bug:点击空文件崩溃问题
- 修复bug:改变窗口大小崩溃问题 
- 下周计划：
   - 解决下载取消时线程阻塞的问题
## 王之旭
- 多窗口学习80%
- https://github.com/potatomagic/DevelopmentMaterials/tree/master/Android/Android%E5%A4%9A%E7%AA%97%E5%8F%A3
- AOSP 9.0的多窗口修改，已实现5%,可以通过修改代码来直接Freeform模式运行程序，但位置不正确，处理不得当，bug较多

# 2019-10-21 ~ 2019-10-25周报
## 董鹏
- 完成右菜单数据自适应屏幕宽度功能--已提交
- 多选功能完成40%有可视效果，存在问题待优化
- 添加框选逻辑10%
- 下周：
   - 完成框选，多选剩余工作
## 王之旭
- 多窗口学习60%
- https://github.com/potatomagic/DevelopmentMaterials/tree/master/Android/Android%E5%A4%9A%E7%AA%97%E5%8F%A3

# 2019-10-14 ~ 2019-10-18周报
## 董鹏
- 整理右菜单数据自适应屏幕宽度逻辑 80% 
- 添加根据屏幕尺寸横竖屏幕动态切换布局，待测试提交 
- 下周任务
   - 添加框选  多选逻辑
## 王之旭
- AOSP的编译 100%
- 测试Oto8中frameworks的Patch 100%
- 学习多窗口 10% 
- 下周任务
   - 学习多窗口 90%
# 2019-10-08 ~ 2019-10-12周报
## 董鹏
- 完成横屏有线网络断开提示
- 添加物理按键ctrl事件响应
- 调研有线网络断开在线程运行时抛出对应的异常
- 下周任务
   - 修复bug---- 横屏菜单快速双击，部分操作系统路径展示错乱问题
   - 修复bug---- 上传没有进度条
   - 优化代码
## 王之旭
- 合并文件管理器和桌面代码，完成度100%
- 桌面压缩解压缩崩溃bug，完成度100%
- 下周任务
   - 优化文件管理器代码
   - 文件管理器：点击右键菜单的“发送”选项使文件管理器崩溃
   - 桌面：我的电脑右键菜单->关于本机，提示桌面停止运行

# 2019-09-23 ~ 2019-09-30周报
## 董鹏
- 修复bug ----notification为空提示 android8.0兼容问题
- 修复bug ----回退按钮在主页面崩溃问题
- 添加手机模式底部功能按钮框架
- 优化桌面版本下载 上传 删除 状态展示以及添加传输列表为空图片
- 下周计划
   - 设置功能
   - 传输列表功能
   - 修复桌面bug
## 王之旭
- 合并桌面和文件管理器的代码，精简代码，并且解决桌面使用压缩缩解压缩打开文件崩溃，目前完成度40%
- 下周计划
   - 完成桌面和文件管理器代码的合并
   
# 2019-09-16 ~ 2019-09-20周报
## 董鹏
- 优化前进，后退，上传的逻辑，清除主页面冗余代码
- 修复bug，打开文件目录crash
- 修复bug，android8.0无数据
- 下周计划
   - 修复bug
## 王之旭
- 文件管理器中使用压缩缩解压缩打开文件崩溃
- 下周计划
  - 桌面和文件管理器的代码，精简代码，并且解决桌面使用压缩缩解压缩打开文件崩溃
  
 
# 2019-09-09 ~ 2019-09-12周报
## 董鹏
- 优化登陆页面
- 优化内存使用状态展示
- 添加窗口权限，上下兼容
- 下周计划
  - 修改剩余bug
  - 优化左侧列表， 主页面，传输列表，设置 功能及其页面
## 王之旭
- oto8：”删除语言和输入法/语言/添加语言“的“粤语”选项
- 调研oto2和oto8中“日期和时间”，“选取时区”里的中国标准时间是否合理
- 调研oto2：“语言和输入法/语言/添加语言”倒数第六个是乱码的情况，结论是非本次icu更新引进的问题。
- 测试icu的其他运行情况。
- 下周计划
  - Auto-Mount

# 2019-09-02 ~ 2019-09-06周报
## 董鹏
- 完成全部开始功能
- 完成开始取消按钮功能
- 账户修改接口已完成（功能有待确定）
- 完成浏览存放路径功能
- 完成服务器切换功能
- 下周计划：
  - 修改bug
  - 优化桌面版代码

## 王之旭
- Auto-Mount调研，应用层工作基本结束，等待系统组工作。
- 国家地区问题，8.1已完成
- 窗口拖拽到屏幕下方尺寸变小，进度60%
- 下周计划：
  - 完成Auto-Mount
  - Openthos 2.0 国家地区问题

# 2019-08-26 ~ 2019-08-30周报
## 董鹏
- 完成文件路径功能
- 完成全部开始功能 70% 
- 完成传输列表状态的展示（下载取消，下载完成，等待下载，以及下载失败）（开始暂停功能延后）
- 完成通用设置页面历史服务器展示功能
- 下周计划
  - 全部开始功能
  - 开始暂停功能
  - 通用设置页面服务器切换功能
  - 通用设置页面浏览路径功能
  - 修复bug

## 王之旭
- 完成隐藏自研应用SU权限弹窗
- Auto-Mount点击崩溃，原因已明确，没有挂载点引起的，正在解决。由于权限问题，涉及到系统层，可能需要系统组帮忙。
- review苗德行，罗浩，张善民，刘晓旭的Patch
- 下周计划：
  - 完成Auto-Mount

# 2019-08-19 ~ 2019-08-23周报
## 王之旭
- 窗口拖拽到屏幕下方，窗口尺寸变小的bug，50%
- 学习兼容模式的代码，100%
- 下周计划：
  - 文件管理器AutoMount功能

## 董鹏
- 完成传输列表单个下载功能
- 完成传输列表删除，全部取消功能
- 添加开始和暂停状态接口
- 下周计划：
 - 完成开始和暂停功能
 - 全部开始功能 文件路径功能



# 2019-08-12 ~ 2019-08-16周报
## 王之旭
  - 深入学习多窗口组代码，文档，了解UI是如何绘制出来的。
  - 正在解决下拉窗口到屏幕下方再松开后，窗口尺寸变小的bug，多次测试中发现该窗口变小在拖拽窗口时就发生了，还未定位到原因
  - 深入学习C C++ ndk，为云服务打基础
  
下周计划
  - 继续解决窗口拖拽缩放问题
  - 深入学习C C++ ndk，为云服务打基础

## 董鹏
- 梳理传输列表逻辑30%

下周计划：
- 继续完善传输列表中的逻辑

# 2019-08-05 ~ 2019-08-09周报
## 王之旭
  - 深入学习多窗口组代码，文档，了解UI是如何绘制出来的。
  - 正在解决下拉窗口到屏幕下方再松开后，窗口尺寸变小的bug，目前已经定位到原因，还未找到很好的改动办法，因为触发该问题的的地方，如果改动了，也会影响窗口缩放，目前怀疑可能没有找到正确的位置，待确定。
  
下周计划
  - 继续解决窗口拖拽缩放问题
  - 深入学习C C++ ndk，为云服务打基础

## 董鹏
  - 添加传输列表功能按钮的接口
  - 梳理传输列表逻辑
本周计划：
  - 继续完善传输列表中的逻辑






# 2019-04-22 ~ 2019-04-26周报
## 王之旭
- 编写应用组文档
- 云服务崩溃bug兼容问题

# 2019-04-15 ~ 2019-04-19人周报
## 王之旭
- 编写应用组文档

# 2019-04-08 ~ 2019-04-12个人周报
## 王之旭
- 解决8.0桌面两个菜单的问题
- 调研网络邻居不能使用的问题

# 2019-04-02 ~ 2019-04-05个人周报
## 王之旭
- 调研网络邻居不能使用的问题
- 解决8.0云服务崩溃的bug

# 2019-03-25 ~ 2019-03-29个人周报
## 王之旭
- 初步完成应用商店添加静默下载状态问题，由于某些原因，可能需要重构代码
- 修复桌面因某些图标不存在，按ctrl+a等操作崩溃的bug
- 修复从桌面删除文件后，进回收站还原概率失败的问题
- 修复回收站由于路径不存在还原失败的bug

# 2019-03-18 ~ 2019-03-22工作计划
## 王之旭
- 云服务地址的更换
- Openthos2.0上日历的隐藏
- 应用商店增加正在下载状态
## 卢宁
- 添加Alt-Tab回到桌面，目前存在问题：再次回到桌面后无焦点问题
- 添加右下角回到桌面按钮的功能
## 董鹏
- 桌面版模式右侧文件列表区域添加右键菜单
- 实现右键菜单：单个下载功能，加入收藏功能

# 2019-03-11 ~ 2019-03-15个人周报
## 王之旭
- 完成修复文件管理器打开文件崩溃的问题，并确定存在的问题
- 完成应用商店静默安装功能

# 2019-03-04 ~ 2019-03-08个人周报
## 王之旭
- 初步文件管理器打开文件崩溃的问题，测试存在的问题
- 调研回收站内的还原和删除功能无效

# 2019-02-25 ~ 2019-03-01个人周报
## 王之旭
- 完成修复文件管理器打开文件崩溃的问题
- 完成修复桌面打开文件崩溃的问题
- 完成录音机运行崩溃的问题
- 下周计划
  - 打开图片错误，包括系统自带的文件应用。
  - 桌面和文件管理器无法打开文档和apk

## 苗德行
- 应用商店增加断点继续，邮件日志；
- chromium 源码下载编译
- chromium修改主页为openthos（未完成）

# 2019-01-18 ~ 2019-01-22个人周报
## 王之旭
- 完成更新云服务技术文档
- 完成更新云服务用户手册
- 完成录音机打开崩溃的问题
- 下周计划
  - 录音机录制音频崩溃的bug
  - 桌面和文件管理器打开文件崩溃的bug


## 苗德行
- 配合测试工程师完成测试，修复bug:抓取不到分类、下载apk异常、下载目录不规范；
- 增加断点继续、日志邮件等功能
- 下周计划
  - 增加环境搭建自动化脚本
  - Android9.0移植研究

# 2019-01-21 ~ 2019-01-25个人周报
## 王之旭
- 完成8.0图片管理器打开崩溃问题
- 8.0自研应用打开文件需要提供一个统一的方法（完成100%，待整理提交）
- 之后计划
  - 8.0录音机崩溃的问题

## 苗德行
- 测试原有应用商店程序，解决google play需要验证码和短信验证，完成60%
- 之后计划
  - 增加黑名单，白名单功能
  - 脱离真机环境，建议VMvare（硬件或其他支援）
  - 实现自动化（人工维护耗时，一周4小时）
  
## 董鹏
- 初步完成openthos云增加桌面版效果，包括桌面版初始页面和回退按钮（但讨论后整体方案有问题，需要重做）

# 2019-01-14 ~ 2019-01-18个人周报
## 王之旭
- 完成 8.0自研应用默认没有权限查看sd卡问题
- 8.0图片管理器打开崩溃问题（完成50%）
- 8.0自研应用打开文件需要提供一个统一的方法（完成50%）
- 之后计划
  - 8.0图片管理器打开崩溃问题
  - 8.0自研应用打开文件需要提供一个统一的方法
  - 8.0录音机崩溃的问题

## 苗德行
- 完成 实现根据包名下载所有应用程序的图标，并实现了去除重名的应用程序，更新数据库和应用商店需要的参数字段
- 完成 按照应用商店要求，生成接口文件，并通过测试
- 完成 监测应用程序更新，并更新数据库表
- 之后计划
  - 增加黑名单，白名单功能
  - 脱离真机环境，建议VMvare（硬件或其他支援）
  - 实现自动化（人工维护耗时，一周4小时）
  
## 董鹏
- 根据效果图在title栏中添加 上传，下载，新建文件，删除按钮，其中新建文件已实现其余按钮未实现
- 添加左侧资料库栏和右侧展示资料库内容的布局，并实现了点击左侧资料库，动态刷新右侧展示资料库内容（有bug）

# 2019-01-14 ~ 2019-01-11个人周报
- 完成 8.0Launcher的移植
- 分析、解决文件管理器和桌面无法用相关应用打开文件（正在找最优方法）
- 应用商店默认打开存储权限（正在找最优方法）
- 完成 cloud服务器无法通过文件管理器上传下载文件，原因是ssl证书验证失败
- 完成 设置cloud.openthos.org服务器为缺省
- 完成 seaf_start.sh改为seafile-keeper或cloud-service-keeper
- 完成 按ctrl+alt+t调出终端后，会出现ctrl键粘滞的问题，此时双击文件或文件夹无法进入，需要再次按ctrl解除粘滞

# 2019-01-02 ~ 2019-01-04个人周报