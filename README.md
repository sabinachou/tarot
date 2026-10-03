# ✦ Tarot Table 塔羅牌桌

**Draw a card, talk it through.** A cute, black-and-white tarot reading site you can use for yourself or to read for friends, in English or Traditional Chinese.

🔗 **Live site:** https://sabinachou.github.io/tarot/

---

## What it does

Tarot Table walks someone through a full reading, from a few quick questions about themselves to a detailed, personal interpretation of the cards they draw.

1. **Get to know the person.** A short, tap-only quiz with hand-drawn icons asks who's asking, their love life, today's mood, and what they want from the reading (a clear answer, advice, clarity, or comfort).
2. **Shape the question.** Pick a topic (General, Love, Career, Money, Health, Family, Friends) and, for most topics, a quick follow-up about their situation. A question helper nudges them to be specific and offers ready-made question templates.
3. **Choose a spread.** One card, Time Flow (three cards whose positions change with the topic), or the ten-card Celtic Cross.
4. **Prepare.** A calm preparation screen shares five simple guidelines, guides three slow breaths, and gently reminds people if they've asked the same question in the last 30 days.
5. **Shuffle and draw.** The deck is washed across the table, then spread out so the person can pick by feel. Picked the wrong one? Undo it.
6. **Read the cards.** Flip them one by one or all at once, and get:
   - **A detailed reading for each card**: what's on the card and what it means, how it applies to their question and position, and a constructive "toward a better place" note.
   - **A combined reading** that names the real theme, weaves the cards into one story, notices patterns between cards, brings in their background, offers two concrete next steps, and answers their question directly.
   - **An optional AI deep reading** for an even more personal interpretation.
7. **Share and give feedback.** Copy the whole reading to send to a friend, and tap a quick "did this speak to you?" rating.

---

## Highlights

**78 original hand-drawn cards.** Every card is drawn in code as black-and-white chibi line art with a slightly hand-sketched feel. Each one shows a real scene, following the traditional symbolism of the public-domain Rider–Waite–Smith deck, so you can tell what's happening at a glance.

**Readings that stay on topic.** Choose Love, and the reading talks only about love. Each topic has its own position names, card meanings, advice, and follow-up situations (for example, "Single, hoping to meet someone" or "Happy together, just curious" for Love).

**Readings that respond to the question.** The site recognizes question types (yes/no, either/or, why, when, how) and 30+ common subjects such as rent, job interviews, confessing feelings, sleep, or parents, then tailors the conclusion and advice.

**Warm and constructive.** Difficult cards are framed as early heads-ups, not verdicts. Every card includes a hopeful, practical note, and health readings never give medical advice.

**Thoughtful details**
- English / 中文 toggle on every screen
- Reversed cards can be turned on or off (about 1 in 4 cards come up reversed)
- Works on phones and desktops, supports dark mode, and respects reduced-motion settings
- A cute thank-you animation at the end

---

## Tech overview

The whole site is a **single self-contained `index.html`**: HTML, CSS, JavaScript, card art, and all reading content in one file. No build step, no framework, no database.

| File | What it's for |
|---|---|
| `index.html` | The entire website |
| `worker.js` | Optional Cloudflare Worker that powers the AI deep reading |
| `.nojekyll` | Tells GitHub Pages to publish the site as-is |
| `README.md` | This file |

- **Hosting:** GitHub Pages (free)
- **AI:** Cloudflare Workers AI on the free plan, running an open-source Qwen3 model with an automatic backup model
- **Feedback:** an anonymous Google Form

---

## Setup

### Publish the site
1. Upload `index.html` and `.nojekyll` to the root of a public GitHub repository.
2. Go to **Settings → Pages**, set the source to **Deploy from a branch**, branch **main**, folder **/ (root)**.
3. Your site will be live at `https://<username>.github.io/<repo>/` in a minute or two.

To update the site, upload a new `index.html` over the old one.

### Turn on the AI deep reading (optional, free)
1. In Cloudflare, create a Worker (**Workers & Pages → Create → Start with Hello World!**), replace its code with `worker.js`, and deploy.
2. In the Worker's **Settings → Bindings**, add **Workers AI** with the variable name `AI`.
3. Copy the Worker's address and paste it into `const AI_ENDPOINT = '...'` in `index.html`.

If `AI_ENDPOINT` is empty, the AI button simply stays hidden and everything else works normally.

### Collect feedback (optional)
Create a Google Form with three questions (Rating as multiple choice with `Spot on` / `A little` / `Not really`, plus Topic and Cards as short answers). Use **Pre-fill form** to find each question's `entry.` ID, then fill them into `const FEEDBACK` in `index.html`. Results appear as a pie chart under the form's **Responses** tab.

---

## Settings you can change

| Setting | File | Default | What it does |
|---|---|---|---|
| `REV_CHANCE` | `index.html` | `0.25` | Chance a card comes up reversed |
| `AI_ENDPOINT` | `index.html` | your Worker URL | Where AI readings are sent |
| `AI_DAILY` | `index.html` | `3` | AI readings per person per day |
| `FEEDBACK` | `index.html` | your Google Form | Where ratings are sent |
| `ALLOWED_ORIGINS` | `worker.js` | your site address | Which sites may use the Worker |
| `MODELS` | `worker.js` | Qwen3 30B, Llama 3.1 8B | AI model and backup |
| `MAX_PER_IP_PER_HOUR` | `worker.js` | `6` | Extra protection against heavy use |

On Cloudflare's free plan, the shared daily allowance supports roughly 150–300 AI readings a day across all visitors. When it runs out, visitors see a friendly message and no charges are made.

---

## Privacy

- No sign-up and no accounts.
- The language choice, recent questions (for the 30-day reminder), and the daily AI count are stored only in the visitor's own browser.
- A feedback rating sends only the rating, the topic, and the card names, with nothing that identifies the person.
- An AI deep reading sends the cards, question, topic, and quiz answers to the Cloudflare Worker to generate the reading. The site doesn't save them.

---

## A note on tarot

Tarot is a tool for reflection, not a fixed prophecy. Big decisions are yours to make. 🃏

---

## 中文簡介

**塔羅牌桌**是一個可愛的黑白手繪風塔羅網站，可以自己抽，也可以幫朋友算，支援中文和英文。

- **抽牌前**：先用幾個小問題了解求問者（感情狀態、今天的心情、想得到什麼），再選主題、補充狀況、寫下具體的問題。
- **準備與洗牌**：抽牌前的提醒與深呼吸引導，接著推散洗牌，憑直覺從整排牌中挑選，點錯可以收回。
- **78 張手繪 Q 版牌**：每張都有具體的人物動作和場景。
- **深入解讀**：每張牌都有牌意介紹、放在問題裡的解析，以及往好的方向的建議。綜合解讀會點出這次真正的課題、把牌串成故事、給兩個具體建議，並直接回應問題。
- **AI 深入解讀（選用）**：透過 Cloudflare 免費方案提供更貼近個人的解讀，每人每天 3 次。
- **其他**：可複製解讀分享給朋友、匿名回饋統計，也支援手機和深色模式。

塔羅牌是幫助思考的工具，不是命定的預言。重要的決定，請留給自己。
