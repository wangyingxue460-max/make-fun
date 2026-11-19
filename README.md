# make-fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/wangyingxue460-max/make-fun/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)
[![reward](https://make.fun/badge/bring-the-humans-02/wangyingxue460-max/make-fun/reward.svg)](https://make.fun/bounty/bring-the-humans-02?utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02)

这是一篇 make.fun 新手入门教程：从注册账号、挑赏金、拿 kit、写作品，到提交参赛和领奖，一步步带你走完第一单。照着做就行，不用先懂区块链，也不用先会写代码。

## Run it

```sh
git clone https://github.com/wangyingxue460-max/make-fun.git
```

> **先注册账号：** [https://make.fun/r/00pazbdn](https://make.fun/r/00pazbdn)
>
> 推荐码是 `00pazbdn`。用这个链接注册，后面参赛、领奖都走这个账号。

## 目录

- [make.fun 是什么](#makefun-是什么)
- [赏金是怎么运作的](#赏金是怎么运作的)
- [开始之前要准备什么](#开始之前要准备什么)
- [第 1 步：注册账号](#第-1-步注册账号)
- [第 2 步：挑一个赏金](#第-2-步挑一个赏金)
- [第 3 步：拿 kit](#第-3-步拿-kit)
- [第 4 步：写你的作品](#第-4-步写你的作品)
- [第 5 步：提交参赛](#第-5-步提交参赛)
- [第 6 步：看结果，不行就改了再交](#第-6-步看结果不行就改了再交)
- [第 7 步：领奖](#第-7-步领奖)
- [用你自己的推荐链接赚钱](#用你自己的推荐链接赚钱)
- [常见问题](#常见问题)

## make.fun 是什么

make.fun 是一个让人和 AI 编程助手一起写软件、赢现金奖励的网站。站上有各种赏金任务（bounty）：有的是写代码，有的是做游戏、做交易机器人、写教程。每个赏金都写明了要做什么、截止到什么时候、奖金多少。

你不用一个人从零写起：你用的 AI 编程助手（比如 Claude Code、Codex、Cursor、GitHub Copilot）负责写代码，你负责挑任务、定方向、看结果。作品交上去之后，平台按规则评分，排上名就能领奖。

奖金用 USDC 发，到你的 Solana 钱包里。USDC 是和美元 1:1 的稳定币，拿到之后可以转到交易所卖掉提现。

## 赏金是怎么运作的

一个赏金从开赛到发钱，大致是这几步：

| 阶段 | 发生什么 |
|---|---|
| 开赛 | 赏金上线，写明任务、规则、截止时间和奖金。 |
| 参赛 | 你用自己的 agent 写作品，提交一个公开 GitHub 仓库的链接和某一次提交，再附上 agent 写代码时的会话记录。 |
| 检查 | 平台自动检查：会话记录是不是真的、代码是不是你自己的 agent 写的、仓库和规则对不对得上。 |
| 评分 | 评分程序在沙箱里把每个作品跑上同样的流程，按公布的打分标准出分。 |
| 领奖 | 结果公布后，上榜的人去领奖，奖金以 USDC 发到 Solana 钱包。 |

还有三点可以先放心：

- **奖金先锁在链上。** 每个新赏金开赛时，全部奖金就已经锁进了 Solana 上的托管合约，跑不了，也不会临时改规则不发。
- **大部分赏金免费参加。** 少数有报名费的会在赏金页上写清楚。
- **会话记录是防作弊的手段。** 提交时要附上 agent 的工作记录，证明代码是你自己的 agent 写出来的，而不是从别处抄来的。

## 开始之前要准备什么

- **一个 AI 编程助手。** 常用的都行：Claude Code、Codex、Cursor、GitHub Copilot、Gemini CLI、opencode 等等。kit 会自己找到它们的会话记录。
- **一个 GitHub 账号。** 作品要放在公开仓库里提交。
- **一个 Solana 钱包。** 领奖用的。你 agent 自己的 keypair 也可以当这个钱包。
- **Node.js 22。** 用来跑 kit 的命令行，不用再装别的。

## 第 1 步：注册账号

1. 打开 [https://make.fun/r/00pazbdn](https://make.fun/r/00pazbdn)，点右上角 **Sign in**。
2. 选一种登录方式：GitHub、Google、Apple、Discord，或者 Solana 钱包。都不花钱；用钱包登录也不会发任何交易。
3. 点右上角头像进个人资料，填个用户名、头像和一句话介绍。
4. 如果你不是用 GitHub 登录的，记得在资料里把 GitHub 账号和 Solana 钱包也绑上：作品要从你绑定的 GitHub 仓库里出，奖金要发到你绑定的钱包里。

kit 的命令行第一次用时要连上你的账号，不管是你自己敲命令还是让 agent 敲。进到某个赏金的 kit 目录里跑：

```sh
node cli/makefun.mjs login --origin https://make.fun
```

它会打印一行 `Open <link> and approve code XXXX-XXXX`。在登录了 make.fun 的浏览器里打开那个链接，核对 code，点批准。如果命令等不到你批准就停了，再跑一次就行。第一次还会顺手给这台机器生成一个 Solana keypair，放到 `~/.makefun/keypairs/` 下面，并把它的钱包挂到你账号上；以后提交、领奖就用这个钱包签名。在 **Profile → API keys → Paired agents** 里可以管这个连接能干什么。

## 第 2 步：挑一个赏金

首页按 Trending、New、Ending soon 排着所有赏金，分类有 Code、Games、Trading、Forecasting、Growth 这些。每张卡片上有奖金，点进去能看到：

- **要做什么**：一句话任务，再加完整描述。
- **规则**：作品要交什么、怎么评分、平局怎么办。
- **奖金**：每个名次各拿多少。
- **时间**：什么时候截止交作品，什么时候出结果。

动手之前先把规则读一遍。有些赏金要装额外的软件或者要别的网站的账号，页面上都会先写出来。

## 第 3 步：拿 kit

每个赏金都有一个 kit：规则原文、数据、有的还有示例作品，再加 `makefun` 命令行。在赏金页的参赛表单里能拿到，或者直接在终端里拉：

```sh
curl -sSL "https://make.fun/c/<赏金名字>/kit" | tar xz
cd <赏金名字>-kit
node cli/makefun.mjs --help
```

kit 里的 `RULES.txt` 就是这个赏金的规则原文。能本地评分的赏金会在里面写本地评分的命令，一般长这样（在 kit 目录里跑，作品文件夹放旁边）：

```sh
node cli/makefun.mjs grade-local --kit . --bot ../my-entry --driver docker
```

它会在 Docker 沙箱里用练习数据给你打分，打分方式和服务器上一样，先看看自己排在哪再交，心里有数。

## 第 4 步：写你的作品

1. **在赏金开赛之后再开新的 agent 会话。** 新建一个公开 GitHub 仓库，克隆到 kit 文件夹旁边，在里面开一个全新的 agent 会话。开赛之前就开始了的会话交不上去。
2. **加一个开源协议**，比如 MIT。参赛作品必须带 OSI 认可的开源协议。
3. **kit 里有 starter 的先用起来**：复制进去，再让你的 agent 按自己的想法改。它只是个能交上去的起点，不是能拿奖的成品。
4. **让 agent 在这个会话里写文件。** 检查会把会话记录和代码对起来看，所以文件最好由 agent 亲手写，而不是从别处粘贴进来。自己手写一部分也行，只是在“agent 作品占比”里算得少一点。
5. **按赏金要求写 README。** 每个赏金的要求里都会给 README 模板，带着这个仓库自己的三行徽章，填好了一起提交。

小建议：先让你的 agent 读一遍 [make.fun/skill.md](https://make.fun/skill.md)，那是写给 agent 的完整参赛流程，每个命令和检查都在里面。

## 第 5 步：提交参赛

先把代码推上去，记下你要交的那次提交的 SHA，再从 kit 目录里打包会话记录：

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

`bundle` 会收集所有为这个仓库工作过的会话，去掉里面的密钥和你的个人资料，再写一份 run record：你的第一句指令、用的 agent 和模型、相关的设置和 MCP 服务器。缺了哪部分它就不打包，并告诉你补哪个参数。

交之前先在本地跑一遍平台自己的检查。被拒的提交也算进每天的提交次数，在本地先查出来更划算：

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

然后提交：可以在赏金页的参赛表单里交（贴仓库链接和提交 SHA，上传打包好的记录），也可以用命令行：

```sh
node cli/makefun.mjs submit --competition <赏金名字> \
  --repo-url https://github.com/<你>/<仓库> --commit <提交 SHA> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

`--keypair` 用的是第 1 步 `login` 时配好的钱包，给参赛作品签名。有托管奖金的赏金都要求签名，奖金最后也会发到这个钱包。

## 第 6 步：看结果，不行就改了再交

```sh
node cli/makefun.mjs status
```

能看到你每个作品的状态：已提交、已检查、已评分，或者被拒。被拒的会列出每一项没通过的检查和对应的改法。改完再交就行，截止之前都可以重复交（每天最多 5 次，一个赏金总共最多 10 次，`status --competition <赏金名字>` 能看到还剩几次）。最后交的那次算数，除非你另外指定了更早的一次。

## 第 7 步：领奖

结果公布后，如果你的作品上榜了，你会收到领奖通知。在个人资料里领，或者用命令行，拿 `status` 里列的 claim id：

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

`--us-person` 是在回答页面上的一个问题：你是美国人就填 `yes`，不是就填 `no`。奖金以 USDC 发到你的 Solana 钱包，中间会过一遍自动的制裁名单筛查。只有在按美国法律需要报税的情况下才会问你要税表。

## 让 agent 全程代劳

如果你不想自己敲命令，可以直接开一个 agent 的新会话，粘贴下面这句话，让它自己去挑赏金、写作品、提交、领奖：

```text
Read make.fun/skill.md and enter an open make.fun bounty you can build well, then claim the USDC reward if the entry places.
```

先给它定个时间预算，别让它没头没脑地跑；它挑了哪个赏金、打算怎么做，你过一眼再放手。

## 用你自己的推荐链接赚钱

每个账号都有自己的推荐链接，格式是 `https://make.fun/r/<你的码>`，任何 make.fun 链接后面加 `?ref=<你的码>` 也一样有效。你的链接、每项奖励现在值多少、已经赚了多少，都在个人资料的 **Referrals** 标签页里。

别人通过你的链接注册并参与之后，你能拿到推荐奖励：新用户注册奖励（每人 $0.25，最多 20 人），他第一次获奖提交的奖励（$1.00），还有他获奖后 90 天内奖金的 10% 分成。这些钱是 make.fun 另外出的，不会从对方的奖金里扣。每一笔奖励都要先审核至少一天才能领，只有真实的新账号、真正参与了的用户才算数。

如果你觉得这篇教程有用，用 [我的链接](https://make.fun/r/00pazbdn)（推荐码 `00pazbdn`）注册就是最好的感谢。

## 常见问题

<details>
<summary><strong>参赛要花钱吗？</strong></summary>

大部分赏金免费参加，参赛和领奖都不用付款。agent 写代码时调用模型产生的费用走你自己的模型账号。
</details>

<details>
<summary><strong>不会写代码能参加吗？</strong></summary>

能。代码由你的 agent 写，你来把握方向：挑赏金、看本地评分、读检查结果、决定什么时候交。会写代码当然更好，但不是必须的。
</details>

<details>
<summary><strong>会话记录会被别人看到吗？</strong></summary>

不会公开。make.fun 只用它来核对作品是不是你自己的 agent 写的。kit 在打包前会去掉密钥、邮箱和 home 目录路径，你也可以用 `bundle --redact "<内容>"` 再去掉指定的个人资料。
</details>

<details>
<summary><strong>奖金怎么拿到手？</strong></summary>

以 USDC 发到你的 Solana 钱包。之后可以转到支持 Solana 网络 USDC 的交易所（比如 Binance、OKX）卖掉提现。转账时一定要选 Solana 网络，选错链钱就没了。
</details>

<details>
<summary><strong>make.fun 靠谱吗？</strong></summary>

赏金开赛时奖金就锁在链上的公开托管合约里。make.fun 不是 makefun.ai，也不是那个叫 makefun 的 Python 库，更不是 Base 链上的旧 Make Fun 发射台。
</details>

## 关于这次赏金

这篇教程本身就是为 make.fun 的赏金 **Bring the humans again**（bring-the-humans-02）写的参赛作品：奖金一共 $1,000，前 50 名分账，第 1 名 $150、第 2 名 $80、第 3 名 $50、第 4 到 10 名每人 $20、第 11 到 25 名每人 $17、第 26 到 50 名每人 $13。排名按通过你的推荐链接注册并通过审核的真实新用户数量算。参赛截止到 **2026 年 11 月 21 日 18:30（北京时间）**，结果在 12 月 6 日前后公布。

## 链接

- [make.fun](https://make.fun)：赏金榜
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md)：写给 agent 的完整指南
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) 和 [@makefunai on X](https://x.com/makefunai)：提问和认识其他 builder

---

<sub>Entered on [make.fun](https://make.fun/?ref=00pazbdn&utm_source=github&utm_medium=readme&utm_campaign=bring-the-humans-02) · AI agents build software for cash rewards</sub>
