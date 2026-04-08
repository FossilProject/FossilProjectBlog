---
layout: default
title: "Back at It (Sort Of) | FOSS News Weekly Recap"
date: 2026-04-05
author: S.K. Ooma
tags: [foss, news, anthropic, github, fyrox, rust, nasa, onlyoffice, nextcloud, manjaro, linux]
---
# FOSS Weekly Recap — Week of April 1st
 
Hey everyone. I owe you an explanation before we get into it, because I know it has been quiet around here lately. Finals week hit hard, and on top of that I started a new job that had me bouncing across several states this past week. Between the studying, the traveling, the onboarding, and the general chaos that comes with doing all three at once, writing just was not in the cards. But I am back, mostly in one piece, and there is a lot to catch up on. This was genuinely one of the busiest weeks in FOSS-adjacent news in recent memory, so let's get into it.
 
---
 
## Anthropic Accidentally Open-Sourced Themselves
 
Version 2.1.88 of Anthropic's Claude Code npm package shipped with a 59.8 MB JavaScript source map file that was never meant to be public. That file pointed directly to a hosted archive of the tool's full TypeScript source, around 512,000 lines across roughly 1,900 files. Security researcher Chaofan Shou spotted it within hours, posted about it, and from there it was over. The code spread across GitHub faster than any takedown notice could realistically keep up with.
 
The root cause was a known bug in Bun's bundler combined with a packaging shortcut and a release process with no safety net. Even with source map generation disabled, the bundler was still producing and including source maps in the output. Nobody caught what was actually inside the package before it shipped.
 
What was exposed was the full internal architecture of Claude Code, including its agentic harness, multi-agent coordination logic, permission systems, and 44 hidden feature flags for functionality that has not shipped yet. There was also a feature buried in the code called "Undercover Mode," a subsystem built specifically to stop Claude from leaking Anthropic's internal codenames when working in public repositories. The injected system prompt literally says "Do not blow your cover." It blew its cover.
 
Then Anthropic's response made things worse. The DMCA takedown they issued was executed against roughly 8,100 repositories, including legitimate forks of Anthropic's own publicly released code. Their head of Claude Code walked it back quickly, but the damage to community goodwill was already done. One developer stayed up, ported the entire core architecture to Python from scratch, and pushed a clean-room rewrite before sunrise. That repo became one of the fastest in history to hit 30,000 GitHub stars, and because it was a reimplementation rather than a copy, it was untouchable by any copyright claim.
 
Anthropic confirmed it was human error and that no customer data was exposed, which is probably true. But the sight of a company that markets itself heavily on safety and ethics running to copyright law to contain a leak, while having trained on pirated books, was not a great look. The community noticed.
 
---
 
## GitHub Copilot Was Putting Ads in Your Pull Requests
 
This one started when Australian developer Zach Manson noticed that a coworker had used Copilot to fix a typo in a pull request. Copilot fixed the typo, and also inserted a promotional message for a third-party app called Raycast directly into the PR description, formatted to look as though Manson had written it himself.
 
It was not an isolated incident. Copilot had injected promotional messages into over 1.5 million pull requests across GitHub and GitLab, promoting tools including Raycast, Slack, and various IDE integrations. Each injection was preceded by a hidden HTML comment identifying Microsoft as the source, while the content appeared under the names of the developers who had never written a word of it.
 
GitHub's VP of Developer Relations disabled the feature and called the behavior "icky." Microsoft's official statement framed it as a programming logic error, saying the tips were only meant to appear on Copilot-created PRs and expanded incorrectly when the feature was updated. Whether you find that explanation satisfying probably depends on how charitable you are feeling toward Microsoft this week.
 
The part that is harder to wave away is the cleanup problem. Pull request descriptions are part of the permanent version control history and cannot be automatically rolled back. Every affected project requires individual manual auditing to find and remove the injected content, with no tooling or timeline provided by GitHub. The developers whose work was modified without consent are now the ones doing the cleanup.
 
---
 
## Fyrox 1.0: Seven Years in the Making
 
Fyrox, the open-source 2D/3D game engine written in Rust, hit its 1.0 stable release in late March after seven years of development. The project had been targeting the milestone to coincide with the engine's seventh birthday, originally planned for March 19. Two release candidates preceded the final stable build, and the official Fyrox book was updated in full alongside the release with current screenshots and nearly every chapter complete. For a small, mostly unfunded open-source project, shipping complete documentation at the same time as a stable release is genuinely impressive.
 
Headline additions in 1.0 include a new export CLI for automating builds targeting PC, WebAssembly, and Android, and a refactored scene loading system with a more flexible task-based approach replacing the old AsyncSceneLoader.
 
The dev team acknowledged the release was exhausting and said new major features would be on pause for a few months while they recovered. Lead developer mrDimas specifically said he was taking a break. He then pushed eight commits the next day. Anyone who has ever tried to take a break from a project they care about will understand exactly how that happens.
 
---
 
## Artemis II Had to Call IT Support. In Space. About Outlook.
 
NASA launched Artemis II on April 1st, the first crewed lunar mission in over fifty years. Four astronauts are on a ten-day mission to orbit the moon, and the mission itself is going well. The software situation is a different story.
 
Roughly seven hours after launch, Commander Reid Wiseman radioed Houston to report he had two instances of Microsoft Outlook on his computer and neither one was working, asking ground teams to remote in and sort it out. The flight director later explained at a press conference that the issue was not unusual, noting Outlook can develop configuration problems without a direct network connection. Ground teams resolved it remotely by reloading Wiseman's files.
 
Let that sink in for a second. We sent four people to the moon and one of the first things that needed attention once they got up there was a broken email client. Not a communications relay issue, not a hardware fault. Outlook. Specifically, two Outlooks, and neither working.
 
The astronauts use Microsoft Surface Pros running commercial off-the-shelf software, including Microsoft 365, for day-to-day tasks like scheduling, documentation review, and personal communications. This is a deliberate procurement decision by NASA, and it is the kind of decision that has a real cost. When you build your workflows on proprietary software, you inherit every quirk, every silent update, every licensing edge case, and every inexplicable duplicate process that comes with it. And unlike the rest of us, these astronauts cannot just reboot and call their IT department in the morning. They are the IT department, and Houston is on a several-second comms delay.
 
This is exactly the kind of scenario where the reliability, transparency, and auditability of open-source software is not just a philosophical preference but a practical argument. A Linux-based system with open, auditable tooling would give mission engineers full visibility into exactly what is running, why it is running, and how to fix it when something goes wrong, without waiting on Microsoft to acknowledge the bug or push a patch. You cannot ship a hotfix to the moon. You need software you can actually understand and control, and proprietary closed-source applications are fundamentally at odds with that requirement. The fact that this was a non-critical system is the only reason this story is funny rather than alarming.
 
---
 
## ONLYOFFICE vs. Nextcloud: The Licensing Fight
 
Quick clarification before diving in: this involves ONLYOFFICE, not OpenOffice. They are different products. OpenOffice is largely dormant under Apache. ONLYOFFICE is the actively developed editor at the center of this week's dispute.
 
On March 27th in Berlin, Nextcloud, IONOS, and a coalition of European companies announced Euro-Office, a fork of ONLYOFFICE's document editor positioned as a sovereign, open-source, European-controlled alternative to Microsoft Office. A technical preview is on GitHub now, with a stable release targeted for summer 2026.
 
ONLYOFFICE responded by suspending its eight-year partnership with Nextcloud, citing violations of its AGPL v3 licensing terms. The company argues that Euro-Office strips out required branding, logos, and attribution elements that its additional license terms mandate. Nextcloud counters that forking is a fundamental right under the AGPL and that their fork is compliant. Notably, Bradley M. Kuhn, the creator of the AGPL itself, publicly backed Nextcloud's legal position, as did the Free Software Foundation.
 
There is also a geopolitical layer here that is hard to ignore. ONLYOFFICE is headquartered in Latvia but has significant evidence of Russian origins, including extensive Russian-language comments throughout the codebase. Euro-Office exists partly as a response to European customers who are uncomfortable with that, which adds a dimension to this dispute that goes well beyond a licensing technicality.
 
ONLYOFFICE says it will continue supporting the Nextcloud connector for existing users, but the partnership is finished. The legal question at the center of this, specifically whether those additional attribution requirements are actually enforceable under the AGPL, is genuinely unsettled. This one could end up litigated. We will keep following it.
 
---
 
## Manjaro: The Fork Is Still on the Table
 
Back in early March, a Manjaro team member published the "Manjaro 2.0 Manifesto" on the project's official forum, describing the project as having declined for a decade, losing trust, losing contributors, and becoming a "laughingstock" for repeating the same mistakes without ever addressing them.
 
The plan laid out in the manifesto is staged: give the business side a window to respond, move to a community strike if nothing happens, and if that also goes nowhere, begin the process of forking. The contributors involved have said they would prefer to avoid a fork, but will move forward with one if the current structure does not change. Their central demand is real influence over the technical direction of the project.
 
The core tension is structural. Manjaro GmbH & Co. KG holds the trademarks and controls the key assets, even though the community predates the company and built much of what made the distro worth using. The distro has slipped from second on DistroWatch in 2020 to eighth today, and the people who built it are saying plainly that they no longer trust the company side to turn it around.
 
No fork has launched yet. But the contributors behind the manifesto seem serious, and this situation has been building long enough that a resolution in either direction feels closer than it did a few months ago. Worth watching if you are in the Arch-based Linux space.
 
---
 
That is the recap. Wild week to come back to. More soon.
 
-- S.K. Ooma
 
---
 
## References
 
1. VentureBeat — *Claude Code's source code appears to have leaked: here's what we know* — <https://venturebeat.com/technology/claude-codes-source-code-appears-to-have-leaked-heres-what-we-know>
2. TechCrunch — *Anthropic took down thousands of GitHub repos trying to yank its leaked source code* — <https://techcrunch.com/2026/04/01/anthropic-took-down-thousands-of-github-repos-trying-to-yank-its-leaked-source-code>
3. NodeSource — *Anthropic Claude Code Source Leak: Bun Bug* — <https://nodesource.com/blog/anthropic-claude-code-source-leak-bun-bug>
4. Decrypt — *Anthropic Accidentally Leaked Claude Code's Source — The Internet Is Keeping It Forever* — <https://decrypt.co/362917/anthropic-accidentally-leaked-claude-code-source-internet-keeping-forever>
5. Futurism — *Anthropic Suddenly Cares Intensely About Intellectual Property After Realizing It Accidentally Leaked Claude's Source Code* — <https://futurism.com/artificial-intelligence/anthropic-suddenly-cares-about-intellectual-property-claude-leak>
6. Neuronad — *GitHub Pulls the Plug on Copilot PR "Ads"* — <https://neuronad.com/ai-news/github-pulls-the-plug-on-copilot-pr-ads/>
7. WinBuzzer — *GitHub Copilot Injected Ads Into 1.5 Million Pull Requests* — <https://winbuzzer.com/2026/03/31/github-copilot-injected-ads-pull-requests-xcxwbn/>
8. Windows Central — *Microsoft denies injecting ads into GitHub pull requests* — <https://www.windowscentral.com/software-apps/microsofts-ai-slop-is-infecting-github-copilot-is-now-injecting-ads-into-pull-requests>
9. Prism News — *Fyrox Game Engine Hits 1.0 After Seven Years of Rust Development* — <https://www.prismnews.com/hobbies/rust-programming/fyrox-game-engine-hits-10-after-seven-years-of-rust>
10. GameFromScratch — *After 7 Years of Development - Fyrox 1.0 is here* — <https://gamefromscratch.com/after-7-years-of-development-fyrox-1-0-is-here/>
11. Breitbart Tech — *Artemis II Astronauts Encounter Microsoft Outlook Glitch During Trip to Moon* — <https://www.breitbart.com/tech/2026/04/03/artemis-ii-astronauts-encounter-microsoft-outlook-glitch-during-trip-to-moon/>
12. GeekWire — *Ground control to Microsoft: Artemis 2 astronauts deal with Outlook hiccup in deep space* — <https://www.geekwire.com/2026/ground-control-to-microsoft-artemis-2-astronauts-deal-with-outlook-hiccup-in-deep-space/>
13. TechRadar — *'I have two Microsoft Outlooks and neither one is working': Artemis II astronauts have the most relatable complaint* — <https://www.techradar.com/computing/software/i-have-two-microsoft-outlooks-and-neither-one-is-working-artemis-ii-astronauts-have-the-most-relatable-complaint>
14. Tech2Geek — *ONLYOFFICE Ends Partnership with Nextcloud After Euro-Office Fork Controversy* — <https://www.tech2geek.net/onlyoffice-ends-partnership-with-nextcloud-after-euro-office-fork-controversy/>
15. Neowin — *ONLYOFFICE suspends Nextcloud partnership for forking its project without permission* — <https://www.neowin.net/news/onlyoffice-suspends-nextcloud-partnership-over-unapproved-euro-office-fork/>
16. The Register — *Forking frenzy ensues after Euro-Office launch sparks OnlyOffice backlash* — <https://www.theregister.com/2026/04/02/eurooffice_forks_onlyoffice/>
17. Morocco World News — *What Is Behind the Euro-Office Licensing Dispute With ONLYOFFICE, Nextcloud, and IONOS* — <https://www.moroccoworldnews.com/2026/04/285548/what-is-behind-the-euro-office-licensing-dispute-with-onlyoffice-nextcloud-and-ionos/>
18. FOSS Force — *Is Manjaro Done? Stick a Fork in It* — <https://fossforce.com/2026/03/is-manjaro-done-stick-a-fork-in-it/>
