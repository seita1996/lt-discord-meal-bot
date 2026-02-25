---
theme: ./theme/zen-gradient
title: 「今週なに食べる？」をAIで終わらせた話
info: |
  「俺たちのAI活用LT」 / Tahara Seitaro
class: text-center
transition: slide-left
highlighter: shiki
mdc: true
---

## 「今週なに食べる？」を<br>AIで終わらせた話

2026-02-27

「俺たちのAI活用LT」 / Tahara Seitaro

<!--
0:00-0:15
-->

---
layout: two-cols
class: profile
---

## 自己紹介

### Tahara Seitaro

- Software Engineer
- 普段はWebアプリケーション開発
- 子育て奮闘中
- 悩み「可処分時間が足りない」

::right::

![](./assets/github-qr.png){width=250px lazy}

.

<!--
0:15-0:30
-->

---
layout: section
---

# pain

日々の献立を考えるのが面倒

<!--
0:00-0:15
面倒ですよね。
-->

---
layout: two-cols
---

## 我が家の献立運用

Discordで週2回Threadを立てる

![](./assets/meal-thread.jpg){width=250px lazy}

::right::

平日はコープ・休日はスーパーで買い出し

<!--
0:00-0:15
献立は買い出し頻度と合わせて週2回まとめて考えています。
夫婦のチャットは基本的にDiscordで行っているので、都度フォーラムのThreadを立てて考えています。
-->

---
layout: default
class: ideation
---

## 作りたいものをイメージする

<v-clicks>

- Discord Botに「献立考えて」コマンドを送る
- Botが数日分の献立を考えてくれる
- Botに「献立から買い物リスト作って」コマンドを送る
- Botがリストを作ってくれる・Discordから消し込みできる

</v-clicks>

<!--
1:25-1:50
ただレシピを出すだけじゃダメで、
「うちの家の運用」に合わせないと使われないんですよね。
月曜はコープ休みとか、水曜は15分以内とか。
-->

---

## Userの声を聞く

<div class="grid grid-cols-3 gap-6 mt-8">
<v-clicks>
<div>

### User = 私 + 妻

雑談を

**ChatGPTで文字起こし**

![](./assets/gpt-voice-pre.jpg){width=250px lazy}

↓

![](./assets/gpt-voice-after.jpg){width=250px lazy}

</div>
<div>

### まずは困りごとを言語化

![](./assets/gpt-voice-text.jpg){width=250px lazy}

</div>
<div>

### いきなり作らない

思い込みで作ると、  
誰も使わないものができる

</div>
</v-clicks>
</div>


<!--
1:50-2:20
いきなりコーディングじゃなくて、先にユーザーインタビューしました。
ユーザーは僕と妻です。
雑談を音声で録って、ChatGPTに要件をMarkdown化させたら、仕様が一気に固まりました。
ということで
雑談をChatGPTアプリで文字起こし
いきなり作らないのが大切
思い込みで作ると、  
誰も使わないものができる
まずは困りごとを言語化する
-->

---
class: ai-dialogue
---

## AIと壁打ち

<div class="ai-quote-grid mt-4">

<v-clicks>

> OpenRouter の無料APIを使い、discordの実用的なAIチャットボットを作ることはできる？

> 夫婦のdiscord スペースだけで使える献立botを作ろうと思う。
> サーバーコストをかけず、cloudflare workersでホストしたい。

> Slash Commandの設計をしたい。
> 献立は献立用のForumに「2/1-2/4」など数日単位でスレッドを作り、以下のような形で管理している。
> ...

> 実装はCodexにさせる予定。仕様書のMarkdownを作成したいが、検討しておくべき事項は残っている？

</v-clicks>

</div>

<!--
2:20-2:50
インタビューログはChatGPTのメモリに載っているので、要件を把握したうえで仕様書を書いてくれる
-->

---
layout: two-cols
---

## いざ実装

構成は

- Discord Bot（UI）
- Cloudflare Worker（Bot処理）
- D1（データ永続化）
- OpenRouter（LLM）
- GitHub Actions（デプロイ）

::right::

<div class="h-full grid place-content-center">

![](./assets/codex-app.png){width=600px lazy}

</div>

<!--
2:50-3:20
実装はDiscord Bot + Cloudflare Worker + D1のシンプル構成です。
仕様のMarkdownをそのままCodexに渡して書かせました。
-->

---
layout: quote
---

# ( っ'-')╮ =͟͟͞͞📝ﾌﾞｫﾝ

Hey AI, これ作って！

<!--
Markdownの仕様書をCodexに投げつけるだけ。
実装が一番短かったかもしれません。
-->

---
layout: section
---

## 完成！

<div class="h-4" />

<BotCrossfade />

<!--
-->

---
layout: section
class: learnings
---

## 学び

1. 勝負どころは実装前（要件化）
2. オリジナルの制約に価値が宿る
3. 完成より定着（使われるUX）

<!--
4:20-4:50
いきなりコードを書かせるより、家庭内の運用ルールと言語化を先にやるほうが成功率が上がる。
月曜はコープ休み・水曜は15分以内、みたいな生活の制約を入れた瞬間に、ただのAIデモから実用品になる。
動くBotはすぐ作れる。難しいのは、家族の導線に自然に乗せて定着させるUX設計。
-->

---
layout: quote
---

# Keep building.

Enjoy coding, happy hacking.

<!--
5:15-5:30
AIのおかげで作るハードルがぐっと下がり、面白い時代になりました。
ソフトウェアエンジニアの仕事はなくなるかもなんて言われていますが
この荒波を乗りこなしながら、自分が欲しいものをどんどん作っていきましょう。
ありがとうございました。
-->
