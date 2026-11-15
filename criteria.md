# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

My data: 198 NFL posts from Bluesky, labelled `neutral` (about 104), `hot_take`
(67) and `reasoned` (27). The notebook's 15% test split is about 30 posts, so
roughly 16 neutral, 10 hot_take and only 4 reasoned. Every target below has to
hold on all three seeds in unit 6.

---

## 1.

Overall accuracy of at least **0.70** on the held-out test split, on every one
of the three seeds.

**Why this target:** `neutral` is about 53% of my posts, so a model that always
guesses `neutral` would score about 0.53. I want the model to beat that by a
clear margin, not just squeak past it. I didn't go higher because the test split
is only about 30 posts, so each wrong answer costs about 3 points, and the
target has to survive the worst of three seeds.

---

## 2.

F1 of at least **0.65** for `hot_take` and for `neutral`, and at least **0.40**
for `reasoned`, on the held-out test split, on every seed.

**Why this target:** `hot_take` and `neutral` have enough examples (67 and about
104) that their scores should be fairly stable, so I hold them to a real bar.
`reasoned` is my smallest label with only 27 posts, so only about 4 land in the
test split. One mistake there can move its F1 by 0.2 or more, so its target is
looser on purpose. It is still well above zero, which is what a model that never
predicts `reasoned` would get.

---

## 3.

In the whole `labels.csv` (before the notebook splits it), no label is more than
**60%** of the rows, and the smallest label has at least **25** examples.

**Why this target:** The assignment caps any label at 70%, but I set a stricter
60% because a lopsided set teaches the model to guess `neutral`. My Bluesky
searches pulled in a lot of news headlines and links, which all land in
`neutral`, so this is the cap I'm most at risk of creeping toward if I add more
posts. The 25-example floor is there because `reasoned` (27) is barely above it,
and below that its test split would be 3 posts or fewer.

---

## 4.

When I label the 30 staff posts under the **staff taxonomy** (unit 6,
`agreement.py`), I agree with the staff labels on at least **70%** of them
(21 of 30).

**Why this target:** This measures me, not the model: whether I can apply
someone else's written rules the way they meant them, which is the only check I
have on whether my own 198 labels are consistent. I chose 70% rather than
something higher because it's a taxonomy I didn't design, and my own labels had
a fuzzy `hot_take` / `reasoned` boundary (for example, posts calling Lamar
Jackson overrated with one reason attached). Each disagreement is about 3
points, so 70% allows up to 9 misses.

---

## 5.

Of the test posts whose true label is `hot_take` or `reasoned`, at most **25%**
are predicted as the other one of the two, on every seed.

**Why this target:** The line between a hot take and a reasoned take ("does the
post give a reason?") is the boundary I found hardest to apply myself, so it's
the confusion I most expect. Confusing either of them with `neutral` is a
different mistake. There are only about 14 hot_take and reasoned posts in the
test split, so 25% allows about 3 swaps. I'll read this off the confusion matrix
in section 7.

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
