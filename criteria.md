# Acceptance criteria — TakeMeter

Five criteria that say what "working" means for this classifier, written in
unit 5 **before** anything was trained.

**All five are yours this time.** None are given. You've had two projects of
practice.

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

The model's recall on `warning` is at least 0.65 on the held-out test split.

**Why this target:**

`warning` is only 17% of my data right now (6 of 36 reviews), so a
   model that guesses `recommendation` every time would score 0.00 recall on
   it while still looking about 72% accurate. I also found `warning` hard to
   label consistently: a review like "Crispy roll and fresh ingredients, but
   very sparse meat, for the price... Disappointing." has praise and a
   negative ending together. Missing warnings means the model would label a
   complaint as a recommendation, so a reader could be steered toward a place
   the reviewer warned against.


---

## 2.

<!-- Your criterion. -->
The model's recall on `neutral` is at least 0.50 on the held-out test split.


**Why this target:**

`neutral` is only 11% of my data right now (4 of 36 reviews), so
  a model that guesses `recommendation` every time would score 0.00 recall on
  it, and with so few examples the model may never learn the label. It is also
  my vaguest label: "takes no side" has no quotable words to point at, and I
  labeled rows like "I been coming here" differently on different passes. I
  set the bar lower than for `warning` because it is the label I have the
  least data for and it has the loosest definition of the two.



---

## 3.

<!-- Your criterion. -->
Overall accuracy on the held-out test split is at least 0.80, which is
  8 points above the 72% I'd get by always guessing `recommendation` on
  today's data.



**Why this target:**
 the vast majority of my data is `recommendation`, so a model can
  look strong just by labeling that class well. A test split of about 40
  reviews moves 2.5 points per review, so a gap under about 3 reviews could
  be luck. An 8-point margin is about 3 reviews, enough to say the model
  learned something beyond guessing. I will recompute the always-guess
  baseline from my final label counts. If more `warning` and `neutral`
  reviews lower it, I keep 0.80 and report the larger gap.





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
