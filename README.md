# Deis是一个轻量级的应用程序平台，用来在CoreOS集群中以Docker容器的方式部署并扩展十二要素应用程序（中文资料）。

十二要素（Twelve-Factor）

十二要素应用程序是一套方法论，用来指导如何构建现代的、可扩展的分布式应用程序。
我们觉得它集合了很多的关于软件即服务(software-as-a-service)的经验和智慧，特别是在Heroku的平台上。
Deis遵循十二要素应用程序的方法论和最佳实践来设计运行应用程序。

Docker

Docker是一个开源项目，通过一个轻量级、可移植、可独立运行的容器来打包、交付并运行应用程序。
Deis能把你的应用组装(curates)成Docker的镜像，然后通过Docker容器的方式在集群上发布。
(Deis自身也是一系列的互相写协作的Docker容器。)

CoreOS

CoreOS是一个新的、精简的Linux发行版，其架构专为运行现代的、容器式程序栈而设计。
Deis运行在CoreOS上，并部署到任何地方 - 公有云、私有云、裸机(bare metal)，甚至是你的工作站。
CoreOS能让Deis高弹性（high resilience）、规模化的部署应用或者服务，并且操作简单。

应用

Deis是围绕着应用的概念而设计的。应用存在集群上，并且使用容器来处理请求。
开发者使用应用来推送代码、更改配置、增加进程数、查看日志、运行管理命令和其他很多事情。

构建、发布、运行（Build, Release, Run）



构建阶段

Builder组件处理git push请求并且在临时的Docker容器内构建应用并生成一个新的Docker镜像(image)。

发布阶段

在发布阶段，一个Build和配置结合起来创建出一个新的数字型的发行版本（release）。紧接着这个发行版本会被推送到Docker registry以便稍后执行。当一个新的build被创建或者配置发生改变时，都会触发构建新的发行版本，这样回滚代码或配置更改都会变的很容易。

运行阶段

在运行阶段，容器会被分派到调度器（scheduler）并且更新相应的路由。调度器负责将容器发布到主机上，并且在保证它们在集群上的均衡。容器一旦处于健康状态koi会被推送到路由组件。旧的容器只有在新的容器上线并且开始处理请求后才会被收起来会以保证零停机部署。

备份服务

Deis把数据库、缓存、存储、消息系统以及其它后端服务当作附加资源，以符合十二要素应用程序的最佳实践。
应用通过使用环境变量附加后端服务。因为应用与后端服务之间没有耦合，所以应用可以任意独立的进行扩展，与由其它应用提供的服务通信，或者切换为外部服务以及第三方提供的服务。
# Deis

Deis (pronounced DAY-iss) is an open source PaaS that makes it easy to deploy and manage applications on your own servers. Deis builds upon [Docker](http://docker.io/) and [CoreOS](http://coreos.com) to provide a lightweight PaaS with a [Heroku-inspired](http://heroku.com) workflow.

[![Build Status](http://ci.deis.io/buildStatus/icon?job=test-master)](http://ci.deis.io/job/test-master/)
[![Current Release](http://img.shields.io/badge/release-v1.0.1-1eb0fc.svg)](https://github.com/deis/deis/releases/tag/v1.0.1)
[![Latest Docs](http://img.shields.io/badge/docs-latest-fc1e5e.svg)](http://docs.deis.io/en/latest/)

![Deis Graphic](https://s3-us-west-2.amazonaws.com/deis-images/deis-graphic.png)


New to Deis?  Learn more about Deis [Concepts](http://docs.deis.io/en/latest/understanding_deis/concepts/), [Architecture](http://docs.deis.io/en/latest/understanding_deis/architecture/) and how to [Deploy an Application](http://docs.deis.io/en/latest/using_deis/deploy-application/).

# Installing Deis

Deis is a set of Docker containers that can be deployed anywhere including public cloud, private cloud, bare metal or your workstation. Decide where you'd like to deploy Deis, then follow the [provider-specific documentation](http://docs.deis.io/en/latest/installing_deis/) for provisioning.

Trying out Deis? Please follow the documentation on [getting set up with Vagrant](http://docs.deis.io/en/latest/installing_deis/vagrant/).
Upgrading from a previous Deis release? See [Upgrading Deis](http://docs.deis.io/en/latest/managing_deis/upgrading-deis/) for additional information.

## Testing the cluster

Please follow the documentation on [testing Deis](http://docs.deis.io/en/latest/contributing/testing/).

## Hacking on Deis

Learn how to [hack on Deis](http://docs.deis.io/en/latest/contributing/hacking/) with a Docker-based development workflow.

## Troubleshooting

See the [Troubleshooting Deis](http://docs.deis.io/en/latest/troubleshooting_deis/) documentation for
assistance with common issues.

## License

Copyright 2014, OpDemand LLC

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at <http://www.apache.org/licenses/LICENSE-2.0>

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
