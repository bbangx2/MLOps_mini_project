# Intel Geti를 활용한 MLOps 프로젝트: 과적/적재 불량 트럭 탐지

**작성자: 황경태**

## 📖 프로젝트 소개

[cite_start]이 프로젝트는 **Intel Geti (OpenVINO Toolkit)** 플랫폼을 활용하여 코딩 없이 AI 모델을 개발하고 배포하는 MLOps 실습 프로젝트입니다[cite: 1, 2].

[cite_start]초기에는 뇌 MRI 이미지의 이상을 탐지하는 프로젝트를 시도했으나, 데이터셋의 특성과 Anomaly Detection 모델의 한계로 인해 실패를 경험했습니다[cite: 10, 71]. [cite_start]이 경험을 바탕으로, **도로 위 과적 또는 적재 불량 대형 트럭을 탐지**하는 프로젝트로 방향을 전환하여 성공적으로 마무리했습니다[cite: 12, 78].

[cite_start]이 저장소는 해당 프로젝트의 과정과 결과를 담은 발표 자료를 포함하고 있으며, 코드 없이 MLOps 툴을 활용한 AI 모델 개발 과정을 보여줍니다[cite: 139].

---

## 🚀 프로젝트 과정

### **1️⃣ 초기 도전: 뇌 MRI 이상 탐지 (실패)**

* [cite_start]**목표**: 뇌 MRI 사진을 학습하여 뇌종양 등 뇌 질환을 자동으로 검출하고자 했습니다[cite: 19].
* [cite_start]**방법**: 정상/비정상 이미지를 분류하는 **Anomaly Detection 모델**을 사용했습니다[cite: 34].
* [cite_start]**결과**: 약 **50~60%** 의 낮은 정확도를 보이며 사실상 실패했습니다[cite: 36, 42, 47, 52, 57].
* [cite_start]**실패 원인**: Anomaly Detection은 **정형화된 '정상' 데이터**가 있을 때 효과적입니다[cite: 69]. [cite_start]하지만 뇌 MRI는 사람마다 형태가 모두 달라 일관된 데이터셋 구축이 어려웠고, 이는 모델의 사용 목적에 맞지 않았습니다[cite: 70, 71].

<br>

### **2️⃣ 메인 프로젝트: 과적/적재 불량 트럭 탐지 (성공)**

* [cite_start]**목표**: 다양한 도로 환경(고속도로, 국도, 다리 위 등)의 CCTV, 대시캠 이미지 속에서 대형 트럭을 먼저 찾아낸 후, 해당 트럭의 과적/적재 불량 여부를 판별합니다[cite: 79, 136].
* [cite_start]**방법**: 객체 탐지(Detection)와 이미지 분류(Classification)를 순차적으로 수행하는 **Chained Tasks** 모델을 활용했습니다[cite: 89].
* [cite_start]**데이터셋**: 직접 수집한 528장의 도로 위 트럭 이미지[cite: 80]. (학습 80%, 검증 10%, 테스트 10%로 분할) [cite_start][cite: 130]

---

## 🛠️ 기술 스택 및 모델

* **플랫폼**: **Intel Geti (OpenVINO Toolkit)**
* [cite_start]**주요 기능**: Annotation, 모델 학습, 테스트 등 MLOps 파이프라인 전반을 **No-Code**로 진행[cite: 139].
* **모델 아키텍처**:

| 단계 | 모델명 | 역할 |
| :--- | :--- | :--- |
| **Detection** | [cite_start]**MobileNetV2-ATSS** [cite: 127] | 이미지 속에서 '대형 트럭'의 위치를 찾아냄 |
| **Classification** | [cite_start]**EfficientNet-V2-S** [cite: 131] | 탐지된 트럭 이미지를 '정상'/'불법'으로 분류 |

---

## 📊 프로젝트 결과

* [cite_start]**Detection (트럭 탐지)**: **테스트 정확도 96점** [cite: 129]
* [cite_start]**Classification (적재 불량 분류)**: **테스트 정확도 92점** [cite: 129]


> [cite_start]다양한 카메라 구도와 도로 환경 속에서도 높은 정확도로 과적/적재 불량 트럭을 성공적으로 탐지했습니다[cite: 136].

---

## 💡 프로젝트 회고 및 느낀 점

* **좋았던 점**
    * [cite_start]OpenVINO 툴 덕분에 **코드 한 줄 없이** Annotation부터 모델 학습, 테스트까지 MLOps의 전 과정을 경험할 수 있었습니다[cite: 139].
    * [cite_start]다양한 최신 AI 알고리즘을 쉽게 적용하고 테스트해 볼 수 있었습니다[cite: 138].

* **아쉬운 점**
    * [cite_start]플랫폼이 네트워크 서버를 이용하다 보니, 데이터셋 업로드 및 Annotation 작업 시 속도 저하가 발생했습니다[cite: 140].
    * [cite_start]동시에 학습 가능한 인원 제한과 시간 부족으로 인해, 더 다양한 하이퍼파라미터 튜닝을 시도해보지 못한 점이 아쉽습니다[cite: 140].
