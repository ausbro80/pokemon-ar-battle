# ⚔️ Pokemon AR Battle 🥊

> 포켓몬 카드 두 장으로 진짜 배틀하는 AR 웹앱 — HP, 데미지, KO, 승부 시스템 완비!

[![Live Demo](https://img.shields.io/badge/Live-Demo-FFCB05?style=for-the-badge)](https://ausbro80.github.io/pokemon-ar-battle/)
[![Made with Three.js](https://img.shields.io/badge/Three.js-r160-000000?style=for-the-badge&logo=three.js)](https://threejs.org/)
[![MindAR](https://img.shields.io/badge/MindAR-1.2.5-EE1515?style=for-the-badge)](https://github.com/hiukim/mind-ar-js)

## 🎬 데모

**카드 두 장 동시 인식** → "VS" 인트로 → 배틀 시작 → ATTACK → 승부 결정!

> **이전 버전 ([pikachu-ar](https://ausbro80.github.io/pikachu-ar/))** 과의 차이: 단순 등장이 아닌 **진짜 게임 시스템**

## ⚔️ 배틀 시스템 기능

- 💚 **HP 바** — 좌측 리자몽 (150 HP), 우측 피카츄 (60 HP)
- ⚔️ **VS 인트로** — 두 카드 인식되면 자동으로 "BATTLE START!" 화면
- 💥 **데미지 시스템** — 피카츄 20, 리자몽 35 데미지
- 😵 **피격 효과** — 빨간 깜빡 + 좌우 흔들림 + 진동
- 💀 **KO 시스템** — HP 0 되면 90도 쓰러짐
- 🏆 **승리 화면** — "K.O.!" + 승자 표시 + REMATCH 버튼
- 📱 **가로 모드 안내** — 세로면 가로로 돌리라고 안내

## ✨ 기존 기능 (1편에서 가져옴)

- 🎴 두 카드 동시 인식
- 🐉 3D 모델 등장 (피카츄 + 리자몽)
- ⚡ 피카츄: 펀치 모션 + 전기 스파크
- 🔥 리자몽: 날개짓 + 입에서 화염 분사
- 📱 모바일 친화적 — iPhone/Android 지원

## 🛠️ 기술 스택

| 영역 | 사용 기술 |
|------|----------|
| AR 트래킹 | [MindAR.js](https://github.com/hiukim/mind-ar-js) |
| 3D 렌더링 | [Three.js](https://threejs.org/) r160 |
| 모델 포맷 | GLB (glTF Binary) |
| UI | 순수 HTML/CSS (애니메이션 포함) |
| 호스팅 | GitHub Pages |

## 📂 프로젝트 구조

```
pokemon-ar-battle/
├── index.html              # 메인 앱 (배틀 시스템 포함)
├── assets/
│   ├── pikachu.glb         # 피카츄 3D 모델
│   ├── charizard.glb       # 리자몽 3D 모델
│   ├── pikachu_card.jpg    # 피카츄 카드 이미지
│   ├── charizard_card.jpg  # 리자몽 카드 이미지
│   └── pikachu_card.mind   # MindAR 트래킹 데이터
└── README.md
```

## 🎮 사용법

1. **시작 화면**에서 `START` 버튼 누르기
2. 카메라 권한 허용
3. **폰을 가로로 돌리기** (배틀 모드는 가로가 박진감 폭발!)
4. 피카츄 카드와 리자몽 카드 **동시에** 비추기
5. **VS 화면** 등장 → "BATTLE START!"
6. **ATTACK** 버튼 누르기 → 양쪽 동시 공격!
7. HP 다 깎이면 → KO! → 승부 결정
8. **REMATCH** 버튼으로 재시작

## ⚖️ 밸런스 시스템

실제 카드 게임처럼 HP 차이 반영:

| 포켓몬 | HP | 받는 데미지 | KO까지 공격 횟수 |
|--------|-----|-----------|---------------|
| ⚡ 피카츄 | 60 | 35 (Fire Spin) | 2번 |
| 🔥 리자몽 | 150 | 20 (Electro Ball) | 8번 |

**리자몽이 압도적 유리** — 실제 카드 게임의 밸런스를 그대로 반영했어요. 피카츄가 이기려면 운이 따라야...!

## 🚀 직접 실행하기

```bash
git clone https://github.com/ausbro80/ausbro80.github.io.git
cd pokemon-ar-battle
python -m http.server 8000
# http://localhost:8000 접속
```

## 🎨 커스터마이징

### HP/데미지 조정
`index.html`에서 `maxHP` 값 조정:
```javascript
maxHP: 60,  // 피카츄
maxHP: 150, // 리자몽
```

데미지는 `triggerPunch()` 안에서:
```javascript
const damage = attacker.name === 'Pikachu' ? 20 : 35;
```

### 새 포켓몬 추가
```javascript
loadPokemon({
  name: 'Mewtwo',
  glbPath: './assets/mewtwo.glb',
  anchor: mindarThree.addAnchor(2),
  fixedScale: 0.1,
  maxHP: 200,
});
```

## 📝 라이선스

- 코드: MIT License
- 포켓몬 IP는 닌텐도/게임프리크/크리쳐스/The Pokémon Company 소유
- 비상업적 용도로만 사용

## 🙏 Credits

- AR 엔진: [MindAR.js](https://github.com/hiukim/mind-ar-js)
- 3D 라이브러리: [Three.js](https://threejs.org/)
- 펀치 애니메이션: [Mixamo](https://www.mixamo.com/)
- 리자몽 모델: 공식 포켓몬 게임 모델 (pm0006)

---

⚔️ **Made by Boss Terry** | 바이브코딩 스쿨 | 2026

🔗 **이전 버전**: [pikachu-ar](https://ausbro80.github.io/pikachu-ar/) (등장만)
🔗 **이번 버전**: [pokemon-ar-battle](https://ausbro80.github.io/pokemon-ar-battle/) (진짜 배틀!)
