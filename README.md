# 🤖 작작먹자 — AI 식단 비서

텔레그램에 음식 사진 보내면, AI가 칼로리 분석해서 구글 시트에 자동 저장해주는 AI 에이전트.

> "매일 뭐 먹었는지 검색해서 입력하는 게 너무 귀찮아" — 그래서 만들었습니다.

## 어떻게 작동하나요?

```
📸 음식 사진 찍기
   → 텔레그램으로 전송
   → Vision AI가 음식/칼로리 분석
   → 구글 시트에 자동 기록
   → "✅ 제육볶음 200g, 450kcal 기록완료!"
```

## 필요한 것

- [Hermes Agent](https://hermes-agent.sh) 설치된 Mac
- Telegram 계정
- OpenRouter API 키 ([openrouter.ai](https://openrouter.ai))

## 설치 방법

### 1. Hermes Agent 설치

```bash
curl -fsSL https://hermes-agent.sh/install | sh
```

### 2. 작작먹자 profile 다운로드

```bash
git clone https://github.com/isaacdigs/ggakggak-meokja.git ~/.hermes/profiles/ggakggak-meokja
```

### 3. Telegram Bot 생성

1. 텔레그램에서 `@BotFather` 검색
2. `/newbot` → 이름: `작작먹자` → 봇 토큰 받기
3. `~/.hermes/profiles/ggakggak-meokja/config.yaml` 에 토큰 입력

### 4. 실행

```bash
hermes run --profile ggakggak-meokja
```

텔레그램에서 작작먹자에게 음식 사진을 보내보세요!

## 파일 구조

```
ggakggak-meokja/
├── config.yaml            # 설정 (API 키, 시트 ID 등)
├── SOUL.md                # Agent 성격 정의
├── skills/
│   └── calorie-tracker/
│       └── SKILL.md       # 칼로리 트래킹 로직
└── README.md              # 지금 보고 있는 파일
```

## License

MIT — 마음대로 쓰세요.