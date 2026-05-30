# Calorie Tracker Skill — 작작먹자 핵심 기능

## Trigger
사용자가 텔레그램으로 이미지(음식 사진)를 보내면 실행

## Workflow

1. **Image Analysis**
   - Vision AI (GPT-4o or Claude 3.5)로 음식 사진 분석
   - 식별: 음식 이름, 예상 중량(g), 칼로리, 단백질/탄수화물/지방
   - Output JSON:
   ```json
   {
     "food": "제육볶음",
     "estimated_weight_g": 200,
     "calories_kcal": 450,
     "protein_g": 28,
     "carbs_g": 35,
     "fat_g": 18,
     "confidence": 0.85
   }
   ```

2. **Log to Sheet**
   - Google Sheet에 기록
   - Columns: 날짜 | 시간 | 음식 | 칼로리 | 단백질 | 탄수화물 | 지방 | 메모

3. **Reply**
   - 텔레그램으로 확인 메시지 전송
   - Format: "✅ {음식} {중량}, {칼로리}kcal 기록완료!"
   - If low confidence: "이거 혹시 {추측}? 맞으면 ✅, 틀리면 직접 입력해줘!"

## Korean Food Recognition Tips
- GPT-4o is good at recognizing Korean foods (kimchi jjigae, bibimbap, etc.)
- For ambiguous dishes, ask the user to clarify
- Portion estimation is approximate — always add a confidence note

## Testing
```bash
# Local test
hermes run --profile ggakggak-meokja
# Then send a food photo via Telegram
```