---
marp: true
paginate: true
header: 'Academic Conferences Theme'
footer: 'Moreno La Quatra | Demo Deck'
theme: academic-conferences
math: mathjax
---

<!-- _class: lead -->

# A Minimal Theme for Conference Talks

<p class="subtitle">Color-coded components, no one-sided borders, built for slides</p>

<p class="authors">Moreno La Quatra · Kore University of Enna</p>

---

## Agenda

1. Why a new theme
2. Semantic components
3. Layouts for results
4. Wrap-up

---

<!-- _class: section -->

# Semantic Components

---

## Whole-slide components need zero HTML

Apply a component to an entire slide with a single directive comment:

```
<!-- _class: definition -->
```

Everything below the front matter on that slide is automatically styled
with a soft tinted background and a color-matched heading.

---

<!-- _class: definition -->

## Self-Attention

Self-attention lets every token attend to every other token in a sequence
directly, regardless of distance:

- Removes the fixed-size bottleneck of recurrent models
- Enables constant path length between any two positions
- Forms the core building block of the Transformer

---

<!-- _class: example -->

## Worked Example

For the sentence *"The animal didn't cross the street because it was too tired"*:

- Attention lets **"it"** connect strongly to **"animal"**
- The correct antecedent is resolved without an explicit coreference module

---

<!-- _class: important -->

## Key Takeaway

Scaling the dot product by $\sqrt{d_k}$ keeps gradients well-behaved as the
head dimension grows. Without it, softmax saturates and gradients vanish.

---

<!-- _class: warning -->

## Caution

Self-attention has $O(n^2)$ time and memory complexity in sequence length.
For long documents or high-resolution inputs, this quickly becomes the
dominant cost.

---

<!-- _class: note -->

## Note

Sparse and linear-attention variants (Longformer, Performer, Mamba) trade
some expressivity for sub-quadratic scaling. Covered in a follow-up talk.

---

## Boxes also work inline, next to other content

<div class="cols-2">

<div class="important">

### Why it matters
Use an inline box only when a component must sit **beside** other content:
one wrapper `<div>`, nothing nested inside it.

</div>

<div class="example">

### In practice
Prefer the whole-slide `_class` form whenever a slide has only one idea.

</div>

</div>

---

<!-- _class: section teal -->

# Layouts for Results

---

## Two-column layout

<div class="cols-2">

<div>

### Method
- Multi-head self-attention
- Learned positional encodings
- Pre-norm residual blocks

</div>

<div>

### Result
Native markdown lists, headings and tables render inside a plain `cols-2`
div without any extra styling required.

</div>

</div>

---

## Native blockquote as a pull-quote

> Attention is All You Need.
> Vaswani et al., 2017

---

## Results table

| Model        | Params | Accuracy   | Latency    |
|--------------|:------:|:----------:|:----------:|
| Baseline RNN | 25M    | 81.2%      | 1.0x       |
| Transformer  | 44M    | <span class="value-high">89.7%</span> | <span class="value-low">2.3x</span> |
| Our method   | 31M    | <span class="value-high">90.4%</span> | 1.1x       |

---

## Headline metrics

<div class="stats">

<div class="stat">

### 90.4%
Accuracy

</div>

<div class="stat">

### 31M
Parameters

</div>

<div class="stat">

### 1.1x
Relative latency

</div>

</div>

---

<figure>

![w:520](https://placehold.co/900x500?text=Architecture+Diagram)

<figcaption>Figure 1: Overall model architecture (placeholder image).</figcaption>

</figure>

---

<!-- _class: section plum -->

# Wrap-up

---

## Summary

- One `_class` directive is enough for most slides, no HTML at all
- Five color-coded components: definition, example, important, warning, note
- Reusable author and QR cards for the closing slide
- No one-sided borders anywhere in the theme

---

<!-- _class: lead -->

# Thank You

<p class="subtitle">Questions welcome</p>

---

## Get in Touch

<div class="cols-2">

<div class="author-card">

### Moreno La Quatra
Kore University of Enna
[moreno.laquatra@unikore.it](mailto:moreno.laquatra@unikore.it)

</div>

<div class="author-card">

### Jane Doe
Some Other University
[jane.doe@example.edu](mailto:jane.doe@example.edu)

</div>

</div>

<div class="qr-row">

<div class="qr-card">

![w:120](https://placehold.co/120x120?text=QR)

Paper

</div>

<div class="qr-card">

![w:120](https://placehold.co/120x120?text=QR)

Code

</div>

</div>
