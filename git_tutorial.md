# Git 和 GitHub 最基础使用教程

本文面向第一次接触 Git 和 GitHub 的同学。目标很简单：

1. 会把课程仓库下载到自己的电脑。
2. 看得懂 VS Code 里文件变色和左侧源代码管理的提示。
3. 会保存自己的修改并提交 commit。
4. 会在课程更新 notebook 后，获取最新版本。
5. 知道运行 notebook 后产生的输出可能会被 Git 追踪，并知道怎么避免常见问题。

不需要一开始理解 Git 的所有概念。先把最常用的几个动作学会即可。

## 0. Git 和 GitHub 是什么

**Git** 是版本管理工具。它记录一个文件夹里文件的变化，例如某个 notebook 被改了、某个 `.py` 文件新增了、某一行代码被删除了。

**GitHub** 是放 Git 仓库的网站。课程代码会放在 GitHub 上，同学们可以从 GitHub 下载，也可以把自己的修改上传到 GitHub。

可以简单理解为：

| 名词 | 含义 |
| --- | --- |
| repository / repo / 仓库 | 一个被 Git 管理的项目文件夹 |
| clone | 把 GitHub 上的仓库下载到自己电脑 |
| fork | 在自己的 GitHub 账号下复制一份别人的仓库 |
| commit | 保存一次版本记录，类似“存档” |
| pull | 从 GitHub 获取最新版本 |
| push | 把自己的 commit 上传到 GitHub |

## 1. 先安装并配置 Git

使用 GitHub 前，电脑上需要先安装 Git。下载地址：

<https://git-scm.com/downloads>

安装过程如果看不懂某个选项，可以问 AI。建议把自己的电脑系统、安装界面截图或报错信息一起发给 AI，例如：

```text
我在 Windows/macOS 上安装 Git，用于 VS Code 和 GitHub。现在看到这个安装选项/报错，请告诉我应该怎么选，以及如何检查是否安装成功。
```

安装完成后，需要做一次最基础配置：告诉 Git 你的名字和邮箱。它们会出现在 commit 记录里。

打开终端，运行：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

这里的名字可以是真名、拼音或 GitHub 用户名。邮箱建议使用 GitHub 账号邮箱；如果你不想公开邮箱，也可以在 GitHub 设置里找到 GitHub 提供的 private email。

### 怎样算 Git 配好了

至少满足下面三点，就可以继续后面的 clone 和 commit：

1. 终端里运行下面命令，能看到 Git 版本号：

```bash
git --version
```

例如：

```text
git version 2.45.0
```

2. 终端里运行下面命令，能看到自己的名字和邮箱：

```bash
git config --global user.name
git config --global user.email
```

3. VS Code 左侧能看到 **Source Control / 源代码管理** 图标；打开一个 Git 仓库后，VS Code 不再提示找不到 Git。

如果这三点有任何一步不成功，不要硬往下做。把命令输出或 VS Code 提示复制给 AI、课程助教或同学，通常很快就能定位问题。

## 2. 推荐的两种使用方式

### 方式 A：只想下载课程代码并跟着运行

如果你只是想获取课程 notebook、运行代码、每节课同步课程更新，最简单的是直接 clone 课程仓库。

适合：

- 只需要看课件和运行 notebook。
- 不打算把自己的修改提交回课程仓库。
- 不熟悉 Git，想先用最简单流程。

### 方式 B：想保留自己的修改，或者以后提交作业/改动

如果你想在自己的 GitHub 账号下保存修改，建议先 fork，再 clone 自己 fork 后的仓库。

适合：

- 想把自己的代码改动上传到 GitHub。
- 想长期保留自己的版本。
- 以后可能需要提交 Pull Request。

如果不确定，初学阶段可以先用方式 A。

## 3. clone：把仓库下载到电脑

### 3.1 用 VS Code 下载

1. 确认已经按第 1 节安装并配置好 Git。
2. 打开 VS Code。
3. 按 `Ctrl + Shift + P`，macOS 是 `Command + Shift + P`。
4. 输入并选择 `Git: Clone`。
5. 粘贴课程仓库地址，例如：

```text
https://github.com/ZichongWang/BioStat_Intro.git
```

6. 选择一个本地文件夹保存项目。
7. VS Code 询问是否打开 cloned repository 时，选择打开。

### 3.2 用命令行下载

如果你已经会打开终端，可以使用：

```bash
git clone https://github.com/ZichongWang/BioStat_Intro.git
cd BioStat_Intro
code .
```

`code .` 的意思是用 VS Code 打开当前文件夹。

## 4. fork：复制一份到自己的 GitHub 账号

如果你想拥有自己的版本：

1. 打开课程仓库网页。
2. 点击右上角 **Fork**。
3. GitHub 会在你的账号下创建一份复制品。
4. 打开你自己 fork 后的仓库页面。
5. 点击绿色 **Code** 按钮，复制 HTTPS 地址。
6. 按第 3 节的方法 clone 你自己的仓库。

注意：fork 后，你电脑里 clone 的地址应该是你自己的账号，例如：

```text
https://github.com/你的用户名/BioStat_Intro.git
```

而不是课程原始仓库地址。

## 5. 在 VS Code 里看懂 Git 提示

打开课程文件夹后，VS Code 会自动识别这是一个 Git 仓库。

### 5.1 文件颜色和字母提示

在 VS Code 左侧文件列表里，经常会看到文件名变色，或者旁边出现字母：

| 提示 | 含义 |
| --- | --- |
| `M` | Modified，文件被修改过 |
| `U` | Untracked，新文件，Git 还没有开始追踪 |
| `D` | Deleted，文件被删除 |

这不是报错，只是 VS Code 告诉你：这个文件和上一次 commit 时不一样了。

### 5.2 左侧源代码管理

VS Code 左侧有一个像分支一样的图标，叫 **Source Control / 源代码管理**。

点进去可以看到：

- 哪些文件改了。
- 每个文件具体改了哪些行。
- 可以输入 commit message。
- 可以点按钮完成 commit。

如果你运行 notebook 后发现很多 `.ipynb` 文件出现在这里，通常是因为 notebook 保存了输出结果。

## 6. commit：保存一次自己的修改

commit 可以理解为一次“版本存档”。建议每完成一个小任务就 commit 一次。

### 6.1 用 VS Code commit

1. 点击左侧 **Source Control / 源代码管理**。
2. 检查有哪些文件被修改。
3. 把想保存的文件点 `+`，这一步叫 stage。
4. 在上方输入一句 commit message，例如：

```text
finish mnist notebook exercise
```

5. 点击 **Commit**。

commit message 不需要很复杂，但要让自己看得懂这次改了什么。

### 6.2 用命令行 commit

```bash
git status
git add 文件名
git commit -m "finish mnist notebook exercise"
```

如果想一次加入所有修改：

```bash
git add .
git commit -m "update notes"
```

初学者使用 `git add .` 前，建议先看一眼 `git status`，确认没有把不想提交的文件也加进去。

## 7. push：把自己的 commit 上传到 GitHub

如果你 clone 的是自己的 fork，commit 后可以上传：

```bash
git push
```

在 VS Code 中，commit 后通常也会出现 **Sync Changes** 或 **Push** 按钮。

如果你是直接 clone 课程仓库，通常没有权限 push 到课程仓库。这是正常的。你仍然可以在自己电脑上运行和修改代码。

## 8. pull：获取课程更新的最新 notebook

每节课课程 notebook 可能会更新。你需要定期获取最新版本。

### 8.1 如果你直接 clone 的是课程仓库

如果你 clone 的地址是：

```text
https://github.com/ZichongWang/BioStat_Intro.git
```

那么获取课程更新通常只需要 `git pull`。

如果你没有修改过文件，在 VS Code 中：


1. 点击左侧 **Source Control / 源代码管理**。
2. 找到 `...` 菜单。
3. 选择 **Pull**。

或者用命令行：

```bash
git pull
```

### 8.2 如果你 clone 的是自己的 fork

如果你 clone 的地址是：

```text
https://github.com/你的用户名/BioStat_Intro.git
```

那么 `git pull` 默认获取的是你自己 fork 仓库的更新，不一定是课程仓库的最新更新。

最简单的方法是在 GitHub 网页上同步 fork：

1. 打开你自己 fork 后的仓库页面。
2. 找到 **Sync fork**。
3. 点击 **Update branch**。
4. 回到 VS Code 或命令行，运行：

```bash
git pull
```

这样你的 GitHub fork 会先跟上课程仓库，然后你的电脑再跟上你的 fork。

命令行熟悉以后，也可以添加课程仓库作为 `upstream`：

```bash
git remote add upstream https://github.com/ZichongWang/BioStat_Intro.git
git fetch upstream
git merge upstream/main
```

初学阶段不必强行记住这组命令。会用 GitHub 网页上的 **Sync fork** 就够了。

### 8.3 如果你修改过文件

如果你本地有修改，直接 `git pull` 有时会失败。Git 这样做是为了避免覆盖你的改动。

推荐流程：

```bash
git status
git add .
git commit -m "save my local notes"
git pull
```

意思是：

1. 先看看自己改了什么。
2. 把自己的改动 commit 保存起来。
3. 再获取课程的最新版本。

### 8.4 如果只是运行 notebook 产生了输出

很多同学会遇到这种情况：

1. 打开课程 notebook。
2. 运行了一些 cell。
3. 没有主动改代码。
4. VS Code 却显示 `.ipynb` 被修改了。

这是因为 notebook 会保存运行结果，例如表格、图片、报错信息、执行编号。这些内容也会写进 `.ipynb` 文件，所以 Git 会认为文件变了。

如果你不需要保留这些运行输出，建议在 pull 之前清除 notebook 输出：

1. 打开 `.ipynb` 文件。
2. 在 VS Code notebook 顶部或右上角找到 **Clear All Outputs**。
3. 保存文件。
4. 再看 Source Control 中是否还有改动。

如果这个 notebook 只是运行输出变了，你也可以放弃本地修改，让它回到课程版本。

在 VS Code 中：

1. 打开 Source Control。
2. 找到被修改的 notebook。
3. 点击文件旁边的撤销图标。
4. VS Code 可能会询问是否 discard changes，确认即可。

注意：discard changes 会丢掉这个文件里的本地修改。如果你在 notebook 里写了自己的答案或笔记，不要随便 discard。

## 9. notebook 冲突怎么办

当你本地修改了课程 notebook，而且又想获取课程最新版本时，可能出现 conflict / 冲突。

初学阶段，最常见的冲突来自 notebook 输出，而不是代码本身。

建议按这个顺序处理：

1. 如果你没有重要修改，只是运行过 notebook：放弃本地 notebook 修改，然后重新 pull。
2. 如果你写了重要笔记：先复制自己的重要内容到一个新文件，例如 `my_notes.md`，再处理冲突。
3. 如果你不确定：不要乱点 Accept Current 或 Accept Incoming，先问课程助教或 AI。

对于课程学习，最稳妥的习惯是：

- 课程提供的 notebook 尽量只运行，不大改。
- 自己的笔记写到单独文件，例如 `notes/week01.md`。
- 自己的练习可以另存为新文件，例如 `mnist_01_data_explore_my_work.ipynb`。

这样每节课更新时，和课程原始 notebook 冲突的概率会小很多。

## 10. 一个推荐的日常流程

每节课开始前：

```bash
git pull
```

上课时：

- 打开 notebook。
- 运行 cell。
- 如果要写较多自己的内容，建议另存为新 notebook 或写到自己的 notes 文件。

课后如果想保存自己的修改：

```bash
git status
git add .
git commit -m "add week 1 notes"
git push
```

如果你没有自己的 fork，最后一步 `git push` 可以跳过。

## 11. 常见问题

### Q1：VS Code 显示很多文件变了，是不是坏了？

不是。多数情况只是你运行了 notebook，输出被保存了。

先看文件是不是 `.ipynb`。如果只是输出，不需要保存，可以清除输出或 discard changes。

### Q2：我 pull 的时候提示有本地修改，怎么办？

先不要强行操作。运行：

```bash
git status
```

如果是自己重要的修改，先 commit：

```bash
git add .
git commit -m "save my work"
git pull
```

如果只是运行输出，可以在 VS Code 中 discard notebook changes，然后再 pull。

### Q3：我能不能直接改课程 notebook？

可以，但不推荐大量修改原文件。更推荐：

- 少量运行和临时修改：可以直接用。
- 想长期保存自己的答案：复制一份新 notebook。
- 想写课堂笔记：新建 `notes/` 文件夹，写自己的 Markdown 文件。

### Q4：我点错了 commit，会影响课程仓库吗？

不会。commit 默认只保存在你自己的电脑。只有 `git push` 才会上传到 GitHub。

如果你 clone 的是课程仓库，通常也没有权限 push 到课程仓库。

### Q5：我应该用 main 还是 dev？

初学阶段，如果只是上课使用，跟着仓库默认分支即可。

如果你开始自己维护课程材料，可以采用：

- `main`：稳定版本。
- `dev`：平时修改和准备中的版本。

但对于刚开始学习 Git 的同学，不需要马上掌握分支。先学会 clone、commit、pull 就足够了。

## 12. 最少需要记住的命令

```bash
# 下载仓库
git clone https://github.com/ZichongWang/BioStat_Intro.git

# 查看当前改动
git status

# 保存修改
git add .
git commit -m "message"

# 获取课程更新
git pull

# 上传到自己的 GitHub 仓库
git push
```

不确定当前发生了什么时，先运行：

```bash
git status
```

然后把输出复制给课程助教或 AI，通常就能判断下一步该怎么做。
