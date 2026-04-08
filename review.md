# **_Skepthical_** review: *Quantifying Endogenous Investment Dynamics and Policy Moderators of Convergence Speed*

## Summary

The paper proposes a two-stage empirical framework to separate (i) endogenous determinants of investment (levels/steady states) from (ii) policy-related moderators of the speed of convergence in capital accumulation (transition dynamics). Using a synthetic panel of 50 countries over 1990–2019 generated from a structural Cobb–Douglas growth model (Sec. 2.1), the first stage estimates an income–investment relationship with country fixed effects (Eq. (3); Secs. 2.2, 3.1) and uses the implied investment behavior together with an estimated depreciation rate to construct an (implied) country–time steady-state capital stock and a log distance-to–steady-state measure (Eq. (4)). The second stage estimates a moderated transition/convergence regression of capital growth on the distance to steady state and its interaction with policy variables (trade openness, government expenditure), described as an IV model to address endogeneity of the interaction terms (Secs. 2.3, 3.2; Table 1; Fig. 1).

Conceptually, the decomposition into “level effects” (through investment/steady states) versus “speed effects” (through policy–gap interactions) is appealing and could be useful in applied growth work. However, the current draft falls short of being a convincing validation exercise because core components are not internally consistent (e.g., System GMM claims vs. fixed-effects implementation), the synthetic DGP and IV identification are under-documented, and the key advantage of synthetic data—recovering known parameters with controlled Monte Carlo evidence—is not exploited. In addition, the two-stage construction creates a generated-regressor problem (the gap depends on first-stage predictions), and the steady-state construction requires clearer derivation under Cobb–Douglas. Addressing these issues would substantially strengthen the paper’s methodological credibility and clarify what exactly is learned from the synthetic setting and what would generalize to real data.

## Strengths

- Clear motivation: disentangling determinants of investment levels from moderators of convergence speed is a relevant question in growth empirics (Sec. 1).
- The two-stage structure aligns well with growth theory: an estimated investment function feeds into an implied steady state, which then enters a transition equation (Secs. 2.2–2.3).
- Using synthetic data generated from a known structural model is an appropriate design choice for method validation (Sec. 2.1).
- The transition regression is written in an economically interpretable way: distance to steady state has the expected sign and can be mapped to a convergence rate (Sec. 3.2; Eq. (5)).
- Figure 1 (trade openness panel) aims to translate interaction terms into marginal effects at policy percentiles, which is a good practice for interpretability.
- The manuscript is generally readable and logically organized from motivation to method to results (Secs. 1–4).

## Major issues

1.  **Internal inconsistency on the first-stage estimator: the Abstract/Introduction state that a dynamic System GMM approach is used to capture endogenous feedback/persistence in investment (Sec.** 1), but the Methods/Results present only a static fixed-effects regression of ln(s_{i,t}) on ln(y_{i,t}) (Eq. (3); Secs. 2.2, 3.1), with no lagged dependent variable, no GMM instrument strategy, and no GMM diagnostics. This undermines a central methodological claim (handling endogeneity/dynamics in investment) and makes it hard to interpret what the framework is actually validating.
    
    *Recommendation:* Make the narrative and implementation consistent. Either: (i) implement the dynamic System GMM version of Eq. (3) explicitly (e.g., include ln(s_{i,t-1})), fully document instrument sets/lag structure in Sec. 2.2, and report standard diagnostics (AR(1)/AR(2), Hansen/Sargan) in Sec. 3.1; or (ii) remove/modify System GMM claims in the Abstract/Sec. 1 and justify why FE is the intended estimator in this synthetic validation (including a brief discussion of simultaneity and why it does/does not matter under the DGP). Ideally, include FE vs. GMM as a robustness comparison if endogeneity is part of the motivation.

2.  **Synthetic DGP is under-specified, preventing meaningful validation against “known truth.” Sec.** 2.1 does not provide the explicit equations and parameter values (production function, α, δ, technology/population growth, shock processes, cross-country heterogeneity), nor does it clearly state how trade openness and government expenditure are generated and whether they affect steady states (levels) and/or convergence speed (transition). Sec. 3 does not compare estimated parameters (γ1, δ, β1, β2) to their true DGP values, which is the key advantage of synthetic data.
    
    *Recommendation:* Expand Sec. 2.1 (or add a dedicated Appendix) with full DGP documentation: write down the Cobb–Douglas production function and laws of motion, list parameter values and shock processes (including persistence/cross-country heterogeneity), and specify exactly how policy variables are generated and where they enter the true model (investment/steady state vs. speed). Then, in Sec. 3, add a validation subsection reporting true vs. estimated values (with bias and uncertainty) for γ1, δ, β1, β2. This should be presented as the main methodological deliverable, not a side note.

3.  **Lack of Monte Carlo evidence: results appear to be based on a single synthetic draw, so statistical significance (e.g., the 10% trade openness interaction in Sec.** 3.2) is hard to interpret as method performance rather than sampling luck. In a validation paper, single-sample p-values are much less informative than bias/RMSE/coverage across repeated simulations.
    
    *Recommendation:* Add a Monte Carlo section: repeat the full two-stage procedure many times under the same DGP and report distributions for γ1, δ, β1, β2 (bias, RMSE, coverage of nominal 95% CIs, and rejection rates under null moderation). Include scenarios where true moderation is zero vs. nonzero for each policy variable (trade openness/government expenditure) to quantify Type I/II error and power. Reframe the empirical claims in Sec. 4 in terms of estimator performance rather than one-off significance.

4.  **IV identification for the moderated transition model is not described, making β2 difficult to trust.** Sec. 2.3 labels Eq. (5) as an IV regression to handle endogeneity of D_{i,t}×Policy_{i,t}, and Table 1 reports IV estimates, but the paper does not specify (a) which regressors are treated as endogenous (interaction only vs. also D and Policy levels), (b) what instruments are used and how constructed from the DGP, (c) first-stage results and weak-IV diagnostics, or (d) overidentification tests. Also, Table 1 reports items (e.g., “Adj. R-squared”) whose meaning depends on the exact IV routine used.
    
    *Recommendation:* In Sec. 2.3, explicitly list endogenous regressors and instruments for D_{i,t}, Policy_{i,t}, and D_{i,t}×Policy_{i,t} (e.g., lags, exogenous shifters from the DGP, or constructed instruments like D×Z where Z instruments Policy). State whether estimation is 2SLS or IV-GMM and how SEs are computed. In Sec. 3.2/Table 1, report first-stage coefficients, partial R², Kleibergen–Paap (or analogous) F-statistics, and overidentification tests where applicable; adjust reported fit statistics to those appropriate for the estimator (or explain them). If the DGP implies exogeneity for some variables, say so and justify a non-IV baseline alongside the IV specification.

5.  **Generated-regressor and two-stage inference problem: D_{i,t} is constructed using \hat{s}_{i,t} from the first stage (Secs.** 2.2–2.3; Eqs. (3)–(4)), making the second-stage regressor a function of estimated parameters and potentially shared shocks. Standard IV/OLS SEs in the second stage may understate uncertainty, and mechanical dependence of D_{i,t} on y_{i,t} (and fixed effects) can blur interpretation of “speed” versus “level” channels.
    
    *Recommendation:* Address two-stage inference explicitly. At minimum, bootstrap the entire pipeline (first-stage estimation → K^* construction → D computation → second-stage IV) and report bootstrap SEs/CIs in Sec. 3.2. Also add a robustness check constructing D_{i,t} using the true s_{i,t} from the DGP (or using observed s_{i,t} rather than \hat{s}_{i,t}) to quantify how first-stage estimation error affects β1 and β2. If feasible, discuss (or implement) a joint estimation approach as an alternative.

6.  **Ambiguity/possible inconsistency in the steady-state construction under Cobb–Douglas.** Sec. 2.3 defines K^*_{i,t} via s_{i,t}Y_{i,t} = δK^*_{i,t}, apparently using observed Y_{i,t}. But in a Cobb–Douglas model Y depends on K, so a steady state typically requires evaluating Y at K^* (a fixed-point condition). Without a derivation, it is unclear whether K^*_{i,t} is a structural steady state, an ‘implied’ accounting steady state, or a shortcut inconsistent with the stated DGP.
    
    *Recommendation:* Provide a clear derivation in Sec. 2.3 (or Appendix): either (i) explicitly define K^*_{i,t} as an “implied steady state” holding Y fixed at observed Y_{i,t} and justify why this is the target estimand, or (ii) derive the structural steady state under Cobb–Douglas (solve s·Y(K^*) = (δ+g+n)K^* with the appropriate growth terms) and implement that version. Clarify whether you use s_{i,t} or \hat{s}_{i,t}, and whether technology/labor are treated as fixed or evolving in the steady-state expression.

7.  **Timing/indexing is inconsistent across equations and affects interpretation of convergence speed.** Eq. (1) uses K_{i,t+1}; Eq. (2) defines Δln(K_{i,t+1}) using period-t objects; Eq. (5) uses Δln(K_{i,t}) with unclear dating of D_{i,t} and Policy_{i,t}. The text interprets β1 as “closing ~35% of the gap per period” without clearly stating the time unit (annual 1990–2019) or mapping to standard convergence metrics (e.g., half-life).
    
    *Recommendation:* Standardize timing across Secs. 2.1–2.3: define Δln(K_{i,t}) ≡ ln(K_{i,t})−ln(K_{i,t−1}) (or the forward version) and date D and Policy consistently (typically t−1 on the RHS for a t growth rate). State explicitly that the panel is annual and interpret β1 accordingly; optionally report implied half-life (ln(2)/β) for the baseline and at selected policy percentiles. Ensure Table 1 and Fig. 1 match the chosen timing.

8.  **Separation of “level” vs “speed” effects is asserted but not demonstrated.** If policy variables affect investment/savings (level channel) in the DGP (or in real data), omitting policy from the first-stage investment function (Eq. (3)) can shift policy variation into the second stage and confound moderation (β2) with misspecified steady states. Conversely, if the maintained restriction is that policy affects only speed, the paper should state and verify this against the DGP.
    
    *Recommendation:* Make the maintained restriction explicit: do trade openness and/or government expenditure affect investment/steady states in the DGP, or only convergence speed? Then demonstrate the separation empirically: (i) include policy variables (and possibly their interactions) in the first-stage investment regression as a robustness check, (ii) recompute K^* and D, and (iii) show how β2 changes. In the Monte Carlo, add scenarios where policy affects levels only, speed only, both, or neither, to show when the two-stage approach correctly attributes channels.

9.  **External relevance is not yet established: the paper remains largely inside the synthetic environment, with limited guidance for real-data implementation (Sec.** 4). Practical obstacles—capital stock measurement, depreciation estimation, policy endogeneity, structural breaks, shorter/noisier panels—are not discussed in a way that would help applied researchers adopt the framework.
    
    *Recommendation:* Strengthen Sec. 4 with a concrete implementation roadmap for real data: data sources (e.g., Penn World Table, WDI), how to construct K and δ (perpetual inventory vs. provided series), how to handle measurement error and policy endogeneity, and what instrument strategies might be plausible outside a synthetic DGP. If feasible, add a short illustrative empirical application (even a minimal replication on a standard dataset) to demonstrate feasibility; otherwise clearly scope the paper as a simulation-validation study and articulate what remains before applied use.

## Minor issues

1.  Depreciation rate δ is mentioned as “estimated” (Sec. 2.1) but the estimator is not shown and results are not reported. Because δ directly affects K^* and thus D_{i,t}, it is important for both stages.
    
    *Recommendation:* In Sec. 2.1, provide the exact estimating equation/procedure for δ (and any assumptions). In Sec. 3, report δ̂ with SE (and true δ from the DGP) and briefly quantify sensitivity of β1/β2 to δ (e.g., recompute using true δ vs estimated δ).

2.  Policy variable definitions/scaling are unclear (Secs. 2.1, 2.3, 3.2). The text/figure suggest standardized measures (e.g., *_std), but the paper does not clearly define whether policies are ratios to GDP, logs, or z-scores, and whether they are mean-centered (which matters for interpreting β1 in the presence of interactions).
    
    *Recommendation:* Define trade openness and government expenditure precisely (construction, units, transformations) in Sec. 2.1 or 2.3. State explicitly whether they are standardized/mean-centered in Eq. (5) and Table 1, and interpret β2 in meaningful units (e.g., effect of a 1 SD increase in openness on the convergence slope).

3.  Figure 1 and accompanying text/caption are inconsistent: caption/text refer to two panels (trade openness and government expenditure) but only one appears; uncertainty (CIs) is not shown; and the plotted object (bars) makes it hard to connect to the underlying marginal effect formula.
    
    *Recommendation:* Either add the missing government expenditure panel or revise the caption/text to match what is shown. Plot the implied marginal effect ∂ΔlnK/∂D = β1 + β2·Policy at selected percentiles with 95% CIs (error bars or interaction plot with ribbons). Clearly state the percentile values used and whether policies are standardized.

4.  Sample size/accounting inconsistency: 50 countries over 1990–2019 suggests 1500 level observations, but growth/lag constructions typically reduce the sample (e.g., to 1450). Table 1 reports 1500 observations, creating confusion about whether differencing/lagging was applied and what years are included.
    
    *Recommendation:* Reconcile the observation counts by stating the exact sample window used in each regression (levels vs growth), which years are dropped due to lags/differences, and whether the panel is balanced after transformations. Update Table 1 notes accordingly.

5.  Interpretation of the baseline convergence coefficient β1 may be incomplete when interactions are included. The statement “~35% of the gap closes per period holding policy at its mean” is only correct if Policy is centered or if the speed is evaluated explicitly at the sample mean; otherwise, the relevant slope is β1 + β2·Policy (Sec. 3.2).
    
    *Recommendation:* Explicitly report the convergence slope at Policy = mean (and at key percentiles) using β1 + β2·Policy, and state whether Policy is mean-centered. Consider reporting implied half-lives at these values.

6.  The mapping from the accumulation identity (Eq. (1)) and log-linear approximation (Eq. (2)) to the regression form in Eq. (5) is not shown, which makes it harder to understand what assumptions justify linearity in D_{i,t} and the role of δ and other growth terms.
    
    *Recommendation:* Add a short derivation (main text or Appendix) linking Eq. (1)/(2) to Eq. (5), clarifying what is approximated/held constant and how D_{i,t} enters. This can be brief but should make the econometric specification feel grounded in the model.

7.  Table 1 reports “Adj. R-squared” and z-statistics in an IV context without clarifying the exact estimator/routine (2SLS vs IV-GMM) and how those statistics are computed/interpreted for the chosen method (Sec. 3.2).
    
    *Recommendation:* State the estimator explicitly (2SLS or IV-GMM), the covariance estimator (clustered by country, etc.), and adjust reported fit/diagnostic statistics to those standard for the estimator (or explain how the reported values are defined).

8.  Notation and measurement units are occasionally unclear: y_{i,t} is described as GDP per capita while Y_{i,t} appears as total output, and it is not clear whether K_{i,t} and Y_{i,t} are aggregate or per-capita/per-worker throughout (Secs. 2.1–2.3).
    
    *Recommendation:* Add a notation/definitions paragraph clarifying whether variables are aggregate or per-capita (and keep the accumulation equation consistent with that choice). Use consistent symbols for fixed effects and error terms across Eqs. (3) and (5) or explicitly distinguish them.

## Very minor issues

1.  Minor formatting/typographical issues reduce polish: mid-word line breaks (e.g., “struc\n\ntural” in Sec. 2.1), inconsistent heading formatting (e.g., a stray “# 3.2”), and small inconsistencies in Table 1 formatting.
    
    *Recommendation:* Proofread and standardize formatting: fix line breaks, harmonize heading styles/numbering, and align table columns/notes consistently.

2.  Some phrasing is informal or verbose in the Introduction/Conclusions (Secs. 1, 4), and figure captioning is somewhat repetitive (Sec. 3.2).
    
    *Recommendation:* Tighten language to a neutral academic tone (e.g., replace metaphors like “journey” with “convergence”) and streamline Figure 1 caption/text to avoid repeating the same explanations.

3.  Figure styling/accessibility: abbreviations like “SS” may be unclear; colors lack a legend and may not be color-blind safe; fonts may be small for print.
    
    *Recommendation:* Spell out “steady state,” add a legend (or direct labels) and use a color-blind–safe palette, and increase font size/resolution for publication readability.


## Mathematical consistency audit

This section audits **symbolic/analytic** mathematical consistency (algebra, derivations, dimensional/unit checks, definition consistency).

**Maths relevance:** light

The paper uses a small set of central equations: a capital accumulation identity, a first-stage log-linear investment-rate regression, a steady-state capital condition used to construct a log 'distance to steady state', and a second-stage moderated convergence regression with interaction terms. The main mathematical risks are specification mismatches (narrative vs equations), ambiguous steady-state construction under Cobb–Douglas, and inconsistent timing/standardization assumptions that affect interpretation.

### Checked items

1.  ✔ **Capital accumulation identity** (Eq. (1), Sec. 2.1, p.3)
    
    - **Claim:** Capital next period equals undepreciated capital plus investment: Ki,t+1 = (1−δ)Ki,t + Ii,t.
    - **Checks:** symbol/definition consistency, dimensional/units consistency
    - **Verdict:** PASS; confidence: high; impact: moderate
    - **Assumptions/inputs:** δ is the depreciation rate (0≤δ≤1 implied but not stated)., Ii,t is gross investment in the same units as K.
    - **Notes:** Equation is internally consistent as a definitional law of motion; units match (K and I in capital units).

2.  ✔ **From accumulation to log-growth approximation** (Eq. (2), Sec. 2.1, p.3)
    
    - **Claim:** Assuming I = sY, the (approximate) log growth of capital is Δln(Ki,t+1) ≈ si,t·Yi,t/Ki,t − δ.
    - **Checks:** algebra between shown steps, dimensional/units consistency, sanity/limiting cases
    - **Verdict:** PASS; confidence: medium; impact: moderate
    - **Assumptions/inputs:** Investment is a fraction si,t of output: Ii,t = si,t Yi,t., Small-change approximation: Δln(K) ≈ (K_{t+1}−K_t)/K_t.
    - **Notes:** Starting from K_{t+1}−K_t = −δK_t + s_t Y_t gives (K_{t+1}−K_t)/K_t = s_t Y_t/K_t − δ. This matches Eq. (2) up to the stated approximation. If s=0, predicted log-growth ≈ −δ (reasonable).

3.  ✖ **First-stage investment-rate equation vs described 'dynamic System GMM'** (Eq. (3), Sec. 2.2, p.3; Abstract & Sec. 1–2 narrative, pp.1–2)
    
    - **Claim:** Investment rate is modeled as ln(si,t) = γ0 + γ1 ln(yi,t) + μi + ϵi,t and estimated to quantify endogenous investment; the paper also states this is done with System GMM and a dynamic specification with lag dependence.
    - **Checks:** symbol/definition consistency, derivation/specification consistency
    - **Verdict:** FAIL; confidence: high; impact: critical
    - **Assumptions/inputs:** si,t is an investment rate (share), yi,t is GDP per capita., Fixed effects μi are time-invariant country heterogeneity.
    - **Notes:** Eq. (3) is a static fixed-effects regression and contains no lagged dependent variable, contradicting the claimed 'dynamic function of its own lag' and 'System GMM' estimation described in the abstract/introduction. This is a specification inconsistency central to constructing Ŝi,t and thus K*i,t and Di,t.

4.  ⚠ **Steady-state capital condition** (Sec. 2.3, p.3–4 (text preceding Eq. (4)))
    
    - **Claim:** Steady-state capital stock K*i,t is defined by si,t Yi,t = δK*i,t.
    - **Checks:** algebra/logic from Eq. (1), definition consistency
    - **Verdict:** UNCERTAIN; confidence: medium; impact: critical
    - **Assumptions/inputs:** Steady state defined as investment equals depreciation (net change in K is zero)., Ii,t = si,t Yi,t.
    - **Notes:** From Eq. (1), a steady state with K_{t+1}=K_t implies I=δK, so sY=δK is logically consistent. However, the paper states the data are generated from a Cobb–Douglas production function (Y depends on K). In that case, a steady state requires the fixed-point condition s·Y(K*) = δK*, not s·(observed Y_t) = δK*. The paper does not specify whether Yi,t is evaluated at K*i,t or taken as observed, nor does it show the computation of K*i,t.

5.  ✔ **Distance-to-steady-state definition** (Eq. (4), Sec. 2.3, p.4)
    
    - **Claim:** Define the convergence gap as Di,t = ln(K*i,t) − ln(Ki,t).
    - **Checks:** symbol/definition consistency, dimensional/units consistency
    - **Verdict:** PASS; confidence: high; impact: moderate
    - **Assumptions/inputs:** K*i,t and Ki,t are strictly positive.
    - **Notes:** A log gap is dimensionless; positive Di,t indicates K below K*. Requires K, K*>0 (reasonable for capital).

6.  ✔ **Moderated transition (convergence) regression** (Eq. (5), Sec. 2.3, p.4)
    
    - **Claim:** Capital growth depends on the gap and an interaction with policy: Δln(Ki,t) = β0 + β1 Di,t + β2(Di,t×Policyi,t) + νi + ηi,t.
    - **Checks:** dimensional/units consistency, symbol/definition consistency, sanity/limiting cases
    - **Verdict:** PASS; confidence: medium; impact: moderate
    - **Assumptions/inputs:** Δln(Ki,t) is a one-period log change (timing not explicitly defined)., Policyi,t is either trade openness or government expenditure share.
    - **Notes:** All regressors are dimensionless (log gap; policy shares/ratios; interaction), consistent with Δln(K). Sanity: if Di,t=0 then gap-driven term is zero; remaining predicted growth is β0+νi, which may or may not align with the conceptual notion of 'steady state' unless β0 is constrained/near 0 (not discussed).

7.  ⚠ **Time-indexing coherence across Eqs. (1)–(2) vs Eq. (5)** (Eqs. (1)–(2) Sec. 2.1 p.3; Eq. (5) Sec. 2.3 p.4)
    
    - **Claim:** The paper uses Δln(Ki,t+1) in Eq. (2) and Δln(Ki,t) in Eq. (5) without clarifying the timing convention.
    - **Checks:** notation consistency
    - **Verdict:** UNCERTAIN; confidence: high; impact: moderate
    - **Assumptions/inputs:** Δln(Ki,t) could mean ln(Ki,t)−ln(Ki,t−1) or ln(Ki,t+1)−ln(Ki,t).
    - **Notes:** The lack of a stated convention prevents verifying that the right-hand-side variables (Di,t, Policyi,t) are correctly dated relative to the dependent variable. This is fixable by defining Δ explicitly and aligning indices.

8.  ⚠ **Interpretation of convergence coefficient as '% of gap closed'** (Sec. 3.2, p.5 (text interpreting Table 1))
    
    - **Claim:** With β1=0.348, a country closes ~35% of the log gap to steady state per period, holding policy variables at their mean.
    - **Checks:** algebra/interpretation consistency
    - **Verdict:** UNCERTAIN; confidence: medium; impact: minor
    - **Assumptions/inputs:** The marginal effect of Di,t on Δln(Ki,t) is β1 + β2·Policyi,t., Policy is at its mean; if Policy is standardized to mean 0, marginal effect at mean equals β1.
    - **Notes:** Because Eq. (5) includes an interaction term, the gap-closure rate depends on Policy: ∂ΔlnK/∂D = β1 + β2·Policy. The statement using β1 alone is only exact if Policy is mean-centered/standardized to have mean 0 (hinted by figure labels with '_std' but not clearly stated for Table 1).

### Limitations

- Only the provided PDF text/pages were available; no appendices or supplemental derivations (e.g., the synthetic data-generating model details, Cobb–Douglas parameterization, or explicit K* computation) were provided to verify omitted steps.
- The paper references instrumental-variable handling of interaction terms but does not specify instruments or first-stage equations, preventing analytic verification of identification/orthogonality conditions (treated as out-of-scope empirically, but still a missing symbolic specification).
- Figures/tables are used for interpretation, but the audit does not validate numerical estimates and treats statistical output only for algebraic/interpretive consistency.


## Numerical results audit

This section audits **numerical/empirical** consistency: reported metrics, experimental design, baseline comparisons, statistical evidence, leakage risks, and reproducibility.

One structural consistency check indicates a potential mismatch between the stated panel structure (50 countries over 1990–2019) and the reported observation count under common transformations (p.2; p.5 Table 1). All other intended numerical recomputations (z-statistics, p-values, and rounding-based interpretation) were not executed due to an error, so no PASS/FAIL determinations are made for those items.

### Checked items

1.  ✖ **C1_panel_size_observations** (p.2 (Dataset and model specification) and p.5 Table 1 (Observations))
    
    - **Claim:** Dataset described as 50 countries over 1990–2019; Table 1 reports 1500 observations.
    - **Checks:** panel_dimensions_vs_reported_observations
    - **Verdict:** FAIL
    - **Notes:** Balanced panel in levels gives 50×(2019−1990+1)=50×30=1500, matching Table 1; however, the Methods include a one-period change term (∆ ln(Ki,t+1) in Eq. (2), p.3), which would typically reduce a balanced sample to 50×29=1450. The reported 1500 is therefore inconsistent with a universally applied one-period differencing/lag structure unless additional clarification is provided.

2.  ⚠ **C2_z_stat_distance_to_ss** (p.5 Table 1, row: Distance to SS (Di,t))
    
    - **Claim:** Table reports Coef.=0.348, Std. Err.=0.015, z=23.16 for Distance to SS.
    - **Checks:** z_stat_equals_coef_div_se
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

3.  ⚠ **C3_z_stat_trade_interaction** (p.5 Table 1, row: Di,t× Trade Openness)
    
    - **Claim:** Table reports Coef.=0.022, Std. Err.=0.013, z=1.74 for Di,t×Trade Openness.
    - **Checks:** z_stat_equals_coef_div_se
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

4.  ⚠ **C4_z_stat_gov_interaction** (p.5 Table 1, row: Di,t× Gov. Expend.)
    
    - **Claim:** Table reports Coef.=0.016, Std. Err.=0.015, z=1.06 for Di,t×Gov. Expend.
    - **Checks:** z_stat_equals_coef_div_se
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

5.  ⚠ **C5_p_value_distance_to_ss_from_z** (p.5 Table 1, row: Distance to SS (Di,t))
    
    - **Claim:** Table reports z=23.16 and p-value <0.001 for Distance to SS.
    - **Checks:** two_sided_p_value_from_z
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

6.  ⚠ **C6_p_value_trade_interaction_from_z** (p.5 Table 1, row: Di,t× Trade Openness)
    
    - **Claim:** Table reports z=1.74 and p-value=0.082 for Di,t×Trade Openness.
    - **Checks:** two_sided_p_value_from_z
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

7.  ⚠ **C7_p_value_gov_interaction_from_z** (p.5 Table 1, row: Di,t× Gov. Expend.)
    
    - **Claim:** Table reports z=1.06 and p-value=0.289 for Di,t×Gov. Expend.
    - **Checks:** two_sided_p_value_from_z
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

8.  ⚠ **C8_approx_35_percent_from_beta1** (p.5 Results text under Table 1; also p.7 Conclusions)
    
    - **Claim:** Text interprets coefficient on Di,t of 0.348 as closing approximately 35% of the logarithmic gap each period.
    - **Checks:** rounding_percent_interpretation
    - **Verdict:** UNCERTAIN
    - **Notes:** Not recomputed due to execution error.

### Limitations

- Only the provided parsed PDF text was used; no external datasets or internet sources were consulted.
- Several statistical claims (e.g., γ1 p-value, adjusted R-squared details) lack sufficient accompanying numeric components (standard errors, df, sums-of-squares) to allow recomputation.
- Figure-based quantitative checks are excluded because they would require extracting numeric values from plot imagery.
- Sandbox policy violation: from-import of 'typing' is not allowed
