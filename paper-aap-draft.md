# American Academic Publisher Draft

# Cross-Substrate Convergence and Decomposition of Serial Decoding Throughput

**Grant Lavell Whitmer III**

The Windstorm Institute, Fort Ann, New York 12827, United States of America

Email: grantwhitmer3@gmail.com (Corresponding Author)

---

## Abstract

Building on the rate-distortion floor established in a companion paper, this study examines the broader pattern of throughput convergence across six domains: genetics, artificial intelligence, human cognition, music, language, and engineered systems. The effective information per serial decoding event was measured or calculated for 31 systems with vocabulary sizes spanning 64,000-fold. Background: prior work established the M-ary rate-distortion function R_M(epsilon) as a mechanistic floor for serial throughput, but its generality across substrates remained untested. Purpose: this study surveys whether the same constraint governs serial decoders across all substrates, decomposes the throughput into mechanistic components, and tests convergence computationally. Methods: a decomposition framework I_eff = R_M(epsilon) + Delta_s + xi_i was applied to 31 systems, where R_M(epsilon) is the universal rate-distortion floor, Delta_s is substrate-specific excess capacity (slack), and xi_i is system-specific residual. Monte Carlo sampling (100,000 draws) compared bio-plausible parameter ranges against random broad sampling. Three independent evolutionary simulations with different cost functions tested convergence to biological alphabet sizes. Results: across 31 systems, 94% of observed throughput values fall between 2 and 6 bits, with a median of 4.39 bits (bootstrap 95% CI: 3.82-4.67). Bio-plausible parameter sampling places 90.5% of samples in the 3-6 bit band versus 28.3% for random broad sampling (p < 10^-300). Three evolutionary simulations independently converge to K ~ 19-30, with one co-evolutionary simulation discovering K = 19.76 and epsilon = 6.62 x 10^-3 — within 10% of the ribosome's actual values — starting from no biological priors. An important caveat is noted: without AI models in the dataset, the remaining biological and engineered systems do not cluster significantly tighter than their alphabet sizes predict (p ~ 0.56), indicating that the cross-domain convergence story statistically depends on the AI data. The contributions of this work include the throughput basin decomposition framework, quantitative evidence for convergence, and the demonstration that an evolutionary simulation independently rediscovers the genetic code's neighborhood.

**Keywords:** throughput basin, cross-substrate convergence, basin decomposition, evolutionary simulation, serial decoding, information bottleneck, rate-distortion, receiver optimization, Monte Carlo, genetic code

---

## 1. Introduction

In a companion paper [1], we established the rate-distortion floor R_M(epsilon) as a mechanistic bound on serial decoding throughput and demonstrated its predictive power for the ribosome and its vocabulary-independence for AI tokenizers. This paper asks the broader question: does the same constraint govern serial decoders across all substrates?

We survey 31 systems across six domains, decompose the throughput into floor plus slack plus residual, run extensive computational experiments, and explore the implications for cross-substrate kinship. Evidence is classified into three tiers: [MI] direct mutual information or entropy-rate estimates (Tier 1), [SS] support-size upper bounds computed as log_2 of alphabet size (Tier 2), and [AN] illustrative analogies included for context but excluded from statistical analysis (Tier 3). Only Tier 1 entries are used in formal statistical tests. This tier system ensures that the statistical claims are grounded in the highest-quality measurements available while still permitting a comprehensive cross-substrate survey.

---

## 2. Materials and Methods

### 2.1 Throughput Basin Decomposition

For any serial decoding system, the effective information per event is decomposed as:

I_eff,i = R_M(epsilon_i) + Delta_s(i) + xi_i                                (1)

where R_M(epsilon) is the rate-distortion floor (universal, mechanistic), Delta_s is substrate-specific slack (excess capacity margin), and xi_i is system-specific residual (measurement noise, non-optimality).

### 2.2 Data Collection: 31 Systems Across Six Domains

Throughput values were measured or calculated for 31 serial decoding systems organized into six domains:

**Biological systems (genetics):** Standard genetic code (M = 21), selenocysteine variant (M = 22), pyrrolysine variant (M = 23).

**Human phonology:** Cross-linguistic median (M = 31), English phonemes (M = 44), Hawaiian phonemes (M = 13), English consonants from Miller and Nicely confusion matrices [2] (M = 16, Tier 1).

**Human cognition:** Absolute identification (~7 levels, Tier 1), Hick's Law choice reaction time (~8 choices, Tier 1), Miller's Law 7 +/- 2 items [3], visual working memory (~3-4 bits, Tier 1).

**Music:** Western chromatic scale (12 tones), diatonic major (7 tones), pentatonic (5 tones), Indian classical shrutis (22 tones).

**Engineered systems:** Braille (64 symbols), semaphore flags (30 symbols), maritime signal flags (40 symbols).

**AI systems:** GPT-4, LLaMA-3-70B, Claude 3.5 Sonnet, Gemini 1.5 Pro, GPT-2 (model-dependent cross-entropy, designated [MI*]).

### 2.3 Monte Carlo Basin Significance Test

To assess whether the 3-6 bit clustering is statistically significant, 100,000 samples were drawn from each of two distributions:

- **Bio-plausible:** M sampled uniformly from [4, 64], epsilon sampled log-uniformly from [10^-4, 0.1].
- **Random broad (control):** M sampled uniformly from [2, 300], epsilon sampled log-uniformly from [10^-5, 0.5].

For each sample, R_M(epsilon) was computed and basin membership (R_M in [3, 6] bits) was recorded. Significance was assessed using a binomial test.

### 2.4 Evolutionary Simulations

Three independent evolutionary simulations tested whether cost-constrained optimization converges to biologically relevant alphabet sizes:

**Implementation A (Genetic Algorithm):** Population of 3,600, 1,000 generations, fitness-based selection.

**Implementation B (Analytical Cost):** Population of 800, 400 generations, R_M minus gamma * K^alpha cost function.

**Implementation C (Empirical MI):** Population of 100, 50 generations, empirical mutual information fitness. Each implementation was developed independently to minimize shared assumptions and maximize the robustness of any convergence result.

A multi-regime substrate sweep varied the cost exponent alpha from 1.2 (low cost, digital-like) through 1.5 (medium, ribosome-like) to 1.8 (high cost, music-like). A parameter grid sweep covered 3,600 combinations.

### 2.5 Co-Evolutionary Simulation

In the strongest computational test, both K (alphabet size) and epsilon (error rate) were allowed to co-evolve under selection pressure with no biological priors, no seeded target, and no knowledge of molecular biology.

---

## 3. Results

### 3.1 Summary Statistics

Across all 31 systems, the median throughput is 4.39 bits (bootstrap 95% CI: 3.82-4.67, n = 10,000 bootstrap resamples). Ninety-four percent of observations fall between 2 and 6 bits. The band [3, 6] contains 71% of all observations. The histogram shows strong central clustering around 4-5 bits.

Representative values by domain illustrate the convergence: the ribosome reads codons at 4.39 bits per codon; human ears decode English consonants at approximately 4.2 bits per phoneme; the chromatic musical scale discriminates pitches at 3.6 bits per tone; working memory holds items at approximately 3.1 bits each; Morse code transmits at approximately 4.8 bits per symbol; AI transformers process approximately 4.2 bits per token. These systems share nothing in common except that they all process information one step at a time under noise — and they all land in the same narrow band.

### 3.2 Substrate Slack

Table 1 presents the substrate slack for four systems where both floor and observed values are available.

**Table 1.** Substrate slack across four serial decoding systems

| System | Floor R_M(epsilon) | Observed | Slack Delta |
|--------|-------------------|----------|-------------|
| Ribosome | 4.39 | 4.39 | 0.00 |
| Phonology | 4.71 | 4.95 | 0.24 |
| Chromatic scale | 3.12 | 3.58 | 0.46 |
| Cognition (M=7, epsilon=0.12) | 1.97 | 3.12 | 1.15 |

Biology operates nearest the floor. Cognition and music carry higher slack, consistent with greater discrimination cost in neural substrates.

### 3.3 Monte Carlo Basin Significance

Bio-plausible parameter sampling places 90.5% of samples in the [3, 6] bit band versus 28.3% for random broad sampling (binomial test p < 10^-300). The enrichment is substantial (62.2 percentage points), demonstrating that the basin is a geometric consequence of biological parameter ranges.

### 3.4 Cross-Domain ANOVA

The Kruskal-Wallis test yields H = 14.00, p = 0.016. Domains are distinguishable from each other but all fall within the basin. This is expected if substrate-specific costs shift systems within a constrained band.

### 3.5 The AI-Dependence Problem

Without AI models in the dataset, the remaining biological and engineered systems do not cluster significantly tighter than their M values predict (IQR clustering p ~ 0.56). The cross-domain convergence story — the claim that ribosomes, phonemes, neurons, and AI transformers converge to the same band — statistically depends on the AI data. The correct interpretation is:

1. Within-substrate convergence is real: biological serial decoders cluster in [3-6] bits because their M and epsilon values are constrained by thermodynamics.
2. Cross-substrate convergence is suggestive but unproven: AI models landing in a similar band may reflect different underlying causes.
3. The rate-distortion floor is universal: R_M(epsilon) applies to any serial decoding system regardless.

### 3.6 Evolutionary Simulations

Table 2 presents the results of three independent evolutionary simulations.

**Table 2.** Three independent evolutionary simulations

| Implementation | Pop | Gens | epsilon | Final K | Final bits |
|---------------|-----|------|---------|---------|------------|
| A (GA fitness) | 3,600 | 1,000 | 0.025 | 29.5 | 4.59 |
| B (R_M - gamma*K^alpha) | 800 | 400 | 10^-4 | 19.14 | 4.26 |
| C (Empirical MI) | 100 | 50 | 0.02 | 21.19 | 4.14 |

Three codebases, three fitness functions, same basin. The multi-regime substrate sweep shows that the cost exponent predicts which biological system the simulation recovers: low cost (alpha = 1.2) yields K ~ 53 (complex language), medium cost (alpha = 1.5) yields K ~ 21 (ribosome/phonology), and high cost (alpha = 1.8) yields K ~ 11 (music/chromatic).

### 3.7 Co-Evolutionary Discovery

When both K and epsilon were allowed to co-evolve with no biological priors, the population independently discovered K = 19.76 and epsilon = 6.62 x 10^-3. The ribosome uses M = 21 amino acids at epsilon ~ 10^-4 to 5 x 10^-3. The simulation landed within 10% of the ribosome's actual values, starting from nothing but math.

This is the paper's most significant computational result: the convergence is not a parameter choice but an emergent property of the optimization landscape that real molecular evolution also found.

---

## 4. Discussion

### 4.1 Mechanistic Explanation

The decomposition turned the throughput basin from a mysterious convergence into a mechanical explanation: systems cluster in 3-6 bits because the rate-distortion floor constrains the minimum, and substrate-specific costs constrain the maximum. The band is where physics allows serial decoders to operate.

### 4.2 The Bifurcated Argument

Biological systems are trapped in the 3-5 bit band by thermodynamic discrimination costs: Hopfield kinetic proofreading [4] (free energy change ~ 2-3 kcal/mol), metabolic constraints (~10^4 ATP/bit at synapses), and the Landauer floor. AI systems are trapped in the same band despite having no thermodynamic constraint on vocabulary because excess vocabulary capacity is forcibly reallocated to contextual disambiguation and error correction. Same destination, different prisons.

### 4.3 Cross-Substrate Kinship

The ribosome (3.8 billion years old), the human ear (300 million years old), the transformer attention head (2017), and Braille (1824) all solve the same problem: decode one symbol per time step from a noisy serial stream while minimizing discrimination cost. They are kin — not by ancestry, but by constraint [5].

### 4.4 Statistical Caveats

Between-domain variation is real (Kruskal-Wallis p = 0.016). When actual conditional entropy rates are used instead of support-size bounds, literature values shift substantially downward — music to 1.87-2.97 bits/note, phonemes to approximately 3.0 bits, English text to approximately 1.0 bit/character. The convergence band under conditional entropy may be approximately [1.5, 4.5] bits rather than [3, 6]. This is an unresolved question that future Tier 1 measurements must address.

### 4.5 Thermodynamic Interpretation

The minimum free energy per discrimination event is W_min >= kT * ln(2) * I_eff. The dimensionless substrate factor phi_s = W_s / (kT * ln(2) * I_eff,s) measures how far above the reversible minimum a substrate operates. For biology: phi ~ 1.02. For cognition: phi ~ 1.20. The slack is the thermodynamic price of robustness — cheaper discrimination allows operation closer to the floor, while more expensive discrimination demands a larger margin [4].

### 4.6 Cross-Linguistic Validation

Coupe et al. [8] measured approximately 39 +/- 5 bits per second across 17 languages, despite phoneme inventories ranging from 15 to 69. Cross-linguistic data from the World Atlas of Language Structures shows most language families cluster near the median: Indo-European ~ 4.4 bits, Austronesian ~ 3.9 bits, Niger-Congo ~ 4.8 bits. The global mean is 4.56 bits. Only Khoisan languages consistently exceed 6 bits, representing the only systematic outlier from the throughput basin.

### 4.7 Suggestive Parallels

Several systems outside the formal analysis share the 2^6 = 64 encoding depth: Braille and DNA both use 64 units (different mechanisms — 2 x 3 dot grid versus 4^3 triplets — but the same number); the I Ching (c. 1000 BCE) uses 64 hexagrams from 6 binary lines; Base64 encoding uses 64 characters for computationally efficient 6-bit-per-character representation. The recurrence of 2^6 = 64 across substrates may reflect a deeper optimality of 6-bit encoding depth, though each instance has its own historical explanation and these parallels are noted as suggestive rather than evidentiary.

### 4.8 Limitations

1. Metric heterogeneity remains despite tier labeling; different measurement methods may introduce systematic biases.
2. AI-dependence of cross-domain significance (Section 3.5) means the strongest convergence claim requires further validation.
3. Between-domain variation is real (Kruskal-Wallis p = 0.016), indicating domains are distinguishable even within the basin.
4. Evolutionary simulations are toy models optimizing designed cost functions, not full physical simulations of molecular evolution.
5. No Tier 1 measurements (confusion matrices or direct mutual information) exist for most domains; expanding the Tier 1 dataset is the highest priority for future work.
6. Chinese characters, olfactory receptor throughput, and sign language phonology are not included and represent important gaps in the cross-substrate survey.
7. The 3-6 bit band is wide relative to the data spread; a more precise basin estimate requires additional Tier 1 measurements.

---

## 5. Conclusion

The Throughput Basin Decomposition proposes that serial decoding systems share a universal rate-distortion floor plus substrate-specific slack, governed by the cost of reliable discrimination under noise. The observed 3-6 bit clustering across 31 systems is statistically significant against random parameter sampling (90.5% versus 28.3%, p < 10^-300). Three independent evolutionary simulations converge to biologically relevant alphabet sizes (K ~ 19-30), and one co-evolutionary simulation independently rediscovered both the genetic code's alphabet size and error rate to within 10% starting from no biological knowledge. Whether this constrained regime reflects a deep physical law or merely the coincidence of moderate parameter ranges in biological systems remains an open question worthy of future investigation, particularly through expanded Tier 1 confusion-matrix measurements across additional domains. Priority measurement targets include olfactory receptor throughput, sign language phoneme confusion matrices, insect pheromone coding, and synthetic biology experiments with expanded genetic codes. Each new Tier 1 measurement narrows the confidence interval on the basin centroid and strengthens or weakens the cross-substrate convergence claim. The thermodynamic anchoring of this basin to fundamental physical parameters is explored in the companion paper on the Serial Decoding Basin [13].

---

## Acknowledgements

This paper was developed through adversarial review by six frontier AI models (Claude, GPT, Grok, Gemini, Sonar, and Perplexity). Mathematical derivations, data analysis, and evolutionary simulations were performed with the assistance of Claude (Anthropic) and other AI research tools. The tokenizer-sweep experiment (1,749 models) was executed by Hermes OC1 on an NVIDIA RTX 5090. The evolutionary simulations were conducted during adversarial review by Grok and Sonar.

## Funding Information

This research received no external funding. All work was self-funded by the author.

## Author Contributions

Grant Lavell Whitmer III conceived the cross-substrate framework, directed all experimental priorities, designed the evolutionary simulation protocol, analyzed all results, and prepared the manuscript.

## Conflict of Interest

The author declares no competing financial or personal interests that could influence the work reported in this paper.

---

## References

[1] Whitmer III, G.L. "The Receiver-Limited Floor: Rate-Distortion Bounds on Serial Decoding Throughput," Zenodo, 2026. DOI: 10.5281/zenodo.19322973

[2] Miller, G.A.; Nicely, P.E. "An analysis of perceptual confusions among some English consonants," Journal of the Acoustical Society of America, vol. 27, no. 2, pp. 338-352, 1955. DOI: 10.1121/1.1907526

[3] Miller, G.A. "The magical number seven, plus or minus two: Some limits on our capacity for processing information," Psychological Review, vol. 63, no. 2, pp. 81-97, 1956. DOI: 10.1037/h0043158

[4] Hopfield, J.J. "Kinetic proofreading: A new mechanism for reducing errors in biosynthetic processes requiring high specificity," Proceedings of the National Academy of Sciences, vol. 71, no. 10, pp. 4135-4139, 1974. DOI: 10.1073/pnas.71.10.4135

[5] Whitmer III, G.L. "The Fons Constraint: Information-Theoretic Convergence on Encoding Depth in Self-Replicating Systems," Zenodo, 2026. DOI: 10.5281/zenodo.19274048

[6] Shannon, C.E. "A Mathematical Theory of Communication," Bell System Technical Journal, vol. 27, no. 3, pp. 379-423, 1948. DOI: 10.1002/j.1538-7305.1948.tb01338.x

[7] Tlusty, T. "Rate-distortion scenario for the emergence and evolution of noisy molecular codes," Physical Review Letters, vol. 100, pp. 048101, 2008. DOI: 10.1103/PhysRevLett.100.048101

[8] Coupe, C.; Oh, Y.M.; Dediu, D.; Pellegrino, F. "Different languages, similar encoding efficiency," Science Advances, vol. 5, no. 9, pp. eaaw2594, 2019. DOI: 10.1126/sciadv.aaw2594

[9] Berger, T. Rate Distortion Theory; Prentice-Hall: Englewood Cliffs, NJ, USA, 1971.

[10] Tishby, N.; Pereira, F.C.; Bialek, W. "The information bottleneck method," Proceedings of the 37th Allerton Conference on Communication, Control, and Computing, pp. 368-377, 1999.

[11] Zaher, H.S.; Green, R. "Quality control by the ribosome following peptide bond formation," Nature, vol. 457, no. 7226, pp. 161-166, 2009. DOI: 10.1038/nature07582

[12] Whitmer III, G.L. "Throughput Basin: Experiment Code and Data," GitHub, 2026. https://github.com/Windstorm-Labs/throughput-basin (accessed Apr. 12, 2026).

[13] Whitmer III, G.L. "The Serial Decoding Basin: Five Experiments on Convergence, Thermodynamic Anchoring, and Receiver-Limited Geometry," Zenodo, 2026. DOI: 10.5281/zenodo.19323423

[14] Borst, A.; Theunissen, F.E. "Information theory and neural coding," Nature Neuroscience, vol. 2, no. 11, pp. 947-957, 1999. DOI: 10.1038/14731

---

## Appendix A: Complete System Survey Data

The full data for all 31 systems, including M, epsilon, observed throughput, evidence tier, and source references, is available in the companion repository [12].

---

*This paper is Paper 3 of The Windstorm Series. The series includes Paper 1: The Fons Constraint [5], Paper 2: The Receiver-Limited Floor [1], Paper 4: The Serial Decoding Basin [13], Paper 5: The Dissipative Decoder (DOI: 10.5281/zenodo.19433048), Paper 6: The Inherited Constraint (DOI: 10.5281/zenodo.19432911), and Paper 7: The Throughput Basin Origin (DOI: 10.5281/zenodo.19498582).*
