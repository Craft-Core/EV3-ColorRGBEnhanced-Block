# 컬러 분류기 — 사용 가이드

**데이터 조작** 탭용 거리 기반 컬러 분류 블록입니다. 최대 8개의 기준 컬러를 학습시키고 실시간 RGB가 어떤 컬러에 가장 가까운지 식별합니다.

## 개념

```
정규화:  Rn = R / (R+G+B) × 100   (조명 불변)
Setup ×8: 각 슬롯에 기준 컬러 저장
Distance: 각 슬롯 n에 대해: D{n} = (R-Rn)² + (G-Gn)² + (B-Bn)²
Identify: BestColor = argmin(D1..D8); BestDistance = min(D1..D8)
```

## 사용법

1. 프로그램 시작 시 n=1..8 각각에 대해 `Setup_C{n}`을 기준 R, G, B와 함께 호출.
2. 메인 루프: RGB 읽기 → 정규화 (선택) → Distance → Identify.

## 모드

| 모드 | 카테고리 | 설명 |
|------|---------|------|
| `Normalize` | — | 각 채널 / (R+G+B) × 100 |
| `Setup_C1`..`Setup_C8` | 설정 | 슬롯 n에 기준 컬러 저장 |
| `Distance` | — | 입력 RGB에서 8개 슬롯 각각까지의 제곱 거리 |
| `Identify` | — | 가장 가까운 컬러의 인덱스와 거리 반환 |

## 팁

- 최대 8 슬롯.
- BestDistance는 제곱 거리. 실제 유클리드 거리는 sqrt로 계산.
- Identify는 항상 1–8 반환. "일치 없음"이 필요하면 `BestDistance > 임계값` 확인.
