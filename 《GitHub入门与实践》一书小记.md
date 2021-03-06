#《GitHub入门与实践》一书小记

> 活学活用，记好笔记

### Github Flow的流程

**开发流程**

- 令 master 分支时常保持可以部署的状态  

- 进行新的作业时要从 master 分支创建新分支，新分支名称要具有 

  描述性

- 在❷新建的本地仓库分支中进行提交  

- 在 GitHub 端仓库创建同名分支，定期 push  

- 需要帮助或反馈时创建 Pull Request，以 Pull Request 进行交流 

- 让其他开发者进行审查，确认作业完成后与 master 分支合并 

- 与 master 分支合并后立刻部署 

要注意，没有进行过测试或者测试未通过的代码绝不可以合并到 master 分支。因此势必要用到持续集成等手段。 

**进行新的作业时要从 master 分支创建新分支**

新分支的名称要具有描述性 

新分支中进行提交，不要再新分支中做无关的修改，方便pull Request进行审查

**定期push**

开发过程中最好能让其他开发者看到自己的嗲吗，同时养成积极查看他人代码的习惯

**使用Pull Request**

不一定非得在合并master分支时才使用pull request，今早创建pull request让其他开发者能进行审查

pull request 可以显示差别及对单行代码插入评论

**务必让其他开发者进行审查**

审查之后如果认为可以与 master 分支合并，则需要明确地告知对 方。按照 GitHub 的文化，这里会用到“:+1:”或“:shipit:”等表情(图 9.5)。偶尔也会见到 LGTM 的字样，这是 Looks good to me 的简写。 

征得多个人同意后，便可找个适当的时机让其他开发者将该分支与 master 分支进行合并。 

<img src="http://qiniu.s001.xin/xi9uf.jpg">

审查结束后立刻部署

### 部署

如果一天需多次部署时，可花费少量时间来使部署实现自动化，

避免工作中的费时费力，同时减少失误，并且可以让开发人员以外的人都能参与部署，

这就需要一个好的部署工具，也可以通过web界面进行部署

<img src="http://qiniu.s001.xin/1s4p1.jpg">

**导入开发时的注意事项**

团队人越来越多且成熟度提高，开发速度会增快，往往会出现一个部署尚未完成，下一个pull request结束并开始实施部署，这时，就会难分辨是哪个部署造成的影响，所以在部署过程中可以通过工具上锁，或者在部署时通知整个团队

### 重视测试

- 测试自动化
- 编写测试代码，通过全部测试
- 维护测试代码

**不要让Pull Request中有太多反馈**

代码存在多处问 题，进行多次指正和修改后仍然无法达到与 master 分支合并的水准。出 现这种情况大概有两个原因。 

一是交流不足。如果创建 Pull Request 的理由没有获得认同，那就 不要通过 Pull Request 进行讨论，而是应该选择其他手段进行交流。最 好的解决途径是直接面谈。 

另一个原因是技术或能力不足。如果代码经常被指出问题，那么不 是编程能力方面有问题，就是团队编写代码时没有一个明确的规则。为 避免在无用的讨论上浪费时间，团队应该制定一个最低限度的编程规 则，并且告知每一名团队成员。如果在开发过程中还需要其他规则，可 以将这些规则整合到 Wiki 中，便于阅览及修改 

- 结对编程 
-  组织学习小组共享知识 
-  共享可供参考的资料 

**不要积攒Pull Request**

在以部署为中心的开发流程中，如果总有大量 Pull Request 处于等 待审查或等待修正的状态，会导致长期无法部署，引发严重问题。 

如果每一名开发者都在忙于实现各自的新功能，把所有精力都放在 编写代码和创建 Pull Request 上，势必会忽视审查与反馈工作。时间一 长，无法部署的 Pull Request 就会堆积如山。 

为防止这一情况发生，建议团队制定一个新的规则:想创建 Pull Request 的人要先去对其他人的 Pull Request 进行审查及反馈，并在可以 部署时及时部署。 

这样一来，自己想创建 Pull Request 时必须先处理其他人的 Pull Request，就可以有效避免 Pull Request 堆积的情况发生。 

<img src="http://qiniu.s001.xin/33djo.jpg">

### 导入git flow前的准备

**安装**

```bash
# mac
brew install git-flow
# linux
sudo apt-get install git-flow
```

**确认运行状况**

```bash
git flow
```

