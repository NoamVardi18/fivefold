# Research log

Compiled 2026-09-27 in a cloud session. **Important limitation:** that environment blocked youtube.com, chatgpt.com, tiktok.com, reddit.com, x.com, medium.com, substack.com and several other sites. Most findings below come from **search-engine extracts**, not full reads of the page. An automated "deep research" run fetched 0 of 25 sources, so its verification step never ran.
Legend: ✅ confirmed from an official page or a direct search extract of it · ⚠️ UNVERIFIED (third-party or vendor blog, or extract only) · ❌ refuted.
**The local session must open each source and update these marks.**

## 1. Reference videos and chat sent by the client
| Item | What we know | Status |
|---|---|---|
| https://youtu.be/NnvRMs_0UQ8 | "How to Build a Kids Animation Channel with AI (Full Workflow)", 2026-06-28. The description promotes "Seedance 2.0 on Higgsfield AI", so it is likely sponsored or affiliate. Channel and transcript unknown. | ⚠️ |
| https://youtu.be/4LryAnzFLMw | "How to Create AI Animated Stories That Make Money on YouTube in 2026 (Beginner Tutorial)" | ⚠️ |
| https://chatgpt.com/share/6ab8c610-32d4-83eb-96cf-e86cfc908514 | Not opened (blocked). | — |
| Closest written equivalent | Higgsfield's official prompt library for an animated short: make a hero keyframe and multi-angle prop sheets first, then reference them in each scene prompt. https://higgsfield.ai/blog/guide-animation-seedance2.0 · Academy course: https://higgsfield.ai/academy/courses/ai-animated-short | ⚠️ vendor |

## 2. Image models and character consistency
- Nano Banana Pro accepts up to 14 reference images and is suited to character sheets. https://selfielabstudio.com/blog/nano-banana-pro-consistent-character-sheets-guide-20260216 ⚠️
- Higgsfield's own recommendation: Soul ID for recurring *photoreal* faces, Nano Banana Pro for layout and controlled identities, then Seedance/Kling for motion. https://higgsfield.ai/blog/soul-2-vs-nano-banana-pro ⚠️ vendor
- Soul ID needs 20+ photos and advises against sunglasses. Not a fit for a stylized cartoon. https://higgsfield.ai/creator-hub/help-center/ai-models/how-do-i-create-and-use-a-soul-id-character ✅
- Consistency benchmarks written by vendors that rank their own tool first: https://toonystory.com/blog/best-ai-for-character-consistency-2026 , https://www.neolemon.com/blog/best-ai-character-generator-consistency-benchmark/ ⚠️
- Identity drift test, Soul ID vs Nano Banana: https://gregpreece.com/articles/higgsfield-ai-vs-nano-banana-i-tested-which-beats-identity-drift ⚠️
- Kids example: Nano Banana consistent characters across 6 scenes, then Kling 2.6, about 90 minutes. https://www.aitoolsforkids.com/blog/nano-banana-review-ai-learning-games-kids ⚠️

## 3. Video models
- Seedance 2.0 multi-reference: up to 9 images, 3 videos and 3 audio files per generation. https://www.atlabs.ai/blog/how-to-build-a-consistent-cast-of-ai-characters-in-seedance-2.0-for-a-video-series ⚠️ vendor
- Kling 3.0 / Omni rated strongest for multi-shot animated characters. Seedance 2.x is best when the character is driven by reference images and at keeping a stylized look across separate generations. https://www.elser.ai/blog/best-ai-video-model-character-consistency-2026 ⚠️ vendor
- Seedance 2.0 is said to rank #1 on the Artificial Analysis T2V/I2V leaderboards (June 2026). Kling 3.0 "AI Director" handles up to 6 shots per clip. Veo 3.1 is best for close-ups. https://aijourn.com/seedance-2-0-vs-kling-3-0-vs-veo-3-1-ai-video-benchmark-test-for-2026/ ⚠️
- Head-to-head of Seedance 2.5 vs 2.0 vs Kling 3.0 vs Veo 3.1: https://seedance2-video.com/blog/seedance-2-5-tested-2026 ⚠️ fan/affiliate
- Higgsfield's comparison of 5 models: https://higgsfield.ai/blog/5-Best-AI-Video-Models-2026-Tested-Compared ⚠️ vendor

## 4. Pricing, Unlimited, terms, training
- Higgsfield plans: Starter $19 (270 credits); Plus $47/mo annual or about $59 monthly (1,200 credits, 6 parallel generations); Ultra $99/mo annual (3,000 credits). A 5-second Seedance 2.0 1080p clip costs about 45 credits. Checked 2026-09-11 by a third party. https://www.blotato.com/blog/higgsfield-pricing ⚠️ · Official: https://higgsfield.ai/pricing (check live)
- Unlimited: the Plus/Ultra annual plans include a 365-day unlimited set of models. The newest flagship models are unlimited only in about 7-day promo windows. "All Unlimited" bundle costs $99 for 1 day or $250 for 3 days. Clips capped at 15 seconds, 1 concurrent generation. Web UI only: not available via API/MCP/CLI, and no automation. https://higgsfield.ai/blog/higgsfield-all-unlimited-explained ✅ vendor (official)
- Higgsfield terms, effective 2026-08-27: users own inputs and outputs, commercial use is allowed, content may be used to improve models, and deleted content is excluded from training afterwards. https://higgsfield.ai/blog/terms-of-use-privacy-policy-update ✅ official · Background on the backlash: https://www.mindstudio.ai/blog/higgsfield-terms-of-service-backlash ⚠️
- fal.ai prices (Sept 2026): Seedance 2.0 about $0.24/s; Kling 3.0 about $0.224/s with audio off or $0.336/s with audio on; Veo 3.1 about $0.40/s. fal charges about 2× BytePlus's direct price for Seedance. https://www.teamday.ai/blog/ai-api-pricing-comparison-2026 ⚠️
- fal does not train on customer data. Generated media stays on the CDN for at least 7 days by default. Zero data retention is available on enterprise plans. https://fal.ai/legal/data-processing-addendum ✅ official (via extract)

## 5. Voice and music
- ElevenLabs Eleven v3 supports 70+ languages including Hebrew, with audio tags such as [whispers] and [laughs]. It is not real-time. https://elevenlabs.io/docs/overview/models ✅ official
- ElevenLabs: every paid plan includes a commercial license (the free plan does not). You keep rights to audio generated while subscribed. https://help.elevenlabs.io/hc/en-us/articles/13313564601361 ✅ official
- Fish Audio is strongest in East Asian languages. There is no Hebrew evidence, and reviews favor ElevenLabs for Hebrew. https://speechgeneration.ai/compare/fish-audio-vs-elevenlabs ⚠️
- Suno: commercial rights only for output made on Pro/Premier. Songs from the free plan stay non-commercial even after upgrading. https://suno.com/terms-of-service ✅ official · After the WMG deal, Suno models may change in 2026, and raw AI audio can trigger Content ID risk. https://dynamoi.com/learn/ai-music-distribution/suno-commercial-rights-explained ⚠️
- Eleven Music has a separate "Social Media" license tier. https://elevenlabs.io/music-terms ✅ official

## 6. Platform policy
- **TikTok:** AI-generated content showing the likeness of anyone under 18 is not allowed, even when labeled. AIGC label required. https://support.tiktok.com/en/using-tiktok/creating-videos/ai-generated-content ✅ (extract) · Unclear whether a stylized cartoon derived from photos counts as "likeness" ⚠️
- **YouTube disclosure:** required for realistic synthetic content, not for clearly animated or unrealistic content. https://blog.youtube/news-and-events/disclosing-ai-generated-content/ ✅
- **YouTube Made for Kids (COPPA):** https://support.google.com/youtube/answer/9528076 ✅ · Estimated revenue loss of up to 80% (TechTimes) ⚠️
- **YouTube inauthentic content:** since July 2025, clarified July 2026. Generic, template-based and "interchangeable when watched in a row" content is non-monetizable, and it applies channel-wide. https://support.google.com/youtube/answer/1311392 ✅ · https://www.tubefilter.com/2026/07/13/youtube-inauthentic-content-monetization-policy-update/ ⚠️ · https://techcrunch.com/2026/07/20/youtube-clarifies-policies-around-ai-slop-and-upsetting-videos/ ⚠️
- **Jan 2026:** 16 AI channels terminated (about 35M subscribers). https://outlierkit.com/resources/youtube-ai-slop-crackdown-2026/ ⚠️
- **YouTube Kids** limits AI content to a small set of high-quality channels. Over 200 experts urged restrictions. https://www.spokesman.com/stories/2026/apr/01/google-faces-calls-to-prohibit-ai-videos-for-kids-/ ⚠️

## 7. Case studies of creators who succeeded
- **Instagram series based on the creator's real dog:** 4,411,496 views in 90 days, 97.2% from non-followers. 15-second episodes, 4–5 frames each, character sheets, about 30 minutes per episode. Stories drawn from real dog behavior. Every post labeled AI, with no reach penalty. https://aijourn.com/one-person-one-studio-what-4-4-million-views-reveal-about-ai-native-animation/ ⚠️ (reads like a PR piece; creator not named)
- **Dr. Carla Engelbrecht** (ex-Sesame Street/PBS Kids/Netflix): character sheets first; references used as "ingredients"; frames from finished clips reused as references; stories need cause, consequence and meaning; slow, simple songs. https://carlaeng.substack.com/p/make-ai-videos-kids-guide · https://carlaeng.substack.com/p/how-to-create-kids-videos-not-slop ⚠️ (also sells a course)
- **FUNTASTIC YT** (Philippines): about 600K subscribers, $9K/month, Kling + ChatGPT, 1–2 uploads a day. A cautionary example of the pattern YouTube is now demonetizing. https://www.npr.org/2025/08/28/nx-s1-5493485/ai-slop-videos-youtube-tiktok ✅ (NPR interview)
- **Atlabs guides** (vendor; growth tables are marketing): https://www.atlabs.ai/blog/how-to-start-a-kids-educational-youtube-channel-using-ai-and-claude-in-2026-(in-10-minutes) ⚠️
- **Character DNA from 10–20 photos** (LongStories): https://longstories.ai/blog/design-ai-characters-series ⚠️
- **Hype to ignore:** "$7M/month Cocomelon" posts, course-selling "35M views" videos.

## 8. Editing tools
- Remotion official agent skills: https://www.remotion.dev/docs/ai/skills ✅ · Coding agents: https://www.remotion.dev/docs/ai/coding-agents ✅ · License: free for individuals and companies up to 3 employees (check https://www.remotion.dev/license) ⚠️
- HyperFrames (HeyGen) is open source. HTML with timing attributes is rendered in headless Chrome and encoded with FFmpeg. Good for motion graphics and titles. https://github.com/heygen-com/hyperframes ✅
