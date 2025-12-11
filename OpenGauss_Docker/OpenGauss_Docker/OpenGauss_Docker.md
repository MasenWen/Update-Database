# <p align="center">PDS Project2 Report</p>
# <p align="center">WSL→Docker→OpenGauss</p>

**<p align="center">Masen Wen</p>**
**<p align="center">2025-12-05</p>**


* 实验代码&实验报告已上传Github
  * https://github.com/MasenWen



---
## 实验设计

#### Goal
* Feed This Document to AI, AI can Follow Steps to complete OpenGauss installation.


#### 实验步骤
* 第一步：安装和配置WSL​
  * 在Windows上启用WSL功能并安装Ubuntu发行版。
* 第二步：在WSL中安装Docker​
  * 在WSL子系统内更新软件源并安装Docker引擎。
* 第三步：使用Docker安装和运行openGauss​
  * 拉取官方镜像，并通过docker run命令启动一个openGauss容器实例。
* 第四步：使用DataGrip连接数据库​
  * 在DataGrip中配置连接信息（主机、端口、密码），测试并连接至数据库。


---
## 第一步：安装和配置WSL（课程讲义）


## **Skip WSL**
* For Linux and MacOS, it is recommneded to get Docker directly. Skip to success parts and continue.
* For Windows WSL is convenient. However, you can also skip WSL and get yourself a docker and continue.
 
## **Using WSL**
* We start with downloading **WSL**. WSL is very easy to use and we later activate docker and further openGauss using WSL command lines.
* The upside of this approach is that **AI is extremly good at solving command line problems**: you simply copy the errors info and AI reacts to it with extremly high precision.
* The following information is from CS219Lab1(于++), it's recommended to use the PPT directly if possible.

![image.png](c1be126d-50c5-4caa-8108-1ecf7fa3e1fc.png)

![image.png](90bf44f9-ed27-4fbb-a27b-872f13affa1b.png)

![image.png](b69a5413-3503-42a2-80d5-b8d41922a5c4.png)

![image.png](52c1a848-a36e-4b5d-aceb-fe3f8b66b5f7.png)

![image.png](93aef3d2-d04b-4c76-80e9-c238fc67c684.png)

![image.png](f433f405-797a-4842-b6e9-405fb75f5228.png)

![image.png](30b2a96a-b9dc-4757-b074-606cd4ac1272.png)

![image.png](be7875d9-4309-4d04-ae0d-46e940d1eec7.png)

![image.png](540cac22-a7b7-460f-aa35-2f632a7c477b.png)

![image.png](44f14f8b-c091-44ac-a52d-3884f57ba2c0.png)

![image.png](e528721a-6486-4e5e-9ed8-017cc77ac07f.png)

![image.png](1c2f2fc1-0250-47ec-bc4b-592c69588741.png)

#### **Procedures** (conditions possibly met during WSL preparations are skiped)



---
## 第一步：安装和配置WSL（实操）

![image.png](20dc412e-7d42-4afe-b8d9-7316a9f15178.png)

![image.png](bc82c52d-6aaf-4714-93e3-77fe3f8e8cb1.png)

![image.png](51fa9ba7-8c0c-424e-b4c5-b4597a4dfffa.png)

![image.png](b4219ead-cc56-4f23-834a-38b7da357162.png)

![image.png](bb15bbc4-cde3-46aa-a112-61a6c5d992e4.png)

![image.png](36773c0b-4161-4531-8d30-feaa7ce197ea.png)

![image.png](339ef2f0-028a-4ad9-9e44-f8871c3a7f8d.png)

![image.png](707e3617-ec1b-4978-83ef-fbed6d7f048e.png)


---
## 第二步：在WSL中安装Docker

![image.png](071036de-1d79-4822-a269-6926bd64e23a.png)

![image.png](df586ad5-dd9d-4b8d-a02a-9bb414a2854a.png)

![image.png](7c1af673-657c-4dde-a8c0-4aa8fb25938a.png)
![image.png](169d5b31-c714-4462-8a6f-928f311ae82d.png)

![image.png](6bfad559-0098-4005-8188-cb711bfb6d6c.png)

![image.png](adc4bab0-801b-4936-8153-039ca56bf2e2.png)

![image.png](a2ba34ee-f113-46d5-beb2-d606fa97a2af.png)

![image.png](22d5acba-b42e-4eef-9a87-bfeb4a43f0e6.png)

![image.png](4ecc288b-fed9-4054-ac1e-8cd6620a52a5.png)

![image.png](a30d4c85-0c28-48b7-8189-bb935ab12891.png)

---
## 第三步：使用Docker安装和运行openGauss

![image.png](01b75d0c-0f1a-48af-9f7d-1bb88f874223.png)

#### 获取活跃稳定的镜像源 https://hub.docker.com/r/enmotech/opengauss

![image.png](81e9c0e8-053a-4fef-9950-8e4815268962.png)

![image.png](8c1cdb62-2faf-4034-9fdc-9f684a84e492.png)

![image.png](e2d690b1-b32a-4c93-b18a-7e815a95dd5e.png)

![alt text](image-4.png)

![image.png](31d22206-ce11-4259-a9e0-21f23ee50af8.png)

![image.png](a1cfcc3a-f5db-482d-8fb2-a290fdfbfe43.png)

![image.png](c8973649-6ca3-4fb8-b91d-fab83d3ff2a3.png)


---
## 第四步：使用DataGrip连接数据库

![image.png](bb1f01a8-5604-4bb2-a737-7900f39c32b4.png)

![image.png](52b5c43c-7fbe-469c-9791-08ff946edcad.png)

![image.png](1b350420-1dd1-432f-bbef-c8d86cb5c8d6.png)

![image.png](fbea7e65-1cfb-4597-8d29-91a0c354ceaa.png)

---

# About Docker
### Docker 是基于 Go 语言开发的开源项目
#### 官网： https://www.docker.com/
#### 文档： https://docs.docker.com/
#### 仓库： https://hub.docker.com/

#### 阅读材料链接: [虚拟机和Docker介绍](https://aws.amazon.com/cn/compare/the-difference-between-docker-vm/)
#### 阅读材料链接: [基于openGauss学习Docker](https://opengauss.org/zh/blogs/2022/%E5%9F%BA%E4%BA%8EopenGauss%E5%AD%A6%E4%B9%A0Docker.html)

#### Docker不是**虚拟机** 而是虚拟**容器** 多个容器共享同一个操作系统 Docker容器直接与内核共享资源 与虚拟机相比 消耗的系统资源更少 性能更优

#### Docker的**操作简单**: build pull run 但是依赖Docker容器能实现的**功能很多**(这取决于容器内存放的内容 如:openGauss)

![alt text](image-1.png)

![alt text](image-3.png)
---

## Refference & Other Ways
#### [通过Docker安装openGauss](https://opengauss.org/zh/blogs/xiteming/%E9%80%9A%E8%BF%87Docker%E5%AE%89%E8%A3%85openGauss.html)
#### [openGauss快速安装方法(docker)](https://opengauss.org/zh/blogs/zhengwen2/openGauss%E5%BF%AB%E9%80%9F%E5%AE%89%E8%A3%85%E6%96%B9%E6%B3%95(docker).html)
#### [openGauss安装并使用DataStudio工具连接使用](https://opengauss.org/zh/blogs/mingruifu/openGauss%E5%AE%89%E8%A3%85%E5%B9%B6%E4%BD%BF%E7%94%A8DataStudio%E5%B7%A5%E5%85%B7%E8%BF%9E%E6%8E%A5%E4%BD%BF%E7%94%A8.html)(不要使用DataStudio)
