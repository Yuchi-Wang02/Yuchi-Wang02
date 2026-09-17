# Yuchi Wang

M.S. in Business Analytics and Artificial Intelligence, Johns Hopkins Carey Business School (expected Aug 2027) ·
B.S. in Business Administration, Accounting and Logistics Management, The Ohio State University (cum laude) ·
Washington, DC · yuchiwang02@outlook.com

I build LLM and ML pipelines on business data, then audit the numbers the way a skeptical reviewer would:
the baseline that beats the model gets reported, labels carry their provenance, and a model I had already
published got re-scored a year later and written up as a leakage case study.

## Projects

### BizHallu — span-level evidence-grounding audit of LLM-written retail analysis

[Site and cases](https://yuchi-wang02.github.io/bizhallu/) ·
[Repository](https://github.com/Yuchi-Wang02/bizhallu) ·
[One-page research brief (PDF)](https://yuchi-wang02.github.io/bizhallu/assets/bizhallu_research_brief.pdf)

*Finding: a correct number can still support the wrong business claim. Qwen3-0.6B copies real ledger values into wrong
product/rank bindings at near-100% token confidence; uncertainty signals miss this, and a deterministic evidence tie-out
catches it on this data.*

- Built the pipeline: 541k UCI Online Retail rows; 100 deterministic questions (7 types) with gold answers and evidence
  tables; local Qwen3-0.6B answers with token traces; 12 uncertainty signals scored on 205 pre-identified, AI-assisted
  provisional span labels (no independent human annotation yet).
- Reported every metric beside its baseline: on 103 pre-identified test spans (61 positive, error-enriched), top-2 margin
  AP 0.835 [question-cluster bootstrap 95% CI 0.724–0.923], the exploratory maximum over 12 signals chosen on test; a
  fact-type prior baseline (AUROC 0.768) beats that signal’s AUROC (0.757 [0.656–0.863]); within-question AUROC 0.760
  (permutation p < 0.0005); dev and test share periods.
- Traced one inspectable error: an April 2011 answer ranks WOODEN UNION JACK BUNTING 3rd at GBP 4,173.18; the amount
  matches its source row, but the product is 7th of the 8 evidence rows shown (a hand-checked case, not an automated
  detector output).
- Audited the revenue definition with accounting rules: 46.8% of “cancellation/return” negative revenue was
  non-merchandise, a GBP 11,062.06 bad-debt line sat inside August revenue, and same-day reversal pairs inflated
  January’s return rate from 8.84% to 19.04%; issued metric contract v1.1 for new questions (v1 gold unchanged).
- Shipped 120 Python and 25 Node tests, GitHub Actions CI on public artifacts, and a GitHub Pages site with interactive
  cases; designed a hash-committed follow-up study (48 period-disjoint contexts, 96 frozen private questions;
  design-only, 3 of 7 gates, not executed).

Independent project; directed with AI-assisted implementation and review. Data: UCI Online Retail (CC BY 4.0). Code: MIT.

### DelaySentinel — label-leakage self-audit of a fine-tuned Llama-3.2-1B

[Repository](https://github.com/Yuchi-Wang02/delaysentinel) ·
[Model card](https://huggingface.co/Yuchiwang02/Llama-3.2-1B-DelaySentinel) ·
[Frozen split](https://huggingface.co/datasets/Yuchiwang02/smart-logistics-delay-split-v0) ·
[Case study](https://github.com/Yuchi-Wang02/delaysentinel/blob/main/docs/case_study.md)

*Finding: the training label was a two-column rule over the model’s own inputs (Shipment_Status = “Delayed” OR
Traffic_Status = “Heavy” on 1,000/1,000 rows); the model keys on the surface form of those two values, not on any delay
driver.*

- Fine-tuned Llama-3.2-1B-Instruct (full-parameter SFT) on a 1,000-row synthetic Kaggle table and uploaded it to Hugging
  Face (Sep 2025) without computing accuracy; rescored it a year later: accuracy 1.000 on its 200-row split, matched
  exactly by a depth-2 decision tree.
- Localized the trigger with 104 counterfactual probe sets scored by teacher-forced logit margin: all 261 edits to the two
  rule fields flip the answer, 3,200 edits to the other 13 fields change nothing; gradient boosting without the leaked
  columns scores AUROC 0.452.
- Ran a positive control on real Olist orders (train 53,644 / test 37,702): logistic regression AUROC 0.691 [month-block
  bootstrap 0.633–0.760]; packaged the audit with 56 pytest cases and a CI check that fails when a quoted number is
  missing from the saved results.

Code: MIT. Weights: Llama 3.2 Community License. The Kaggle table is synthetic (CC0); the Olist control uses the public
Olist e-commerce dataset (CC BY-NC-SA 4.0), which is not redistributed here.

## Toolbox

Python (pandas, NumPy, scikit-learn, SciPy), PyTorch, Hugging Face Transformers (local Qwen3-0.6B inference,
Llama-3.2-1B SFT, llama.cpp/GGUF), pytest, Git/GitHub Actions/Pages, SQL (basic), Excel (Solver, pivot tables),
R (coursework). Methods: LLM evaluation and uncertainty signals (entropy, top-2 margin), label-leakage audits,
counterfactual probing, cluster-bootstrap and permutation inference, tied-score AP, Holt-Winters forecasting, integer
programming, P50/P90 cost modeling.

Before this: Supply Chain Management Intern at SF Express (remote, 2025) and Social Intelligence Analytics Intern at
Ipsos (China), Shanghai (2025).
