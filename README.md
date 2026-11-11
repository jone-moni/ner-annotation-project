# ner-annotation-project
Hand-labeled NER dataset:100 sentences with annotation guidelines.
built to practice consistent, guideline-driven data annotation.
---

## What is NER?

Named Entity Recognition means finding names and values in text (people, organizations, places, dates, money) and labeling each with its type. Models learn NER from text that humans have labeled, so label quality directly decides model quality.

**Example**

> **Narendra Modi** `PERSON` inaugurated the new terminal at **Navi Mumbai International Airport** `FAC` on **Tuesday** `DATE`.

---

## Dataset

| Property | Value |
|---|---|
| Sentences | 100 |
| Domains (10 sentences each) | News, Business, Technology, Sports, Health, Science, Entertainment, Travel, Education & Legal, Informal |
| Difficulty levels | Easy (clear names), Medium (multi-word names, dates, money), Hard (ambiguous cases) |
| Entity types | 14 |

The **Informal** domain uses chat, email and social-media style text (lowercase names, abbreviations), because real-world data is rarely as clean as news writing.

---

## Label Set

| Tag | Full form | What it covers | Example |
|---|---|---|---|
| `PERSON` | Person | Real people | Virat Kohli |
| `ORG` | Organization | Companies, institutions, courts, teams, universities, hospitals, media | Infosys, Delhi High Court |
| `GPE` | Geopolitical entity | Countries, states, cities | India, Chennai |
| `LOC` | Location | Natural features, planets, regions, neighborhoods | Pacific Ocean, Mars |
| `FAC` | Facility | Buildings, airports, stadiums, bridges, monuments | Taj Mahal, Wembley Stadium |
| `DATE` | Date | Dates, months, years, relative days, durations | 12 November 2023, last Friday |
| `TIME` | Time | Times of day | 10:30 AM, midnight |
| `MONEY` | Money | Monetary values with currency | $2.5 billion, Rs 3,500 |
| `PERCENT` | Percentage | Percentage values | 6.5%, 50 percent |
| `PRODUCT` | Product | Named devices, apps, software, languages | iPhone 15 Pro, WhatsApp |
| `EVENT` | Event | Tournaments, festivals, conferences, ceremonies | FIFA World Cup 2022, Diwali |
| `LAW` | Law | Acts, constitutional articles, schemes | Right to Information Act |
| `WORK_OF_ART` | Work of art | Titles of films, books, songs, shows | Oppenheimer, Stranger Things |
| `AWARD` | Award | Named prizes and honors | Nobel Prize in Physics |

---

## Annotation Rules

I applied the same rules to every sentence so that two annotators would label it the same way.

1. Tag the **longest meaningful name**: "Reserve Bank of India" is one `ORG`, with no separate tag for "India".
2. Label by **meaning in context**, not by the word itself.
3. **No nested entities.** Tag only the outermost span.
4. Leave **titles out** of `PERSON` spans (Dr., Mr., Justice, Prime Minister are not tagged).
5. Include the **currency** in `MONEY` spans: "Rs 3,500", not "3,500".
6. Leave nationalities ("Indian"), diseases, generic drugs and plain numbers **untagged**, unless the adjective is part of a proper name (e.g. Indian Premier League).
7. Tag relative dates such as "last Friday" or "next week" as `DATE`.

Full guidelines: [`docs/annotation_guidelines.md`](docs/annotation_guidelines.md)

---

## Hard Cases

The "Hard" sentences test whether a label depends on context.

| Case | Example | Decision |
|---|---|---|
| Same word, different type | "Jordan" the player vs. "Jordan" the country | `PERSON` vs. `GPE` |
| Company vs. common noun | "Apple sold iPhones" vs. "apple prices fell" | `ORG` vs. untagged |
| Person name vs. place | "Paris Hilton" vs. "Paris, Texas" | `PERSON` vs. `GPE` |
| Planet vs. company | "Mars" vs. "Mars Inc." | `LOC` vs. `ORG` |
| App vs. company | WhatsApp as a service vs. Twitter as a company | `PRODUCT` vs. `ORG` |
| Person inside a facility name | "Narendra Modi Stadium" | one `FAC` span, no `PERSON` |
| Date boundaries | "Monday morning" | one `DATE` span |

---

## Repository Structure

```
ner-annotation-project/
├── README.md
├── data/
│   └── ner_dataset.xlsx          # sentences + entity labels
└── docs/
    └── annotation_guidelines.md  # full annotation guidelines
```

---

## Skills Demonstrated

- Designing a label schema and writing annotation guidelines
- Consistent manual text annotation across different writing styles
- Resolving ambiguous cases by written rule instead of guesswork
- Documenting decisions so the work can be reproduced by another annotator

---

## Author

Jonemoni Kalita
linkedIn - www.linkedin.com/in/jonemoni-kalita-6a56b2234


