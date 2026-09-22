# Airport Reviews with a Silent Stratum: 33,257 Google Maps Ratings from Nine Southeast Asian Airports

A review corpus built for research on **voice selection** — the fact that most people who rate an
entity never write about it. Unlike most public review datasets, which keep only reviews that carry
text, this one retains the **star-only stratum**: 16,588 ratings with no accompanying text sit
alongside 16,669 that have text. Both groups rated the same nine airports on the same scale in the
same period, which makes the corpus usable as two measurements of one population rather than one
measurement of a self-selected subset.

**File.** `airport_reviews_9_sea.csv` — 33,257 rows × 36 columns, UTF-8, 21 MB.

## Coverage

| | |
|---|---|
| Entities | 9 international airports |
| Countries | Vietnam (SGN, HAN, DAD), Thailand (BKK, DMK, HKT), Malaysia (KUL, PEN, BKI) |
| Period | August 2023 – August 2026 |
| Reviews | 33,257 (16,669 with text, 16,588 star-only) |
| Reviewers | 30,421 distinct |
| Languages | 30+; English 8,805, Vietnamese 1,959, Thai 918, Korean 672, Chinese 565 |
| Ratings | 5★ 18,426 · 4★ 6,778 · 3★ 2,740 · 2★ 1,325 · 1★ 3,988 |
| Per airport | 3,179 – 4,369 reviews |

Reviews per airport are roughly balanced by design, so the corpus is not dominated by the largest
hub.

## Columns

**Identity and entity** — `reviewer_pseudonym`, `review_id`, `place_name`, `country`

**Rating and participation** — `rating` (1–5), `has_review_text` (as displayed),
`has_text_derived` (whether usable text is actually present; **use this one**), `n_words_original`,
`n_words_en`

**Review text** — `review_text_original` (as posted), `text_en` (English rendering),
`text_for_llm` (normalised for machine reading), `review_lang`, `is_translated`,
`translation_clicked`

**Reviewer metadata** — `reviewer_info` (the public activity string), `is_local_guide`,
`reviewer_n_reviews`, `reviewer_n_photos`, `reviewer_info_missing`, `photo_count`

**Time** — `review_date_est` (best estimate), `date_raw`, `date_rel_value`, `date_rel_unit`,
`date_is_estimate`, `date_accuracy`, `date_precision`, `is_edited`, `crawled_at`

**Other** — `owner_response`, `like_text`, `visited_on`, `wait_time`,
`reservation_recommended`, `crawler_version`

Google Maps reports most review dates relatively ("2 months ago"), so `review_date_est` is an
estimate; `date_precision` and `date_accuracy` state how good each estimate is. Filter on those
before using dates for anything time-sensitive.

## Privacy

Reviewer display names, contributor profile URLs and crawl provenance fields were removed before
release. `reviewer_pseudonym` is a salted hash: it is stable within the dataset, so repeat
reviewers can be identified as the same person, but it does not invert to a name. Email addresses,
phone numbers and URLs appearing inside review text were replaced with `[EMAIL REDACTED]`,
`[NUMBER REDACTED]` and `[URL REDACTED]` (71 cells).

Public activity counts (`reviewer_info`, `reviewer_n_reviews`, `reviewer_n_photos`,
`is_local_guide`) are retained because participation models need them.

## What it was built for

The corpus supports questions that need both strata:

- How steeply does writing propensity fall as the rating given rises?
- How much of the variance that distinguishes one entity from another sits in the written channel
  rather than the star-only channel?
- How far does a displayed average diverge from the writers' average, and is that divergence
  behavioural or simply arithmetic?
- Which rating-based decision rules — thresholds, rankings, differences — break under selection,
  and which survive?

It also suits multilingual review research: nine entities across three countries and thirty-odd
languages, with original and English-rendered text side by side.

## Known limits

Nine entities, one vertical, one platform. No external quality benchmark, so the data cannot say
which stratum is closer to true quality — only how the two differ. Text is as Google served it,
including its own translations. Star-only ratings carry no text by definition, so anything text-based
is estimable on the written stratum alone.

## Citation

> Dang, T.-D. (2026). *Airport reviews with a silent stratum: 33,257 Google Maps ratings from nine
> Southeast Asian airports* [Data set].

Please also cite the accompanying paper once it appears.

## Licence and terms

The data were collected from publicly visible Google Maps review pages. Review text remains the
work of its authors, and Google's terms govern what may be done with content obtained from its
services. The dataset is released for **non-commercial research and teaching**. Do not use it to
re-identify reviewers, and do not redistribute the review text as a commercial product.
