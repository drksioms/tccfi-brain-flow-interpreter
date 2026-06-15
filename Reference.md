# Reference.md

# TCCFI / TCCS / TCD Brain Flow Interpreter

## Purpose

This file defines the evidence base and implementation rules used by the application.

The app is a bedside interpretation support tool.

The app must never make a definitive diagnosis.

---

# Evidence Levels

Level A

- Guidelines
- Consensus Statements
- Meta-analysis
- Systematic Review

Level B

- Prospective Cohort
- Multicenter Cohort

Level C

- Exploratory Physiology
- Feasibility Studies

When evidence conflicts, prioritize higher level evidence.

---

# SAH Module

Primary references

1. Hoh et al. Stroke 2023
DOI: 10.1161/STR.0000000000000436

2. Kumar et al. J Neurosurg 2016

3. Sviri et al. Neurosurgery 2006
DOI: 10.1227/01.NEU.0000223502.93013.6E

## Supported interpretation

MCA MFV ≥120 cm/s

AND

Lindegaard ratio ≥3

Output:

"Findings are compatible with vasospasm physiology."

Do not output:

"Patient has DCI."

---

Posterior circulation

BA MFV >85 cm/s

AND

BA/VA ratio >2.5

Output:

"Findings are compatible with posterior circulation vasospasm."

BA/VA ratio >3

Output:

"Findings suggest severe basilar vasospasm."

---

# TBI Module

Primary references

1. Robba et al. B-ICONIC 2025
DOI: 10.1007/s00134-024-07756-2

2. Depreitere et al. 2021
DOI: 10.1007/s12028-020-01185-x

3. Brasil et al. 2024
PMID: 37932509

## Supported interpretation

PI ≥1.3

and/or

EDV <20 cm/s

Output:

"Possible high distal resistance pattern."

"Possible low CPP pattern."

Do not output:

"ICP is elevated."

"ICP = xx mmHg"

---

# Brain Death Module

Primary references

1. Greer et al. Neurology 2023
DOI: 10.1212/WNL.0000000000207740

2. Reynolds et al. J Neuroimaging 2025
DOI: 10.1111/jon.70021

## Supported interpretation

Patterns

- Oscillating flow
- Reverberating flow
- Systolic spikes
- Signal disappearance

Output:

"Pattern compatible with cerebral circulatory arrest."

Do not output:

"Brain death confirmed."

Adult only.

---

# Stroke Module

Primary references

1. Antipova et al. Ultrasound Journal 2019
DOI: 10.1186/s13089-019-0140-8

Output:

"Findings may support large vessel occlusion."

Do not output:

"LVO excluded."

CTA remains the reference standard.

---

# PCAS/HIBI Module

Version:

0.2

## Supported interpretation

PCAS/HIBI interpretation must be based on serial trend and clinical context.

Do not use a single TCD/TCCFI/TCCS measurement to determine neurological prognosis.

Do not output:

- Favorable prognosis
- Poor prognosis
- Treatment recommendation

Supported classification:

- absolute supportive pattern
- trend favorable supportive
- trend concerning
- indeterminate
- research caution

Clinical context required for cautious interpretation:

- MAP
- EtCO2 or PaCO2
- Temperature management status
- Sedation level
- Vasopressor use
- Mechanical circulatory support
- Days after ROSC
- Previous MFV / PI / EtCO2 / MAP

## Supported outputs

Single-measurement absolute values may support physiologic pattern interpretation.

Do not use absolute values for neurological prognosis.

When PI is high and EDV is low:

"PI上昇とEDV低下は高末梢抵抗またはpossible low CPP patternに整合します。PCAS/HIBIではMAP、CO2、TTM、鎮静、循環補助の影響を強く受けるため慎重に解釈してください。"

Classification:

absolute supportive pattern

When MCA MFV is low:

"MCA MFV低値はlow flowまたはhypoperfusion patternの可能性を示唆します。低MAP、低CO2、深鎮静、TTM、循環補助条件を考慮してください。"

Classification:

absolute supportive pattern

When MCA MFV is high:

"MCA MFV高値はhyperemia、reperfusion、高CO2影響など複数の可能性を示唆します。単独で予後良好とは判定できません。"

Classification:

absolute supportive pattern

When EDV is preserved and PI is not high:

"EDVが保たれPI高値が目立たない所見はpreserved diastolic forward flowに整合します。ただしPCAS/HIBIでは単独で予後良好とは判定できません。"

Classification:

absolute supportive pattern

When previous MFV is missing:

"PCAS/HIBIでは単回測定値のみでの解釈は限定的です。serial trendでの評価を推奨します。"

Classification:

indeterminate

When MCA MFV is clearly lower than previous value:

"MCA MFV低下傾向は脳低灌流または循環・CO2条件変化に整合する可能性があります。MAP、EtCO2/PaCO2、鎮静、体温管理、循環補助の変化を確認してください。"

Classification:

trend concerning

When MCA MFV is higher than previous value:

"MCA MFV上昇傾向は脳血流速度の改善、hyperemia、CO2変化など複数の可能性があります。PCASでは時相依存性が大きく、単独で予後良好とは判定できません。"

Classification:

trend favorable supportive or indeterminate

When PI is high and EDV is low:

"PI上昇とEDV低下は高末梢抵抗または低CPPパターンに整合します。PCAS/HIBIでは循環動態、CO2、TTM、鎮静の影響を強く受けるため慎重に解釈してください。"

Classification:

trend concerning

When days after ROSC is 5-7 and PSV is high:

"一部研究ではday 5-7の高PSVと不良転帰の関連が報告されていますが、標準化された閾値ではありません。予後判定には使用しないでください。"

Classification:

research caution

## Required warnings

Warnings should be displayed for:

- EtCO2/PaCO2 missing
- MAP missing
- TTM active
- Rewarming
- Deep sedation
- VA-ECMO
- Previous values missing

---

# Research Features

Not for routine clinical decision making.

- nICP
- nCPP
- CPPopt
- MAPopt
- Autoregulation indices
- CO2 reactivity
- HITS/MES

Display as:

Research Use Only

---

# Universal Warnings

Interpretation reliability decreases when:

- Poor acoustic window
- Significant MAP changes
- Significant PaCO2 changes
- ECMO
- Non-pulsatile flow
- Decompressive craniectomy
- Uncertain vessel identification

---

# Required Disclaimer

This application is intended for clinical decision support and educational use.

It is not a medical device.

Final clinical decisions remain the responsibility of the treating clinician.

---

Created by Kosei Omasa
