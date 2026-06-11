# AGENTS.md

## 開発方針

このアプリは医療者向けの補助解釈ツールであり、診断確定アプリではない。

出力は必ず以下の表現に留める。

- 〜に整合
- 〜を示唆
- 〜の可能性
- 〜を考慮
- 追加評価を検討

以下のような断定表現は禁止する。

- ICPは○mmHgである
- DCIである
- brain deathである
- LVOを否定できる
- 予後不良である

## 技術方針

- React
- TypeScript
- Tailwind CSS
- Netlify公開を想定
- 1アプリ = 1リポジトリ
- スマホ優先
- 大きなボタン
- Step表示
- 夜間でも見やすいUI

## 医療安全上の原則

- TCD由来閾値をTCCFI/TCCSに流用する場合は注意文を表示する
- 比較血管が未入力の場合、ratioに基づく判定を provisional にする
- Brain death moduleは成人限定とする
- 小児には成人閾値を流用しない
- ECMO、PaCO2変動、MAP変動、術後・減圧開頭では警告を出す
- MAP、EtCO2/PaCO2、ICP、CPPは臨床コンテキストとして扱う
- ICP/CPPは実測値または臨床的算出値のみ入力可
- TCD/TCCFI/TCCSからICP/CPPを自動推定しない
- CO2とMAPの交絡を必ずwarningに反映する
- PCAS moduleでは予後判定をしない

## 表示すべきフッター

Created by Kosei Omasa
