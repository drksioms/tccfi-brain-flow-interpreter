# TCCFI/TCCS/TCD Brain Flow Interpreter

TCCFI/TCCS/TCD で得られた脳血流速度指標をもとに、神経集中治療領域での補助的な解釈を表示するWebアプリです。

## Version 1

Version 1 は、GitHub Pages または Netlify でそのまま公開できる静的HTMLアプリです。

## 目的

本アプリは、TCD/TCCFI/TCCSによる以下の評価を補助します。

- SAHにおけるvasospasm physiologyの補助評価
- TBIにおけるhigh distal resistance / possible low CPP patternの補助評価
- 成人brain death / cerebral circulatory arrestに整合する波形パターンの確認
- PCAS/HIBIにおけるserial trendと臨床コンテキストの補助評価

## 注意

本アプリは診断・治療判断を代替するものではありません。

TCCFI/TCCS/TCDは、絶対脳血流量、正確なICP、正確なCPP、神経学的予後を単独で確定できません。

最終判断は、神経診察、CT/CTA/CTP、ICP/CPP、EEG、PbtO2、NIRS、臨床経過などを統合して医療者が行ってください。

## Version 1 実装範囲

- 疾患カテゴリ選択
- PSV / EDV / MFV / MCA MFV / ICA MFV / BA MFV / VA MFV 入力
- MAP / EtCO2 / PaCO2 / ICP / CPP 入力
- PI / RI / Lindegaard ratio / BA/VA ratio 自動計算
- SAH module
- TBI module
- 成人brain death ancillary-pattern module
- PCAS/HIBI trend module
- 測定条件と臨床コンテキストに基づくwarning表示
- GitHub Pages / Netlify向け静的公開

## 主な計算式

- PI = (PSV - EDV) / MFV
- RI = (PSV - EDV) / PSV
- Lindegaard ratio = MCA MFV / ipsilateral extracranial ICA MFV
- BA/VA ratio = BA MFV / extracranial VA MFV

## 実装しないもの

- TCD/TCCFI/TCCS単独によるICP/CPP推定
- PCAS/HIBIでの予後判定
- 治療推奨
- CPPopt/MAPoptによる治療目標表示

## Created by

Created by Kosei Omasa
