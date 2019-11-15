#### 任务列表

1. 分析eng,user, userdebug的区别，形成分析报告
2. 学习crystal语言
3. 同步kis-analysis并学习
4. 分析lkp-test的代码
5. 学习linux-lab
6. 学习kernelci, gitlab的ci，gitlab-ce
   - [gitlab-ci](https://about.gitlab.com/product/continuous-integration/)
   - [kernelci](https://github.com/kernelci)
   - [under-the-hood-1](https://cki-project.org/posts/under-the-hood-part-1/)
   - [under-the-hood-2](https://cki-project.org/posts/under-the-hood-part-2/)
7. 搭建自动化测试环境，要求自动生成img，且测试到启动界面，使用qemu即可。

#### 101115

- [x] 简历筛选
- [ ] 更新周报，本周进度
- [ ] 搭建自动化测试环境：调研Openthos执行特定脚本，自主输出信息的方法

#### 101112~101114

- [x] 搭建自动化测试环境

  可跑通编译过程

  安装过程基于android-x86采用文件复制的方法，不建议使用

  启动测试的部分已实现从qemu启动，但adb连不上

#### 101111

- [x] 调研云服务需求：试用坚果云
- [x] 搭建自动化测试环境：尝试运行自动化测试但未跑通

#### 101108

- [x] 搭建自动化测试环境：搭建docker环境，本地跑通编译
- [x] 更新周报、本周进度

#### 101107

- [x] 记录oto8镜像发布过程
- [x] 搭建自动化测试环境：下载cts，下载oto8源码

#### 101106

- [x] 发布user版镜像：联系ZJ添加长期运营者
- [x] 测试openthos cloud桌面端

#### 101105

- [x] 发布user版镜像:完成镜像上传

#### 101104

- [x] musl libc集成到oto8的测试
- [x] 发布user版镜像：发布前测试

#### 101101

- [x] 统计周报，月报，进度报告
- [x] patch测试：解决user版重启的问题
- [x] 搭建自动化测试环境：阅读代码