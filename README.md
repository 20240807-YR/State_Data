# State_Data

다음은 사용자가 제시한 내용을 GRID_DATA에서 학습한 형식에 맞춰 정리한 결과이며,
요청대로 하다체를 유지하고, 구조 중심·검증 중심 서술로 변환하였다.

⸻

## 전체 프로젝트 구조 (Core-based Architecture)

| Core | 핵심 질문 | 검증 대상 |
| :--- | :--- | :--- |
| **Core 1** | 개인 건강 상태는 예측 가능한가? | **헬스케어 시계열 + ML 예측 가능성** |
| **Core 2** | 예측만으로 보험 의사결정이 가능한가? | **예측 기반 + 단순 규칙 의사결정** |
| **Core 3** | 규칙을 늘리면 문제가 해결되는가? | **규칙 확장의 한계** |
| **Core 4** | 상태 기반 시스템은 왜 다른가? | **배터리 상태 관리 구조 대비** |
| **Core 5** | 보험 의사결정의 구조적 한계는 무엇인가? | **사건 중심 vs 상태 중심 구조** |
| **Core 6** | 상태를 직접 계측하면 달라지는가? | **μHSM 상태 계측 삽입** |
| **Core 7** | 상태 기반 판단은 더 안정적인가? | **의사결정 안정성 재검증** |
| **Core 8** | 왜 상태는 규칙을 이기는가? | **구조 재해석** |
| **Core 8** | 보험은 어떤 구조로 진화해야 하는가? | **사건 보험 → 상태 관리 보험** |

⸻
## Core별 상세 수행 계획 및 실제 작업 정

### 🔵 Core 1 — Prediction Feasibility (Healthcare Data + ML — Health Risk Is Predictable)

* 핵심 목표 : 헬스케어 환경에서 수집되는 개인 건강 데이터를 활용하여,개인의 건강 리스크 상태가 예측 가능한 대상인지 여부를 최소 수준에서 검증한다. 이를 통해 이후 보험 의사결정 한계가 예측 실패인지, 구조적 문제인지를 구분한다.

* 수행 내용
  * 심박, 활동량, 수면, 스트레스 지표 등 개인 단위 시계열 데이터 구성한다.
  * 단일 진단이 아닌 상태 변화 추세를 관측할 수 있도록 데이터 구조 설계한다.
  * 기본 시계열 예측 모델 적용 및 단기 변화 패턴 재현 여부 확인한다.

* 검증 포인트
→ 개인 건강 상태는 무작위 사건이 아니라, 일정 수준에서 예측 가능한 상태 변수임을 확인한다.

⸻

### 🔵 Core 2 — Rule-based Insurance Decision (Prediction-based Insurance Decision with Simple Rules)

* 핵심 목표: Core 1의 예측 결과를 보험 의사결정 입력으로 활용하여,단순 규칙 기반 보험 의사결정 구조의 가능성과 한계를 검증한다.

* 수행 내용
  * 예측된 건강 리스크를 입력으로 사용한다.
  * 사전 관리 개입 여부를 단순 규칙 기반으로 설계한다.
  * 개입 효과 및 리스크 안정화 여부 관찰한다.

* 검증 포인트
→ 예측 정보는 존재하나, 의사결정이 단일 정보 축에 의존하면서 보험 리스크가 일관되게 안정화되지는 않음을 확인한다.

⸻

### 🔵 Core 3 — Rule Extension Experiments (Rule Expansion Does Not Solve Structural Limits)

* 핵심 목표 : Core 2의 한계를 규칙 단순성 문제로 가정하고, 규칙 확장을 통해 구조적 한계가 해소되는지 검증한다.

* 수행 내용
  * 다양한 조건과 예외를 포함한 규칙 확장 실험 수행한다.
  * 규칙 복잡도 증가에 따른 의사결정 결과 변화 관찰한다.

* 검증 포인트
→ 규칙이 복잡해질수록 의사결정 일관성은 오히려 저하된다.
→ 문제의 원인은 규칙 설계가 아니라 정보 구조에 있음을 확인한다.

⸻

### 🔵 Core 4 — Contrast Case (Battery-based State Management)

* 핵심 목표
보험 의사결정 구조의 한계를 해결책 제시가 아닌, 비교 사례를 통해 구조적으로 해석한다.

* 수행 내용
  * 보험 의사결정 구조와 배터리 관리 시스템 구조 대비한다.
  * 배터리 시스템에서 SOH, 열화율 등 상태 변수를 지속적으로 계측하는 구조 분석한다.

* 검증 포인트
→ 동일한 예측 사고를 적용하더라도, 상태 정보 밀도의 차이가 제어 가능성을 구조적으로 결정함을 확인한다.

⸻

### 🔵 Core 5 — Structural Implications (Redefining Conditions for Preventive Insurance Decision)

* 핵심 목표 : 앞선 비교를 바탕으로, 보험 의사결정이 사전 개입에 실패하는 구조적 원인을 정리한다.

* 수행 내용
  * 사건 중심 보험 구조와 상태 기반 배터리 관리 구조 통합 해석한다.
  * 상태 누적 관측 여부에 따른 개입 가능성 비교한다.

* 검증 포인트
→ 예측 기반 의사결정 구조의 효과는 상태 정보의 밀도와 해석 구조에 의해 결정됨을 확인한다.

⸻

### 🔵 Core 6 — State-based Observability Insertion (μHSM-based Insurance State Monitoring)

* 핵심 목표 : 보험 의사결정 한계가 예측이나 규칙 문제가 아니라, 상태를 직접 계측하지 못하는 구조에서 비롯된 것인지 검증한다.

* 수행 내용
  * μHSM(micro Health State Monitor) 개념 정의한다.
  * 건강 리스크를 사건 확률이 아닌 연속 상태 변수(HSI, HDR, Recovery Margin)로 계측한다.
  * 기존 예측 기반 입력을 μHSM 상태 변수 기반 입력으로 전환한다.

* 검증 포인트
→ 보험 의사결정의 핵심 한계는 예측 실패가 아니라, 상태 비가시성에 있었음을 확인한다.

⸻

### 🔵 Core 7 — Re-validation: Decision Stability Test (State-based Decision vs Prediction-based Decision)

* 핵심 목표
μHSM 기반 상태 관측 구조가 기존 예측 기반 의사결정의 불안정성을 완화하는지 재검증한다.

* 수행 내용
  * 예측 기반 의사결정 구조와 μHSM 기반 상태 의사결정 구조 비교한다.
  * 동일 데이터·동일 예측 모델 조건에서 입력 구조만 변경한다.

* 검증 포인트
→ μHSM 구조에서 개입 타이밍 일관성 증가, 불필요한 개입 감소 확인한다.
→ 판단 안정성은 규칙 수가 아니라 상태 인식 여부에 의해 결정됨을 확인한다.

⸻

### 🔵 Core 8 — Structural Reinterpretation (Why μHSM Works Where Rules Failed)

* 핵심 목표
규칙 확장이 실패한 구조적 이유를 재해석한다.

* 수행 내용
  * 사건 중심 판단과 상태 중심 판단 구조 대비한다.
  * 배터리 관리 시스템의 SOH 개념과 μHSM 구조 재연결한다.

* 검증 포인트
→ 보험 의사결정의 본질적 문제는 규칙 부족이 아니라, 연속 상태를 관측하지 못한 구조에 있었음을 구조적으로 정리한다.

⸻

### 🔵 Core 9 — Final Implication (From Event-driven Insurance to State-managed Insurance)

* 핵심 목표: 전체 Core를 통해 도출된 구조적 결론을 최종 정리한다.

* 최종 결론 : 상태 기반 계측·관리 구조는 스마트그리드와 배터리 관리 영역뿐 아니라, 보험 리스크 관리에도 동일하게 적용 가능한 산업 인프라 설계 원리임을 확인하였다.
μHSM은 보험을 사건 사후 보상 구조에서, 상태 열화를 관리하는 사전 개입 금융 구조로 전환하기 위한 핵심 관측 단위로 기능한다.

---
## 파일 정리 

### 📅 12월 25일: Core 1 — Health State Backbone & State Variable 정의 (12_25_core1main.ipynb)
* 헬스케어 시계열 Backbone 데이터 로드 및 구조 확인 후 health_timeseries_core_backbone.csv 파일을 로드했습니다.
* date 컬럼을 datetime으로 변환하고 user_id, date 기준으로 정렬하고 전체 row 수, 사용자 수, 날짜 범위를 확인했습니다. 그 다음 컬럼별 결측치 개수를 점검했습니다.
* (user_id, date) 기준 중복 행 존재 여부를 확인했습니다. 그리고 사용자별 관측 일수 분포(days per user)를 요약했습니다.
* 사용자 샘플 시계열 시각화 하여 상태가 사건이 아님을 확인하였다. 이후에 샘플 사용자 3명을 추출했습니다.
  * 심박 상태 시계열
  * mean_hr
  * hr_std
  * 활동량 시계열
  * steps
  * calories
  * 수면 시계열
  * sleep_minutes
* 모든 변수들이 단발 이벤트가 아니라 연속적 상태 변화임을 시각적으로 확인하고 상태 변수 정의 (State Variables)하였습니다. 
* 상태 변수로 다음 컬럼을 사용했습니다.
  * mean_hr
  * hr_std
  * steps
  * sleep_minutes
* 사용자 기준 Z-score 정규화하고 사용자별 평균·표준편차 기준으로 Z-score를 계산했습니다.분산이 0이거나 결측인 경우 Z-score를 0으로 처리했습니다.
* 방향성 보정
  * steps_z → 부하 감소 방향이므로 부호 반전
  * sleep_minutes_z → 회복 지표이므로 부호 반전
  * Health State Level 계산 (12_25_core1main.ipynb)
  * 정규화된 상태 변수들의 평균으로 상태 레벨을 정의했습니다.
* 계산식
  * health_state_level = (mean_hr_z + hr_std_z + steps_z + sleep_minutes_z) / 4
* ealth State Speed 계산 (열화 속도) (12_25_core1main.ipynb)
  * WINDOW = 7 기준 rolling window를 사용했습니다.
  * 각 시점에서 과거 상태 레벨의 기울기(선형 회귀 slope)를 계산했습니다.
  * 사용자별로 정렬 후 health_state_speed 컬럼을 생성했습니다.
  * 상태의 “수준(Level)”과 “변화 속도(Speed)”를 명확히 분리했습니다. 이후 SOH(상태 수준) + 열화율 대응 논리 고정하였습니다. 
* 최종 Health State Index 정의 (12_25_core1main.ipynb)
  * 상태 수준과 속도를 결합한 단일 지표를 정의했습니다.
* 계산식
  * health_state_index = health_state_level + health_state_speed * WINDOW
* 상태 분포 확인 (사건 아님 재검증) (12_25_core1main.ipynb)
  * 샘플 사용자별 health_state_index 분포 통계를 출력했습니다.
  * 상태가 이산 이벤트가 아닌 연속 분포 상태 변수임을 재확인했습니다.
* Core State CSV 저장 (12_25_core1main.ipynb)
* 출력 컬럼
  * user_id, date
* 원천 상태 변수
  * health_state_level
  * health_state_speed
  * health_state_index
* 저장 파일 : ../data_csv/health_timeseries_core_state.csv

⸻

📅 12월 25일: Core 1 — 원천 Fitbit 데이터 병합 (Backbone 생성)
* 원천 CSV 컬럼 구조 확인 (12_25_csv파일merge.ipynb)
  * heartrate_seconds_merged.csv
  * dailyActivity_merged.csv
  * sleepDay_merged.csv
  * 각 파일의 컬럼 목록을 출력해 구조를 사전 점검했습니다.
* 활동 데이터 일 단위 Backbone 생성하였습니다. 
  * dailyActivity_merged.csv에서
  * ActivityDate → date
  * TotalSteps → steps
  * Calories → calories
  * 사용자–날짜 기준 일 단위 activity backbone을 생성했습니다.
* 심박 데이터 일 단위 집계하였습니다. 
  * heartrate_seconds_merged.csv에서 아래를 계산했습니다.
  * Time → date
  * 사용자–날짜 기준으로
  * 평균 심박(mean_hr)
  * 심박 표준편차(hr_std)
* 수면 데이터 일 단위 Backbone 생성하였습니다. 
  * sleepDay_merged.csv에서
  * SleepDay → date
  * TotalMinutesAsleep → sleep_minutes
  * 사용자–날짜 기준 수면 backbone을 구성했습니다.
  * 헬스케어 시계열 Backbone 병합하였습니다.
* 병합 순서
	1.	activity × heart rate (left join)
	2.	결과 × sleep (left join)
  * 병합 키
  * user_id
  * date
* 병합 후 사용자 수, 날짜 수, 결측 요약을 점검했습니다.
* Core Backbone CSV 저장 (12_25_csv파일merge.ipynb)
  * 저장 파일 : ../data_csv/health_timeseries_core_backbone.csv

### 📅 12월 25일: Core 2 — Health State Δ예측 (12_25_prediction.ipynb)
* Core 1 상태 CSV 로드 및 정합성 확인하고 health_timeseries_core_state.csv 파일을 로드했습니다. 그리고 date 컬럼을 datetime으로 변환했습니다.
* (user_id, date) 기준으로 평균 집계를 수행해 중복을 정리한 후 사용자·날짜 기준으로 정렬했습니다.그리고 전체 row 수, 사용자 수, health_state_index 결측 여부를 확인했습니다.
* Supervised Dataset 구성 (Δstate 예측 문제 정의) (12_25_prediction.ipynb)
  * 예측 문제를 상태 절대값이 아닌 상태 변화량(Δstate) 예측으로 정의했습니다.
  * 입력(X)
     * 과거 LOOKBACK = 14일의 health_state_inde 
  * 타깃(y)
     * t + HORIZON(7) 시점의
health_state_index(t+h) - health_state_index(t)
* 사용자별 시계열을 유지한 상태로 sliding window를 구성했습니다.
* 출력
  * X: (N, lookback)
  * y: (N,)
  * meta: user_id, t_date, target_date
* Time-based Train / Validation 분리하여 target_date 기준으로 전체 샘플을 시간 순 정렬했습니다.
* 앞 80%를 train, 뒤 20%를 validation으로 분리한 후 사용자 섞임은 허용하되 미래 정보 누수는 차단했습니다.
* 모델 1 — Linear Regression (Baseline) 
  * LinearRegression 모델을 사용했습니다.
  * 입력: 과거 14일 state 벡터
  * 출력: 7일 후 Δstate
  * 평가 지표
     * MAE
     * RMSE
  * train / validation 모두에서 성능을 계산했습니다.
     * validation 샘플 일부에 대해 아래를 출력해 sanity check를 수행했습니다.
     * 실제 Δstate
     * 예측 Δstate
     * user_id
* 모델 2 — LSTM (얕은 구조)
  * LSTM 입력 형태로 reshape
  * (N, lookback, 1)
  * 모델 구조
     * LSTM(16)
     * Dense(1)
     * epochs = 15, batch_size = 32
     * loss: mse
  * Linear 모델과 동일한 방식으로 train / validation 성능을 평가하고 validation 샘플 일부에 대해 예측 결과를 비교 출력했습니다.
  * Core 2 요약 출력 
     * LOOKBACK, HORIZON 설정값을 출력하고 Linear vs LSTM을 정량 비교만 수행했습니다.
     * 모델 선택·확장은 Core 3에서 MLflow 기반으로 진행하기로 고정했습니다.
  * 예측 결과 테이블 구성하하고 validation 구간 기준으로 결과를 정리했습니다.
  * 공통 컬럼
     * user_id
     * date (target_date)
     * y_true
     * y_pred
     * abs_error
     * run_tag = core2_baseline
  * 모델 구분
     * mode_type = linear
     * mode_type = lstm
  * Linear / LSTM 결과를 하나의 DataFrame으로 병합했습니다.
  * MySQL 예측 결과 적재
     * sqlalchemy, pymysql을 사용해 DB 연결을 구성했습니다.
     * DB
     * HEALTH
     * 테이블
     * prediction_results
     * if_exists="append" 옵션으로 결과를 누적 저장했습니다.
  * Core 2 baseline 예측 결과 저장 완료를 확인했습니다.
