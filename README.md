# TGV Simulator

**Live demo: <https://dodobing.github.io/TGVSimulator/>**

Laser modification 후 chemical etching으로 형성되는 Through-Glass Via (TGV) 공정 시뮬레이터.
단일 HTML 파일로 동작하며, 위 링크에 접속하거나 브라우저에서 [`index.html`](index.html)을 열면 바로 실행됩니다.

An interactive simulator of through-glass via (TGV) formation by laser modification + chemical etching.
Single self-contained HTML file — visit the live demo above or open [`index.html`](index.html) in a browser.

## Features

- **입력 파라미터**: 유리 두께, laser modified 직경, modified area / 유리 식각 selectivity, 기준 식각 속도, 총 식각 시간 (자동/수동)
- **2D 유리 단면**: 시간 전개에 따른 blind via 성장 → 관통(breakthrough) → hourglass via 확장 과정을 치수선과 함께 표시
- **3D volume rendering**: WebGL raymarching 기반 — 유리는 투명(테두리 와이어프레임), 형성된 via는 컬러 본체로 렌더링, 1/4 cut-away 지원
- **수직/수평 표시 배율**: 자동 맞춤 · 수동(×0.5–200) · 1:1 실축척, 2D/3D 공통 적용
- **재생 제어**: ×0.5 – ×100 재생속도, 시간 슬라이더 스크럽
- **Crack 포함 모드**: laser modification 유발 micro-crack 을 Z slice 단위로 배치(길이/두께/개수/상대각도/변동율/간격 파라미터, 오버레이 패널), modified area 와 동일한 selectivity 로 crack 을 따라 식각 전파 — 2D fin + 3D blade 렌더링
- **다국어 UI**: 한국어 · English · 日本語 · 简体中文 · 繁體中文

## Physics model

- 유리 식각 속도 `vG = R0·Sg`, modified track 축방향 전파 속도 `vM = R0·Sm`
- 깊이 ζ의 via 반경: front 통과 후 등방 확장 `r(ζ,t) = d/2 + vG·(t − ζ/vM)`
- Taper 각도 `tanθ = vG/vM = Sg/Sm` 의 모래시계(hourglass) 프로파일
- 양면 식각: 표면 후퇴 `s(t) = vG·t`, 관통 시각 `t_break = (T/2)/vM`
