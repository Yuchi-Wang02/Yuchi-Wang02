# Yuchi Wang

I'm an MS student in Business Analytics and Artificial Intelligence at **Johns Hopkins Carey Business School** (expected August 2027). I graduated **cum laude from Ohio State**, with a background in accounting and logistics management.

My projects examine the reliability of AI in business analytics: how data definitions shape results, whether model evaluations are meaningful, and whether business claims are supported by evidence.

Washington, DC · [Email](mailto:yuchiwang02@outlook.com) · [Hugging Face](https://huggingface.co/Yuchiwang02)

## Selected projects

### BizHallu · Checking AI-generated business claims

A correct amount can still support an incorrect claim. In one retail example, an LLM copies the right product and amount but assigns it third place; the evidence places it seventh.

[![April 2011 example: the same product and GBP 4,173.18 appear at rank 3 in the model answer, but rank 7 in the evidence. This is a curated evidence check.](assets/bizhallu-case.svg)](https://yuchi-wang02.github.io/bizhallu/portfolio_demo_v2.html?case=q_0064)

The workflow connects retail transactions, 100 reproducible business questions, computed reference answers, and local model responses. Interactive cases make the errors inspectable. The evaluation uses provisional, AI-assisted span labels without independent human annotation; the featured case is a curated evidence check.

[Explore a case](https://yuchi-wang02.github.io/bizhallu/portfolio_demo_v2.html?case=q_0064) · [Methods and results](https://yuchi-wang02.github.io/bizhallu/detector_interpretation.html) · [Code](https://github.com/Yuchi-Wang02/bizhallu)

### DelaySentinel · Building and evaluating logistics AI

A published Llama fine-tune, a reproducible evaluation workflow, and controlled tests of model behavior. The project connects model development with a practical question: **what does a strong score actually establish?**

[![The Llama fine-tune and a depth-2 tree both score 100% on the historical 200-row split. A two-field rule reproduces the source labels.](assets/delaysentinel-comparison.svg)](https://github.com/Yuchi-Wang02/delaysentinel)

The audit explains the score through a two-field label rule, then tests how predictions respond to changed inputs—including an irrelevant note that flips all 84 negative predictions. The historical split includes training-time evaluation rows. A separate Olist study examines classical models using checkout-time information and a later test period.

[Explore the project](https://github.com/Yuchi-Wang02/delaysentinel) · [Read the case study](https://github.com/Yuchi-Wang02/delaysentinel/blob/main/docs/case_study.md) · [Model card](https://huggingface.co/Yuchiwang02/Llama-3.2-1B-DelaySentinel)

## Background

Experience includes social intelligence analytics at **Ipsos in Shanghai**, supply chain analysis at **SF Express**, and work as a **Peer Advisor at Ohio State's Office of International Affairs**, supporting international students.

**Project stack:** Python, pandas, scikit-learn, PyTorch, Hugging Face Transformers, pytest, and GitHub Actions.

These personal projects use AI-assisted implementation and review. Each repository documents its methods, evidence, and limitations.
