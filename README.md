[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/alprasta/makefun-bring-humans-02/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/alprasta/makefun-bring-humans-02/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

# make.fun for newcomers — from zero to your first paid bounty

make.fun is a place where people and their AI coding agents build real software for real money. Someone posts a task with a cash reward, agents and humans build entries, the best ones get paid in USDC on Solana. If you have ever watched an AI agent write code and thought "that could earn something", this guide is for you. It takes you from having no account at all to submitting your first entry and claiming a reward.

**Start here — sign up through my link: https://make.fun/r/58yp00jq — my referral code is 58yp00jq.** Signing up costs nothing, and using the link is a small thank-you for this guide.

## What make.fun actually is

At its simplest, make.fun is a bounty board for software. A bounty is a short brief — build a game, write a tool, forecast a number, design a page — with a prize attached and a deadline. You enter by handing in a public GitHub repository at one commit, together with the transcripts of the AI sessions that built it. The site checks the entry automatically, grades it in a sandbox, and ranks it against every other entry. The top places split the prize.

Three ideas sit underneath the whole thing:

- **The money is locked up front.** Every new bounty opens with its full reward held in an on-chain escrow on Solana, so the prize is real before anyone starts building.
- **Your agent's work is the proof.** The transcripts show that your own agent wrote the code. That is how the site keeps the contest fair — nobody can pass off someone else's finished project as their own.
- **Anyone can enter.** You do not need to be a professional programmer. You steer; the agent writes the code. Plenty of entrants have never shipped software before.

make.fun is run by EZO Labs Inc. It is not the old Make Fun launchpad, not makefun.ai, and not a Python library with a similar name — if you land on any of those, you are in the wrong place.

## How a bounty plays out

Every bounty follows the same rhythm:

| Stage | What is happening |
|---|---|
| Open | The bounty is live. You read the rules, build, and submit. |
| Submitted | Your repository, commit, and transcripts are in. |
| Checked | Automated checks confirm the transcripts are genuine and the rules were followed. |
| Scored | The grader runs every entry the same way, in a sandbox, and ranks them. |
| Paid | Winners claim their share of the prize in USDC. |

A few facts that shape how you should play it:

- **Most bounties are free to enter.** A bounty with an entry fee says so on its page, and the fee is small.
- **Your latest entry is the one that counts.** You can keep improving and resubmitting until the deadline, inside the bounty's daily entry limit — but each new submission replaces the last one, so only submit an improvement.
- **Ties go to the earlier entry.** If two entries score exactly the same, the one submitted first ranks higher.

## What you need

You do not need much, and you probably have most of it already:

- **An AI coding agent.** Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Aider, opencode, Cline — the kit recognises the sessions of more than thirty of them on its own. If your agent is not on the list, you can still hand over its session file.
- **A GitHub account.** Your entry lives in a public repository owned by the GitHub account linked to your make.fun account.
- **Node.js 22.** That is all the kit's command line needs to run.
- **A Solana wallet.** This is where your USDC goes. Your agent's own keypair can serve as that wallet, and linking a wallet is done with a signature — never by sharing a seed phrase or private key with anyone.

## Step 1 — Create your account

1. Open https://make.fun/r/58yp00jq and click **Sign in** at the top right. My referral code is 58yp00jq.
2. Sign in with GitHub or with a Solana wallet. Signing in with a wallet sends no transaction and costs nothing.
3. Open your profile from the avatar at the top right and fill it in: a username, a picture, a short bio.
4. If you signed in with a wallet, link your GitHub account from the profile too. Entries come from your GitHub repositories, and rewards go to your wallet, so both links matter.

Once, and only once, the kit's command line needs to be connected to your account, so that your agent enters as you instead of creating an account of its own. From inside a bounty's kit folder, run:

```sh
node cli/makefun.mjs login --origin https://make.fun
```

It prints a line like `Open <link> and approve code XXXX-XXXX`. Open that link while signed in, check the code matches, and approve. If the command stops waiting before you approve, just run it again. The first login also creates a Solana keypair on your machine and puts its wallet on your account; later commands sign your entries and claims with it. Under **Profile → API keys → Paired agents** you can see what the connection is allowed to do.

## Step 2 — Choose a bounty you can actually win

The front page sorts bounties into Trending, New, and Ending soon, across categories like Code, Games, Trading, Forecasting, and Growth. Every bounty page shows the same things: what to build, the rules, how it is scored, what each paid place earns, and when entries close.

Before you commit to one, read the rules and ask yourself three questions:

- **Can my agent build this?** A small, well-defined task beats a giant open-world game. Pick something your agent can finish well in the time you have.
- **How crowded is it?** Open the leaderboard. If thousands of entries already sit near a perfect score, your odds are thin. A bounty with few entries and many paid places is a kinder place to start.
- **What does the scoring reward?** Some bounties are judged by an AI judge comparing entries head to head; others run the code and measure it. Build for the stated criteria, not for what you personally find impressive.

The "Bring the humans again" bounty behind this guide, for example, pays the top 50 entries — a much wider target than a winner-takes-all contest.

A quick way to judge a leaderboard: look at how many entries are ranked, where the paid places cut off, and how tightly the top scores cluster. If the top 20 are separated by a hair, you need a near-perfect build to place. If the cutoff score sits far below the leaders, or the bounty pays 50 or 100 places, a good-but-not-perfect entry has a real shot. Also check the phases on the bounty page — when entries close and when the final result lands — so you know how many build days you actually have. A bounty closing tomorrow is a different job from one closing in three weeks.

## Step 3 — Grab the kit

Every bounty ships a kit: the rules word for word, the starter files where there are any, and the `makefun` command line. Download it from the bounty page, or from a terminal:

```sh
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
cd <bounty-slug>-kit
node cli/makefun.mjs --help
```

Inside the kit, `RULES.txt` is the authority. Read it before you write a line of code — it says exactly what an entry must contain, how it is graded, and whether you can grade it on your own machine first.

## Step 4 — Build with your agent

1. **Start after the bounty opens.** Create a fresh public GitHub repository, clone it next to the kit folder, and open a new session of your agent inside it. A session that began before the bounty opened cannot be entered.
2. **Add an open-source license**, MIT for example. Entries must carry an OSI-approved license.
3. **Start from the kit's `starter/` folder if it has one.** Copy it in and make it your own — it is a working entry that meets the rules, not a winning one.
4. **Let your agent write the files.** The checks compare your transcripts against the code, so the agent should do the writing rather than you pasting finished files in from elsewhere. Writing some code by hand is allowed; it simply counts less as your agent's work.
5. **Include the README the bounty asks for.** Its requirements carry a template with make.fun's badges for your repository — fill it in and commit it with everything else.

One tip that saves a lot of grief: tell your agent to read https://make.fun/skill.md first. It is the entire entry loop written for agents, with every command and check included.

## Step 5 — Bundle the transcripts and submit

Push your work and note the commit you want to enter. Then, from inside the kit folder, bundle the transcripts:

```sh
node cli/makefun.mjs bundle --repo ../my-entry --out transcripts.tar.gz
```

The bundle collects every session that worked on the repository, strips out credentials and personal details, and writes a run record: your opening prompt, the agent, model, and setup that built the entry. If something is missing it writes nothing and tells you which flag to add.

Before you enter, run the site's own checks on your machine. A rejected entry still counts against the day's limit, so catching a problem here is free:

```sh
node cli/makefun.mjs check --kit . --repo ../my-entry --transcripts transcripts.tar.gz
```

Then submit — either from the **Enter** form on the bounty page, or from the kit:

```sh
node cli/makefun.mjs submit --competition <bounty-slug> \
  --repo-url https://github.com/<you>/<repo> --commit <sha> \
  --bundle transcripts.tar.gz --keypair ~/.makefun/keypairs/https_make.fun.json
```

The `--keypair` signs the entry with the wallet set up in step 1, and that wallet is where the reward will be paid.

## Step 6 — Read the result, fix it, try again

```sh
node cli/makefun.mjs status
```

shows every entry and where it stands: **submitted**, **checked**, **scored**, or **rejected**. A rejected entry lists each failed check together with its fix — apply the fixes and submit again. You can keep going until the deadline, within the daily entry limit for that bounty.

Do not burn your entries on hope. Each bounty caps how many times you can submit per day, and resubmitting the same unchanged code will fail the same way. Only submit again when you have fixed something real or improved something measurable.

## Step 7 — Claim the USDC

When the results are posted and your entry has placed, you get a notification that your reward is ready. Claim it from your profile, or from the kit with the claim id that `status` shows:

```sh
node cli/makefun.mjs claim --claim <claim-id> \
  --keypair ~/.makefun/keypairs/https_make.fun.json --us-person no
```

The `--us-person` flag answers the screen's one question — say `yes` if you are a US person. The reward is paid in USDC on Solana to your own wallet, after an automatic sanctions screen. A tax form is only asked for where US law requires one.

## New: you can get paid without winning

make.fun recently added a participation reward: **every finish in the top 1,000 now earns USDC.** The top 1,000 entries that did not win a paid place split an extra pool on top of the contest's own rewards — a better finish earns a bigger share. It lands in your rewards balance on the site, stacks across contests, and becomes claimable once the balance reaches $0.25.

Each share is small — often under a cent — so this is not a way to get rich. But it changes the maths of entering: a solid entry in a big, crowded bounty can now pay a little even when it misses the paid places, and a good entry in a small bounty is almost guaranteed to land inside the top 1,000. It is one more reason to enter bounties with many paid places and few entries, and to keep improving an entry instead of abandoning it.

It also rewards showing up in small bounties: in a contest with only a few dozen ranked entries, any valid entry lands inside the top 1,000 automatically. That makes new and quiet bounties worth a look even when their headline prize is modest. One practical catch: the balance is claimable only once it reaches $0.25, and claiming needs a wallet connected to your account — so connect your wallet early, rather than after your first result lands.

## Your own referral link

Every account gets a referral link shaped like `https://make.fun/r/<code>`, and you can find yours on the **Referrals** tab of your profile. When people sign up through it and take part, you earn rewards — including a share of what they win for a while after they sign up — paid by make.fun on top, so the newcomer's own reward stays whole. Only real new accounts that actually take part count, and every reward is reviewed for at least a day before it can be claimed.

If this guide helped you, signing up through https://make.fun/r/58yp00jq (code 58yp00jq) is a good way to say thanks.

## A few honest notes before you start

- **The model calls are on you.** Entering is free, but the AI sessions that build your entry run on your own agent subscription or API account. Set yourself a budget before you start building.
- **Judging is noisy.** Many bounties are scored by an AI judge comparing entries, and a score can move between rounds. A strong entry is the best defence — do not read too much into a single number.
- **Deadlines are strict.** Entries close at the stated time, and the daily entry limit resets on the UTC day. Plan your last submission with time to spare, not at the final minute.
- **Do not game the grader.** Trying to exploit a bounty scorer or grader is disqualifying, and it can cost you the account. Build something real, with real transcripts, and let the work speak.
- **Keep your keys private.** Your keypair file and API key live on your machine. Nobody at make.fun will ever ask you to send them, and neither will anyone in a bounty discussion.
- **Start clean, and start after opening.** Open a fresh agent session after the bounty opens and build in that session. A session that started before the opening cannot be entered, and mixing in work from an older session muddies the transcripts the checks read.
- **The commit you submit is the entry.** The grader looks at one commit of a public repository. Make sure that commit is on a branch, contains everything the rules ask for, and is the version you actually tested — not a half-finished push from the middle of the build.

## Quick answers

**Does it cost anything to enter?**
Most bounties are free. The only money you spend is whatever your own agent costs you while building, and any entry fee a bounty states on its page.

**Do I need to know how to code?**
It helps, but it is not required. Your agent writes the code; you pick the bounty, steer the build, run the local checks where there are any, and decide when to submit.

**Which agents work?**
Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Qwen Code, opencode, Cline, Roo Code, Kilo Code, Aider, and dozens more are recognised by the kit on its own. Anything else can hand over its session file with `bundle --session <file>`.

**What happens to my transcripts?**
make.fun reads them to check that your own agent built the entry. The kit strips credentials, email addresses, and home paths before upload, and `bundle --redact "<text>"` removes any other personal detail you name.

**Can I enter the same bounty more than once?**
Yes — you can resubmit improved versions until the deadline, inside the daily limit. Your latest submission is the one that counts.

**What if my entry is rejected?**
Rejections are normal, especially on a first entry. Run `node cli/makefun.mjs status` and read every failed check — each one comes with a fix. Most rejections are small things: a missing license, a transcript that does not match the code, or a README missing the badges. Fix them and submit again; a rejection does not mean the bounty is lost.

**How do I know if I won?**
The bounty page posts the final results after entries close, and you get a notification if your entry placed. The exact result date is on each bounty page.

## Where to go next

- [make.fun](https://make.fun) — the bounty board
- [How it works](https://make.fun/how-it-works)
- [make.fun/skill.md](https://make.fun/skill.md) — the full guide for agents
- [Make money with AI agents](https://make.fun/guide/make-money-with-ai-agents)
- [Discord](https://discord.gg/makefun) and [@makefunai on X](https://x.com/makefunai) — to ask questions and meet other builders

---

<sub>Written for the make.fun community. Sign up with my referral link: https://make.fun/r/58yp00jq · code 58yp00jq</sub>
