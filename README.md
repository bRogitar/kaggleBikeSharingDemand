Bike Sharing Demand
1) 피처 엔지니어링: 수행한 내용 작성
peak 피처 추가 (시간이 피크시간인지 아닌지 나타냄 근무일 휴무일에 따라 다름)
hurricanesandy 피처 추가 (태풍)
holiday (크리스마스 같은 휴일 표시)
workingday 피처추가 (12월 24일과 31일의 근무일 상태를 휴무일로 조정)
ideal 피처추가 (운도와 풍속 기반 날씨가 좋은 날씨)
sticky 피처추가 (습도가 높은 날)
각 계절에 잘못된 들어가 있는게 있어서 수정
XGBoost를 사용할려 했으니 모든 입력이 수치형이야 하는데 year, hour의 문제로 시행이 안됨 -> 숫자 레이블 인코딩으로 피처를 범주형으로 변환한 후, 각 범주를 고유한 정수로 변환과정 시행
2) 모델 선택: 수행한 내용 작성
KNN로 시행시 RMSLE 값은 낮게 나오나 스코어 값은 높게나옴
xgb모델 얼리스탑 시행시 RMSLE값이 오히려 높게나옴
xgb모델로 진행후 RMSLE 값 : 0.2505 xgb로 모델선택
3) 하이퍼파라미터 최적화: 수행한 내용 작성
하이퍼파라미티 탐색공간 내용 수정 'max_depth': range(1, 11, 1), # 깊이

'n_estimators': [1, 10, 100], # 트리의 개수

'learning_rate': [0.01, 0.1, 0.2], # 학습률 추가

'subsample': [0.7, 0.8, 1.0], # 트리 당 데이터 샘플링 비율

'colsample_bytree': [0.7, 0.8, 1.0] # 각 트리마다의 피처 샘플링 비율

'gamma': [0.1],#최소 손실 감소량 지정

'min_child_weight': [5]#최소 자식 가중치 설정

감마와 최소 자식 가중치는 샐플링시 너무 오래걸려서 임의의 숫자를 넣고 수행

랜덤서치로 시도 해봤는 X_train과 y 자료 갯수가 달라 실패
0.38226 점
