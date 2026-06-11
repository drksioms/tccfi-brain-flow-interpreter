# DataDictionary.md

# TCCFI / TCCS / TCD Brain Flow Interpreter

## Purpose

Defines all variables used by the application.

Units, validation rules, calculations and interpretation dependencies are specified here.

---

# Patient Context

## Disease Category

Field:

diseaseCategory

Type:

string

Required:

Yes

Allowed Values:

- SAH
- TBI
- PCAS_HIBI
- AIS_LVO
- BrainDeathAdult
- GeneralICU

---

# Acquisition Information

## Modality

Field:

modality

Type:

string

Required:

Yes

Values:

- TCD
- TCCFI
- TCCS

---

## Acoustic Window

Field:

window

Type:

string

Required:

Yes

Values:

- transtemporal
- transorbital
- suboccipital
- submandibular

---

## Vessel

Field:

vessel

Type:

string

Required:

Yes

Values:

- MCA
- ACA
- PCA
- TerminalICA
- BA
- VA
- OphthalmicArtery
- CarotidSiphon

---

## Side

Field:

side

Type:

string

Required:

Yes

Values:

- Left
- Right
- Midline

---

## Angle Correction

Field:

angleCorrection

Type:

boolean

Required:

No

---

## Vessel Identification Confidence

Field:

vesselConfidence

Type:

string

Required:

Yes

Values:

- High
- Moderate
- Low

Low should trigger warning.

---

# Hemodynamic Variables

## MAP

Field:

map

Type:

number

Unit:

mmHg

Required:

Optional

Warning:

If missing, display:

MAP未入力のため、低灌流・高抵抗パターンの解釈は限定的です。

If MAP <65, display:

低MAPでは低CPP/低灌流パターンの可能性があり、TCD/TCCFI所見の解釈に注意が必要です。

Range:

20-200

---

## PaCO2

Field:

paco2

Type:

number

Unit:

mmHg

Required:

Optional

Priority:

If both PaCO2 and EtCO2 are entered, PaCO2 is preferred for display.

Warning:

PaCO2 <35 should trigger low CO2 warning.

PaCO2 >45 should trigger high CO2 warning.

Range:

15-100

---

## EtCO2

Field:

etco2

Type:

number

Unit:

mmHg

Required:

Optional

Priority:

EtCO2 is used as CO2 context when PaCO2 is not entered.

If neither EtCO2 nor PaCO2 is entered, display:

EtCO2未入力のため、CO2変化による脳血流速度への影響を評価できません。

Warning:

EtCO2 <30 should trigger low CO2 warning.

EtCO2 >50 should trigger high CO2 warning.

Range:

5-80

---

## ICP

Field:

icp

Type:

number

Unit:

mmHg

Required:

Optional

Input Rule:

Enter only when a measured ICP value exists.

Do not estimate ICP from TCD/TCCFI/TCCS in the current version.

Display:

実測ICP: xx mmHg

Warning:

If the user enters ICP and PI is high, display:

PI高値と実測ICPの整合性を確認してください。PI単独でICPを推定しないでください。

---

## CPP

Field:

cpp

Type:

number

Unit:

mmHg

Required:

Optional

Input Rule:

Enter only when measured CPP or clinically calculated CPP is available.

Do not estimate CPP from TCD/TCCFI/TCCS in the current version.

Display:

実測/算出CPP: xx mmHg

Reference Calculation:

If MAP and measured ICP are entered and CPP is not entered, reference CPP may be displayed as:

参考CPP = MAP - 実測ICP

This is not an automatic CPP estimate from TCD/TCCFI/TCCS.

---

# Clinical Context Rules

MAP, EtCO2/PaCO2, ICP and CPP are clinical context variables.

ICP and CPP must not be used as primary interpretation logic in the current version.

CO2 and MAP confounding must be reflected in warnings.

TCD/TCCFI/TCCS alone cannot confirm ICP or CPP.

---

# PCAS/HIBI Variables

These variables are used only for Version 0.2 PCAS/HIBI serial trend support.

PCAS/HIBI module must not determine favorable or poor neurological prognosis from TCD/TCCFI/TCCS.

## Days After ROSC

Field:

daysAfterROSC

Type:

number

Unit:

days

Required:

Optional

Interpretation dependency:

Timing context only. Do not use as a standalone prognosis variable.

---

## TTM Status

Field:

ttmStatus

Type:

string

Required:

Optional

Values:

- normothermia
- activeTemperatureManagement
- hypothermia
- rewarming

Warning:

activeTemperatureManagement, hypothermia and rewarming should trigger caution for PCAS/HIBI trend interpretation.

---

## Sedation Level

Field:

sedationLevel

Type:

string

Required:

Optional

Values:

- none
- light
- deep
- unknown

Warning:

deep should trigger caution for PCAS/HIBI trend interpretation.

---

## Vasopressor Use

Field:

vasopressorUse

Type:

string

Required:

Optional

Values:

- yes
- no

Interpretation dependency:

Clinical context only.

---

## Mechanical Circulatory Support

Field:

mechanicalCirculatorySupport

Type:

string

Required:

Optional

Values:

- none
- IABP
- Impella
- VA_ECMO
- other

Warning:

VA_ECMO should trigger caution for PCAS/HIBI trend interpretation.

---

## Previous MFV

Field:

previousMfv

Type:

number

Unit:

cm/s

Required:

Recommended for PCAS/HIBI

If missing:

PCAS/HIBIでは単回測定値のみでの解釈は限定的です。serial trendでの評価を推奨します。

Classification:

indeterminate

---

## Previous PI

Field:

previousPi

Type:

number

Unit:

none

Required:

Recommended for PCAS/HIBI

---

## Previous EtCO2

Field:

previousEtco2

Type:

number

Unit:

mmHg

Required:

Recommended for PCAS/HIBI

---

## Previous MAP

Field:

previousMap

Type:

number

Unit:

mmHg

Required:

Recommended for PCAS/HIBI

---

# Doppler Measurements

## PSV

Field:

psv

Type:

number

Unit:

cm/s

Required:

Yes

Range:

0-400

---

## EDV

Field:

edv

Type:

number

Unit:

cm/s

Required:

Yes

Range:

0-250

---

## MFV

Field:

mfv

Type:

number

Unit:

cm/s

Required:

Yes

Range:

0-300

---

# Derived Variables

## Pulsatility Index

Field:

pi

Formula:

(PSV - EDV) / MFV

Unit:

none

Reference:

Typical adult range approximately 0.7-1.1

Interpretation:

PI >1.3 may indicate elevated distal resistance.

Do not interpret as exact ICP.

---

## Resistance Index

Field:

ri

Formula:

(PSV - EDV) / PSV

Unit:

none

Interpretation:

Supportive variable only.

Not a primary decision variable.

---

# SAH Variables

## Extracranial ICA MFV

Field:

icaMfv

Unit:

cm/s

Required:

For Lindegaard ratio

---

## Lindegaard Ratio

Field:

lr

Formula:

MCA MFV / extracranial ICA MFV

Required:

For vasospasm assessment

Threshold:

>=3

Interpretation:

Supports vasospasm physiology.

---

# Posterior Circulation Variables

## Basilar MFV

Field:

baMfv

Unit:

cm/s

Required:

Posterior circulation module

---

## Extracranial VA MFV

Field:

vaMfv

Unit:

cm/s

Required:

Posterior circulation module

---

## BA/VA Ratio

Field:

baVaRatio

Formula:

BA MFV / mean extracranial VA MFV

Thresholds:

>2.5

Compatible with moderate vasospasm

>3

Compatible with severe vasospasm

---

# Brain Death Module

## Waveform Pattern

Field:

waveformPattern

Type:

string

Values:

- ContinuousForwardFlow
- OscillatingFlow
- ReverberatingFlow
- SystolicSpikes
- SignalDisappearance

Interpretation:

Ancillary-compatible pattern only.

Never diagnose brain death.

Adult use only.

---

# Clinical Context Flags

## ECMO

Field:

ecmo

Type:

boolean

Default:

false

Warning:

Interpretation reliability reduced.

---

## Decompressive Craniectomy

Field:

decompressiveCraniectomy

Type:

boolean

Default:

false

Warning:

PI interpretation may be unreliable.

---

## Postoperative State

Field:

postOperativeState

Type:

boolean

Default:

false

Warning:

Interpretation reliability reduced.

---

# Research Variables

Not used in Version 0.1

- nICP
- nCPP
- CPPopt
- MAPopt
- Mx
- COx
- PRx
- HITS
- MES

Display as Research Use Only.

---

Created by Kosei Omasa
