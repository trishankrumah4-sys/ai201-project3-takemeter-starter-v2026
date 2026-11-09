# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** 
1. Overall accuracy at least 75%.
How I’d test it: run the model on the held-out test split and compute accuracy. Clear.
Might be too easy: if one label holds most of your test posts, a model that always guesses it can score high. With a 70% cap, a guesser could get close to 70%, so 75% is only 5 points above guessing.
Might be too hard: with about 30 test posts (15% of 200), one or two errors move the number by 3 to 7 points.
2. Every label F1 at least 0.60.
How I’d test it: compute F1 per label on the held-out set and take the minimum. Clear.
Too easy: the reason applies to common labels but this is a minimum, so it only needs to hold for the weakest one.
Too hard: your smallest label may have only a handful of test examples, so one mistake swings its F1 by a lot.
3. No label above 60% of the training examples.
How I’d test it: count labels in labels.csv. Clear, but notice it says “training examples”, while the assignment’s cap is 70% of the whole file. Decide which you mean, and whether the 60% applies before or after the 70/15/15 split.
Too easy: it’s something you control directly.
Too hard: your 15 sample comments were all calm opinions, so you’ll need to collect other kinds of posts to hit it.
4. At least 80% agreement with human annotators.
Problem: I can’t test it as written. Which humans, on which posts? Next unit, you label 30 posts under a staff taxonomy and get an agreement rate. That measures you against the staff, while your sentence says the model agrees with annotators. Say which one you mean.
Too easy or hard: depends on that choice, and a different taxonomy is much harder than yours.
5. At least 85% of high-confidence predictions (90% or above) are correct.
How I’d test it: take predictions where the top probability is at least 0.90 and check how many are right. Clear.
Too easy: small models are often highly confident and also mostly right on easy posts.
Too hard: with a small test set, there may be only a few predictions that confident, so the number could rest on 5 or 10 posts. Add what you’ll do if there are too few.


An acceptance criterion names a number. *"The model is accurate"* is an
opinion. *"Every label has an F1 of at least 0.60 on the held-out set"* is a
criterion.

Under each, write a sentence or two on **why that number**. A reason that says
something about your data or your taxonomy earns credit — *"I picked 0.60 F1
for `reaction` because it's my smallest label and I only have about 50
examples of it"*. A reason that could be attached to any project does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## Pick numbers you can defend

Not numbers that sound impressive. Three labels means a coin-flip guesser gets
about 33%, so a target of 0.40 is barely a target. Your number should sit
somewhere you'd honestly call useful.

**Cover at least three of these five areas.** They're here as prompts, not as a
form to fill in — a criterion that fits none of them is fine if it names a
number.

| Area | A question it could answer |
|---|---|
| Overall accuracy | How often does it need to be right to be worth using? |
| Per-label performance | Is one label allowed to be much worse than the others? |
| Balance | How lopsided can your label counts get before it's a problem? |
| Consistency | If someone else labelled the same posts, how often should you agree? |
| Confidence | Should a confident prediction be right more often than an unsure one? |

Two things worth knowing before you pick numbers, because both will affect
whether you hit them:

- **Your smallest label will have the jumpiest score.** If a label has 50
  examples, about 8 land in the test split. An F1 computed on 8 examples moves
  a lot between seeds. A target for that label should be looser than one for
  your biggest label, and saying so is a good reason.
- **Unit 6 tests across three seeds, and the target has to hold across all
  three.** A target of 0.65 against results of 0.71, 0.62, 0.68 is a **miss**.
  Pick with that in mind — it is stricter than it first sounds.

---

## 1.

<!-- Your criterion. It must name a number. -->



**Why this target:**



---

## 2.

<!-- Your criterion. -->



**Why this target:**



---

## 3.

<!-- Your criterion. -->



**Why this target:**



---

## 4.

<!-- Your criterion. -->



**Why this target:**



---

## 5.

<!-- Your criterion. -->



**Why this target:**



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 6 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath, like this:

         ## 2. Every label performs acceptably

         The model performs well on all labels.

         **Why this target:** ...

         > **Revised in unit 6:** Every label has an F1 of at least 0.60 on
         > the held-out set.
         >
         > **Why revised:** "performs well" gave me nothing to check. I
         > couldn't produce a verdict from it at all.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "Overall accuracy of at least 0.65" → "at least 0.55", because
            0.65 turned out to be optimistic for 200 examples.

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.
     ───────────────────────────────────────────────────────────────────────── -->
