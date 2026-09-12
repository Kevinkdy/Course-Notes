# 계량경제학 보충 노트 (학부)

**Wooldridge를 읽되, 교재가 넘어간 자리를 채우는 한국어 해설 (R + Stata 병기)**

Wooldridge 『Introductory Econometrics: A Modern Approach』 7판을 기본 교재로 하는
학부 계량경제학 수업의 보조 자료입니다. 서울시립대학교 수업 기준으로 작성하고 있습니다.

**교재를 대체하지 않습니다.** 교재를 펴 놓고 그 옆에서 읽는 보충 해설입니다.

## 왜 만드는가

Wooldridge는 좋은 교재지만, 학부용이라 결정적인 자리마다 "it can be shown that"으로
넘어갑니다. 그리고 강의는 대개 그 자리를 그대로 건너뜁니다.

- 왜 하필 **제곱합**을 최소화하는가? ("부호를 없애려고"는 답이 아닙니다)
- "잔차가 설명변수와 **직교**한다"는 게 무슨 뜻인가?
- $R^2$ 는 왜 **0과 1 사이**인가?
- "다른 조건이 같다면"에서 **통제한다**는 게 정확히 무엇인가?

## 원칙

- **표기는 Wooldridge 7판을 기준으로 삼습니다.** 다른 교재와 충돌하는 기호
  (특히 SSE / SSR)는 그 자리에 대조표를 붙입니다.
- **그림이 그려지는 상태에서 시작합니다.** 관측치 3개, 설명변수 2개처럼 종이에
  그릴 수 있는 크기로 먼저 보여주고, "이 논리는 n이 몇이든 같다"를 덧붙입니다.
- **행렬대수를 쓰지 않습니다.** 벡터, 선형결합, 내적, 직교까지만 씁니다.
- **모든 주장을 숫자로 확인합니다.** R과 Stata 양쪽에서 실행합니다.
- 각 장에 **"강의에서 막히는 지점"** 과 **"흔한 오해"** 칸이 있습니다.

## 구성

**파일 하나가 교재의 한 장에 대응합니다.**

### 1부 · 횡단면 자료의 회귀분석

| | 장 | 상태 |
|---|---|---|
| [ch01](chapters/ch01.md) | 계량경제학의 성격과 경제 자료 | 준비 중 |
| [ch02](chapters/ch02.md) | **단순회귀모형** | ✅ 설명 |
| [ch03](chapters/ch03.md) | **다중회귀분석: 추정** | ✅ 설명 + 코드 |
| [ch04](chapters/ch04.md) | 다중회귀분석: 추론 | 준비 중 |
| [ch05](chapters/ch05.md) | 다중회귀분석: OLS의 점근적 성질 | 준비 중 |
| [ch06](chapters/ch06.md) | 다중회귀분석: 추가적인 문제들 | 준비 중 |
| [ch07](chapters/ch07.md) | 질적 정보를 포함한 다중회귀분석 | 준비 중 |
| [ch08](chapters/ch08.md) | 이분산 | 준비 중 |
| [ch09](chapters/ch09.md) | 모형설정과 자료 문제 | 준비 중 |

### 2부 · 시계열 자료의 회귀분석

| | 장 | 상태 |
|---|---|---|
| [ch10](chapters/ch10.md) | 시계열 자료를 이용한 기본적 회귀분석 | 준비 중 |
| [ch11](chapters/ch11.md) | 시계열 자료에 OLS를 사용할 때의 추가 문제 | 준비 중 |
| [ch12](chapters/ch12.md) | 시계열 회귀에서의 계열상관과 이분산 | 준비 중 |

### 3부 · 고급 주제

| | 장 | 상태 |
|---|---|---|
| [ch13](chapters/ch13.md) | 시간에 걸친 횡단면 자료의 결합 | 준비 중 |
| [ch14](chapters/ch14.md) | 고급 패널 자료 기법 | 준비 중 |
| [ch15](chapters/ch15.md) | 도구변수 추정과 2SLS | 준비 중 |
| [ch16](chapters/ch16.md) | 연립방정식 모형 | 준비 중 |
| [ch17](chapters/ch17.md) | 제한종속변수 모형과 표본선택 보정 | 준비 중 |
| [ch18](chapters/ch18.md) | 고급 시계열 주제 | 준비 중 |
| [ch19](chapters/ch19.md) | 실증분석 프로젝트 수행하기 | 준비 중 |

우선순위는 [다룰 내용](reference/roadmap.md) 참조.

## 각 장의 구성

1. 교재 대응 → 2. 강의에서 막히는 지점 → 3. 직관 → 4. 수식 →
5. 숫자로 확인하기 (R / Stata) → 6. 흔한 오해 → 7. 연습문제

새 장은 [`TEMPLATE.md`](_template.md)를 `chapters/chNN.md`로 복사해서 시작합니다.

## 표기 주의

**SSE와 SSR은 교재마다 정반대입니다.**

| | Wooldridge 7e (이 노트) | 통계학 계열 교재 |
|---|---|---|
| 설명된 제곱합 | **SSE** (Explained) | SSR (Regression) |
| 잔차제곱합 | **SSR** (Residuals) | SSE (Error) |

**시험과 과제에서는 반드시 수업에서 지정한 교재의 표기를 쓰십시오.**
자세한 내용은 [들어가며](index.md)의 「표기 규약」 참조.

## 읽는 방법

**GitHub에서 그냥 읽으면 됩니다.** 모든 문서가 마크다운이라 아래 표의 링크를
누르면 바로 열립니다. 수식과 표, 경고 박스가 GitHub에서 그대로 렌더됩니다.

교재를 펴 놓고, 막히는 부분이 있을 때 해당 장을 여는 순서를 권합니다.

## 폴더 구조

```
chapters/     교재 한 장 = 파일 하나 (ch01.md ~ ch19.md)
figures/      그림
reference/    작성 로드맵
TEMPLATE.md   새 장 작성용 템플릿
_grad/        대학원용 초안 (보류 — 추후 작업)
index.md      들어가며 · 표기 규약
```

## 참고한 자료

- [JustinMShea/wooldridge](https://github.com/JustinMShea/wooldridge) — R 데이터 패키지, Stata `.dta` 포함
- [mca91/EconometricsWithR](https://github.com/mca91/EconometricsWithR) — 서술 구조 참고
- [LOST-STATS](https://github.com/LOST-STATS/lost-stats.github.io) — R/Stata 병기 포맷 참고
- [stata2r](https://stata2r.github.io/) — Stata ↔ R 명령 대응
- 한치록, 『계량경제학강의』 — 한국어 용어 기준

## 라이선스

- 문서: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.ko)
- 코드: MIT

교재 본문이나 그림을 복제하지 않습니다. 이 노트는 교재를 **소유한 독자**를 전제로 합니다.
