# STATE_DATA

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
 
 ### 📅 12월 25일: Core 3 — 공통 포맷 정규화 · supervised 생성 · MLflow 실험 베이스 구축

* 공통 작업 목표
  * 출처가 다른 열화 데이터(NASA / liBattery / Synthetic / EV)를 동일한 상태 시계열 구조로 통일했다.
  * 학습 타깃을 절대 상태값이 아니라 Δstate = state(t+horizon) - state(t)로 고정했다.
  * 이후 Core 4·5에서 제어, 불확실성, 이식 가능성 비교가 가능하도록 데이터와 실험 구조를 정리했다.

* 공통 데이터 포맷
  * 모든 Stage 결과를 asset_id, t_index, state_value 3컬럼으로 통일했다.

#### 12_25_공통포맷정규화.ipynb

* Stage A — NASA (Canonical Degradation)
  * NASAmetadata.csv를 로드하고 메타 정보로 판단해 battery_id, test_id, uid, filename만 남겼다.
  * 실제 열화 상태는 discharge 파일의 Capacity/SOH에서 나온다고 판단 후 load_nasa_cell() 함수를 정의하고 discharge 파일을 로드했다.
  * Capacity를 state_value로 매핑했지만 시간 정보가 없어 t_index = range(len(df))로 정의했다.
  * 결과 포맷을 asset_id, t_index, state_value로 고정했다.

* Stage B — liBattery (Real-world Noise)
  * liBattery_Data_Cleaned.csv를 로드했지만 시간 컬럼이 없어 행 순서를 시간으로 가정했다.
  * t_index = groupby(battery_id).cumcount()로 생성하고 asset_id=battery_id, state_value=Capacity로 통일해 li_core를 생성했다.

* Stage C-1 — Synthetic Degradation
  * battery_degradation.csv를 로드하고 battery_id, time 기준으로 정렬했다. 이후 rul을 이미 계산된 열화 결과로 보고 state_value=rul로 매핑했다.
  * 배터리별 cumcount()로 t_index를 생성 후 synth_core를 생성했다.

* Stage C-2 — EV Synthetic
  * ev_battery_synth.csv를 로드 후 battery_id, charge_cycles 기준으로 정렬하고 t_index=charge_cycles로 직접 사용했다.
  * state_value=capacity_kWh로 매핑했으며 결과 포맷을 asset_id, t_index, state_value로 통일했다.

#### 12_25_stage_check.ipynb

* Stage A — nasa_core.csv 생성
  * NASAmetadata.csv에서 type == "discharge"만 남기고 Capacity 결측 행을 제거했다.
  * asset_id=str(battery_id), t_index=cumcount(), state_value=Capacity로 nasa_core를 생성했다.
  * ../data_csv/nasa_core.csv로 저장했다.

* Stage B — libattery_core.csv 생성
  * liBattery_Data_Cleaned.csv를 battery_id, uid 기준으로 정렬했다.
  * asset_id=str(battery_id), t_index=cumcount(), state_value=Capacity로 li_core를 생성했다.
  * ../data_csv/libattery_core.csv로 저장했다.

* Stage C-1 — synthetic_degradation_core.csv 생성
  * battery_degradation.csv를 battery_id, time 기준으로 정렬하고 asset_id=str(battery_id), t_index=cumcount(), state_value=rul로 synth_core를 생성했다.
  * ../data_csv/synthetic_degradation_core.csv로 저장했다.

* Stage C-2 — ev_synth_core.csv 생성
  * ev_battery_synth.csv를 battery_id, charge_cycles 기준으로 정렬했다.
  * asset_id=str(battery_id), t_index=charge_cycles, state_value=capacity_kWh로 ev_core를 생성했다.
  * ../data_csv/ev_synth_core.csv로 저장했다.

#### 12_25_컬럼확인.ipynb
* CSV 점검 유틸 inspect_csv()를 정의한 후 파일별로 columns, head, null count, row count를 출력했다.
* 점검 대상 파일을 다음으로 고정했다.
  * NASAmetadata.csv
  * liBattery_Data_Cleaned.csv
  * battery_degradation.csv
  * ev_battery_synth.csv
  * health_timeseries_core_state.csv
* 목적을 Stage 정규화에서 실제 사용 가능한 컬럼 구조를 사전에 확정하는 것으로 두었다.

#### 12_25_공통supervised생성기.ipynb

* MLflow 세팅
  * tracking uri를 sqlite:////Users/mac/Desktop/HW/State_Data/mlflow.db로 고정했으며 experiment를 core3_degradation_hierarchical로 고정했다.

* 공통 supervised 생성기
  * make_supervised_delta()를 정의하고 asset_id별로 t_index 기준 정렬 후 시퀀스를 생성했다.
  * 입력 X를 lookback 길이의 state_value 시퀀스로 구성했다.
  * 타깃 y를 state(t+horizon) - state(t) 형태의 Δstate로 정의했다.
  * state_value를 to_numeric(..., errors="coerce")로 수치화했다.
  * 입력 또는 타깃에 NaN이 포함된 샘플은 제거하고 Δstate를 현재 시점 t에 매핑되는 값으로 보고 asset_id, t_index(t)를 함께 반환했다.

* 학습 루틴
  * train_linear()를 정의한 후 LinearRegression을 학습했다.
  * val 예측 후 MAE, RMSE, error_std(residual std)를 계산했으며 train_lstm()를 정의했다.
  * 입력을 X[..., None]로 reshape한 후 모델을 LSTM(32) → Dense(1)로 구성했다.
  * epochs=20, batch_size=32, Adam(lr=0.001), loss=mse로 학습했다.
  * val 예측 후 MAE, RMSE, error_std를 계산했다.

* Stage별 실행
  * Stage A 입력으로 nasa_core.csv를 사용하고 Stage B 입력으로 libattery_core.csv를 사용했다.
  * 각 Stage에서 80/20 train–val split을 적용했다.
  * 각 run에 다음을 로깅했다.
     * params: stage, dataset, model_type, lookback, horizon
     * metrics: val_MAE, val_RMSE, error_std
  * model artifact를 MLflow에 저장했다.

* Stage C용 Stress Transform
  * stress_transform(df, gap, noise_sigma)를 정의하고 터리별 t_index 기준으로 iloc[::gap] 다운샘플링을 적용했다.
  * state_value에 정규분포 노이즈 N(0, noise_sigma)를 추가한 후 목적을 정보 밀도(gap)와 노이즈 수준 변화에 따른 예측 안정성 확인으로 설정했다.

⸻
 
### 📅 12월 26일: Core 4 — MySQL 로그 스키마 구축 · 적재 파이프라인 · Rule-based 액션 생성 · Core4 최종 조인 산출

* 공통 작업 목표
  * Core3에서 만든 state(상태)와 prediction(예측)을 MySQL 로그 테이블로 적재하고 중복 입력/중복 키를 처리할 수 있게 UNIQUE INDEX + INSERT IGNORE + 사전 dedup 구조를 넣었다.
  * 예측의 불확실성(error_std)만으로 보험 액션(approve/watch/deny) 을 생성한 후 state + prediction + action을 조인한 Core4 최종 결과 CSV를 만들었다.

#### 12_26_main.ipynb

* DB 연결 및 테이블 생성
  * mysql+pymysql://health_user:...@localhost:3306/HEALTH로 엔진을 생성하고 다음 3개 테이블을 없으면 생성하도록 DDL을 실행했다.
     * health_state_log
        * asset_id, t_index, state_value, source, created_at 구조로 만들었다.
     * prediction_log
        * asset_id, t_index, y_pred, error_std, model_tag, created_at 구조로 만들었다.
     * insurance_action_log
        * asset_id, t_index, action, reason, created_at 구조로 만들었다.
  * 중복 방지용 UNIQUE INDEX를 만들었다.
     * health_state_log(asset_id, t_index, source)
     * prediction_log(asset_id, t_index, model_tag)
     * insurance_action_log(asset_id, t_index, action)
  * 이미 인덱스가 있는 경우를 고려해 인덱스 생성 에러는 무시했다.

* 상태 로그 적재 (health + battery) — 중복 제거 포함한 후 source == "health"인 경우만 변환 로직을 적용했다.
  * user_id → asset_id, health_state_index → state_value로 컬럼을 바꾸고 date를 datetime으로 파싱했다.
  * asset_id, date 기준 정렬 후 t_index = cumcount()로 생성했다.
  * source != "health"(nasa/libattery/synthetic)는 asset_id,t_index,state_value가 이미 있다고 보고 그대로 사용했다.
  * 공통 정제 규칙을 적용하고 state_value를 수치화하고 결측을 제거, asset_id를 문자열로 통일, t_index를 정수로 강제 변환하고 결측을 제거, asset_id,t_index,source 기준 중복행을 제거했다.
  * insert_health_state_log(df)로 DB에 넣은 후 같은 키(asset_id,t_index,source)가 이미 테이블에 여러 개 있으면 id가 큰 쪽을 삭제하도록 사전 dedup 쿼리를 실행했다.
  * 이후 INSERT IGNORE로 중복 insert를 막았다.
  * 다음 파일을 적재했다.
     * ../data_csv/nasa_core.csv (source="nasa")
     * ../data_csv/libattery_core.csv (source="libattery")
     * ../data_csv/synthetic_degradation_core.csv (source="synthetic")
     * ../data_csv/health_timeseries_core_state.csv (source="health")

* 예측 로그 적재 — core3_output의 *_pred.csv 일괄 적재 (중복 제거 포함)
  * load_pred_csv(csv_path, model_tag)로 예측 CSV를 적재용 포맷으로 정제하고 필수 컬럼 asset_id,t_index,y_pred,error_std 존재를 강제 체크했다.
  * t_index,y_pred,error_std를 수치화하고 결측을 제거 후 model_tag는 파일명에서 _pred.csv를 제거한 문자열로 만들었다.
  * asset_id,t_index,model_tag 기준 중복행을 제거하고 insert_prediction_log(df)로 DB에 넣었다.
  * 같은 키(asset_id,t_index,model_tag) 중복이 있으면 id 큰 쪽을 삭제하도록 사전 dedup을 실행하고 이후 INSERT IGNORE로 중복 insert를 막았다.
  * pred_dir = "../data_csv/core3_output"에서 _pred.csv를 전부 찾아 반복 적재했다.

* Rule-based action 생성 — prediction_log 기반
  * 보험 의사결정 규칙 decide_insurance_action(error_std)를 정의하고 error_std < 0.3이면 approve / low uncertainty로 결정했다.
  * 0.3 ≤ error_std < 0.7이면 watch / medium uncertainty로 결정한 후 error_std ≥ 0.7이면 deny / high uncertainty로 결정했다.
  * prediction_log 전체에서 asset_id,t_index,error_std를 읽어오고 각 row에 대해 위 규칙으로 action, reason을 만들었다.
  * asset_id,t_index,action 기준 중복행을 제거했다.

*  action_log 적재 + 샘플 JOIN 출력
  * insert_action_log(df)로 insurance_action_log에 넣었고 같은 키(asset_id,t_index,action) 중복이 있으면 id 큰 쪽을 삭제하도록 사전 dedup을 실행했다.
  * 이후 INSERT IGNORE로 중복 insert를 막았으며 health_state_log + prediction_log + insurance_action_log를 asset_id,t_index로 조인해 20행을 출력했다.

* Core4 최종 산출물 CSV 저장 (Core5 입력)
  * ../core4_output 폴더를 생성했다.
  * 다음 조인 결과를 전체 추출해 df_core4로 만들었다.
     * health_state_log(h)
     * prediction_log(p)
     * insurance_action_log(a)
  * join key는 모두 asset_id,t_index로 고정했다.
  * df_core4를 ../core4_output/core4_state_prediction_action_log.csv로 저장한 후 확인용으로 상위 20행을 출력했다.

#### 12_26_Mysql.ipynb

* 목적 및 역할
  * 12_26_main.ipynb보다 단순한 형태로 MySQL 적재와 액션 생성을 빠르게 재현한 실행본이었다.

* health_state_log 적재
  * insert_state_log(csv_path, source)를 정의한 후 source == "health"인 경우만 컬럼 매핑과 t_index=cumcount() 생성을 수행했다.
  * 나머지 nasa/libattery/synthetic은 기존 asset_id,t_index,state_value가 있다고 보고 그대로 적재하고 to_sql(if_exists="append")로 health_state_log에 적재했다.

* prediction_log 적재
  * insert_prediction_log(csv_path, model_tag)를 정의한 후 예측 CSV에서 asset_id,t_index,y_pred,error_std만 남겼다.
  * model_tag를 추가해 prediction_log에 append 적재 후 예시는 A/B 일부 파일만 직접 지정해 적재했다.

* 보험 의사결정 규칙 및 action_log 적재
  * decide_insurance_action(error_std) 규칙을 동일하게 정의하고 insert_action_log_from_prediction(csv_path)로 예측 CSV를 읽어 액션 레코드를 생성했다.
  * 생성한 액션 레코드를 insurance_action_log에 append 적재했다.

#### 12_26_mysqlerror.ipynb

* 역할
  * 이미 적재된 테이블에서 중복이 생긴 상태를 정리하기 위해 생성하였다. 

* health_state_log 중복 정리
  * SELECT * FROM health_state_log로 전체를 읽었다.
  * id 기준 정렬 후 asset_id,t_index,source 기준으로 첫 행만 남기고 중복을 제거했다.
  * TRUNCATE TABLE health_state_log로 테이블을 비운 후 dedup된 데이터를 다시 to_sql(append)로 적재했다.
  * 정리 전/후 row 수를 출력했다.

* prediction_log 중복 정리
  * 동일한 방식으로 asset_id,t_index,model_tag 기준 dedup을 수행하고 TRUNCATE → 재적재 순서로 정리했다.

* insurance_action_log 중복 정리
  * 동일한 방식으로 asset_id,t_index,action 기준 dedup을 수행하고 TRUNCATE → 재적재 순서로 정리했다.

⸻

### 📅 12월 26일: Core 5 — 상태 기반 보험 개입 규칙 실험 및 안정화 효과 검증
* 공통 작업 목표
  * 건강 상태 시계열 데이터를 기반으로 상태 변화율(열화율)을 정의했다.
  * 외부 위험 요인(risk group)을 결합해 rule-based 개입 규칙을 설계하고 개입 이후 상태가 실제로 안정화되었는지를 시간 지연 기준으로 검증했다.
  * Core5 단계에서 사용할 의사결정 로그(core5_decision_log.csv)를 생성했다.

#### 12_26_coremain.ipynb
* 건강 상태 데이터 로드 및 정규화
  * health_timeseries_core_state.csv를 로드한 후 user_id → asset_id, health_state_index → state_value로 컬럼을 정규화했다.
  * asset_id, date 기준으로 정렬하고 asset별 누적 순서를 기준으로 t_index = cumcount()를 생성했다.

* 상태 변화량 및 열화율(degradation_rate) 계산
  * asset별 state_value 차분으로 delta_state를 계산하고 delta_state에 대해 7일 이동평균(window=7, min_periods=3)을 적용해 degradation_rate를 정의했다.
  * 이는 단일 시점 변화가 아닌 추세 기반 상태 악화 속도를 의미하도록 설계했다.

* 외부 위험도(risk_group) 구성
  * diabetes_dataset.csv를 로드하고 Glucose, BMI, Age, BloodPressure의 평균으로 risk_score를 계산했다.
  * risk_score를 3분위로 나눠 low / mid / high risk group을 생성하였으며 health 데이터의 asset 수에 맞춰 risk group을 랜덤 샘플링해 매핑했다.
  * 이는 실제 환자 매칭이 아닌 구조 실험용 위험도 주입이었다.

* 1차 개입 여부(intervention_flag) 규칙 정의
  * 다음 rule-based 개입 규칙을 정의했다.
     * risk_group == high 이고 degradation_rate < -0.05 → 개입
     * risk_group == mid 이고 degradation_rate < -0.10 → 개입
  * 그 외는 미개입
  * row 단위로 규칙을 적용해 intervention_flag (0/1)를 생성했다.

* 개입 이후 안정화(stabilized) 판단
  * compute_stabilization(df, window=7) 함수를 정의하고 현재 시점 대비 window 이후의 state_value를 post_state로 정의했다.
  * post_state - state_value > 0이면 상태가 안정화된 것으로 판단하고 기본 window=7 기준으로 안정화율을 계산했다.
  * intervention_flag별 안정화 비율을 비교했다.

* 개입 강도별 규칙 재정의 실험
  * 개입 강도를 "strong" / "weak" / "none"으로 확장했다.
     * high + 강한 열화 → strong
     * high/mid + 완만한 열화 → weak
  * 그 외 → none
  * 동일한 안정화 지표를 기준으로 개입 강도별 효과를 비교했다.

* 시간 지연(window) 효과 분석
  * 안정화 판단 window를 [3, 7, 14]로 바꿔가며 반복 실험한 후 window 변화에 따라 개입 효과가 어떻게 달라지는지 출력으로 확인했다.
  * 단기/중기/장기 지연 효과를 비교하기 위한 구조였다.

* 개입 효율(Efficiency) 지표 정의
  * stabilize_rate = stabilized.mean()
  * count = 표본 수
  * efficiency = stabilize_rate / count로 정의했다.
  * 이는 단순 성공률이 아니라 개입 빈도 대비 효과 밀도를 보려는 목적이었다.

* False Intervention(개입 실패) 분석
  * intervention_flag == 1 이지만 stabilized == False인 샘플을 추출 후 해당 샘플의 risk_group, degradation_rate 분포를 기술통계로 확인했다.
  * 이는 과잉 개입 / 잘못된 개입 조건 탐색을 위한 분석이었다.

* Core5 의사결정 로그 생성
  * 다음 컬럼만 추려 core5_log를 구성했다.
     * asset_id
     * date
     * t_index
     * state_value
     * degradation_rate
     * risk_group
     * intervention_flag
     * stabilized
  * 이를 core5_decision_log.csv로 저장하였으며 Core5 통합 실험 및 상위 제어 로직 입력용 로그로 사용된다.

⸻

### 📅 12월 26일: Core 6 — μHSM(State Monitor) · 상태 추세 계측 · 개입 효과 검증 · Core7 입력 로그 생성

#### 12_26_μHSM_State_Monitor.ipynb

* 공통 목적
  * 개인 건강 데이터를 사건(event) 이 아니라 연속 상태(state) 로 해석했다.
  * 상태 수준(state_value)과 상태 추세(degradation_rate)를 분리해 μHSM(State Monitor) 를 구성했다.
  * 위험군(risk_group)과 상태 추세를 결합한 rule-based 개입이 실제 안정화로 이어지는지 검증 후 Core7 제어/보상 단계에 입력할 의사결정 로그를 생성했다.

* 상태 데이터 로드 및 정규화
  * health_timeseries_core_state.csv를 로드하고 user_id → asset_id, health_state_index → state_value로 컬럼을 정규화했다.
  * asset_id, date 기준으로 정렬한 뒤 cumcount()로 날짜 기반 t_index를 생성했다.
* 상태 변화량 및 추세(degradation_rate) 계산
  * asset별 state_value.diff()로 delta_state를 계산한 후 delta_state에 rolling(window=7, min_periods=3) 평균을 적용해 단기 열화 추세인 degradation_rate를 계산했다.
  * 이를 통해 순간 노이즈가 아닌 추세 기반 상태 악화만을 포착했다.

* 외부 위험군(risk_group) 생성 및 매핑
  * diabetes_dataset.csv를 로드하고 Glucose, BMI, Age, BloodPressure 평균으로 risk_score를 계산했다.
  * risk_score를 3분위로 나눠 low / mid / high 위험군을 생성했으며 health asset 수만큼 위험군을 샘플링해 asset_id에 매핑했다.
  * 이 단계는 의료 위험 컨텍스트를 상태 모니터에 결합하는 구조 실험이었다.

* 1차 개입 규칙(intervention_flag) 정의
  * 다음 rule-based 조건으로 개입 여부를 정의했다.
     * high 위험군 & degradation_rate < -0.05 → 개입
     * mid 위험군 & degradation_rate < -0.10 → 개입
  * 그 외 → 비개입
  * 이를 intervention_flag (0/1)로 생성했다.

* 안정화(stabilization) 판정 로직
  * compute_stabilization(df, window) 함수를 정의하고 개입 시점 기준 window 이후의 post_state를 계산했다.
  * post_state - state_value > 0이면 안정화(stabilized=True)로 판정했으며 기본 window=7 기준으로 안정화 비율을 계산했다.

* 개입 강도 재정의 실험
  * 개입을 이진 플래그가 아닌 강도로 재정의했다.
     * high & degradation_rate < -0.1 → "strong"
     * high or mid & degradation_rate < -0.05 → "weak"
  * 그 외 → "none"
  * 개입 강도별 안정화 비율을 비교했다.

* 시간 지연(window) 효과 분석
  * window를 [3, 7, 14]로 변경하며 안정화 비율을 비교하고 개입 효과가 즉시 반응이 아닌 시간 누적 효과임을 확인했다.

* 개입 효율(Efficiency) 지표 계산
  * intervention_flag 기준으로 다음을 집계했다.
     * stabilize_rate = 안정화 비율
     * count = 샘플 수
  * efficiency = stabilize_rate / count로 개입 효율 지표를 계산 후 개입 빈도와 효율이 항상 비례하지 않음을 확인했다.

* False Intervention 분석
  * intervention_flag == 1 이면서 stabilized == False 인 사례를 추출했으며 해당 샘플의 risk_group, degradation_rate 분포 통계를 확인했다.
  * 개입 실패 영역을 명시적으로 분리했다.

* Core7 입력 로그 생성
  * 다음 컬럼만 남긴 core5_log를 생성했다.
     * asset_id
     * date
     * t_index
     * state_value
     * degradation_rate
     * risk_group
     * intervention_flag
     * stabilized
  * ../data_csv/core5_decision_log.csv로 저장했다.
  * 이 로그를 Core7 제어·보상·정책 단계의 입력 데이터로 사용하도록 확정했다.

⸻

### 📅 12월 26일: Core 7 — Decision Re-validation · 동일 예측 유지 · 의사결정 입력 구조만 변경 · MLflow/UI 레벨로 결과 고정
* 공통 작업 목표
  * 같은 예측 결과(또는 동일 기준의 Δstate/추세)를 쓰더라도 의사결정 입력 구조(decision input structure) 를 바꾸면 결과가 달라진다는 사실을 UI(MLflow run 비교) 레벨에서 고정했다.
  * threshold를 새로 늘리거나 규칙 개수를 늘리지 않고 입력 변수 구조만 변경해 안정화(stability) 개선이 발생하는지 재검증했다.

#### 12_26_core7_decision_revalidation_mlflow.ipynb
* 역할
  * Core6에서 생성된 로그(core5_decision_log.csv)를 읽어 Case A / Case B 결과를 MLflow에 고정 로깅했다.
  * UI에서 “같은 예측(동일 기준)인데 decision 구조만 바꿨다”는 비교가 가능하도록 run을 분리했다.
* MLflow 연결
  * tracking uri를 sqlite:////Users/mac/Desktop/HW/State_Data/mlflow.db로 설정했다.
  * experiment를 core7_decision_revalidation로 고정했다.
* 입력 데이터 로드
  * ../data_csv/core5_decision_log.csv를 로드했다.
  * 핵심 컬럼을 asset_id, degradation_rate, risk_group, intervention_flag, stabilized 기준으로 사용했다.
* Case A 로깅 (Prediction-based)
  * run_name을 CaseA_prediction_based로 설정하고 param을 decision_type=prediction_only, input=HDR + risk_group로 기록했다.
  * metric을 다음 방식으로 계산해 로깅했다.
     * stabilization_rate는 intervention_flag==1인 샘플의 stabilized.mean()으로 계산했다.
     * false_intervention_rate는 (intervention_flag==1 & stabilized==False)의 평균값으로 계산해 로깅했다.
* Case B 로깅 (μHSM-based)
  * run_name을 CaseB_muHSM_based로 설정하고 param을 decision_type=state_based, input=HSI + HDR + RM + OBS로 기록했다.
  * metric 계산은 Case A와 동일한 방식으로 수행해 stabilization_rate, false_intervention_rate를 로깅했다.
* Core 7 메시지 고정
  * “Same prediction / Same thresholds / Same rule count” 조건을 유지한 채 decision input structure만 바뀌었다는 결론 문장을 노트북 내에 고정했다.
  * 결과 해석은 “구조 변경만으로 stability가 개선되었다”로 정리했다.

#### 12_26_State_vs_Prediction_Decision.ipynb
* 역할
  * Case A(예측 기반)와 Case B(μHSM 기반)를 동일 평가 함수로 재평가하고, false intervention 및 토글 빈도까지 포함해 구조 차이를 수치로 비교했다.
  * “규칙 개수 동일 / threshold 증설 없음” 조건을 코드 수준에서 유지했다.
* 데이터 로드 및 컬럼 확인
  * Case A로 ../data_csv/core5_decision_log.csv를 로드했다.
  * Case B로 ../data_csv/muHSM_state_monitor.csv를 로드했다.
  * 두 데이터프레임의 컬럼 목록을 출력해 비교 기준을 고정했다.
* Case A 구성 (Prediction-based)
  * 입력 구조를 degradation_rate + risk_group로 정의하고 상태 맥락 변수를 쓰지 않는 구조로 고정했다.
  * asset_id, t_index 기준 정렬 후 평가 대상으로 사용했다.
* Case B 구성 (μHSM-based)
  * 입력 구조를 HSI + HDR + RM + OBS로 정의하고 HDR → degradation_rate로 컬럼을 통일했다.
  * asset_id, date 기준 정렬 후 평가 대상으로 사용했다.
* Case B 개입 규칙 정의 (규칙 수 동일 조건 유지)
  * 새 규칙을 다음 조건 1개로 고정했다.
     * degradation_rate < -0.05 AND recovery_margin < 0.3 AND observability_score > 0.6이면 개입(1)으로 판정했다.
  * 규칙 개수를 늘리지 않는 조건을 유지했다.
* 안정화 계산 함수 공통화
  * compute_stabilization(df, state_col, group_col, window=7)를 공통 함수로 정의했다.
  * post_state = group별 shift(-window)로 정의하고 post_state - current_state > 0이면 stabilized로 판정했다.
* Case A 안정화 평가
  * state_col="state_value"로 안정화를 계산했다.
  * intervention_flag별 stabilized.mean()을 출력해 개입 효과를 확인했다.
* Case B 안정화 평가
  * state_col="HSI"로 안정화를 계산했다.
  * intervention_flag별 stabilized.mean()을 출력해 개입 효과를 확인했다.
* False intervention 비교
  * Case A는 (intervention_flag==1 & stabilized==False)를 false_A로 정의했다.
  * Case B는 동일 기준으로 false_B를 정의했다.
  * false intervention rate를 “false 개수 / (개입 개수)”로 계산해 두 케이스를 비교 출력했다.
* 개입 토글 빈도(안정성) 비교
  * intervention_toggle_rate()를 정의해 asset별 flag 변화 횟수를 계산했다.
  * toggles / len(flags)의 평균으로 toggle rate를 정의하고 Case A와 Case B toggle rate를 비교 출력했다.
* Core 7 요약 테이블 생성
  * summary 테이블을 생성 후 포함 지표를 다음 3개로 고정했다.
     * Stabilization_when_intervened
     * False_intervention_rate
     * Intervention_toggle_rate
  * Case A와 Case B를 한 테이블에서 비교 가능하게 만들었다.

⸻

### 📅 12월 26일: Core 8 — Structural Reinterpretation · 규칙 실패의 구조적 원인 해석 · μHSM 안정성의 필연성 설명
* 공통 작업 목표
  * Core 3–7에서 이미 관측된 결과를 바탕으로, 규칙 기반 의사결정이 왜 구조적으로 불안정할 수밖에 없는지와 μHSM 기반 의사결정이 왜 동일 조건에서도 안정될 수밖에 없었는지를 해석 단계에서 고정했다.
  * 새로운 실험, 새로운 지표, 새로운 규칙을 의도적으로 추가하지 않고, 결과가 “그렇게 나올 수밖에 없었던 이유”만을 구조적으로 설명했다.

#### 12_26_structural_interpretation.md
* 역할
  * Core 7에서 확인된 “동일 예측 · 동일 규칙 수 · 동일 threshold” 조건 하의 결과 차이를 모델 성능이나 파라미터 문제가 아닌 의사결정 구조 차원 문제로 재해석했다.
  * Core 8은 실험 단계가 아니라 구조 해석 단계임을 명확히 했다.
  * Core 8에서 의도적으로 하지 않은 것
     * 새로운 성능 지표 추가하지 않았다.
     * 규칙 개수 증가 또는 조건 수정하지 않았다.
     * 예측 모델 변경하지 않았다.
     * 추가 실험 설계하지 않았다.
* 핵심 질문 고정
  * 왜 동일한 예측 결과와 동일한 규칙 수를 사용했음에도 예측 기반 의사결정은 흔들리고,상태 기반(μHSM) 의사결정은 안정되었는가?
* 기존 규칙 기반 의사결정의 암묵적 전제 정리
  * 미래 사건은 예측 가능하며 예측값이 임계값을 넘으면 개입하면 된다고 가정했다.
  * 규칙을 정교하게 만들면 판단은 안정될 것이라 가정했다.
* Core 3–7 결과를 통한 전제 붕괴 해석
  * 보험 의사결정은 사건(event)을 맞히는 문제가 아니라 상태(state)를 관리하는 문제임이 드러났다고 해석했다.
  * 사건 예측은 상태 관리의 필요 조건일 수는 있으나 충분 조건은 아니었다고 결론지었다.
* 구조적 불안정의 원인 분석
  * 예측은 본질적으로 단일 시점의 점(point) 값이라고 규정하고 규칙은 이 점을 임계값으로 절단하는 방식으로만 작동한다고 정리했다.
  * 이 구조 때문에 작은 노이즈에도 판단이 뒤집히고 개입 토글(toggle)이 증가한다고 설명했다.
  * 규칙은 “지금 나쁜가”만 판단하며 회복 중인지, 일시적 하락인지 구분하지 못한다고 해석하고 그 결과 false intervention이 구조적으로 발생할 수밖에 없다고 정리했다.
* μHSM 구조 재정의
  * μHSM을 단일 예측값이 아닌 상태 벡터로 정의했다.
     * HSI: 상태 수준
     * HDR: 변화 방향과 속도
     * RM: 회복 맥락
     * OBS: 관측 신뢰도
  * μHSM은 상태의 위치, 방향, 맥락, 신뢰도를 동시에 담는 최소 상태 계측 단위라고 규정했다.
* μHSM 기반 의사결정의 구조적 차이
  * μHSM 기반 판단은 임계값 판단을 즉시 수행하지 않는 구조라고 설명했으며 HDR이 나쁘더라도 RM이 높거나 OBS가 낮으면 판단을 보류하도록 설계되었다고 해석했다.
  * 이 구조적 지연이 false intervention 감소와 toggle rate 감소로 이어졌다고 연결했다.
* 조건 불변성 재강조
  * 규칙 개수는 변하지 않았으며 threshold 개수와 값도 변하지 않았다고 명시했다.
  * 예측 결과 역시 변하지 않았다고 명시한 후 오직 규칙이 바라보는 입력의 차원만 달라졌다고 결론지었다.
* 도메인 비유 및 보험 재정의 연결
  * 배터리 관리에서 전압 하나로 제어하지 않고 SOH, 열화율, 온도 맥락을 함께 본다는 점을 비유로 사용했다.
  * 보험 의사결정 역시 예측 확률 하나로는 충분하지 않았다고 정리하고 μHSM을 보험에서의 SOH에 해당하는 최소 상태 계측 단위로 정의했다.
* Core 8 결론 고정
  * 규칙 기반 의사결정이 실패한 이유는 규칙이 단순해서가 아니라 규칙이 상태를 보지 못했기 때문이라고 명확히 결론지었다.
  * 문제는 예측이 아니라 무엇을 보고 판단해야 하는지를 몰랐던 구조적 무지였다고 정리했다.
* Core 9 연결
  * 보험을 사건 보상(event-driven) 시스템이 아니라 상태 관리(state-managed) 시스템으로 재정의해야 한다는 질문을 던졌다.
  * 이를 Core 9 — From Event-driven Insurance to State-managed Insurance로 연결했다.
