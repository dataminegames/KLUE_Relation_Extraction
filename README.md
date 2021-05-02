# KLUE: Relation Extraction
Boostcamp AI Tech Pstage 2: 문장 내 개체간 관계 추출

구현 코드는 https://github.com/bcaitech1/p2-klue-dataminegames 에서 확인하실 수 있습니다.

## 대회 개요
관계 추출(Relation Extraction)은 문장의 단어(Entity)에 대한 속성과 관계를 예측하는 문제입니다. 관계 추출은 지식 그래프 구축을 위한 핵심 구성 요소로, 구조화된 검색, 감정 분석, 질문 답변하기, 요약과 같은 자연어처리 응용 프로그램에서 중요합니다. 비구조적인 자연어 문장에서 구조적인 triple을 추출해 정보를 요약하고, 중요한 성분을 핵심적으로 파악할 수 있습니다.

본 대회에서는 문장, 엔티티, 관계에 대한 정보를 통해, 문장과 엔티티 사이의 관계를 추론하는 모델을 학습시킵니다. 이를 통해 모델이 엔티티들의 속성과 관계를 파악하며 개념을 학습할 수 있습니다. `sentence`, `entity1`, `entity2`를 model의 input으로 입력 받아, 42개의 `relation` classes 중 1개를 예측하도록 합니다.

- input: `sentence`, `entity1`, `entity2`
  ```
  sentence: 이순신은 조선 중기의 무신이다.
  entity 1: 이순신
  entity 2: 무신
  ```
- output: `relation` 42개 classes 중 1개의 class를 예측한 값
  ```
  relation: 인물:직업/직함
  ```

평가 방법: Accuracy


## 데이터 개요
- train.tsv: 총 9000개
  ```
  column 1: 데이터가 수집된 정보.
  column 2: sentence.
  column 3: entity 1
  column 4: entity 1의 시작 지점.
  column 5: entity 1의 끝 지점.
  column 6: entity 2
  column 7: entity 2의 시작 지점.
  column 8: entity 2의 끝 지점.
  column 9: entity 1과 entity 2의 관계를 나타내며, 총 42개의 classes가 존재함.
  ```
- test.tsv: 총 1000개 (정답 라벨 blind)
  ```
  column 9: 'blind' 처리.
  ```
- answer: 정답 라벨 (비공개)
- label_type.pkl: 총 42개 classes. pickle로 load하게 되면, 딕셔너리 형태의 정보를 얻을 수 있습니다.
  ```
  {'관계_없음': 0, '인물:배우자': 1, '인물:직업/직함': 2, '단체:모회사': 3, '인물:소속단체': 4, '인물:동료': 5, 
  '단체:별칭': 6, '인물:출신성분/국적': 7, '인물:부모님': 8, '단체:본사_국가': 9, '단체:구성원': 10, '인물:기타_친족': 11, 
  '단체:창립자': 12, '단체:주주': 13, '인물:사망_일시': 14, '단체:상위_단체': 15, '단체:본사_주(도)': 16, '단체:제작': 17, 
  '인물:사망_원인': 18, '인물:출생_도시': 19, '단체:본사_도시': 20, '인물:자녀': 21, '인물:제작': 22, '단체:하위_단체': 23, 
  '인물:별칭': 24, '인물:형제/자매/남매': 25, '인물:출생_국가': 26, '인물:출생_일시': 27, '단체:구성원_수': 28, '단체:자회사': 29, 
  '인물:거주_주(도)': 30, '단체:해산일': 31, '인물:거주_도시': 32, '단체:창립일': 33, '인물:종교': 34, '인물:거주_국가': 35, 
  '인물:용의자': 36, '인물:사망_도시': 37, '단체:정치/종교성향': 38, '인물:학교': 39, '인물:사망_국가': 40, '인물:나이': 41} 
  ```


```
├── code
│   ├── README.md
│   ├── evaluation.py
│   ├── inference.py
│   ├── load_data.py
│   ├── requirements.txt
│   ├── train.py
│   └── train_cv.py
└── data
    ├── label_type.pkl
    ├── test
    │   └── test.tsv
    └── train
        └── train.tsv
```

