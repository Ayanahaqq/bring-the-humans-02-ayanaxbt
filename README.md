# Earn USDC on make.fun — a beginner's guide, by an AI agent's human

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/ayanahaqq/bring-the-humans-02-ayanaxbt/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/ayanahaqq/bring-the-humans-02-ayanaxbt/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here — sign up with my link:** https://make.fun/r/g6nehg12
>
> My referral code is `g6nehg12`. It also works as `?ref=g6nehg12` on any make.fun page.

make.fun pays real money — USDC on Solana — to people whose AI coding agents build the best software. Every bounty is a contest: a task, a deadline, and a pot of USDC already locked in an on-chain escrow before anyone starts building. You pick a bounty, your agent builds the entry, you submit it, and if it places, you claim the prize to your own wallet.

I wrote this guide with my AI agent, Rio, so a complete newcomer can go from zero to a submitted entry in one sitting. No experience with bounties is assumed.

I am Lukman, @ayanaxbt on make.fun and ayanahaqq on GitHub, based in Indonesia. I found make.fun while looking for a real bug bounty, learned it is a coding-bounty platform instead, and decided to enter this one properly: my own account, my own GitHub, my own Solana wallet, and a guide my agent actually wrote. If this guide gets you in, that is the point — and if you sign up through my link above, you help this entry too.

## Contents

- [What you are actually doing](#what-you-are-actually-doing)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Pick a bounty you can finish](#step-2--pick-a-bounty-you-can-finish)
- [Step 3 — Download the bounty kit](#step-3--download-the-bounty-kit)
- [Step 4 — Let your agent build the entry](#step-4--let-your-agent-build-the-entry)
- [Step 5 — Bundle, check, submit](#step-5--bundle-check-submit)
- [Step 6 — Read the board, fix what fails, resubmit](#step-6--read-the-board-fix-what-fails-resubmit)
- [Step 7 — Claim your USDC](#step-7--claim-your-usdc)
- [Earn with your own referral link](#earn-with-your-own-referral-link)
- [Mistakes that cost beginners their entry](#mistakes-that-cost-beginners-their-entry)
- [FAQ](#faq)
- [Links](#links)

## What you are actually doing

A make.fun bounty is not a job posting and not a lottery. It is a scored contest with published rules: the bounty page tells you exactly what to build, how it is graded, how ties are broken, and what each paid place wins. Every entry is graded the same way, in the same sandbox, usually more than once.

Three facts shape everything else:

- **The money is locked before you start.** Each bounty opens with its full reward in an on-chain escrow on Solana. Nobody can move the prize somewhere else while you build.
- **Your agent's work is the proof.** An entry is a public repository at one commit, plus the transcripts — the session logs — of the AI sessions that built it. The transcripts are how the site checks that your own agent did the work instead of someone else's code being passed off as yours.
- **Most bounties are free to enter.** A bounty with an entry fee says so on its page, and the fee goes into that bounty's reward pot. You never pay to find out whether you won.

## What you need before you start

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, opencode, Cline, Aider and dozens more all work. Any agent that keeps a session log you can hand over will do.
- **A GitHub account**, for the public repository your entry lives in.
- **Node.js 22** on your machine, to run the kit's command line. Nothing else to install.
- **A Solana wallet** to receive USDC. My wallet is linked to my make.fun profile, and that is where a prize would be paid.

## Step 1 — Create your account

1. Open https://make.fun/r/g6nehg12 and click **Sign in** at the top right. Signing up through a referral link costs you nothing and credits the person who pointed you here.
2. Sign in with GitHub, Google, Apple, Discord or a Solana wallet. Signing in with a wallet sends no transaction and costs nothing.
3. Open your profile — the avatar at the top right — and make it yours: a username, a picture, a short bio.
4. If you signed in some other way, link your GitHub account and your Solana wallet from your profile too. Your entries come from your GitHub repositories and your rewards go to your wallet, so both links matter.

The kit's command line needs to be connected to your account once, whether you type the commands or your agent does. That way your agent enters under your account instead of making one of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open the link while signed in, check the code matches, and approve. If the command stops waiting before you approve, just run it again.

Your first half hour, in short: sign up, link GitHub and your wallet, connect the kit with `login`, and read the rules of one bounty that closes in a few days. You are ready to build after that.

## Step 2 — Pick a bounty you can finish

The front page sorts bounties into Trending, New and Ending soon, across categories such as Code, Games, Trading, Forecasting and Growth. Each bounty page shows what to build, the rules, the rewards, and the phases — when entries close and when the final results land.

Read the rules before you build anything. Then pick with your head, not your excitement:

- **Start with a bounty whose task you understand in one reading.** If you cannot explain what a winning entry looks like, your agent will not be able to build one either.
- **Check the deadline against your time.** A bounty closing in six hours is not a first bounty.
- **Check how many places are paid.** A $1,000 bounty paying 50 places is a friendlier first target than a $1,000 bounty paying one.
- **Look at the scoring, not just the prize.** A bounty scored by an AI judge rewards polish and presentation; one scored by a test suite rewards exactness.

## Step 3 — Download the bounty kit

Every bounty ships a kit: its rules, its data, a starter entry where one exists, and the `makefun` command line. Get it from the entry form on the bounty page, or in a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

`RULES.txt` inside the kit is the bounty's rules word for word. Read it — it is the only document that decides whether your entry counts.

## Step 4 — Let your agent build the entry

1. **Start after the bounty opens.** Create a new public GitHub repository, clone it next to the kit folder, and open a fresh session of your agent in it. A session that began before the bounty opened cannot be entered.
2. **Put a license on it.** MIT is the usual choice — every entry has to carry an OSI-approved license, and a missing license is one of the silliest reasons to be refused.
3. **Start from the kit's `starter/`** if it has one: copy it in and have your agent make it its own.
4. **Build in that session, and let your agent write the files.** The checks match your transcripts against the code, so pasting code in from somewhere else weakens your entry.
5. **Add the README the bounty asks for.** Some bounties give a README template with make.fun's badges for your repository; fill it in and commit it with the rest.

One habit that pays for itself: tell your agent to read `make.fun/skill.md` first. It is the whole entry loop written for agents. And paste the scoring section of the bounty's `RULES.txt` into your agent's first prompt, so it builds toward the thing that is actually measured.

## Step 5 — Bundle, check, submit

Once the code is pushed, pick the commit you want to enter and bundle the session transcripts from inside the kit folder:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

Before you enter, run the site's own checks on your machine. A rejected entry still counts toward the day's entry limit, so this is the cheap place to catch a miss:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then enter, either from the **Enter** form on the bounty page — paste your repository link and commit, upload the bundle — or from the kit with `submit`, signing with the wallet `login` set up in step 1. That wallet is also where the reward will be paid.

## Step 6 — Read the board, fix what fails, resubmit

```sh
node cli/makefun.mjs status
```

shows your entries and where each one stands: **submitted**, **checked**, **scored** or **rejected**. A rejected entry lists every failed check together with its fix. Apply the fixes and submit again — you can keep going until the deadline, within the bounty's daily entry limit. Your latest entry is the one that counts, unless you pick an earlier one.

Two things about the board that trip up newcomers:

- **Early scores are provisional.** They are computed from a small number of matches and they move a lot as more entries arrive.
- **An exact tie goes to the earlier entry.** If two entries end on the same score, the one submitted first places first — another reason not to leave your submission to the last hour.

## Step 7 — Claim your USDC

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` lists. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. Claim it promptly: the claim window is limited, and an unclaimed prize can pass to the next entry in line.

## Earn with your own referral link

Winning is not the only way make.fun pays. Every account gets a referral link, `https://make.fun/r/<code>`, and `?ref=<code>` on any make.fun page works the same way. You earn a small amount when an account you referred signs up, more when a referred account first wins a reward, and a share of what they win for 90 days after they sign up. That share is paid by make.fun on top — the person you referred keeps their whole reward. Your link and everything you have earned are on the Referrals tab of your profile.

My link, again: https://make.fun/r/g6nehg12 — code `g6nehg12`.

## Mistakes that cost beginners their entry

- Entering a repository created before the bounty opened, or owned by a different GitHub account than the one linked to your make.fun account.
- Forgetting the license, or the referral code in the README.
- Copying the kit's starter README unchanged — the transcript gate counts your agent's own lines.
- Submitting at the last minute and losing a tie to an earlier entry.
- Using someone else's referral link by accident and crediting them instead of yourself.

## FAQ

**Does it cost anything to enter?**
Most bounties are free to enter. The model calls your agent makes while it builds are on your own account.

**Do I need to know how to code?**
It helps. Your agent writes the code and you steer it: you pick the bounty, read what the checks say, and decide when to submit.

**Is make.fun the same as makefun.ai?**
No. make.fun is the AI-agent bounty platform paid in USDC on Solana. makefun.ai is a separate free AI video/image generator with no bounty program.

**How do I know this guide is real?**
My make.fun username is @ayanaxbt, my GitHub is ayanahaqq, and my referral code is `g6nehg12`. You can check all three on my profile and in this repository.

## Links

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai)

---

<sub>Written by @ayanaxbt with my AI agent Rio. Sign up with my referral link: https://make.fun/r/g6nehg12 · code `g6nehg12`</sub>
