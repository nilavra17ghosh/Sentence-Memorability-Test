# Sentence Memorability Analysis

Analysis of a **continuous recognition memory experiment** examining how sentence memorability depends on the memorability of its component nouns and sentence voice.

Sentences follow a **Subject–Verb–Object (SVO)** structure. Subject and object nouns vary in memorability, creating four sentence types, each presented in **active** and **passive** voice.

---

## Experimental Conditions

Sentence memorability is manipulated through noun memorability:

| Condition | Description                                   |
| --------- | --------------------------------------------- |
| HH        | High-memorable subject, High-memorable object |
| HL        | High-memorable subject, Low-memorable object  |
| LH        | Low-memorable subject, High-memorable object  |
| LL        | Low-memorable subject, Low-memorable object   |

Each condition appears in **Active (A)** and **Passive (P)** voice, giving **8 total groups**.

---

## Dataset

Each `.log` file corresponds to one participant's experiment session.

Relevant fields include:

* **participant_ID** – participant identifier
* **Stimulus** – sentence condition and voice
* **isRepeat** – repeated stimulus indicator
* **Button** – participant response
* **Accuracy IR / WR** – recognition accuracy
* **Reaction_time_IR / WR** – response times

---

## Data Processing

The analysis pipeline performs:

1. Load and merge participant log files
2. Clean and format stimulus information
3. Remove practice trials and invalid entries
4. Apply **block validation filtering** based on attention checks

A block is retained only if:

[
CorrectValidation > \frac{WrongValidation}{2} + MissedValidation
]

---

## Memorability Measure

Sentence memorability is estimated using a **corrected recognition score**:

[
Corrected\ Score = Hit\ Rate - False\ Alarm\ Rate
]

This controls for response bias when comparing conditions.

---

## Statistical Analysis

The following tests are applied:

* **Shapiro–Wilk test** – normality check
* **Kruskal–Wallis test** – differences across sentence types
* **Dunn's test** – post-hoc comparisons
* **Mann–Whitney U test** – active vs passive voice comparison

Additional signal detection metrics are also computed:

* **d′ (sensitivity)**
* **c (response bias)**

---

## Dependencies

* numpy
* pandas
* scipy
* matplotlib
* seaborn
* scikit-posthocs

---

## Usage

Run the notebook sequentially after placing participant `.log` files in the data directory.

The notebook performs preprocessing, statistical testing, and visualization of results.

