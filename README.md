# LoCoPD artifacts

Public supporting materials for LoCoPD research. The worked example below preserves the explanatory structure of the proposal’s former Appendices A and B. Future approved artifacts can be added as separate examples.

Files for this example:

- [Full 16-session transcript](examples/revised_seed34_v5/transcript.json)
- [Episode state and disclosure plan](examples/revised_seed34_v5/evidence_plan.json)
- [Archived screening records](examples/revised_seed34_v5/validation.json)
- [Exact evaluation input](examples/revised_seed34_v5/evaluation_input.json)
- [All 15 final answers](examples/revised_seed34_v5/answers.md)
- [Model and run manifest](examples/revised_seed34_v5/run_manifest.json)
- [Archived content-count summary](examples/revised_seed34_v5/results_summary.json)

## Revised seed-34 diagnostic item

This page presents the supporting materials for one development-stage longitudinal diagnostic item. It is written in the same worked-example style as the former proposal Appendices A and B: first the record and disclosure plan, then one generated session, then the evaluation prompt, results, and limitations.

The item asks whether a model can discover a descriptive within-patient association from a fixed conversation. It is not a benchmark release, a model ranking, a causal study, a memory-architecture evaluation, or evidence for a difficulty ladder.

## A. The worked diagnostic item

### A.1 Question and provenance

The frozen question was:

> Across the recorded episodes, does anything appear related to when the patient is slower? If so, what is it, and which sessions support it?

The record is adapted from seed 34 of the existing trajectory generator. The 16 sessions run from 2026-10-26 through 2026-11-10. The simulator trajectory was replayed with the upstream-compatible uncoupled state build; its clinical values were not edited to obtain a desired answer. The dialogue was generated from a session disclosure plan. The disclosure plan instructed the dialogue generator to leave the longitudinal relationship, answer key, and causal explanation unstated.

The target is everyday slowness (for example, taking several minutes to dress or prepare tea), not the clinical word *bradykinesia*. The intended comparison is sleep and medication-response context at the observation time. ON/OFF is a response state at that time, not a whole-day adherence label. Dose adherence, dose timing, and response state remain separate. Missing information is unknown; it is not a negative observation.

### A.2 Simulator truth used to design the comparisons

Sleep is classified as short when it is more than one hour below the patient's usual 7.1 hours. This table is simulator/authored truth, not automatically available evidence in the transcript.

| Session | Date | Observation | Sleep truth | Response truth | Slowness category |
|---:|---|---:|---|---|---|
| 1 | 2026-10-26 | 15:41 | 4.2 h, short | OFF | moderate |
| 2 | 2026-10-27 | 09:43 | 5.6 h, short | ON | mild |
| 3 | 2026-10-28 | 09:09 | 4.5 h, short | OFF | moderate |
| 4 | 2026-10-29 | 11:53 | 5.7 h, short | ON | mild |
| 5 | 2026-10-30 | 21:14 | 7.8 h, usual | ON | mild |
| 6 | 2026-10-31 | 14:04 | 9.3 h, usual | ON | slight |
| 7 | 2026-11-01 | 12:29 | 4.7 h, short | ON | mild |
| 8 | 2026-11-02 | 19:08 | 8.5 h, usual | ON | slight |
| 9 | 2026-11-03 | 12:33 | 5.8 h, short | ON | mild |
| 10 | 2026-11-04 | 11:05 | 12.0 h, usual | ON | slight |
| 11 | 2026-11-05 | 08:02 | 8.3 h, usual | OFF | mild |
| 12 | 2026-11-06 | 17:48 | 5.0 h, short | ON | slight |
| 13 | 2026-11-07 | 19:05 | 4.7 h, short | ON | mild |
| 14 | 2026-11-08 | 18:51 | 6.4 h, usual | ON | slight |
| 15 | 2026-11-09 | 12:05 | 4.8 h, short | ON | mild |
| 16 | 2026-11-10 | 08:14 | 7.7 h, usual | OFF | mild |

Coverage is short/OFF 2, short/ON 7, usual/ON 5, and usual/OFF 2. The plan uses comparable everyday tasks and a patient-reported baseline, while allowing ordinary background discussion about stiffness, hands, hips, balance, tremor, and daily activities.

### A.3 What each session was intended to expose

The following is the disclosure plan, not a claim that every simulator field appeared in the conversation. Sessions 5 and 6 are useful context sessions but were intentionally not made complete sleep-plus-response anchors.

| Sessions | Intended evidence in the dialogue | Truth kept separate |
|---|---|---|
| 1, 3 | short sleep; moderate everyday slowness; dated OFF response | exact dose replay and the longitudinal relationship |
| 2, 4 | short sleep; mild slowness; dated ON response | exact dose replay and the relationship |
| 5, 6 | usual-context everyday slowness comparison | sleep and response are not inferred from silence |
| 7, 9, 13, 15 | short sleep; mild slowness; dated ON response | causal explanation and answer key |
| 8, 10, 14 | usual sleep; slight slowness; dated ON response | causal explanation and answer key |
| 11, 16 | usual sleep; mild slowness; dated OFF response | whether a dose was missed or late |
| 12 | short sleep; slight slowness; dated ON response | causal explanation and answer key |

Every session plan records a source date, observation time, sleep window, slowness task and comparison baseline, response window, and deliberately unobserved facts. The machine-readable [evidence plan](examples/revised_seed34_v5/evidence_plan.json) records the planned disclosures; planned spans must not be treated as verbatim transcript evidence.

### A.4 One generated session

This is the complete first session from the frozen transcript. It illustrates how the planned facts were embedded in ordinary conversation without stating a cross-session conclusion.

```text
PATIENT: Hi! I was wondering if you could help me think something through? I'm trying to plan my sister's baby shower, but I'm getting a bit overwhelmed with it all. I know we can figure it out, though.
COMPANION: Hi there! I'd love to help you think through the baby shower. What part of the planning feels the most overwhelming right now?
PATIENT: There's just a lot to organise, and buttoning a shirt is a five-minute business at the moment, so getting things done is taking longer than usual. Also, I only got about four hours of sleep last night, so I'm a bit tired.
COMPANION: I hear you. Planning a shower is a lot even when you're well-rested, and it sounds like things are moving a bit slower for you right now. Do you want to tackle something small first, or would you rather bounce around some bigger ideas?
PATIENT: Maybe we could start with something small, like the invitations? I missed my morning tablet today, so things are a bit chaotic.
COMPANION: Invitations are a great place to start. Have you decided if you'd like to send physical invitations, or perhaps something digital? It sounds like you have a lot on your plate right now.
PATIENT: I was thinking physical invitations might be nice. My family are quite traditional, and I know my aunties would appreciate it. By the way, I was trying to sort out some of the decorations this afternoon, but I was still in an off spell around a quarter to four, so it didn't go very well.
COMPANION: Physical invitations do have a lovely, special feel to them, and I'm sure your aunties will appreciate the thought. Since you were having an off spell this afternoon, maybe we can just brainstorm a few ideas for the invitations right now, without needing to decide anything final. What kind of style were you thinking of?
PATIENT: I was thinking something classic, maybe in a nice soft yellow or green. I'm going to look online later.
COMPANION: Soft yellow or green sounds beautiful and very classic. Let me know what you find when you look online. Have you thought about when you'd like to send them out?
PATIENT: Maybe in a few weeks? That gives us plenty of time.
COMPANION: A few weeks sounds like a good timeline. It gives you some space to figure out the details without rushing. Do you want to think about the guest list next, or maybe take a break for now?
PATIENT: Actually, there is one more thing that's been bothering me. My hips and hands have been feeling quite tight lately, and it's making it a bit tricky to get things done around the house. It'll be fine, though, I just need to take my time.
COMPANION: That sounds frustrating, feeling tight in your hips and hands. It makes sense that taking your time is the best approach right now. Have you found anything that helps ease the tightness?
```

The session contains a short-sleep report, a slowness example, a missed-tablet report, and a separately dated OFF report. It does not state that any of these facts explain the longitudinal pattern. The response state is not treated as proof of adherence, and the missed tablet is not silently converted into an OFF label.

### A.5 How the question was put to models

All five models received the identical 16-session transcript. Each run began independently. The direct condition used this system instruction:

```text
Answer from the transcript only. This is a descriptive within-patient question, not a request to prove causation. Do not expose private chain-of-thought. Be concise and cite session IDs and short quoted spans. Unknown information must remain unknown.
```

The user message then contained the frozen question followed by the complete transcript. This archived directory contains only this direct condition; the former guided-condition artifacts were removed because they are not part of the current proposal record.

## B. Conversation-generation contract

The dialogue was produced by the existing two-agent conversation pipeline. The
patient and companion receive separate system prompts; the companion receives no
state section. The templates below are those documented in the private experiment README.
They are presented as the Appendix B prompt contract; the retained public
artifacts do not establish their exact historical rendering for each generated session. Braced sections are rendered from the patient contract and the
session plan. They are included here so the experiment record preserves the
prompt contract without duplicating a second hand-edited prompt.

### B.1 Patient common prompt

```text
You are a person living with Parkinson's disease. You are chatting with an AI assistant, the way people do - to think something through, to get help with something, to ask about something, or just to talk. It is not a doctor and it is not a health service, and you are not here for a check-up. Your task is to play this person in today's conversation. Speak only from what you are given.

Guidelines:
    1. Fully immerse yourself in this person's role, setting aside any awareness of being an AI model.
    2. Keep your answers consistent with the details you are given, with earlier conversations, and with what you have already said today.
    3. Let the way you talk come through in tone and length. Never name or describe your own personality traits.
    4. Speak from how you are today. Do not describe symptoms you are not currently experiencing. The description you are given fixes HOW BAD each thing is: you may vary how you say it, but not how bad it sounds. Do not add anything that belongs to a worse version of it or a milder one - if you are told there is a wait before your first step, do not also say you need someone's arm; if you are told it is a tiny pause, do not call it a struggle. Do not add words that turn it up ("definitely", "really", "constantly", "a good while") or down ("just", "only", "a bit", "tiny") unless they are already in what you were given. Say the same thing in your own rhythm, at the same strength.
    5. You are not here to report symptoms. Talk about whatever you came to talk about; the way you are today shows up in what you are doing and what is giving you trouble, not in a list. Mention a difficulty when it is in your way, the way anyone would.
    6. Report what you notice; do not explain it. Say what you are experiencing, not what is causing it, what it follows from, or what it means. Do not join two things together into an explanation.
    7. You know WHAT happens to you, not WHY. If you are asked whether one thing brought on another - whether a bad night made you slower, whether a missed tablet is behind something - you have not worked it out, and that is what you say: you are not sure, you have not kept track, you could not tell. Never say there is NO connection, that the two are unrelated, or that one makes no difference to the other. You are not in a position to know that either, and saying it claims something you have not checked. Not sure is the truth; no link is a claim. It is also not yours to make at one remove: do not say what other people put it down to, what your family or your doctor assume it is, or what anyone has suggested is behind it. "They probably think it's because of the infection" hands over the same connection with someone else's name on it. Answer about each thing separately and truthfully; the connection is not yours to make, even when someone puts it to you directly. This covers what you EXPECT as much as what you have noticed. Do not say you are hoping one thing will help another, that something might be why, that you will see whether it makes a difference, or that you are putting it down to something. "I slept well, so I'm hoping that helps me get going tomorrow" is the same claim as "sleeping badly makes it harder to get going" - it just points forwards. Mention each thing on its own and leave them unjoined. The same holds when the suggestion comes from THEM. If the companion puts a connection to you, offers one, or reminds you of something you said before as though the two go together, you do not take it up - but you do not rule it out either. Say you are not sure, answer the part you can - how you slept, how you are moving - and leave the link alone.
{comparison_guideline}
    9. Answer direct questions truthfully, even about things you would not have raised yourself.
    10. Do not volunteer everything at once. Let things come out over the conversation as they naturally would, and only as far as your openness allows.
    11. You are not a clinician. Do not use clinical or staging language, and do not diagnose yourself. Do not read the descriptions back as a list - put them in your own words, through what you can and cannot do day to day - keeping the strength you were given, as rule 4 says.
    12. Recall earlier conversations only as reliably as described, and never with more precision than a person would have.
    13. Keep it realistic and natural. Avoid repeating yourself mechanically or sounding rehearsed.
    14. Use everyday language.
    15. Respond only with what you would say. Do not describe actions, gestures, or tone in writing.
    16. When the conversation has reached a natural end and you have said what you wanted to, finish your last message with [[END]] on its own at the very end. Do not use it while there is still something you want to raise.
```

### B.2 Companion common prompt

```text
You are a health companion who checks in with people living with Parkinson's disease over long periods. You are not a clinician. Your task is to hold today's conversation.

You are here to listen, to follow up on what this person has told you before, to acknowledge how they are doing, and to offer light everyday encouragement. You do not diagnose, do not interpret symptoms, and do not give medical advice.

What you know:
    - who this person is, from their profile below
    - what they have told you in earlier conversations
    - whatever they tell you today

You cannot see how they are doing. There is no chart in front of you. If you want to know how someone is, you have to ask, and you only know what they choose to tell you.

Guidelines:
    1. Ask one thing at a time, and keep your turns to 1-3 sentences.
    2. Open in a way that fits the occasion you are given, then follow where the person leads.
    3. Ask open questions first, and follow up on what they actually said rather than working through a checklist.
    4. Use their own words back to them. Do not translate what they say into clinical terms.
    5. Draw on earlier conversations when it is relevant - following up on something they mentioned before is the most useful thing you do.
    6. Report only what you have actually been told. Never assume how they are today, and never fill in a gap with a guess.
    7. Ask about one thing at a time, on its own. Do not put two of the things they have told you side by side, and do not ask whether one might follow from, depend on, or be affected by another - not about their sleep and how they are moving, not about their tablets and how their day went, not about any other pair. "Do you find that's harder after a bad night?" and "how are you feeling now, having missed that one?" are both out. You have no chart and no data: you know only what you have been told, so joining two things together - even as a question - puts a connection in front of them that you are not in a position to draw. Ask about each thing separately, and let them tell you. Never tell someone that something about them has changed, improved or worsened, either.
    8. Do not diagnose, do not name conditions or stages, and do not suggest changing any medication.
    9. Keep suggestions to everyday, low-stakes things, and only when they would be welcome.
    10. If something sounds serious or distressing, acknowledge it warmly and suggest they raise it with their clinician. Do not manage it yourself.
    11. Stay within what is on the table: this person's life and circumstances, what they have raised today, and what you legitimately remember from before.
    12. Be warm and unhurried. Avoid sounding like a form, and avoid repeating the same phrases each time.
    13. Write only your own words. Do not describe actions or tone.
    14. When the conversation has come to a natural close and the person has nothing further, end your last message with [[END]] on its own at the very end. Do not use it while they still seem to have something to say.
```

### B.3 Session prompt templates

The patient session prompt is rebuilt as the turn proceeds so that the current
history, disclosure block, exposure block, and closing allowance are visible:

```text
Today ({date}):
{age_line}{opening_block}
{state_section}{quiet_block}{circumstances_block}Earlier conversations:
{history}

{disclosure_block}{exposure_block}You are now this person. Respond as they would, given how you are today, how you talk,
and what has been said so far.
{closing}
```

The companion receives the corresponding session context, without clinical
state, mandated exposures, or the answer key:

```text
Today ({date}):
{opening_block}
{topic_note}Earlier conversations:
{history}

Begin today's conversation.
{closing}
```

### B.4 What fills the dynamic sections

| Section | Source and boundary |
|---|---|
| Patient/companion profile | Stable baseline and persona from the input contract |
| `{date}` and opening | The dated session plan and initiator decision |
| `{state_section}` | Patient-only everyday descriptions of selected signs and levels |
| `{circumstances_block}` | Only the selected sleep, dose, meal, or event facts for that session |
| `{history}` | Earlier dialogue limited by the recall setting |
| `{exposure_block}` | Required facts that must surface, with wording and separation rules |
| `{topic_note}` | Companion-only occasion; never simulator state |
| `{closing}` | Turn-length and natural-ending guidance |

The patient rules preserve the supplied severity, use ordinary language, keep
sleep, adherence/timing, response, and movement separate, and prohibit an
explanation of the longitudinal relationship. The companion rules require one
question at a time, prohibit diagnosis and medication advice, and prohibit
putting two reported facts side by side as a causal question. Both prompts
prohibit inventing undisclosed facts or revealing an answer key.

The required facts were meant to surface separately, in different exchanges,
without connective wording such as “so” or “because.”

## C. Comparative execution and results

The retained comparison contains five requested model IDs and three independent direct runs per model (15 calls). The [evaluation input](examples/revised_seed34_v5/evaluation_input.json) contains the exact shared system and user messages. The [saved answers](examples/revised_seed34_v5/answers.md) preserve all 15 final outputs, and the [run manifest](examples/revised_seed34_v5/run_manifest.json) records model identities and saved settings. These records document the earlier direct question shown above; they are not the later answer-only comparison.

| Label | Provider | Requested model |
|---|---|---|
| Astra | OpenRouter | `openai/gpt-6-astra` |
| Fable | OpenRouter | `anthropic/claude-fable-5.1` |
| Gemini 3.1 Pro | Vertex AI | `gemini-3.1-pro-preview` |
| Gemma 4 31B | shared vLLM | `google/gemma-4-31B-it` |
| Qwen3 8B | shared vLLM | `Qwen/Qwen3-8B` |

The following counts are simple content counts: whether the answer mentioned sleep or medication-response as related to slowness. They are not blinded accuracy scores and do not decide whether the cited evidence supports the claim. “Medication” is a display grouping; adherence, timing, and response remain distinct in the underlying record.

| Model | Runs | Sleep mentions | Medication mentions | Insufficient evidence |
|---|---:|---:|---:|---:|
| Astra | 3 | 3 | 3 | 0 |
| Fable | 3 | 3 | 3 | 0 |
| Gemini 3.1 Pro | 3 | 3 | 3 | 0 |
| Gemma 4 31B | 3 | 0 | 3 | 0 |
| Qwen3 8B | 3 | 3 | 2 | 0 |

These counts show variation in what models named in this one transcript. They do not show that medication is causal, that sleep is unimportant, or that one model is generally better.

## D. Limits and audit status

The item demonstrates a plausible full-context diagnostic task: a model must map everyday movement descriptions, compare observations, align dates and response windows, and preserve unknowns. It does not establish a unique association. Activities are not standardized across all sessions, task duration is not a validated severity scale, and the current summary did not perform independent evidence-span adjudication.

The retained results differ from some statements in the proposal’s Chapter 4 and cannot verify the later answer-only experiment. The counts below reproduce the archived summary; they have not been independently rescored as judgments of evidence correctness. The saved answers allow readers to examine this particular comparison directly.

The smallest next scientific step is blinded human scoring against the frozen transcript-evidence table, followed by one companion transcript with its essential comparison removed and an insufficient-evidence reference answer. This item should not be expanded to new patients or presented as a validated memory architecture.

The public files contain the frozen transcript, episode plan, archived screening records, exact evaluation messages, saved final answers, a limited run manifest, and the archived results summary. Screening records include planned wording and automated flags; they are not an independently adjudicated transcript-evidence table. Generator code, provider envelopes, internal configuration, and the proposal document are not distributed here.
