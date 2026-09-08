---
title: "Orthography and macrons"
page_type: appendix
author: S. Le Boulanger
date: 2026-09-07
description: "The editorial policy of the course: vowel length marking, u/v and consonantal i, the ae/oe digraphs, and the treatment of quoted texts."
tags: ["orthography", "macrons", "editorial-policy"]
---

Latin has been printed in many conventions, and no one of them is correct. What
a course owes its learners is not the right convention but a stated one, applied
without exception, so that a form on page 200 can be trusted to mean what the
same form meant on page 3. This page states the convention this course uses and
gives the reason for each decision. It was fixed before the first unit was
written, because changing it afterwards would mean reflowing every page.

## 1. Vowel length is marked

**Teaching text, vocabulary lists, paradigms and exercises carry macrons.**
Long vowels are printed `ā ē ī ō ū ȳ` and `Ā Ē Ī Ō Ū Ȳ`; short vowels are left
unmarked. The breve (`ă`, `ĕ`) is used only where a contrast is being made
explicitly, never as a default.

The reason is not fastidiousness. Vowel length in Latin is phonemic, and it is
grammatical:

| Unmarked | Marked | Difference |
|---|---|---|
| `liber` | `līber` | *book* against *free* |
| `populus` | `pōpulus` | *a people* against *a poplar* |
| `malum` | `mālum` | *evil* against *apple* |
| `puella` | `puellā` | first declension nominative against ablative |
| `venit` | `vēnit` | present against perfect of *veniō* |

The last two are the decisive ones. In the first declension the nominative and
ablative singular are identical letter for letter and differ only in quantity;
in the third conjugation the present and perfect of a common verb do the same. A
learner reading unmarked text must recover both from context, on every line,
from the first day. Marking the vowel removes an ambiguity that Roman readers
did not have either — they had the language.

**Quoted authentic text does not carry macrons** where fidelity is the point:
inscriptions, manuscript readings, and any passage reproduced to show how it was
actually written. Such passages are set off and labelled. Elsewhere, quoted
classical prose and verse is macronised in line with the standard modern
teaching editions, and the macronisation is declared as editorial.

Macrons are also dropped in Stage IV verse exercises where the task is to
recover quantity from the metre. That is the point of the exercise, and the
guide to it lives in the scansion appendix.

## 2. Encoding

Macronised vowels are written as **precomposed Unicode characters**, not as a
base letter plus a combining macron (U+0304):

- Use `ā` U+0101, `ē` U+0113, `ī` U+012B, `ō` U+014D, `ū` U+016B, `ȳ` U+0233,
  and their capitals.
- Do not use `a` + U+0304, which renders inconsistently, sorts unpredictably,
  and breaks naive substring search.

`ȳ` is the one to watch: it is rarer than the others in font coverage and in
input methods, and it is needed for Greek loanwords (*Ȳlias* is not wanted, but
*lȳra*, *Nȳsa*, *satȳrus* are). Every font shipped or specified by this course is
checked for `ā ē ī ō ū ȳ Ā Ē Ī Ō Ū Ȳ` before it is adopted, in the body face, in
the slide deck face and in the worksheet face, so that a macron never falls back
to a missing-glyph box.

## 3. `u` and `v`

The course **distinguishes `u` from `v`**, in the mainstream school convention:
consonantal *u* is printed `v`, vocalic *u* is printed `u`. So *veniō*, *vīvit*,
*servus* — not *ueniō*, *uīuit*, *seruus*.

Capitals follow the same rule: `V` for the consonant, `U` for the vowel, so
*Vergilius* and *Ursa*. This departs from the Roman practice of writing a single
letter V for both, and from the practice of some scholarly editions which
restore it. The reason for departing is pedagogical: the distinction is one the
learner would otherwise have to make silently before every word, and making it
in print costs nothing that this course needs.

## 4. Consonantal `i`

The course **does not use `j`**. Consonantal *i* is printed `i`: *iam*, *Iūlius*,
*iaciō*, *coniūnx*. Where the consonantal value is not obvious to a beginner it
is noted in the vocabulary entry rather than in the spelling.

`j` belongs to a later printing tradition and to ecclesiastical texts; it appears
in this course only inside a quotation that uses it, where it is kept as the
quoted source has it.

## 5. `ae` and `oe`

The digraphs are printed as **two letters, never as ligatures**: `ae` and `oe`,
not `æ` and `œ`. So *Caesar*, *poena*, *proelium*.

Ligatures are a typographic convention of early modern printing, not a feature of
the language; they complicate search, copy-and-paste and screen reading, and they
gain nothing. Where a quoted facsimile uses a ligature, the transcription
expands it and says so.

In restored classical pronunciation both are diphthongs and are marked as such in
the pronunciation appendix. Where a spelling is genuinely disyllabic — *āēr*,
*poēta* — the second vowel carries its own macron or a diaeresis, so that
*poēta* is never read as a diphthong.

## 6. Capitalisation, punctuation and word division

Latin was written without word spacing, without lower case and without
punctuation. None of that is reproduced. The course uses modern word division,
modern sentence punctuation, and capitalisation restricted to sentence openings
and proper nouns — including adjectives derived from proper nouns, which are
capitalised (*Rōmānus*, *Graecus*), following continental practice.

Quotation marks are used sparingly and direct speech in narrative Latin is
introduced by a verb of speaking rather than by punctuation, because that is how
the authors mark it.

## 7. Variety

The spine of the course is **Classical Latin** of the Golden and Silver ages —
roughly Cicero to Tacitus — and every convention above is set for that variety.

Ecclesiastical and Medieval Latin appear later as a **supplementary reading
track**, not as an alternative default. Where they appear, their own conventions
are respected and the differences are named rather than silently normalised:
*e* for the classical diphthongs, `j` for consonantal *i*, *ti* pronounced as an
affricate, the orthographic habits of a scribe rather than of a print editor.
There is no dialect fork in the course structure; there is one course, with a
declared variety and a labelled supplement.

## 8. Summary

{{< callout type="note" title="The policy in nine lines" >}}
1. Macrons on in teaching text and vocabulary; off in reproduced authentic text.
2. Precomposed Unicode, never base letter plus combining macron.
3. `ȳ` is required; check every font for it.
4. `u` and `v` distinguished.
5. `i` for consonantal *i*; no `j`.
6. `ae` and `oe` as two letters; no ligatures.
7. Modern word division, punctuation and capitalisation.
8. Proper adjectives capitalised.
9. Classical Latin is the spine; other varieties are labelled supplements.
{{< /callout >}}

## Sources and further reading

- W. Sidney Allen, *Vox Latina: A Guide to the Pronunciation of Classical
  Latin*, 2nd edn (Cambridge University Press, 1978) — the standard account of
  the evidence for quantity and pronunciation.
- The Unicode Standard, *Latin Extended-A* and *Latin Extended-B* code charts,
  for the precomposed macronised vowels named above.
- The macronisation conventions of the standard modern teaching editions, against
  which this course's quoted passages are checked.
