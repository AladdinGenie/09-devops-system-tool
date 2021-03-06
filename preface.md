# 研发运营一体化（DevOps）能力成熟度模型 第9部分 系统和工具


## 1. 范围

本标准规定了研发运营一体化（DevOps）的xxxxx。

本标准适用于具备IT软件研发交付运营能力的组织实施IT软件开发和服务过程的能力进行评价和指导；可供其他相关行业或组织进行参考；也可作为第三方权威评估机构衡量软件开发交付成熟的标准依据。

## 2. 规范性引用文件

下列文件对于本文件的应用是必不可少的。凡是注日期的引用文件，仅所注日期的版本适用于本文件。凡是不注日期的引用文件，其最新版本（包括所有的修改单）适用于本文件。

[1] GB/T  32400-2015 信息技术 云计算 概览与词汇

[2] GB/T  32399-2016 信息技术 云计算 参考架构

[3] YD/2441-2013     互联网数据中心技术及分级分类标准

[4] GB/T  33136-2016 信息技术服务数据中心服务能力成熟度模型

[5] GB/T 31496-2015 信息技术 安全技术 信息安全管理体系实施指南

[6] GB/T 22080-2016 信息技术 安全技术 信息安全管理体系要求

[7] GB/T 30975-2014 信息技术 基于计算机的软件系统的性能测量与评级

## 3. 术语

下列术语和定义适用于本文件。

**3.1　项目 project**

需要协同工作的一组任务，其目的在于开发和（或）维护一个具体的产品。产品可以包括硬件、软件或其他成分，一般项目有自己的经费、成本核算和交付进度。【GB/T11457-2006：2.954】

**3.2　项目集 program**

PMI将项目集定义为经过协调管理以获取单独管理所无法取得的收益的一组项目、子项目集和项目集活动。

**3.3　子项目集 sub program**

作为另一个项目集的组成部分而被管理的一个项目集

**3.4　构建项目  Build project**

作为一个构建软件的配置，以及流程。

**3.5　执行记录  Build history**

执行构建的信息，以及结果。

**3.6　构建产出物  Build output**

构建项目中生产的文件。

**3.7　凭据 Credentials**

保存用户保密信息，例如：用户名和密码。

**3.8　容器镜像 Container Image**

容器技术中运行容器软件。包含基本操作系统以及依赖的软件。可以包含构建的产出物。

**3.9　运行环境 Runtime environment**

构建中运行的环境或者计算机。

**3.10　源代码托管软件 Source code management software**

保存源代码的软件。

**3.11　软件单元测试 Unit Test**

是针对程序模块（软件设计的最小单位）来进行正确性检验的测试工作。

**3.12　发布**

发布通常是软件程序的变动，将线上的流量转移到新的软件版本的过程

**3.13　原地发布**

将新的软件版本直接推送到服务器上覆盖旧版本，发布过程可能会引起服务的中断，是一种最直接的发布方式

**3.14　金丝雀发布**

是指在黑与白之间，能够平滑过渡的一种发布方式。又称灰度发布，A/B测试就是一种灰度发布方式，让一部分用户继续用A，一部分用户开始用B，如果用户对B没有什么反对意见，那么逐步扩大范围，把所有用户都迁移到B上面来。可以保证整体系统的稳定，在初始灰度的时候就可以发现、调整问题，以保证其影响度范围的一种发布方式

**3.15　蓝绿发布**

在发布过程中，新旧版本相互热备，发布过程是不停止老版本，直接部署新版本然后进行测试，通过切换路由权重的方式（非0即100）实现将流量切到新版本，然后老版本同时也升级到新版本，是一种可以保证系统在不间断提供服务的情况下的发布方式

**3.16　回滚 Rollback**

回滚（Rollback）指的是程序或数据处理错误，将程序或数据恢复到上一次正确状态的行为。回滚包括程序回滚和数据回滚等类型

**3.17　环境 Environment**

是指应用程序运行所需的所有资源和它们的配置信息，通常分成两大类：基础设施资源及其配置；应用程序独立运行所需要的操作系统和中间件资源及其配置信息。

**3.18　配置项 Configuration item**

一个配置中的实体，它满足一项最终使用功能，并能在给定的基准点上单独标识。【GB/T 8566-2001：3.6】

**3.19　配置管理 Configuration Management**

是一个过程，通过该过程，可以维护一切与环境相关的信息，这些信息可以被定义、修改、存储和检索。应用技术和管理的指导和监控方法以标识和说明配置项的功能和物理特征，控制这些特征的变更，记录和报告变更处理和实现状态并验证与规定的需求的遵循性。【GB/T11457-2006：2.313】

**3.20　开发环境  Development Environment**

用于维持开发过程的一个或者一组资源及其配置信息，面向的是开发者。

**3.21　测试环境 Test Environment**

是指测试运行其上的软件和硬件环境的描述，以及任何其他与被测软件交互的软件，包括驱动和桩。

**3.22　生产环境 Production Environment**

用于维持开发过程的一个或者一组资源及其配置信息，面向的是运维，但其运行服务面向的是用户或者客户。

**3.23　基础设施 Infrastructure**

支持应用运行的所有服务，包括DNS服务器、防火墙、路由器等等。

**3.24　中间件 Middleware**

是处于操作系统和应用程序之间的软件。一种类型的软件模块，它处在系统软件和应用软件之间，依赖系统软件的支持，又为应用软件提供支持，以方便应用软件的开发。【GB/T11457-2006：2.954】

**3.25　性能测试（performance test）**

性能测试是通过自动化的测试工具模拟多种正常、峰值以及异常负载条件来对系统的各项性能指标进行测试。评价系统或部件与规定的性能需求的依从性的测试行为。【GB/T11457-2006：2.1135】

**3.44　在测系统（system under test，SUT）**

CBSS中接受测试的个部分。影响SUT时变行为的所有部件都应是SUT的组成部分，如果此种影响取决于某一工作负载，则该负载也应由RTE来标识。除非对时变行为的影响不可能或不明显时，对其余部分的模拟才可省略。

**3.67　构建环境**

构建环境是指执行构建任务时所在设备的软件和硬件环境。

**3.68　构建任务**

构建任务是指定义从输入到输出过程对构建环境、构建方法等必要因素的定义。

**3.69　构建过程**

构建过程是指构建任务从开始执行到结束。

**3.70　构建策略**

构建策略是指针对构建过程的特定结果设定的处理策略。

**3.71　复刻（Fork）**

复刻是指在软件开发中，开发者为一个版本仓库创建一份拷贝，并在拷贝上进行独立于源版本仓库的开发，从而分离出一个新的软件副本的活动。复刻不仅仅创建了一个分支，还将软件开发活动与源版本库分离开来。

**3.72　合并（Merge）**

是指当一个版本在多个独立分支中被修改后如何合并这些修改成为同一个版本的操作。

**3.73　合并评审（Merge Requests）**

是指在合并之前，允许多人对合并时所提交的变更内容进行代码审查，并给予合并意见的过程。

**3.74　基线（Baseline**

基线是版本仓库中每个版本在特定时期的一个“快照”。它提供一个正式标准，随后的工作基于此标准，并且只有经过授权后才能变更这个标准。建立一个初始基线后，以后每次对其进行的变更都将记录为一个差值，直到建成下一个基线。

**3.75　版本仓库（Repositories）**

版本仓库又称源代码仓库，被用来存储源代码等版本文件。

**3.76　代码审查（Code Review）**

是指对计算机源代码系统化地审查，常用软件同行评审的方式进行，其目的是在找出及修正在软件开发初期未发现的错误，提升软件质量及开发者的技术。代码审查常以不同的形式进行，例如结对编程、非正式的看过整个代码等。

**3.77　测试计划（Testing plan）**

一个叙述了预定的测试活动的范围、途径、资源及进度安排的文档。它确认了测试项、被测特征、测试任务、人员安排，以及任何偶发事件的风险。

**3.78　测试脚本（Testing script）**

一般指的是一个特定测试的一系列指令，这些指令可以被自动化测试工具执行。

**3.79　构建任务  Build task**

​     作为一个构建软件的配置，以及流程。

**3.80　凭据 Credentials**

​     保存用户保密信息，例如：用户名和密码。

**3.81　运行环境 Runtime environment**

​     构建中运行的环境或者计算机

**3.82　源代码托管软件 Source code management software**

​     保存源代码的软件

**3.83　执行记录  Build history**

​     执行构建的信息，日志，以及结果。

**3.84　构建产出物  Build output**

​     构建任务中生产的文件

**3.86　静态源代码扫描 Static code analysis**

​     对源代码执行静态的分析，指出源代码质量(10.9)

**3.87　(制品的)晋级 Promotion**

​     制品管理中，通常是指自构建产物通过某一级别质量关卡后，将其标记为更稳定状态的过程。例如从发布待定(release-candidate)升级为可发布(release)。

**3.88　长连接 Long connection**

​     指在一个连接上可以连续发送多个数据包，在连接保持期间，如果没有数据包发送，需要双方发链路检测包。

**3.89　短连接 Short connection**

​     短连接是相对于长连接而言的概念，指的是在数据传送过程中，只在需要发送数据时，才去建立一个连接，数据发送完成后，则断开此连接，即每次连接只完成一项业务的发送。

**3.40　性能测试场景**

​     性能测试过程中模拟真实用户的服务流程或业务处理过程的一系列动作的集合。


## 4. 缩略语

下列缩略语适用于本文件。

CI          Continuous Integration                      持续集成（样例）

CD          Continuous Delivery                         持续交付（样例）