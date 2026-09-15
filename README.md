# scenario_registry
```json
{
 "doc": "Canonical per-scenarioID registry: the conversational PHENOMENON each scenarioID denotes (stylistics, rhythm, floor mechanics) — NOT the topic. Language-independent; referenced by every events/all_<lang>_scenarios.json via scenarioID. scenario_desc is 1:1 with scenarioID and topic-free; the per-conversation topic lives in each scenario row's conv_desc. scenario_name and family/family_name are also properties of the scenarioID. pause_affinity ('high'|'some'|'none') is how much this scenario should carry FLOOR-HELD intra-turn pauses / hesitations (a turn delivered incrementally as a `turn` + same-speaker `continue`, and/or filled 'um'/'uh' hesitations) — 'high' actively encourages it (planning/uncertain/floor-holding speech), 'none' suppresses it (crisp scenarios whose rhythm depends on continuity), 'some' is the natural-where-it-fits default; generate_scenarios.build_user_prompt turns it into one PACING guidance line. It raises the corpus-wide share of Incomplete (floor-held) turns toward the Easy-Turn reference; verify with analyze_corpus.py turn-states. merge_conv() fills these onto each conversation at render time.",
 "scenarios": {
  "TT-01": {
   "scenario_name": "Clean alternation",
   "family": "TT",
   "family_name": "Turn-taking",
   "scenario_desc": "Baseline back-and-forth; each speaker waits for the other to finish before replying.",
   "pause_affinity": "some"
  },
  "TT-02": {
   "scenario_name": "Quick succession",
   "family": "TT",
   "family_name": "Turn-taking",
   "scenario_desc": "Engaged, high-tempo exchange with minimal silence between turns.",
   "pause_affinity": "none"
  },
  "TT-03": {
   "scenario_name": "Delayed response",
   "family": "TT",
   "family_name": "Turn-taking",
   "scenario_desc": "A noticeable pause before the responder starts (thinking / processing).",
   "pause_affinity": "some"
  },
  "TT-04": {
   "scenario_name": "Latching",
   "family": "TT",
   "family_name": "Turn-taking",
   "scenario_desc": "The next turn begins immediately at the prior turn's end, no perceptible gap.",
   "pause_affinity": "none"
  },
  "TT-05": {
   "scenario_name": "Floor-holding continuer",
   "family": "TT",
   "family_name": "Turn-taking",
   "scenario_desc": "Speaker signals continuation across an internal pause so it is not read as yielding the floor.",
   "pause_affinity": "high"
  },
  "OV-01": {
   "scenario_name": "Barge-in to redirect",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "User barges in mid-answer to switch to a different task, truncating the system; the new task is then handled, with a companion aside and a follow-up.",
   "pause_affinity": "some"
  },
  "OV-02": {
   "scenario_name": "Barge-in to correct",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "The system commits to a wrong value; the user barges in to correct it (system truncated, then resumes corrected), and the exchange continues with a follow-up and a companion confirmation.",
   "pause_affinity": "some"
  },
  "OV-03": {
   "scenario_name": "Cooperative overlap",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "User overlaps the system's walkthrough with agreement tokens that do NOT take the floor (no truncation), then continues normally, including a companion aside.",
   "pause_affinity": "some"
  },
  "OV-04": {
   "scenario_name": "Failed interruption",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "User starts to cut in but the system holds the floor (failed barge_in, interrupts=false, no truncation); the attempt overlaps and trails off, then the conversation continues, with a companion aside.",
   "pause_affinity": "some"
  },
  "OV-05": {
   "scenario_name": "Simultaneous start",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "System and user begin speaking at the same instant (matched gaps on opposite channels); both trail, the user yields, then the exchange continues, with a companion check-in.",
   "pause_affinity": "some"
  },
  "OV-06": {
   "scenario_name": "Repeated interruptions",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "An impatient user cuts in repeatedly, truncating the system each time until it gives the bare answer, then the exchange continues, with a companion helping decide.",
   "pause_affinity": "none"
  },
  "OV-07": {
   "scenario_name": "Interrupted by companion",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "User's exchange with system interrupted by companion; the exchange continues.",
   "pause_affinity": "some"
  },
  "OV-08": {
   "scenario_name": "Barge-in for aside task",
   "family": "OV",
   "family_name": "Overlap & interruption",
   "scenario_desc": "User interrupts the system for an aside task; system acknowledges and responds; the original exchange continues.",
   "pause_affinity": "some"
  },
  "BC-01": {
   "scenario_name": "Human backchannel over answer",
   "family": "BC",
   "family_name": "Backchannels",
   "scenario_desc": "Listener gives brief acknowledgments while the other holds a long turn.",
   "pause_affinity": "high"
  },
  "BC-02": {
   "scenario_name": "System backchannel over request",
   "family": "BC",
   "family_name": "Backchannels",
   "scenario_desc": "System emits short acknowledgments while the human is still specifying.",
   "pause_affinity": "high"
  },
  "BC-03": {
   "scenario_name": "Assessment backchannel",
   "family": "BC",
   "family_name": "Backchannels",
   "scenario_desc": "A reactive judgment ('oh nice') rather than a neutral acknowledgment.",
   "pause_affinity": "some"
  },
  "BC-04": {
   "scenario_name": "Laughter reaction",
   "family": "BC",
   "family_name": "Backchannels",
   "scenario_desc": "Listener laughs in reaction without taking the floor.",
   "pause_affinity": "some"
  },
  "BC-05": {
   "scenario_name": "Companion backchannel over answer",
   "family": "BC",
   "family_name": "Backchannels",
   "scenario_desc": "A companion (a third person on the human side, not the user) gives brief acknowledgments while the system holds a long turn; the acknowledgments do NOT take the floor and never truncate the system and can be in acknowledgement to the user or the system.",
   "pause_affinity": "high"
  },
  "DF-01": {
   "scenario_name": "Filled pause",
   "family": "DF",
   "family_name": "Disfluency",
   "scenario_desc": "Voiced hesitation while the speaker assembles the rest of the utterance.",
   "pause_affinity": "high"
  },
  "DF-02": {
   "scenario_name": "Silent word-search",
   "family": "DF",
   "family_name": "Disfluency",
   "scenario_desc": "A silent intra-turn gap while hunting for the next word.",
   "pause_affinity": "high"
  },
  "DF-03": {
   "scenario_name": "False start",
   "family": "DF",
   "family_name": "Disfluency",
   "scenario_desc": "Speaker begins, abandons it, and restarts the phrasing.",
   "pause_affinity": "high"
  },
  "DF-04": {
   "scenario_name": "Self-correction",
   "family": "DF",
   "family_name": "Disfluency",
   "scenario_desc": "Speaker states a value, then immediately corrects it.",
   "pause_affinity": "high"
  },
  "DF-05": {
   "scenario_name": "Repetition / stutter",
   "family": "DF",
   "family_name": "Disfluency",
   "scenario_desc": "A repeated word or sound within the turn.",
   "pause_affinity": "high"
  },
  "AD-01": {
   "scenario_name": "Side conversation",
   "family": "AD",
   "family_name": "Addressee / multi-party",
   "scenario_desc": "Speaker turns to a third person; the system must stay silent.",
   "pause_affinity": "some"
  },
  "AD-02": {
   "scenario_name": "Mid-turn addressee switch",
   "family": "AD",
   "family_name": "Addressee / multi-party",
   "scenario_desc": "Within one turn the speaker alternates between the system and a bystander.",
   "pause_affinity": "high"
  },
  "AD-03": {
   "scenario_name": "Overheard background speech",
   "family": "AD",
   "family_name": "Addressee / multi-party",
   "scenario_desc": "Speech in the room not directed at the system; the system ignores it.",
   "pause_affinity": "some"
  },
  "AD-04": {
   "scenario_name": "Third party answers",
   "family": "AD",
   "family_name": "Addressee / multi-party",
   "scenario_desc": "A third person answers the human's question mid-exchange (cooperative barge_in).",
   "pause_affinity": "some"
  },
  "TS-01": {
   "scenario_name": "Single clear request",
   "family": "TS",
   "family_name": "Task structure",
   "scenario_desc": "A clean single-intent request and its answer.",
   "pause_affinity": "some"
  },
  "TS-02": {
   "scenario_name": "Multi-intent burst",
   "family": "TS",
   "family_name": "Task structure",
   "scenario_desc": "Multiple tasks packed into one turn, answered together.",
   "pause_affinity": "high"
  },
  "TS-03": {
   "scenario_name": "Change of mind / cancel",
   "family": "TS",
   "family_name": "Task structure",
   "scenario_desc": "Speaker cancels or replaces a task already being acted on.",
   "pause_affinity": "high"
  },
  "TS-04": {
   "scenario_name": "System clarification",
   "family": "TS",
   "family_name": "Task structure",
   "scenario_desc": "System poses a clarifying question before acting.",
   "pause_affinity": "some"
  },
  "TS-05": {
   "scenario_name": "Ambiguity resolved",
   "family": "TS",
   "family_name": "Task structure",
   "scenario_desc": "A clarification exchange that resolves an ambiguous request.",
   "pause_affinity": "high"
  },
  "TS-06": {
   "scenario_name": "Confirmation loop",
   "family": "TS",
   "family_name": "Task structure",
   "scenario_desc": "System confirms, the human assents, the system commits.",
   "pause_affinity": "some"
  },
  "AF-01": {
   "scenario_name": "Impatient / frustrated",
   "family": "AF",
   "family_name": "Affect",
   "scenario_desc": "Affect that tends to drive interruptions and short, sharp turns.",
   "pause_affinity": "none"
  },
  "AF-02": {
   "scenario_name": "Amused",
   "family": "AF",
   "family_name": "Affect",
   "scenario_desc": "Amusement coloring the turn, including laughing-while-speaking.",
   "pause_affinity": "some"
  },
  "AF-03": {
   "scenario_name": "Hesitant / uncertain",
   "family": "AF",
   "family_name": "Affect",
   "scenario_desc": "Unce
   rtain delivery, heavy on fillers and pauses.",
   "pause_affinity": "high"
  },
  "AF-04": {
   "scenario_name": "Excited / fast",
   "family": "AF",
   "family_name": "Affect",
   "scenario_desc": "Fast, eager delivery with short gaps.",
   "pause_affinity": "none"
  },
  "EC-01": {
   "scenario_name": "Trailing off",
   "family": "EC",
   "family_name": "Edge cases",
   "scenario_desc": "Speaker drifts off without finishing the sentence.",
   "pause_affinity": "high"
  },
  "EC-02": {
   "scenario_name": "Human goes silent",
   "family": "EC",
   "family_name": "Edge cases",
   "scenario_desc": "Extended silence; the system waits, then prompts.",
   "pause_affinity": "high"
  },
"EC-03": {
   "scenario_name": "Sustained crosstalk",
   "family": "EC",
   "family_name": "Edge cases",
   "scenario_desc": "An extended span where both speak simultaneously.",
   "pause_affinity": "some"
  },
  "EC-04": {
   "scenario_name": "Non-speech-only turn",
   "family": "EC",
   "family_name": "Edge cases",
   "scenario_desc": "A turn consisting only of a vocalization, no words.",
   "pause_affinity": "none"
  },
  "EC-05": {
   "scenario_name": "Long monologue + backchannels",
   "family": "EC",
   "family_name": "Edge cases",
   "scenario_desc": "One long turn punctuated by the listener's periodic backchannels.",
   "pause_affinity": "high"
  },
  "ML-01": {
   "scenario_name": "Live Translation from English to Mandarin",
   "family": "ML",
   "family_name": "Multilingual",
   "scenario_desc": "User speaks in English; the System interprets it into Mandarin concurrently, lagging ~1.4 s behind (ear-voice span) and never running ahead of its source. Sustained cross-channel overlap, no floor hand-off, no truncation.",
   "pause_affinity": "none"
  },
  "ML-02": {
   "scenario_name": "Live Translation from Mandarin to English",
   "family": "ML",
   "family_name": "Multilingual",
   "scenario_desc": "User speaks in Mandarin; the System interprets it into English concurrently, lagging ~1.4 s behind (ear-voice span) and never running ahead of its source. Sustained cross-channel overlap, no floor hand-off, no truncation.",
   "pause_affinity": "none"
  },
  "ML-03": {
   "scenario_name": "Teaching Mandarin to an English Speaker",
   "family": "ML",
   "family_name": "Multilingual",
   "scenario_desc": "System teaches Mandarin to the User (an English speaker); the System may interrupt to correct the user; the User may interrupt to ask questions.",
   "pause_affinity": "some"
  },
  "ML-04": {
   "scenario_name": "Teaching English to a Mandarin Speaker",
   "family": "ML",
   "family_name": "Multilingual",
   "scenario_desc": "System teaches English to the User (a Mandarin speaker); the System may interrupt to correct the user; the User may interrupt to ask questions.",
   "pause_affinity": "some"
  }
 }
}
```

