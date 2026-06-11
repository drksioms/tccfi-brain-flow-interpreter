# TCCFI/TCCS/TCD Brain Flow Interpreter

TCCFI/TCCS/TCD で得られた脳血流速度指標をもとに、神経集中治療領域での補助的な解釈を表示するWebアプリです。

## 目的

本アプリは、TCD/TCCFI/TCCSによる以下の評価を補助します。

- SAHにおけるvasospasm/DCIリスク評価
- TBIにおける高末梢抵抗・低CPPパターンの補助評価
- 成人brain death / cerebral circulatory arrestに整合する波形パターンの確認
- PCAS/HIBI、Stroke/LVO、General ICUにおける参考表示

## 注意

本アプリは診断・治療判断を代替するものではありません。

TCCFI/TCCS/TCDは、絶対脳血流量、正確なICP、正確なCPP、神経学的予後を単独で確定できません。

最終判断は、神経診察、CT/CTA/CTP、ICP/CPP、EEG、PbtO2、NIRS、臨床経過などを統合して医療者が行ってください。

## 主な計算式

- PI = (PSV - EDV) / MFV
- RI = (PSV - EDV) / PSV
- Lindegaard ratio = MCA MFV / ipsilateral extracranial ICA MFV
- BA/VA ratio = BA MFV / extracranial VA MFV

## 初期実装範囲

Version 0.1では以下を実装します。

- 基本指標計算
- SAH vasospasm module
- TBI high distal resistance / possible low CPP module
- 成人brain death ancillary-pattern module
- 測定条件に基づく警告表示
- serial trendの簡易表示

## Created by

Created by Kosei Omasa