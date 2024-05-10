---
layout: post
title: "业内主流流程引擎有几种？"
category: 流程引擎
---

目前基于Java语言开发的主流开源工作流引擎有osworkflow、jbpm、activiti、flowable、camunda。其中osworkflow、jbpm技术较老已经过时，activiti包括activiti5、activiti6、activiti7三个版本，flowable分开源版和商业版，camunda包括camunda7和camunda8两个系列的版本。这么多版本的开源流程引擎，哪个功能完善、性能最好，该如何选型呢？

### **1、Activiti**

Activiti的源头是由JBPM4流程引擎发展而来，activiti的版本比较复杂，有activiti5、activiti6、activiti7几个版本。

**（1）activiti5和activiti6：**activiti5以及ativiti6的核心开发团队是Tijs Rademakers团队，activiti6最终版本由Salaboy团队发布的，因为Tijs Rademakers团队后来去开发flowable流程引擎了。activiti5和activiti6的代码在github上已经4年没有更新了，官方已经停止维护和发展，新开发项目不建议选择activiti5以及ativiti6。

**（2）activiti7即Activiti Cloud：**定位云产品，完全面向云原生架构设计开发，依赖k8s等多个CNCF云原生组件，开发、集成、部署和运维均比较复杂，对团队技术人员能力要求高，一般中小型项目，不建议选择Activiti7，其它大型项目需谨慎选择Activiti7。

官方网站：[https://www.activiti.org/](https://www.activiti.org/)

### **2、flowable**

flowable基于activiti6衍生出来的版本，Flowable除了提供开源版本flowable-engine，它还提供了商业收费版本：Flowable Work、Flowable Orchestrate和Flowable Engage 。

**（1）Flowable开源版**最新版本是Flowable-7.0.0-M1，开源版本仅仅提供了流程引擎、CMMN引擎、DMN引擎功能，其它功能需要扩展开发。Flowable开源版本目前仍在持续发展，其github上源码工程较多，有技术能力的团队，可用选择Flowable进行扩展开发。

**（2）Flowable Orchestrate**除了支持Flowable开源版本的功能，还支持Automation Models、Case & Process Instances、High Availability & Scalability等功能。

**（3）Flowable Work**是一个功能强大的低代码自动化平台。它建立在我们引擎的开源版本上，但通过将三个开放标准BPMN、CMMN和DMN的强大功能与低代码功能相结合，将业务流程管理提升到了一个新的水平。  Flowable Work是一个基于SaaS化的商业收费版本。

官方网站：[https://flowable.com/open-source/](https://link.zhihu.com/?target=https%3A//flowable.com/open-source/)

### **3、Camunda**

Camunda有Camunda7和Camunda8两个版本。

**（1）Camunda7：** Camunda7基于activiti5发展来来，所以其保留了PVM，最新版本Camunda7.18，BPMN标准模型，保持每年发布2个小版本的节奏，除了开源版本同时也提供了商业版，不过对于一般企业应用，开源版本也足够了。camunda7在功能方面比flowable、activiti流程引擎强大，性能和稳定性更突出。

**（2）Camunda8：**2022年4月，官方发布了Camunda8新版本，Camunda7和Camunda8在技术架构方面有本质区别。Camunda8定位于云架构SaaS模式，基于Zeebe流程引擎内核，采用gRPC API接口技术，不再使用关系型数据库。在开源和商业授权方面，Camunda8有诸多限制，Camunda8仅有Zeebe、modeler、elastic组件是开源的，可以免费使用，其它的组件Camunda Operate、Camunda Tasklist 、 Camunda Optimize等组件是需要商业授权才能使用。

私有化部署流程引擎需求的推荐选择camunda7，大部分组件开源，可免费使用，技术生态较好，程序员上手容易。
