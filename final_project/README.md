# Explainable AI for Predicting Cybersecurity Vulnerabilities in Software Systems
## Toward Trustworthy and Transparent Cybersecurity

> A conceptual review research proposal and final presentation for the course MBAI 5310G, AI Programming.

**Author:** Nusrat Jahan
**Course:** MBAI 5310G, AI Programming, Spring 2026
**Instructor:** Professor Zahra Atf
**Institution:** Ontario Tech University

### Quick Links

| Resource | Where to find it |
|----------|------------------|
| GitHub repository | [MBAI5310G-AI-Programming-NusratJahan](https://github.com/nusratjahan73/MBAI5310G-AI-Programming-NusratJahan) |
| Portfolio | [nusratjahan73.github.io](https://nusratjahan73.github.io/) |
| Research proposal | Final research paper (see the final_project folder) |
| Final presentation | Final Presentation slides (10 slides) |

## Table of Contents

1. [Abstract](#abstract)
2. [Background and Motivation](#background-and-motivation)
3. [Problem Statement](#problem-statement)
4. [Aim and Objectives](#aim-and-objectives)
5. [Research Questions](#research-questions)
6. [Literature Review](#literature-review)
7. [Research Gap](#research-gap)
8. [Conceptual Framework](#conceptual-framework)
9. [Methodology](#methodology)
10. [Expected Contribution](#expected-contribution)
11. [Ethical Considerations](#ethical-considerations)
12. [About the Presentation](#about-the-presentation)
13. [Author](#author)

## Abstract

Software systems face a fast growing number of security vulnerabilities every year. Machine learning is now widely used to predict and rank these vulnerabilities, and it is often very accurate. The problem is that the strongest models act like a black box. They give a result without showing the reason, which leaves security analysts unsure whether they can trust the output.

Explainable Artificial Intelligence, or XAI, has been offered as the answer, because it tries to show the reasons behind a model decision. Yet the evidence is mixed. Some studies show that explanations help people understand and act, while others show that explanations raise trust only moderately and can even be attacked.

This proposal studies how explainable AI can make the prediction of software vulnerabilities more transparent and more trustworthy. It is a conceptual review of eleven recent studies. It compares how explanation methods are applied, how they support transparency and trust, and how well they hold up against distortion. From this reading it proposes a conceptual framework that links prediction, explanation quality, transparency, and trust, and it offers a base for future testing on real vulnerability data.

**Keywords:** explainable AI, vulnerability prediction, software security, SHAP, LIME, transparency, trust, conceptual review.

## Background and Motivation

Software now supports almost every part of modern life, from banking and healthcare to power grids and personal devices. As these systems have grown larger and more connected, the number of reported security vulnerabilities has risen sharply. Public records such as the National Vulnerability Database show a steady climb over the past two decades, and the effort needed to assess each weakness has grown just as fast.

The volume is now too large for teams to review every weakness by hand. To keep up, researchers increasingly use machine learning to predict which vulnerabilities exist, how serious they are, and which ones are most urgent. These models can be highly accurate and can process far more data than a human analyst.

The catch is that many of the strongest models work as black boxes. They return a score with no reason. An analyst who must patch a system, raise an alarm, or warn a client needs to understand why a prediction was made before acting on it. This need for understanding is what gave rise to explainable AI. Methods such as SHAP and LIME show which inputs mattered most for a single prediction, so the result becomes easier to read and to question.

## Problem Statement

Machine learning models reach high accuracy in predicting software vulnerabilities, but their decisions often stay hard to understand, and this lack of clarity limits how far analysts can trust and act on them. Explainable AI is presented as the fix, but the evidence is divided. Some studies show that explanations improve understanding and support action. Others show that explanations raise trust only moderately. Still others show that explanations can be quietly attacked or twisted without the analyst noticing. Because of this, it is not clear whether explainable methods truly make vulnerability prediction transparent and trustworthy, or whether they only create an appearance of clarity. That uncertainty is the problem this proposal addresses.

## Aim and Objectives

This study aims to examine how explainable AI can make the prediction of software vulnerabilities more transparent and trustworthy. The aim breaks into four objectives.

1. Review the explainable methods currently used for predicting and assessing software vulnerabilities.
2. Analyse how these explanations support transparency and trust for the analysts who rely on them.
3. Examine the limitations and risks of these explanations, including how well they resist distortion.
4. Propose a conceptual framework that links vulnerability prediction, explanation quality, transparency, and trust, in a form that a later study could test on real data.

## Research Questions

**Main question:** How can explainable artificial intelligence make the prediction of cybersecurity vulnerabilities in software systems more transparent and trustworthy?

Four supporting questions guide the study.

1. How can explainable AI make the prediction of software vulnerabilities more transparent for analysts?
2. How does the quality of an explanation affect how much an analyst trusts a prediction?
3. What limitations or risks reduce the reliability of these explanations?
4. What conceptual framework can connect explainable prediction, transparency, and trust in this setting?

## Literature Review

The review reads eleven recent papers and sorts them into three camps. The first camp applies explanation methods to real security tasks. The second camp questions whether the explanations themselves can be trusted or attacked. The third camp gives wider context on AI in cybersecurity.

| No. | Paper | Focus or task | Explanation method | Role in this study |
|-----|-------|---------------|--------------------|--------------------|
| 1 | Manai et al., 2024 | Predicting vulnerability severity scores from text | SHAP across classes | Closest work, shows prediction with explanation |
| 2 | Mia and Pritom, 2025 | Attacks on XAI explanations | Adversarial study | Warns that explanations can be deceived |
| 3 | Alabri et al., 2026 | Detecting low rate DDoS in cloud | SHAP with attention | Application of explanation to attack detection |
| 4 | Carter et al., 2024 | XAI in corporate risk and security | Conceptual | Transparency supports trust and compliance |
| 5 | Manthena et al., 2025 | Survey of XAI for malware analysis | Review of methods | Maps open challenges in the field |
| 6 | Hamim et al., 2025 | Hybrid intrusion detection | SHAP and LIME | Shows explanation at both global and single alert level |
| 7 | Atf and Lewis, 2025 | Meta analysis of trust and explainability | Meta analysis | Finds trust is only moderately linked to explanation |
| 8 | Thapliyal and Thapliyal, 2024 | ML across cybersecurity tasks | Review | Wider context for the field |
| 9 | Alshudukhi et al., 2025 | Lightweight XAI for real time defence | Review | Treats explanation as both tool and target |
| 10 | Bhandari, 2025 | AI in security, risks and governance | Review | Gains in speed alongside concerns of bias |
| 11 | Li et al., 2026 | AI powered defence against threats | Robust learning with attention | Joins robustness, privacy, and explanation |

When the three camps are compared, a pattern appears. The application studies treat an explanation as a benefit that improves transparency. The critical studies treat an explanation as something fragile that may mislead. The wider reviews accept both sides but speak in general terms. The hopeful view and the cautious view rarely meet inside the same study.

## Research Gap

Most existing work applies explainable methods to detect attacks such as malware and intrusion, while the prediction of software vulnerabilities has rarely been studied through an explainability lens. At the same time, the studies that question whether explanations can be trusted have formed a separate line of research from the studies that build prediction models. Because these two lines stay apart, the explanations behind strong prediction models are seldom tested for trust and robustness, and no reviewed study brings the two together for vulnerability prediction. This missing connection is the gap this study addresses.

## Conceptual Framework

The framework links four ideas. A vulnerability prediction on its own gives little transparency, because the model is a black box. When an explanation is added, transparency rises, because the analyst can see why the prediction was made. Higher transparency is expected to support higher trust, but only up to a point, since trust also depends on whether the explanation is reliable. Robustness therefore acts as a gate. If the explanation can be attacked or twisted, then transparency becomes misleading and trust is no longer justified. In short, explanation quality and robustness together decide whether transparency leads to real trust or only to the appearance of it.

The chain reads as follows: vulnerability prediction leads to an explanation, the explanation is shaped by quality and robustness, this gives transparency, and transparency leads to trust.

## Methodology

- **Research design:** a conceptual review of existing papers, with no new data and no human participants.
- **Data source:** eleven peer reviewed papers from 2022 to 2026, drawn from IEEE, MDPI, and Elsevier, along with other trusted venues.
- **Data collection:** for each paper, record its aim, method, explanation technique, security task, main findings, and limitations.
- **Analysis:** thematic analysis. Group the notes into the themes of prediction, explanation method, transparency, trust, and robustness, then compare within and across themes to build the framework.

## Expected Contribution

- **Theory:** a conceptual framework that joins two research lines, prediction and trust, which have so far stayed apart.
- **Practice:** clear guidance for security teams and tool designers on when an explanation can be trusted and when it may mislead.
- **Method:** a structured review and a comparison table that organise a scattered body of work into clear themes and offer a base for a later empirical study on real data such as the National Vulnerability Database.

## Ethical Considerations

This study uses only published academic sources, so it does not involve human participants, personal data, or sensitive information. The main duty is the responsible use of sources. Every source is read fairly and reported accurately, and every idea taken from another work is credited through correct citation. The reviewed papers may carry their own bias, for example by reporting mainly positive results, and the study keeps this in mind when drawing conclusions. The work also supports the responsible use of AI by promoting transparency and trust, which are ethical goals in security systems that affect people.

## About the Presentation

The final presentation has ten slides that move from my course work to my research proposal.

| Slide | Title | What it covers |
|-------|-------|----------------|
| 1 | Cover | Course, my name and ID, and the instructor |
| 2 | Roadmap | The plan: GitHub, proposal, and conclusion |
| 3 | Where My Code Lives | My profile, repo, portfolio, and a list of my assignments |
| 4 | Spotlight on Customer Segments | A deep dive into Assignment 5, the K Means segmentation project |
| 5 | The Proposal | My topic, why it matters, and the role of XAI |
| 6 | Research Question and Missing Piece | My main question and the research gap, shown as Figure 1 |
| 7 | Connecting the Dots | My methodology and my conceptual framework, shown as Figure 2 |
| 8 | Why It Matters, What Comes Next | The contribution of the research and its future |
| 9 | Conclusion | A short reflection that ties the course and the research together |
| 10 | Thank You | Closing slide for questions |

## Author

**Nusrat Jahan**
Portfolio: [nusratjahan73.github.io](https://nusratjahan73.github.io/)
Course: MBAI 5310G, AI Programming, Spring 2026
Instructor: Professor Zahra Atf
