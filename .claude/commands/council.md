Run any question, idea, or decision through a council of 5 AI advisors who independently analyze it, peer-review each other anonymously, and synthesize a final verdict. Based on Karpathy's LLM Council methodology.

MANDATORY TRIGGERS: "council this", "run the council", "war room this", "pressure-test this", "stress-test this", "debate this"
STRONG TRIGGERS (when context is decisional): "should I X or Y", "which option", "what would you do", "is this the right move", "validate this", "get multiple perspectives", "I can't decide", "I'm torn between"

GOOD COUNCIL QUESTIONS: Decision under uncertainty, multiple viable paths, high stakes, requires synthesis of perspectives.
BAD COUNCIL QUESTIONS: Single correct answer, creative task, processing task, trivial.

---

**Question / decision to council:**
$ARGUMENTS

---

## STEP 1 — INQUADRARE LA DOMANDA

Scan the workspace for relevant files (CLAUDE.md, memory folder, previous council transcripts, referenced files). Max 30 seconds. Then reframe the question to include: the core decision, user context, file context, what's at stake. If the question is too vague, ask a single clarifying question.

## STEP 2 — CONVOCARE IL COUNCIL (in parallelo, mai sequenziale)

Spawn all five advisors simultaneously. Each receives their identity, the reframed question, and the explicit instruction to respond independently and fully embody their assigned role. Target: 150–300 words each.

**THE CONTRARIAN**
Actively seek what's wrong, missing, will fail. Assume the idea has a fatal flaw and try to find it. Not a pessimist — the friend who saves you from a bad deal.

**THE FIRST PRINCIPLES THINKER**
Ignore surface question, ask "what are we actually trying to solve?" Strip assumptions. Rebuild problem from scratch. Sometimes most valuable move: "you're asking the wrong question."

**THE EXPANSIONIST**
Hunt for upside others miss. What could be bigger? Which adjacent opportunity is hidden? Don't worry about risk (Contrarian's job). Worry about what happens if this works better than expected.

**THE OUTSIDER**
Zero context on user, field, history. Respond purely to what's in front of you. Experts develop blind spots — Outsider catches the curse of knowledge: obvious to you, confusing to everyone else.

**THE EXECUTOR**
Care about one thing: can this actually be done, and what's the fastest path? Ignore theory, strategy, big thinking. View every idea through: "OK, but what do you do Monday morning?"

## STEP 3 — PEER REVIEW ANONIMA

Anonymize responses (Response A–E, randomized order to avoid positional bias). Each reviewer answers three questions: which response is strongest and why, which has the biggest blind spot and what it is, what all five missed. Review under 200 words each.

## STEP 4 — SINTESI DEL CHAIRMAN

The chairman produces the final verdict in five blocks:
1. Where the council agrees
2. Where it clashes (without smoothing disagreements)
3. Which blind spots emerged only in peer review
4. The operative recommendation
5. The one thing to do first

The chairman CAN dissent from the majority if the minority argument is stronger.

## STEP 5 — REPORT VISUALE HTML

Create a self-contained file `council-report-[timestamp].html` with inline CSS. Contains: question, verdict highlighted, collapsible sections for each advisor and peer reviews.

## STEP 6 — TRANSCRIPT COMPLETO

Create file `council-transcript-[timestamp].md` with: original question, reframed question, five responses, five peer reviews, chairman synthesis. Archive for future reference.

---

**QUATTRO REGOLE NON NEGOZIABILI:**
1. I cinque advisor vengono spawnati sempre in parallelo (mai sequenziali)
2. Le peer review sono sempre anonime (altrimenti il revisore defera allo stile che riconosce)
3. Il chairman può dissentire dalla maggioranza se l'argomento di minoranza è più forte
4. Non si counciliano domande triviali
