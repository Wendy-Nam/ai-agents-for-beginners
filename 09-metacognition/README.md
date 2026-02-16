
[![AI 에이전트의 메타인지](./images/lesson-9-thumbnail.png)](https://youtu.be/His9R6gw6Ec?si=3_RMb8VprNvdLRhX)

> _(👆 이미지를 클릭하면 이번 레슨의 강의 영상을 볼 수 있어요!)_

# 🧠 AI 에이전트의 메타인지 - 스스로 생각하는 AI 만들기

## 🧐 소개

AI 에이전트의 메타인지에 관한 레슨에 오신 것을 환영합니다! 이 장은 AI 에이전트가 자신의 사고 과정에 대해 어떻게 생각할 수 있는지 궁금해하는 초보자들을 위해 설계되었습니다. 이 레슨을 마치면 핵심 개념을 이해하고 AI 에이전트 설계에 메타인지를 적용하는 실용적인 예제를 갖추게 될 것입니다.

## 📚 학습 목표

이번 레슨을 완료하면 다음을 할 수 있게 됩니다:

1. 에이전트 정의에서 추론 루프의 의미를 이해합니다.
2. 자기 수정 에이전트를 돕기 위한 계획 및 평가 기술을 사용합니다.
3. 작업을 수행하기 위해 코드를 조작할 수 있는 자신만의 에이전트를 만듭니다.

---

## 🤔 메타인지 소개

메타인지는 자신의 생각에 대해 생각하는 것을 포함하는 고차원적인 인지 과정을 의미합니다. AI 에이전트의 경우, 이는 자기 인식과 과거 경험을 바탕으로 자신의 행동을 평가하고 조정할 수 있는 능력을 의미합니다. 메타인지, 즉 "생각에 대한 생각"은 에이전틱 AI 시스템 개발에서 중요한 개념입니다. 이는 AI 시스템이 자신의 내부 프로세스를 인식하고 그에 따라 행동을 모니터링, 규제 및 적응할 수 있는 능력을 포함합니다. 마치 우리가 상황을 파악하거나 문제를 바라볼 때 하는 것과 같습니다. 이러한 자기 인식은 AI 시스템이 더 나은 결정을 내리고, 오류를 식별하며, 시간이 지남에 따라 성능을 개선하는 데 도움이 될 수 있습니다. 이는 다시 튜링 테스트와 AI가 세상을 지배할 것인지에 대한 논쟁으로 이어집니다.

에이전틱 AI 시스템의 맥락에서 메타인지는 다음과 같은 여러 문제를 해결하는 데 도움이 될 수 있습니다:

- **투명성 (Transparency)**: AI 시스템이 자신의 추론과 결정을 설명할 수 있도록 보장합니다.
- **추론 (Reasoning)**: AI 시스템이 정보를 종합하고 올바른 결정을 내리는 능력을 향상시킵니다.
- **적응 (Adaptation)**: AI 시스템이 새로운 환경과 변화하는 조건에 적응할 수 있도록 합니다.
- **지각 (Perception)**: AI 시스템이 환경의 데이터를 인식하고 해석하는 정확성을 향상시킵니다.

### 메타인지란 무엇인가?

메타인지, 즉 "생각에 대한 생각"은 자신의 인지 과정에 대한 자기 인식과 자기 조절을 포함하는 고차원적인 인지 과정입니다. AI 영역에서 메타인지는 에이전트가 자신의 전략과 행동을 평가하고 적응할 수 있도록 하여 문제 해결 및 의사 결정 능력을 향상시킵니다. 메타인지를 이해함으로써 더 지능적일 뿐만 아니라 더 적응력 있고 효율적인 AI 에이전트를 설계할 수 있습니다. 진정한 메타인지에서는 AI가 자신의 추론에 대해 명시적으로 추론하는 것을 볼 수 있습니다.

예시: "저는 더 저렴한 항공편을 우선시했습니다. 왜냐하면... 직항 항공편을 놓치고 있을 수도 있으니 다시 확인해 보겠습니다."
특정 경로를 어떻게 또는 왜 선택했는지 추적합니다.

- 지난번에 사용자 선호도에 너무 의존해서 실수했다는 것을 인지하고, 최종 추천뿐만 아니라 의사 결정 전략 자체를 수정합니다.
- "사용자가 '너무 붐빈다'고 언급할 때마다 특정 명소를 제거할 뿐만 아니라, 항상 인기순으로 순위를 매긴다면 '인기 명소'를 선택하는 방법 자체에 문제가 있다는 것을 반성해야 한다"와 같은 패턴을 진단합니다.

### AI 에이전트에서 메타인지의 중요성

메타인지는 여러 가지 이유로 AI 에이전트 설계에서 중요한 역할을 합니다:

![메타인지의 중요성](./images/importance-of-metacognition.png)

- **자기 성찰 (Self-Reflection)**: 에이전트는 자신의 성과를 평가하고 개선 영역을 식별할 수 있습니다.
- **적응성 (Adaptability)**: 에이전트는 과거 경험과 변화하는 환경에 따라 전략을 수정할 수 있습니다.
- **오류 수정 (Error Correction)**: 에이전트는 오류를 자율적으로 감지하고 수정하여 더 정확한 결과를 얻을 수 있습니다.
- **리소스 관리 (Resource Management)**: 에이전트는 계획을 세우고 행동을 평가하여 시간 및 계산 능력과 같은 리소스 사용을 최적화할 수 있습니다.

---

## 🧩 AI 에이전트의 구성 요소

메타인지 과정을 살펴보기 전에 AI 에이전트의 기본 구성 요소를 이해하는 것이 중요합니다. AI 에이전트는 일반적으로 다음으로 구성됩니다:

- **페르소나 (Persona)**: 에이전트의 성격과 특성으로, 사용자와 상호작용하는 방식을 정의합니다.
- **도구 (Tools)**: 에이전트가 수행할 수 있는 기능과 함수입니다.
- **기술 (Skills)**: 에이전트가 보유한 지식과 전문성입니다.

이러한 구성 요소는 함께 작동하여 특정 작업을 수행할 수 있는 "전문성 단위"를 만듭니다.

**예시**:
여행 일정을 계획할 뿐만 아니라 실시간 데이터와 과거 고객 여정 경험을 바탕으로 경로를 조정하는 에이전트 서비스를 생각해 보세요.

### 예시: 여행 에이전트 서비스의 메타인지

여행 에이전트 서비스를 설계한다고 상상해 보세요. 이 에이전트는 사용자의 휴가 계획을 돕습니다. 메타인지를 통합하기 위해 여행 에이전트는 자기 인식과 과거 경험을 바탕으로 자신의 행동을 평가하고 조정해야 합니다. 메타인지가 어떻게 작용할 수 있는지 살펴보겠습니다:

#### 현재 작업

현재 작업은 사용자가 파리 여행을 계획하는 것을 돕는 것입니다.

#### 작업 완료 단계

1. **사용자 선호도 수집**: 사용자에게 여행 날짜, 예산, 관심사(예: 박물관, 요리, 쇼핑) 및 특정 요구 사항을 묻습니다.
2. **정보 검색**: 사용자의 선호도와 일치하는 항공편 옵션, 숙박 시설, 명소, 레스토랑을 검색합니다.
3. **추천 생성**: 항공편 세부 정보, 호텔 예약 및 추천 활동이 포함된 개인화된 일정을 제공합니다.
4. **피드백 기반 조정**: 추천에 대한 사용자 피드백을 요청하고 필요한 조정을 합니다.

#### 필요한 리소스

- 항공편 및 호텔 예약 데이터베이스에 대한 액세스.
- 파리 명소 및 레스토랑에 대한 정보.
- 이전 상호작용의 사용자 피드백 데이터.

#### 경험 및 자기 성찰

여행 에이전트는 메타인지를 사용하여 성과를 평가하고 과거 경험에서 학습합니다. 예를 들어:

1. **사용자 피드백 분석**: 여행 에이전트는 사용자 피드백을 검토하여 어떤 추천이 호평을 받았고 어떤 추천이 그렇지 않았는지 확인합니다. 그에 따라 향후 제안을 조정합니다.
2. **적응성**: 사용자가 이전에 붐비는 장소를 싫어한다고 언급했다면, 여행 에이전트는 향후 성수기에 인기 관광지를 추천하지 않을 것입니다.
3. **오류 수정**: 여행 에이전트가 과거 예약에서 만실인 호텔을 추천하는 등의 오류를 범했다면, 추천하기 전에 가용성을 더 엄격하게 확인하는 방법을 학습합니다.

#### 실용적인 개발자 예시

메타인지를 통합할 때 여행 에이전트 코드가 어떻게 보일 수 있는지에 대한 간단한 예시입니다:

```python
class Travel_Agent:
    def __init__(self):
        self.user_preferences = {}
        self.experience_data = []

    def gather_preferences(self, preferences):
        self.user_preferences = preferences

    def retrieve_information(self):
        # 선호도에 따라 항공편, 호텔, 명소 검색
        flights = search_flights(self.user_preferences)
        hotels = search_hotels(self.user_preferences)
        attractions = search_attractions(self.user_preferences)
        return flights, hotels, attractions

    def generate_recommendations(self):
        flights, hotels, attractions = self.retrieve_information()
        itinerary = create_itinerary(flights, hotels, attractions)
        return itinerary

    def adjust_based_on_feedback(self, feedback):
        self.experience_data.append(feedback)
        # 피드백 분석 및 향후 추천 조정
        self.user_preferences = adjust_preferences(self.user_preferences, feedback)

# 사용 예시
travel_agent = Travel_Agent()
preferences = {
    "destination": "Paris",
    "dates": "2025-04-01 to 2025-04-10",
    "budget": "moderate",
    "interests": ["museums", "cuisine"]
}
travel_agent.gather_preferences(preferences)
itinerary = travel_agent.generate_recommendations()
print("제안된 일정:", itinerary)
feedback = {"liked": ["Louvre Museum"], "disliked": ["Eiffel Tower (too crowded)"]}
travel_agent.adjust_based_on_feedback(feedback)
```

#### 메타인지가 중요한 이유

- **자기 성찰**: 에이전트는 자신의 성과를 분석하고 개선 영역을 식별할 수 있습니다.
- **적응성**: 에이전트는 피드백과 변화하는 조건에 따라 전략을 수정할 수 있습니다.
- **오류 수정**: 에이전트는 자율적으로 오류를 감지하고 수정할 수 있습니다.
- **리소스 관리**: 에이전트는 시간 및 계산 능력과 같은 리소스 사용을 최적화할 수 있습니다.

메타인지를 통합함으로써 여행 에이전트는 더 개인화되고 정확한 여행 추천을 제공하여 전반적인 사용자 경험을 향상시킬 수 있습니다.

---

## 📝 에이전트의 계획 수립

계획 수립은 AI 에이전트 행동의 중요한 구성 요소입니다. 여기에는 현재 상태, 리소스 및 가능한 장애물을 고려하여 목표를 달성하는 데 필요한 단계를 개략적으로 설명하는 것이 포함됩니다.

### 계획 수립의 요소

- **현재 작업**: 작업을 명확하게 정의합니다.
- **작업 완료 단계**: 작업을 관리 가능한 단계로 세분화합니다.
- **필요한 리소스**: 필요한 리소스를 식별합니다.
- **경험**: 과거 경험을 활용하여 계획을 수립합니다.

**예시**:
여행 에이전트가 사용자의 여행 계획을 효과적으로 돕기 위해 수행해야 하는 단계는 다음과 같습니다:

### 여행 에이전트의 단계

1. **사용자 선호도 수집**
   - 사용자에게 여행 날짜, 예산, 관심사 및 특정 요구 사항에 대한 세부 정보를 요청합니다.
   - 예시: "언제 여행할 계획이신가요?" "예산 범위는 어떻게 되시나요?" "휴가 때 어떤 활동을 즐기시나요?"
2. **정보 검색**
   - 사용자 선호도에 따라 관련 여행 옵션을 검색합니다.
   - **항공편**: 사용자의 예산과 선호 여행 날짜 내에서 가능한 항공편을 찾습니다.
   - **숙박 시설**: 위치, 가격, 편의 시설에 대한 사용자의 선호도와 일치하는 호텔이나 임대 숙소를 찾습니다.
   - **명소 및 레스토랑**: 사용자의 관심사에 맞는 인기 명소, 활동 및 레스토랑 옵션을 식별합니다.
3. **추천 생성**
   - 검색된 정보를 개인화된 일정으로 정리합니다.
   - 항공편 옵션, 호텔 예약, 추천 활동과 같은 세부 정보를 제공하여 추천이 사용자의 선호도에 맞게 조정되도록 합니다.
4. **사용자에게 일정 제시**
   - 제안된 일정을 사용자에게 공유하여 검토를 요청합니다.
   - 예시: "파리 여행을 위한 제안된 일정입니다. 항공편 세부 정보, 호텔 예약, 추천 활동 및 레스토랑 목록이 포함되어 있습니다. 의견을 알려주세요!"
5. **피드백 수집**
   - 제안된 일정에 대한 사용자 피드백을 요청합니다.
   - 예시: "항공편 옵션이 마음에 드시나요?" "호텔이 필요에 적합한가요?" "추가하거나 제거하고 싶은 활동이 있나요?"
6. **피드백 기반 조정**
   - 사용자 피드백에 따라 일정을 수정합니다.
   - 사용자의 선호도에 더 잘 맞도록 항공편, 숙박 시설 및 활동 추천을 변경합니다.
7. **최종 확인**
   - 업데이트된 일정을 사용자에게 제시하여 최종 확인을 받습니다.
   - 예시: "피드백에 따라 조정했습니다. 업데이트된 일정입니다. 모든 것이 괜찮아 보이나요?"
8. **예약 및 확인**
   - 사용자가 일정을 승인하면 항공편, 숙박 시설 및 사전 계획된 활동 예약을 진행합니다.
   - 확인 세부 정보를 사용자에게 보냅니다.
9. **지속적인 지원 제공**
   - 여행 전과 여행 중에 사용자가 변경 사항이나 추가 요청 사항이 있을 경우 도움을 드릴 수 있도록 대기합니다.
   - 예시: "여행 중 추가 도움이 필요하시면 언제든지 저에게 연락해 주세요!"

### 상호작용 예시

```python
class Travel_Agent:
    def __init__(self):
        self.user_preferences = {}
        self.experience_data = []

    def gather_preferences(self, preferences):
        self.user_preferences = preferences

    def retrieve_information(self):
        flights = search_flights(self.user_preferences)
        hotels = search_hotels(self.user_preferences)
        attractions = search_attractions(self.user_preferences)
        return flights, hotels, attractions

    def generate_recommendations(self):
        flights, hotels, attractions = self.retrieve_information()
        itinerary = create_itinerary(flights, hotels, attractions)
        return itinerary

    def adjust_based_on_feedback(self, feedback):
        self.experience_data.append(feedback)
        self.user_preferences = adjust_preferences(self.user_preferences, feedback)

# 예약 요청 내 사용 예시
travel_agent = Travel_Agent()
preferences = {
    "destination": "Paris",
    "dates": "2025-04-01 to 2025-04-10",
    "budget": "moderate",
    "interests": ["museums", "cuisine"]
}
travel_agent.gather_preferences(preferences)
itinerary = travel_agent.generate_recommendations()
print("제안된 일정:", itinerary)
feedback = {"liked": ["Louvre Museum"], "disliked": ["Eiffel Tower (too crowded)"]}
travel_agent.adjust_based_on_feedback(feedback)
```

---

## 🔧 교정적 RAG 시스템 (Corrective RAG System)

먼저 RAG 도구와 사전 예방적 컨텍스트 로드의 차이점을 이해하는 것부터 시작하겠습니다.

![RAG vs 컨텍스트 로드](./images/rag-vs-context.png)

### 검색 증강 생성 (RAG)

RAG는 검색 시스템과 생성 모델을 결합합니다. 쿼리가 이루어지면 검색 시스템이 외부 소스에서 관련 문서나 데이터를 가져오고, 이 검색된 정보는 생성 모델에 대한 입력을 보강하는 데 사용됩니다. 이는 모델이 더 정확하고 상황에 맞는 응답을 생성하는 데 도움이 됩니다.

RAG 시스템에서 에이전트는 지식 베이스에서 관련 정보를 검색하고 이를 사용하여 적절한 응답이나 행동을 생성합니다.

### 교정적 RAG 접근 방식

교정적 RAG 접근 방식은 RAG 기술을 사용하여 오류를 수정하고 AI 에이전트의 정확성을 향상시키는 데 중점을 둡니다. 여기에는 다음이 포함됩니다:

1. **프롬프트 기법**: 에이전트가 관련 정보를 검색하도록 안내하는 특정 프롬프트를 사용합니다.
2. **도구**: 에이전트가 검색된 정보의 관련성을 평가하고 정확한 응답을 생성할 수 있도록 하는 알고리즘과 메커니즘을 구현합니다.
3. **평가**: 에이전트의 성능을 지속적으로 평가하고 정확성과 효율성을 개선하기 위해 조정합니다.

#### 예시: 검색 에이전트의 교정적 RAG

웹에서 정보를 검색하여 사용자 쿼리에 답변하는 검색 에이전트를 생각해 보세요. 교정적 RAG 접근 방식에는 다음이 포함될 수 있습니다:

1. **프롬프트 기법**: 사용자 입력을 기반으로 검색 쿼리를 공식화합니다.
2. **도구**: 자연어 처리 및 기계 학습 알고리즘을 사용하여 검색 결과의 순위를 지정하고 필터링합니다.
3. **평가**: 사용자 피드백을 분석하여 검색된 정보의 부정확성을 식별하고 수정합니다.

### 여행 에이전트의 교정적 RAG

교정적 RAG는 AI의 정보 검색 및 생성 능력을 향상시키면서 부정확성을 수정합니다. 여행 에이전트가 교정적 RAG 접근 방식을 사용하여 더 정확하고 관련성 높은 여행 추천을 제공하는 방법을 살펴보겠습니다.

여기에는 다음이 포함됩니다:

- **프롬프트 기법:** 에이전트가 관련 정보를 검색하도록 안내하는 특정 프롬프트를 사용합니다.
- **도구:** 에이전트가 검색된 정보의 관련성을 평가하고 정확한 응답을 생성할 수 있도록 하는 알고리즘과 메커니즘을 구현합니다.
- **평가:** 에이전트의 성능을 지속적으로 평가하고 정확성과 효율성을 개선하기 위해 조정합니다.

#### 여행 에이전트에서 교정적 RAG 구현 단계

1. **초기 사용자 상호작용**
   - 여행 에이전트는 목적지, 여행 날짜, 예산, 관심사와 같은 초기 선호도를 사용자로부터 수집합니다.
   - 예시:

     ```python
     preferences = {
         "destination": "Paris",
         "dates": "2025-04-01 to 2025-04-10",
         "budget": "moderate",
         "interests": ["museums", "cuisine"]
     }
     ```
2. **정보 검색**
   - 여행 에이전트는 사용자 선호도에 따라 항공편, 숙박 시설, 명소 및 레스토랑에 대한 정보를 검색합니다.
   - 예시:

     ```python
     flights = search_flights(preferences)
     hotels = search_hotels(preferences)
     attractions = search_attractions(preferences)
     ```
3. **초기 추천 생성**
   - 여행 에이전트는 검색된 정보를 사용하여 개인화된 일정을 생성합니다.
   - 예시:

     ```python
     itinerary = create_itinerary(flights, hotels, attractions)
     print("제안된 일정:", itinerary)
     ```
4. **사용자 피드백 수집**
   - 여행 에이전트는 초기 추천에 대한 사용자 피드백을 요청합니다.
   - 예시:

     ```python
     feedback = {
         "liked": ["Louvre Museum"],
         "disliked": ["Eiffel Tower (too crowded)"]
     }
     ```
5. **교정적 RAG 프로세스**
   - **프롬프트 기법**: 여행 에이전트는 사용자 피드백을 기반으로 새로운 검색 쿼리를 공식화합니다.
     - 예시:

       ```python
       if "disliked" in feedback:
           preferences["avoid"] = feedback["disliked"]
       ```
   - **도구**: 여행 에이전트는 알고리즘을 사용하여 새로운 검색 결과의 순위를 지정하고 필터링하며, 사용자 피드백에 따라 관련성을 강조합니다.
     - 예시:

       ```python
       new_attractions = search_attractions(preferences)
       new_itinerary = create_itinerary(flights, hotels, new_attractions)
       print("업데이트된 일정:", new_itinerary)
       ```
   - **평가**: 여행 에이전트는 사용자 피드백을 분석하고 필요한 조정을 통해 추천의 관련성과 정확성을 지속적으로 평가합니다.
     - 예시:

       ```python
       def adjust_preferences(preferences, feedback):
           if "liked" in feedback:
               preferences["favorites"] = feedback["liked"]
           if "disliked" in feedback:
               preferences["avoid"] = feedback["disliked"]
           return preferences

       preferences = adjust_preferences(preferences, feedback)
       ```

#### 실용적인 예시

여행 에이전트에 교정적 RAG 접근 방식을 통합하는 간단한 Python 코드 예시입니다:

```python
class Travel_Agent:
    def __init__(self):
        self.user_preferences = {}
        self.experience_data = []

    def gather_preferences(self, preferences):
        self.user_preferences = preferences

    def retrieve_information(self):
        flights = search_flights(self.user_preferences)
        hotels = search_hotels(self.user_preferences)
        attractions = search_attractions(self.user_preferences)
        return flights, hotels, attractions

    def generate_recommendations(self):
        flights, hotels, attractions = self.retrieve_information()
        itinerary = create_itinerary(flights, hotels, attractions)
        return itinerary

    def adjust_based_on_feedback(self, feedback):
        self.experience_data.append(feedback)
        self.user_preferences = adjust_preferences(self.user_preferences, feedback)
        new_itinerary = self.generate_recommendations()
        return new_itinerary

# 사용 예시
travel_agent = Travel_Agent()
preferences = {
    "destination": "Paris",
    "dates": "2025-04-01 to 2025-04-10",
    "budget": "moderate",
    "interests": ["museums", "cuisine"]
}
travel_agent.gather_preferences(preferences)
itinerary = travel_agent.generate_recommendations()
print("제안된 일정:", itinerary)
feedback = {"liked": ["Louvre Museum"], "disliked": ["Eiffel Tower (too crowded)"]}
new_itinerary = travel_agent.adjust_based_on_feedback(feedback)
print("업데이트된 일정:", new_itinerary)
```

### 사전 예방적 컨텍스트 로드 (Pre-emptive Context Load)

사전 예방적 컨텍스트 로드는 쿼리를 처리하기 전에 관련 컨텍스트나 배경 정보를 모델에 로드하는 것을 포함합니다. 즉, 모델이 처음부터 이 정보에 액세스할 수 있으므로 프로세스 중에 추가 데이터를 검색할 필요 없이 더 많은 정보에 기반한 응답을 생성하는 데 도움이 될 수 있습니다.

다음은 Python으로 된 여행 에이전트 애플리케이션에 대한 사전 예방적 컨텍스트 로드가 어떻게 보일 수 있는지에 대한 간단한 예시입니다:

```python
class TravelAgent:
    def __init__(self):
        # 인기 여행지와 정보를 미리 로드
        self.context = {
            "Paris": {"country": "France", "currency": "Euro", "language": "French", "attractions": ["Eiffel Tower", "Louvre Museum"]},
            "Tokyo": {"country": "Japan", "currency": "Yen", "language": "Japanese", "attractions": ["Tokyo Tower", "Shibuya Crossing"]},
            "New York": {"country": "USA", "currency": "Dollar", "language": "English", "attractions": ["Statue of Liberty", "Times Square"]},
            "Sydney": {"country": "Australia", "currency": "Dollar", "language": "English", "attractions": ["Sydney Opera House", "Bondi Beach"]}
        }

    def get_destination_info(self, destination):
        # 미리 로드된 컨텍스트에서 여행지 정보 가져오기
        info = self.context.get(destination)
        if info:
            return f"{destination}:\n국가: {info['country']}\n통화: {info['currency']}\n언어: {info['language']}\n명소: {', '.join(info['attractions'])}"
        else:
            return f"죄송합니다. {destination}에 대한 정보가 없습니다."

# 사용 예시
travel_agent = TravelAgent()
print(travel_agent.get_destination_info("Paris"))
print(travel_agent.get_destination_info("Tokyo"))
```

#### 설명

1. **초기화 (`__init__` 메서드)**: `TravelAgent` 클래스는 파리, 도쿄, 뉴욕, 시드니와 같은 인기 여행지에 대한 정보를 포함하는 딕셔너리를 미리 로드합니다. 이 딕셔너리에는 각 여행지의 국가, 통화, 언어, 주요 명소와 같은 세부 정보가 포함됩니다.
2. **정보 검색 (`get_destination_info` 메서드)**: 사용자가 특정 여행지에 대해 문의하면 `get_destination_info` 메서드는 미리 로드된 컨텍스트 딕셔너리에서 관련 정보를 가져옵니다.

컨텍스트를 미리 로드함으로써 여행 에이전트 애플리케이션은 실시간으로 외부 소스에서 이 정보를 검색할 필요 없이 사용자 쿼리에 빠르게 응답할 수 있습니다. 이렇게 하면 애플리케이션이 더 효율적이고 응답성이 높아집니다.

### 반복 전에 목표로 계획 부트스트래핑

목표로 계획을 부트스트래핑한다는 것은 명확한 목표나 대상 결과를 염두에 두고 시작하는 것을 의미합니다. 이 목표를 미리 정의함으로써 모델은 반복 프로세스 전반에 걸쳐 이를 지침 원칙으로 사용할 수 있습니다. 이는 각 반복이 원하는 결과를 달성하는 데 더 가까워지도록 하여 프로세스를 더 효율적이고 집중적으로 만듭니다.

다음은 Python에서 여행 에이전트의 목표로 여행 계획을 부트스트래핑하고 반복하는 방법에 대한 예시입니다:

#### 시나리오

여행 에이전트는 고객을 위한 맞춤형 휴가를 계획하려고 합니다. 목표는 고객의 선호도와 예산에 따라 고객 만족도를 최대화하는 여행 일정을 만드는 것입니다.

#### 단계

1. 고객의 선호도와 예산을 정의합니다.
2. 이러한 선호도를 기반으로 초기 계획을 부트스트래핑합니다.
3. 반복하여 고객 만족도에 최적화되도록 계획을 개선합니다.

#### Python 코드

```python
class TravelAgent:
    def __init__(self, destinations):
        self.destinations = destinations

    def bootstrap_plan(self, preferences, budget):
        plan = []
        total_cost = 0

        for destination in self.destinations:
            if total_cost + destination['cost'] <= budget and self.match_preferences(destination, preferences):
                plan.append(destination)
                total_cost += destination['cost']

        return plan

    def match_preferences(self, destination, preferences):
        for key, value in preferences.items():
            if destination.get(key) != value:
                return False
        return True

    def iterate_plan(self, plan, preferences, budget):
        for i in range(len(plan)):
            for destination in self.destinations:
                if destination not in plan and self.match_preferences(destination, preferences) and self.calculate_cost(plan, destination) <= budget:
                    plan[i] = destination
                    break
        return plan

    def calculate_cost(self, plan, new_destination):
        return sum(destination['cost'] for destination in plan) + new_destination['cost']

# 사용 예시
destinations = [
    {"name": "Paris", "cost": 1000, "activity": "sightseeing"},
    {"name": "Tokyo", "cost": 1200, "activity": "shopping"},
    {"name": "New York", "cost": 900, "activity": "sightseeing"},
    {"name": "Sydney", "cost": 1100, "activity": "beach"},
]

preferences = {"activity": "sightseeing"}
budget = 2000

travel_agent = TravelAgent(destinations)
initial_plan = travel_agent.bootstrap_plan(preferences, budget)
print("초기 계획:", initial_plan)

refined_plan = travel_agent.iterate_plan(initial_plan, preferences, budget)
print("개선된 계획:", refined_plan)
```

#### 코드 설명

1. **초기화 (`__init__` 메서드)**: `TravelAgent` 클래스는 각각 이름, 비용, 활동 유형과 같은 속성을 가진 잠재적 여행지 목록으로 초기화됩니다.
2. **계획 부트스트래핑 (`bootstrap_plan` 메서드)**: 이 메서드는 고객의 선호도와 예산을 기반으로 초기 여행 계획을 만듭니다. 여행지 목록을 반복하고 고객의 선호도와 일치하고 예산 내에 있으면 계획에 추가합니다.
3. **선호도 일치 (`match_preferences` 메서드)**: 이 메서드는 여행지가 고객의 선호도와 일치하는지 확인합니다.
4. **계획 반복 (`iterate_plan` 메서드)**: 이 메서드는 계획의 각 여행지를 더 나은 일치 항목으로 교체하여 고객의 선호도와 예산 제약 조건을 고려하여 초기 계획을 개선합니다.
5. **비용 계산 (`calculate_cost` 메서드)**: 이 메서드는 새 여행지를 포함하여 현재 계획의 총 비용을 계산합니다.

#### 사용 예시

- **초기 계획**: 여행 에이전트는 시티투어에 대한 고객의 선호도와 $2000 예산을 기반으로 초기 계획을 만듭니다.
- **개선된 계획**: 여행 에이전트는 계획을 반복하여 고객의 선호도와 예산에 최적화되도록 합니다.

명확한 목표(예: 고객 만족도 최대화)로 계획을 부트스트래핑하고 계획을 개선하기 위해 반복함으로써 여행 에이전트는 고객을 위한 맞춤형 및 최적화된 여행 일정을 만들 수 있습니다. 이 접근 방식은 처음부터 여행 계획이 고객의 선호도와 예산에 부합하고 각 반복을 통해 개선되도록 합니다.

### 재순위 지정 및 점수 매기기를 위한 LLM 활용

대규모 언어 모델(LLM)은 검색된 문서나 생성된 응답의 관련성과 품질을 평가하여 재순위 지정 및 점수 매기기에 사용될 수 있습니다. 작동 방식은 다음과 같습니다:

- **검색 (Retrieval)**: 초기 검색 단계는 쿼리를 기반으로 후보 문서나 응답 세트를 가져옵니다.
- **재순위 지정 (Re-ranking)**: LLM은 이러한 후보를 평가하고 관련성과 품질에 따라 재순위를 지정합니다. 이 단계는 가장 관련성 높고 품질 좋은 정보가 먼저 표시되도록 합니다.
- **점수 매기기 (Scoring)**: LLM은 각 후보에게 관련성과 품질을 반영하는 점수를 할당합니다. 이는 사용자를 위한 최상의 응답이나 문서를 선택하는 데 도움이 됩니다.

재순위 지정 및 점수 매기기를 위해 LLM을 활용함으로써 시스템은 더 정확하고 상황에 맞는 정보를 제공하여 전반적인 사용자 경험을 향상시킬 수 있습니다.

다음은 여행 에이전트가 Python에서 사용자 선호도에 따라 여행지의 재순위를 지정하고 점수를 매기기 위해 대규모 언어 모델(LLM)을 사용하는 방법에 대한 예시입니다:

#### 시나리오 - 선호도 기반 여행

여행 에이전트는 고객의 선호도에 따라 최고의 여행지를 추천하려고 합니다. LLM은 가장 관련성 높은 옵션이 제시되도록 여행지의 재순위를 지정하고 점수를 매기는 데 도움을 줄 것입니다.

#### 단계:

1. 사용자 선호도를 수집합니다.
2. 잠재적인 여행지 목록을 검색합니다.
3. LLM을 사용하여 사용자 선호도에 따라 여행지의 재순위를 지정하고 점수를 매깁니다.

다음은 Azure OpenAI Services를 사용하도록 이전 예시를 업데이트하는 방법입니다:

#### 요구 사항

1. Azure 구독이 필요합니다.
2. Azure OpenAI 리소스를 만들고 API 키를 가져옵니다.

#### 예제 Python 코드

```python
import requests
import json

class TravelAgent:
    def __init__(self, destinations):
        self.destinations = destinations

    def get_recommendations(self, preferences, api_key, endpoint):
        # Azure OpenAI용 프롬프트 생성
        prompt = self.generate_prompt(preferences)

        # 요청을 위한 헤더 및 페이로드 정의
        headers = {
            'Content-Type': 'application/json',
            'Authorization': f'Bearer {api_key}'
        }
        payload = {
            "prompt": prompt,
            "max_tokens": 150,
            "temperature": 0.7
        }

        # Azure OpenAI API 호출하여 재순위 지정 및 점수 매겨진 여행지 가져오기
        response = requests.post(endpoint, headers=headers, json=payload)
        response_data = response.json()

        # 추천 항목 추출 및 반환
        recommendations = response_data['choices'][0]['text'].strip().split('\n')
        return recommendations

    def generate_prompt(self, preferences):
        prompt = "다음 사용자 선호도에 따라 여행지의 순위와 점수를 매깁니다:\n"
        for key, value in preferences.items():
            prompt += f"{key}: {value}\n"
        prompt += "\n여행지:\n"
        for destination in self.destinations:
            prompt += f"- {destination['name']}: {destination['description']}\n"
        return prompt

# 사용 예시
destinations = [
    {"name": "Paris", "description": "예술, 패션, 문화로 유명한 빛의 도시."},
    {"name": "Tokyo", "description": "현대성과 전통 사원으로 유명한 활기찬 도시."},
    {"name": "New York", "description": "잠들지 않는 도시, 상징적인 랜드마크와 다양한 문화."},
    {"name": "Sydney", "description": "오페라 하우스와 아름다운 해변으로 유명한 항구 도시."},
]

preferences = {"activity": "sightseeing", "culture": "diverse"}
api_key = 'your_azure_openai_api_key'
endpoint = 'https://your-endpoint.com/openai/deployments/your-deployment-name/completions?api-version=2022-12-01'

travel_agent = TravelAgent(destinations)
recommendations = travel_agent.get_recommendations(preferences, api_key, endpoint)
print("추천 여행지:")
for rec in recommendations:
    print(rec)
```

#### 코드 설명 - 선호도 기반 예약자

1. **초기화**: `TravelAgent` 클래스는 각각 이름과 설명과 같은 속성을 가진 잠재적 여행지 목록으로 초기화됩니다.
2. **추천 받기 (`get_recommendations` 메서드)**: 이 메서드는 사용자의 선호도를 기반으로 Azure OpenAI 서비스용 프롬프트를 생성하고 Azure OpenAI API에 HTTP POST 요청을 하여 재순위 지정 및 점수 매겨진 여행지를 가져옵니다.
3. **프롬프트 생성 (`generate_prompt` 메서드)**: 이 메서드는 사용자의 선호도와 여행지 목록을 포함하여 Azure OpenAI용 프롬프트를 구성합니다. 프롬프트는 모델이 제공된 선호도에 따라 여행지의 재순위를 지정하고 점수를 매기도록 안내합니다.
4. **API 호출**: `requests` 라이브러리는 Azure OpenAI API 엔드포인트에 HTTP POST 요청을 하는 데 사용됩니다. 응답에는 재순위 지정 및 점수 매겨진 여행지가 포함됩니다.
5. **사용 예시**: 여행 에이전트는 사용자 선호도(예: 시티투어 및 다양한 문화에 대한 관심)를 수집하고 Azure OpenAI 서비스를 사용하여 여행지에 대한 재순위 지정 및 점수 매겨진 추천을 받습니다.

`your_azure_openai_api_key`를 실제 Azure OpenAI API 키로 바꾸고 `https://your-endpoint.com/...`를 Azure OpenAI 배포의 실제 엔드포인트 URL로 바꾸십시오.

재순위 지정 및 점수 매기기에 LLM을 활용함으로써 여행 에이전트는 고객에게 더 개인화되고 관련성 높은 여행 추천을 제공하여 전반적인 경험을 향상시킬 수 있습니다.

### RAG: 프롬프트 기법 vs 도구

RAG(Retrieval-Augmented Generation)는 AI 에이전트 개발에서 프롬프트 기법이자 도구가 될 수 있습니다. 이 둘의 차이점을 이해하면 프로젝트에서 RAG를 더 효과적으로 활용하는 데 도움이 될 수 있습니다.

#### 프롬프트 기법으로서의 RAG

**무엇인가요?**

- 프롬프트 기법으로서 RAG는 대규모 말뭉치나 데이터베이스에서 관련 정보를 검색하도록 안내하는 특정 쿼리나 프롬프트를 공식화하는 것을 포함합니다. 이 정보는 응답이나 행동을 생성하는 데 사용됩니다.

**작동 방식:**

1. **프롬프트 공식화**: 당면한 작업이나 사용자 입력에 따라 잘 구조화된 프롬프트 또는 쿼리를 만듭니다.
2. **정보 검색**: 프롬프트를 사용하여 기존 지식 베이스나 데이터 세트에서 관련 데이터를 검색합니다.
3. **응답 생성**: 검색된 정보를 생성형 AI 모델과 결합하여 포괄적이고 일관된 응답을 생성합니다.

**여행 에이전트의 예시**:

- 사용자 입력: "파리에서 박물관을 방문하고 싶어요."
- 프롬프트: "파리 최고의 박물관 찾기."
- 검색된 정보: 루브르 박물관, 오르세 미술관 등에 대한 세부 정보.
- 생성된 응답: "파리의 주요 박물관은 다음과 같습니다: 루브르 박물관, 오르세 미술관, 퐁피두 센터."

#### 도구로서의 RAG

**무엇인가요?**

- 도구로서 RAG는 검색 및 생성 프로세스를 자동화하는 통합 시스템으로, 개발자가 각 쿼리에 대해 수동으로 프롬프트를 작성하지 않고도 복잡한 AI 기능을 구현할 수 있도록 합니다.

**작동 방식:**

1. **통합**: RAG를 AI 에이전트의 아키텍처 내에 내장하여 검색 및 생성 작업을 자동으로 처리할 수 있도록 합니다.
2. **자동화**: 도구는 사용자 입력 수신부터 최종 응답 생성까지 전체 프로세스를 관리하며, 각 단계에 대해 명시적인 프롬프트가 필요하지 않습니다.
3. **효율성**: 검색 및 생성 프로세스를 간소화하여 에이전트의 성능을 향상시켜 더 빠르고 정확한 응답을 가능하게 합니다.

**여행 에이전트의 예시**:

- 사용자 입력: "파리에서 박물관을 방문하고 싶어요."
- RAG 도구: 자동으로 박물관에 대한 정보를 검색하고 응답을 생성합니다.
- 생성된 응답: "파리의 주요 박물관은 다음과 같습니다: 루브르 박물관, 오르세 미술관, 퐁피두 센터."

### 비교

| 측면                   | 프롬프트 기법                                       | 도구                                              |
| :--------------------- | :-------------------------------------------------- | :------------------------------------------------ |
| **수동 vs 자동** | 각 쿼리에 대해 수동으로 프롬프트를 작성해야 합니다. | 검색 및 생성을 위한 자동화된 프로세스입니다.      |
| **제어**         | 검색 프로세스에 대한 더 많은 제어를 제공합니다.     | 검색 및 생성을 간소화하고 자동화합니다.           |
| **유연성**       | 특정 요구 사항에 따라 맞춤형 프롬프트를 허용합니다. | 대규모 구현에 더 효율적입니다.                    |
| **복잡성**       | 프롬프트를 만들고 조정해야 합니다.                  | AI 에이전트의 아키텍처 내에 통합하기 더 쉽습니다. |

### 실용적인 예시

**프롬프트 기법 예시:**

```python
def search_museums_in_paris():
    prompt = "파리 최고의 박물관 찾기"
    search_results = search_web(prompt)
    return search_results

museums = search_museums_in_paris()
print("파리 주요 박물관:", museums)
```

**도구 예시:**

```python
class Travel_Agent:
    def __init__(self):
        self.rag_tool = RAGTool()

    def get_museums_in_paris(self):
        user_input = "파리에서 박물관을 방문하고 싶어요."
        response = self.rag_tool.retrieve_and_generate(user_input)
        return response

travel_agent = Travel_Agent()
museums = travel_agent.get_museums_in_paris()
print("파리 주요 박물관:", museums)
```

### 관련성 평가

관련성 평가는 AI 에이전트 성능의 중요한 측면입니다. 이는 에이전트가 검색하고 생성한 정보가 사용자에게 적절하고 정확하며 유용하도록 보장합니다. AI 에이전트에서 관련성을 평가하는 방법을 실용적인 예시와 기술을 포함하여 살펴보겠습니다.

#### 관련성 평가의 핵심 개념

1. **컨텍스트 인식 (Context Awareness)**:
   - 에이전트는 관련 정보를 검색하고 생성하기 위해 사용자 쿼리의 컨텍스트를 이해해야 합니다.
   - 예시: 사용자가 "파리 최고의 레스토랑"을 묻는 경우 에이전트는 사용자의 선호도(예: 요리 유형, 예산)를 고려해야 합니다.
2. **정확성 (Accuracy)**:
   - 에이전트가 제공하는 정보는 사실적으로 정확하고 최신이어야 합니다.
   - 예시: 오래되었거나 문을 닫은 옵션이 아닌, 현재 영업 중이고 좋은 리뷰를 받은 레스토랑을 추천합니다.
3. **사용자 의도 (User Intent)**:
   - 에이전트는 가장 관련성 높은 정보를 제공하기 위해 쿼리 뒤에 숨은 사용자의 의도를 추론해야 합니다.
   - 예시: 사용자가 "저렴한 호텔"을 요청하는 경우 에이전트는 저렴한 옵션을 우선시해야 합니다.
4. **피드백 루프 (Feedback Loop)**:
   - 사용자 피드백을 지속적으로 수집하고 분석하면 에이전트가 관련성 평가 프로세스를 개선하는 데 도움이 됩니다.
   - 예시: 이전 추천에 대한 사용자 평가 및 피드백을 통합하여 향후 응답을 개선합니다.

#### 관련성 평가를 위한 실용적인 기술

1. **관련성 점수 매기기**:
   - 검색된 각 항목이 사용자의 쿼리 및 선호도와 얼마나 잘 일치하는지에 따라 관련성 점수를 할당합니다.
   - 예시:

     ```python
     def relevance_score(item, query):
         score = 0
         if item['category'] in query['interests']:
             score += 1
         if item['price'] <= query['budget']:
             score += 1
         if item['location'] == query['destination']:
             score += 1
         return score
     ```
2. **필터링 및 순위 지정**:
   - 관련 없는 항목을 필터링하고 관련성 점수에 따라 나머지 항목의 순위를 지정합니다.
   - 예시:

     ```python
     def filter_and_rank(items, query):
         ranked_items = sorted(items, key=lambda item: relevance_score(item, query), reverse=True)
         return ranked_items[:10]  # 상위 10개 관련 항목 반환
     ```
3. **자연어 처리 (NLP)**:
   - NLP 기술을 사용하여 사용자의 쿼리를 이해하고 관련 정보를 검색합니다.
   - 예시:

     ```python
     def process_query(query):
         # NLP를 사용하여 사용자 쿼리에서 핵심 정보 추출
         processed_query = nlp(query)
         return processed_query
     ```
4. **사용자 피드백 통합**:
   - 제공된 추천에 대한 사용자 피드백을 수집하고 이를 사용하여 향후 관련성 평가를 조정합니다.
   - 예시:

     ```python
     def adjust_based_on_feedback(feedback, items):
         for item in items:
             if item['name'] in feedback['liked']:
                 item['relevance'] += 1
             if item['name'] in feedback['disliked']:
                 item['relevance'] -= 1
         return items
     ```

#### 예시: 여행 에이전트의 관련성 평가

여행 에이전트가 여행 추천의 관련성을 평가할 수 있는 방법에 대한 실용적인 예시입니다:

```python
class Travel_Agent:
    def __init__(self):
        self.user_preferences = {}
        self.experience_data = []

    def gather_preferences(self, preferences):
        self.user_preferences = preferences

    def retrieve_information(self):
        flights = search_flights(self.user_preferences)
        hotels = search_hotels(self.user_preferences)
        attractions = search_attractions(self.user_preferences)
        return flights, hotels, attractions

    def generate_recommendations(self):
        flights, hotels, attractions = self.retrieve_information()
        ranked_hotels = self.filter_and_rank(hotels, self.user_preferences)
        itinerary = create_itinerary(flights, ranked_hotels, attractions)
        return itinerary

    def filter_and_rank(self, items, query):
        ranked_items = sorted(items, key=lambda item: self.relevance_score(item, query), reverse=True)
        return ranked_items[:10]  # 상위 10개 관련 항목 반환

    def relevance_score(self, item, query):
        score = 0
        if item['category'] in query['interests']:
            score += 1
        if item['price'] <= query['budget']:
            score += 1
        if item['location'] == query['destination']:
            score += 1
        return score

    def adjust_based_on_feedback(self, feedback, items):
        for item in items:
            if item['name'] in feedback['liked']:
                item['relevance'] += 1
            if item['name'] in feedback['disliked']:
                item['relevance'] -= 1
        return items

# 사용 예시
travel_agent = Travel_Agent()
preferences = {
    "destination": "Paris",
    "dates": "2025-04-01 to 2025-04-10",
    "budget": "moderate",
    "interests": ["museums", "cuisine"]
}
travel_agent.gather_preferences(preferences)
itinerary = travel_agent.generate_recommendations()
print("제안된 일정:", itinerary)
feedback = {"liked": ["Louvre Museum"], "disliked": ["Eiffel Tower (too crowded)"]}
updated_items = travel_agent.adjust_based_on_feedback(feedback, itinerary['hotels'])
print("피드백이 반영된 업데이트 일정:", updated_items)
```

### 의도를 가진 검색 (Search with Intent)

의도를 가진 검색은 사용자 쿼리 뒤에 숨은 근본적인 목적이나 목표를 이해하고 해석하여 가장 관련성 높고 유용한 정보를 검색하고 생성하는 것을 포함합니다. 이 접근 방식은 단순히 키워드를 일치시키는 것을 넘어 사용자의 실제 필요와 컨텍스트를 파악하는 데 중점을 둡니다.

#### 의도를 가진 검색의 핵심 개념

1. **사용자 의도 이해**:
   - 사용자 의도는 정보 탐색(informational), 탐색(navigational), 트랜잭션(transactional)의 세 가지 주요 유형으로 분류할 수 있습니다.
     - **정보 탐색 의도**: 사용자가 주제에 대한 정보를 찾습니다 (예: "파리 최고의 박물관은 어디인가요?").
     - **탐색 의도**: 사용자가 특정 웹사이트나 페이지로 이동하려고 합니다 (예: "루브르 박물관 공식 웹사이트").
     - **트랜잭션 의도**: 사용자가 항공편 예약이나 구매와 같은 트랜잭션을 수행하려고 합니다 (예: "파리行 항공편 예약").
2. **컨텍스트 인식**:
   - 사용자 쿼리의 컨텍스트를 분석하면 의도를 정확하게 식별하는 데 도움이 됩니다. 여기에는 이전 상호작용, 사용자 선호도 및 현재 쿼리의 특정 세부 사항을 고려하는 것이 포함됩니다.
3. **자연어 처리 (NLP)**:
   - NLP 기술은 사용자가 제공한 자연어 쿼리를 이해하고 해석하는 데 사용됩니다. 여기에는 개체 인식, 감정 분석, 쿼리 구문 분석과 같은 작업이 포함됩니다.
4. **개인화**:
   - 사용자의 기록, 선호도 및 피드백을 기반으로 검색 결과를 개인화하면 검색된 정보의 관련성이 향상됩니다.

#### 실용적인 예시: 여행 에이전트의 의도를 가진 검색

여행 에이전트를 예로 들어 의도를 가진 검색이 어떻게 구현될 수 있는지 살펴보겠습니다.

1. **사용자 선호도 수집**

   ```python
   class Travel_Agent:
       def __init__(self):
           self.user_preferences = {}

       def gather_preferences(self, preferences):
           self.user_preferences = preferences
   ```
2. **사용자 의도 이해**

   ```python
   def identify_intent(query):
       if "book" in query or "purchase" in query:
           return "transactional"
       elif "website" in query or "official" in query:
           return "navigational"
       else:
           return "informational"
   ```
3. **컨텍스트 인식**

   ```python
   def analyze_context(query, user_history):
       # 현재 쿼리와 사용자 기록을 결합하여 컨텍스트 이해
       context = {
           "current_query": query,
           "user_history": user_history
       }
       return context
   ```
4. **검색 및 결과 개인화**

   ```python
   def search_with_intent(query, preferences, user_history):
       intent = identify_intent(query)
       context = analyze_context(query, user_history)
       if intent == "informational":
           search_results = search_information(query, preferences)
       elif intent == "navigational":
           search_results = search_navigation(query)
       elif intent == "transactional":
           search_results = search_transaction(query, preferences)
       personalized_results = personalize_results(search_results, user_history)
       return personalized_results

   def search_information(query, preferences):
       # 정보 탐색 의도를 위한 예제 검색 로직
       results = search_web(f"best {preferences['interests']} in {preferences['destination']}")
       return results

   def search_navigation(query):
       # 탐색 의도를 위한 예제 검색 로직
       results = search_web(query)
       return results

   def search_transaction(query, preferences):
       # 트랜잭션 의도를 위한 예제 검색 로직
       results = search_web(f"book {query} to {preferences['destination']}")
       return results

   def personalize_results(results, user_history):
       # 예제 개인화 로직
       personalized = [result for result in results if result not in user_history]
       return personalized[:10]  # 상위 10개 개인화된 결과 반환
   ```
5. **사용 예시**

   ```python
   travel_agent = Travel_Agent()
   preferences = {
       "destination": "Paris",
       "interests": ["museums", "cuisine"]
   }
   travel_agent.gather_preferences(preferences)
   user_history = ["Louvre Museum website", "Book flight to Paris"]
   query = "best museums in Paris"
   results = search_with_intent(query, preferences, user_history)
   print("검색 결과:", results)
   ```

---

## 💻 도구로서의 코드 생성

코드 생성 에이전트는 AI 모델을 사용하여 코드를 작성하고 실행함으로써 복잡한 문제를 해결하고 작업을 자동화합니다.

### 코드 생성 에이전트

코드 생성 에이전트는 생성형 AI 모델을 사용하여 코드를 작성하고 실행합니다. 이러한 에이전트는 다양한 프로그래밍 언어로 코드를 생성하고 실행하여 복잡한 문제를 해결하고, 작업을 자동화하며, 귀중한 통찰력을 제공할 수 있습니다.

#### 실용적인 응용 분야

1. **자동화된 코드 생성**: 데이터 분석, 웹 스크래핑 또는 기계 학습과 같은 특정 작업에 대한 코드 스니펫을 생성합니다.
2. **RAG로서의 SQL**: SQL 쿼리를 사용하여 데이터베이스에서 데이터를 검색하고 조작합니다.
3. **문제 해결**: 알고리즘 최적화 또는 데이터 분석과 같은 특정 문제를 해결하기 위한 코드를 생성하고 실행합니다.

#### 예시: 데이터 분석을 위한 코드 생성 에이전트

코드 생성 에이전트를 설계한다고 상상해 보세요. 작동 방식은 다음과 같습니다:

1. **작업**: 데이터 세트를 분석하여 추세와 패턴을 식별합니다.
2. **단계**:
   - 데이터 세트를 데이터 분석 도구에 로드합니다.
   - 데이터를 필터링하고 집계하는 SQL 쿼리를 생성합니다.
   - 쿼리를 실행하고 결과를 검색합니다.
   - 결과를 사용하여 시각화 및 통찰력을 생성합니다.
3. **필요한 리소스**: 데이터 세트 액세스, 데이터 분석 도구 및 SQL 기능.
4. **경험**: 과거 분석 결과를 사용하여 향후 분석의 정확성과 관련성을 개선합니다.

### 예시: 여행 에이전트를 위한 코드 생성 에이전트

이 예시에서는 코드 생성 에이전트인 여행 에이전트를 설계하여 코드를 생성하고 실행함으로써 사용자의 여행 계획을 지원합니다. 이 에이전트는 여행 옵션 가져오기, 결과 필터링, 생성형 AI를 사용한 일정 컴파일과 같은 작업을 처리할 수 있습니다.

#### 코드 생성 에이전트 개요

1. **사용자 선호도 수집**: 목적지, 여행 날짜, 예산, 관심사와 같은 사용자 입력을 수집합니다.
2. **데이터 가져오기 위한 코드 생성**: 항공편, 호텔 및 명소에 대한 데이터를 검색하는 코드 스니펫을 생성합니다.
3. **생성된 코드 실행**: 생성된 코드를 실행하여 실시간 정보를 가져옵니다.
4. **일정 생성**: 가져온 데이터를 개인화된 여행 계획으로 정리합니다.
5. **피드백 기반 조정**: 사용자 피드백을 받고 필요한 경우 결과를 개선하기 위해 코드를 재생성합니다.

#### 단계별 구현

1. **사용자 선호도 수집**

   ```python
   class Travel_Agent:
       def __init__(self):
           self.user_preferences = {}

       def gather_preferences(self, preferences):
           self.user_preferences = preferences
   ```
2. **데이터 가져오기 위한 코드 생성**

   ```python
   def generate_code_to_fetch_data(preferences):
       # 예시: 사용자 선호도에 따라 항공편을 검색하는 코드 생성
       code = f"""
   def search_flights():
       import requests
       response = requests.get('https://api.example.com/flights', params={preferences})
       return response.json()
       """
       return code

   def generate_code_to_fetch_hotels(preferences):
       # 예시: 사용자 선호도에 따라 호텔을 검색하는 코드 생성
       code = f"""
   def search_hotels():
       import requests
       response = requests.get('https://api.example.com/hotels', params={preferences})
       return response.json()
       """
       return code
   ```
3. **생성된 코드 실행**

   ```python
   def execute_code(code):
       # exec를 사용하여 생성된 코드 실행
       exec(code)
       result = locals()
       return result

   travel_agent = Travel_Agent()
   preferences = {
       "destination": "Paris",
       "dates": "2025-04-01 to 2025-04-10",
       "budget": "moderate",
       "interests": ["museums", "cuisine"]
   }
   travel_agent.gather_preferences(preferences)

   flight_code = generate_code_to_fetch_data(preferences)
   hotel_code = generate_code_to_fetch_hotels(preferences)

   flights = execute_code(flight_code)
   hotels = execute_code(hotel_code)

   print("항공편 옵션:", flights)
   print("호텔 옵션:", hotels)
   ```
4. **일정 생성**

   ```python
   def generate_itinerary(flights, hotels, attractions):
       itinerary = {
           "flights": flights,
           "hotels": hotels,
           "attractions": attractions
       }
       return itinerary

   attractions = search_attractions(preferences)
   itinerary = generate_itinerary(flights, hotels, attractions)
   print("제안된 일정:", itinerary)
   ```
5. **피드백 기반 조정**

   ```python
   def adjust_based_on_feedback(feedback, preferences):
       # 사용자 피드백에 따라 선호도 조정
       if "liked" in feedback:
           preferences["favorites"] = feedback["liked"]
       if "disliked" in feedback:
           preferences["avoid"] = feedback["disliked"]
       return preferences

   feedback = {"liked": ["Louvre Museum"], "disliked": ["Eiffel Tower (too crowded)"]}
   updated_preferences = adjust_based_on_feedback(feedback, preferences)

   # 업데이트된 선호도로 코드 재생성 및 실행
   updated_flight_code = generate_code_to_fetch_data(updated_preferences)
   updated_hotel_code = generate_code_to_fetch_hotels(updated_preferences)

   updated_flights = execute_code(updated_flight_code)
   updated_hotels = execute_code(updated_hotel_code)

   updated_itinerary = generate_itinerary(updated_flights, updated_hotels, attractions)
   print("업데이트된 일정:", updated_itinerary)
   ```

### 환경 인식 및 추론 활용

테이블 스키마를 기반으로 환경 인식과 추론을 활용하면 실제로 쿼리 생성 프로세스를 향상시킬 수 있습니다.

작동 방식의 예시는 다음과 같습니다:

1. **스키마 이해**: 시스템은 테이블의 스키마를 이해하고 이 정보를 사용하여 쿼리 생성의 기반을 마련합니다.
2. **피드백 기반 조정**: 시스템은 피드백에 따라 사용자 선호도를 조정하고 스키마에서 업데이트해야 할 필드에 대해 추론합니다.
3. **쿼리 생성 및 실행**: 시스템은 새로운 선호도에 따라 업데이트된 항공편 및 호텔 데이터를 가져오기 위한 쿼리를 생성하고 실행합니다.

다음은 이러한 개념을 통합한 업데이트된 Python 코드 예시입니다:

```python
def adjust_based_on_feedback(feedback, preferences, schema):
    # 사용자 피드백에 따라 선호도 조정
    if "liked" in feedback:
        preferences["favorites"] = feedback["liked"]
    if "disliked" in feedback:
        preferences["avoid"] = feedback["disliked"]
    # 스키마를 기반으로 다른 관련 선호도 조정을 위한 추론
    for field in schema:
        if field in preferences:
            preferences[field] = adjust_based_on_environment(feedback, field, schema)
    return preferences

def adjust_based_on_environment(feedback, field, schema):
    # 스키마 및 피드백에 따라 선호도를 조정하는 사용자 정의 로직
    if field in feedback["liked"]:
        return schema[field]["positive_adjustment"]
    elif field in feedback["disliked"]:
        return schema[field]["negative_adjustment"]
    return schema[field]["default"]

def generate_code_to_fetch_data(preferences):
    # 업데이트된 선호도에 따라 항공편 데이터를 가져오는 코드 생성
    return f"fetch_flights(preferences={preferences})"

def generate_code_to_fetch_hotels(preferences):
    # 업데이트된 선호도에 따라 호텔 데이터를 가져오는 코드 생성
    return f"fetch_hotels(preferences={preferences})"

def execute_code(code):
    # 코드 실행 시뮬레이션 및 모의 데이터 반환
    return {"data": f"Executed: {code}"}

def generate_itinerary(flights, hotels, attractions):
    # 항공편, 호텔, 명소를 기반으로 일정 생성
    return {"flights": flights, "hotels": hotels, "attractions": attractions}

# 예제 스키마
schema = {
    "favorites": {"positive_adjustment": "increase", "negative_adjustment": "decrease", "default": "neutral"},
    "avoid": {"positive_adjustment": "decrease", "negative_adjustment": "increase", "default": "neutral"}
}

# 사용 예시
preferences = {"favorites": "sightseeing", "avoid": "crowded places"}
feedback = {"liked": ["Louvre Museum"], "disliked": ["Eiffel Tower (too crowded)"]}
updated_preferences = adjust_based_on_feedback(feedback, preferences, schema)

# 업데이트된 선호도로 코드 재생성 및 실행
updated_flight_code = generate_code_to_fetch_data(updated_preferences)
updated_hotel_code = generate_code_to_fetch_hotels(updated_preferences)

updated_flights = execute_code(updated_flight_code)
updated_hotels = execute_code(updated_hotel_code)

updated_itinerary = generate_itinerary(updated_flights, updated_hotels, feedback["liked"])
print("업데이트된 일정:", updated_itinerary)
```

#### 설명 - 피드백 기반 예약

1. **스키마 인식**: `schema` 딕셔너리는 피드백에 따라 선호도를 조정하는 방법을 정의합니다. 여기에는 `favorites` 및 `avoid`와 같은 필드와 해당 조정 사항이 포함됩니다.
2. **선호도 조정 (`adjust_based_on_feedback` 메서드)**: 이 메서드는 사용자 피드백과 스키마에 따라 선호도를 조정합니다.
3. **환경 기반 조정 (`adjust_based_on_environment` 메서드)**: 이 메서드는 스키마와 피드백에 따라 조정 사항을 사용자 지정합니다.
4. **쿼리 생성 및 실행**: 시스템은 조정된 선호도에 따라 업데이트된 항공편 및 호텔 데이터를 가져오는 코드를 생성하고 이러한 쿼리의 실행을 시뮬레이션합니다.
5. **일정 생성**: 시스템은 새로운 항공편, 호텔 및 명소 데이터를 기반으로 업데이트된 일정을 만듭니다.

시스템을 환경 인식으로 만들고 스키마에 따라 추론함으로써 더 정확하고 관련성 높은 쿼리를 생성하여 더 나은 여행 추천과 더 개인화된 사용자 경험을 이끌어낼 수 있습니다.

### RAG(Retrieval-Augmented Generation) 기술로서 SQL 사용

SQL(구조화 질의어)은 데이터베이스와 상호 작용하기 위한 강력한 도구입니다. RAG 접근 방식의 일부로 사용될 때 SQL은 AI 에이전트의 응답이나 행동을 생성하기 위해 데이터베이스에서 관련 데이터를 검색할 수 있습니다. 여행 에이전트의 맥락에서 SQL이 RAG 기술로 어떻게 사용될 수 있는지 살펴보겠습니다.

#### 핵심 개념

1. **데이터베이스 상호 작용**:
   - SQL은 데이터베이스를 쿼리하고, 관련 정보를 검색하며, 데이터를 조작하는 데 사용됩니다.
   - 예시: 여행 데이터베이스에서 항공편 세부 정보, 호텔 정보 및 명소를 가져옵니다.
2. **RAG와의 통합**:
   - SQL 쿼리는 사용자 입력 및 선호도에 따라 생성됩니다.
   - 그런 다음 검색된 데이터는 개인화된 추천이나 행동을 생성하는 데 사용됩니다.
3. **동적 쿼리 생성**:
   - AI 에이전트는 컨텍스트와 사용자 요구에 따라 동적 SQL 쿼리를 생성합니다.
   - 예시: 예산, 날짜 및 관심사에 따라 결과를 필터링하기 위해 SQL 쿼리를 사용자 지정합니다.

#### 응용 분야

- **자동화된 코드 생성**: 특정 작업을 위한 코드 스니펫을 생성합니다.
- **RAG로서의 SQL**: SQL 쿼리를 사용하여 데이터를 조작합니다.
- **문제 해결**: 문제를 해결하기 위한 코드를 생성하고 실행합니다.

**예시**:
데이터 분석 에이전트:

1. **작업**: 데이터 세트를 분석하여 추세를 찾습니다.
2. **단계**:
   - 데이터 세트를 로드합니다.
   - 데이터를 필터링하기 위한 SQL 쿼리를 생성합니다.
   - 쿼리를 실행하고 결과를 검색합니다.
   - 시각화 및 통찰력을 생성합니다.
3. **리소스**: 데이터 세트 액세스, SQL 기능.
4. **경험**: 과거 결과를 사용하여 향후 분석을 개선합니다.

#### 실용적인 예시: 여행 에이전트에서 SQL 사용

1. **사용자 선호도 수집**

   ```python
   class Travel_Agent:
       def __init__(self):
           self.user_preferences = {}

       def gather_preferences(self, preferences):
           self.user_preferences = preferences
   ```
2. **SQL 쿼리 생성**

   ```python
   def generate_sql_query(table, preferences):
       query = f"SELECT * FROM {table} WHERE "
       conditions = []
       for key, value in preferences.items():
           conditions.append(f"{key}='{value}'")
       query += " AND ".join(conditions)
       return query
   ```
3. **SQL 쿼리 실행**

   ```python
   import sqlite3

   def execute_sql_query(query, database="travel.db"):
       connection = sqlite3.connect(database)
       cursor = connection.cursor()
       cursor.execute(query)
       results = cursor.fetchall()
       connection.close()
       return results
   ```
4. **추천 생성**

   ```python
   def generate_recommendations(preferences):
       flight_query = generate_sql_query("flights", preferences)
       hotel_query = generate_sql_query("hotels", preferences)
       attraction_query = generate_sql_query("attractions", preferences)

       flights = execute_sql_query(flight_query)
       hotels = execute_sql_query(hotel_query)
       attractions = execute_sql_query(attraction_query)

       itinerary = {
           "flights": flights,
           "hotels": hotels,
           "attractions": attractions
       }
       return itinerary

   travel_agent = Travel_Agent()
   preferences = {
       "destination": "Paris",
       "dates": "2025-04-01 to 2025-04-10",
       "budget": "moderate",
       "interests": ["museums", "cuisine"]
   }
   travel_agent.gather_preferences(preferences)
   itinerary = generate_recommendations(preferences)
   print("제안된 일정:", itinerary)
   ```

#### 예제 SQL 쿼리

1. **항공편 쿼리**

   ```sql
   SELECT * FROM flights WHERE destination='Paris' AND dates='2025-04-01 to 2025-04-10' AND budget='moderate';
   ```
2. **호텔 쿼리**

   ```sql
   SELECT * FROM hotels WHERE destination='Paris' AND budget='moderate';
   ```
3. **명소 쿼리**

   ```sql
   SELECT * FROM attractions WHERE destination='Paris' AND interests='museums, cuisine';
   ```

RAG(Retrieval-Augmented Generation) 기술의 일부로 SQL을 활용함으로써 여행 에이전트와 같은 AI 에이전트는 관련 데이터를 동적으로 검색하고 활용하여 정확하고 개인화된 추천을 제공할 수 있습니다.

### 메타인지의 예시

그렇다면 메타인지의 구현을 보여주기 위해, 문제를 해결하는 동안 *자신의 의사 결정 과정을 반성*하는 간단한 에이전트를 만들어 보겠습니다. 이 예시를 위해 에이전트가 가격과 품질의 조합을 기반으로 호텔을 선택하려고 시도하지만, 자신의 추론을 평가하고 오류나 차선책 선택 시 전략을 조정하는 시스템을 구축할 것입니다.

우리는 에이전트가 가격과 품질의 조합을 기반으로 호텔을 선택하지만, 자신의 결정을 "반성"하고 그에 따라 조정하는 기본적인 예시를 사용하여 이를 시뮬레이션할 것입니다.

#### 이것이 메타인지를 어떻게 보여주는가:

1. **초기 결정**: 에이전트는 품질 영향을 이해하지 못한 채 가장 저렴한 호텔을 선택합니다.
2. **반성 및 평가**: 초기 선택 후, 에이전트는 사용자 피드백을 사용하여 호텔이 "나쁜" 선택인지 확인합니다. 호텔의 품질이 너무 낮다는 것을 알게 되면, 자신의 추론에 대해 반성합니다.
3. **전략 조정**: 에이전트는 자신의 반성에 따라 전략을 조정합니다. "가장 저렴한"에서 "최고 품질"로 전환하여 향후 반복에서 의사 결정 과정을 개선합니다.

예시는 다음과 같습니다:

```python
class HotelRecommendationAgent:
    def __init__(self):
        self.previous_choices = []  # 이전에 선택한 호텔 저장
        self.corrected_choices = []  # 수정된 선택 저장
        self.recommendation_strategies = ['cheapest', 'highest_quality']  # 사용 가능한 전략

    def recommend_hotel(self, hotels, strategy):
        """
        선택한 전략에 따라 호텔을 추천합니다.
        전략은 'cheapest' 또는 'highest_quality'일 수 있습니다.
        """
        if strategy == 'cheapest':
            recommended = min(hotels, key=lambda x: x['price'])
        elif strategy == 'highest_quality':
            recommended = max(hotels, key=lambda x: x['quality'])
        else:
            recommended = None
        self.previous_choices.append((strategy, recommended))
        return recommended

    def reflect_on_choice(self):
        """
        마지막 선택에 대해 반성하고 에이전트가 전략을 조정해야 하는지 결정합니다.
        에이전트는 이전 선택이 나쁜 결과로 이어졌는지 고려합니다.
        """
        if not self.previous_choices:
            return "아직 선택이 없습니다."

        last_choice_strategy, last_choice = self.previous_choices[-1]
        # 마지막 선택이 좋았는지 나빴는지 알려주는 사용자 피드백이 있다고 가정합니다.
        user_feedback = self.get_user_feedback(last_choice)

        if user_feedback == "bad":
            # 이전 선택이 만족스럽지 않으면 전략 조정
            new_strategy = 'highest_quality' if last_choice_strategy == 'cheapest' else 'cheapest'
            self.corrected_choices.append((new_strategy, last_choice))
            return f"선택에 대해 반성 중입니다. 전략을 {new_strategy}(으)로 조정합니다."
        else:
            return "선택이 좋았습니다. 조정이 필요하지 않습니다."

    def get_user_feedback(self, hotel):
        """
        호텔 속성을 기반으로 사용자 피드백을 시뮬레이션합니다.
        간단히 하기 위해 호텔이 너무 저렴하거나 품질이 7 미만이면 피드백은 "bad"입니다.
        """
        if hotel['price'] < 100 or hotel['quality'] < 7:
            return "bad"
        return "good"

# 호텔 목록 시뮬레이션 (가격 및 품질)
hotels = [
    {'name': 'Budget Inn', 'price': 80, 'quality': 6},
    {'name': 'Comfort Suites', 'price': 120, 'quality': 8},
    {'name': 'Luxury Stay', 'price': 200, 'quality': 9}
]

# 에이전트 생성
agent = HotelRecommendationAgent()

# 1단계: 에이전트가 "cheapest" 전략을 사용하여 호텔 추천
recommended_hotel = agent.recommend_hotel(hotels, 'cheapest')
print(f"추천 호텔 (cheapest): {recommended_hotel['name']}")

# 2단계: 에이전트가 선택에 대해 반성하고 필요한 경우 전략 조정
reflection_result = agent.reflect_on_choice()
print(reflection_result)

# 3단계: 에이전트가 조정된 전략을 사용하여 다시 추천
adjusted_recommendation = agent.recommend_hotel(hotels, 'highest_quality')
print(f"조정된 호텔 추천 (highest_quality): {adjusted_recommendation['name']}")
```

#### 에이전트의 메타인지 능력

여기서 핵심은 에이전트의 능력입니다:

- 이전 선택과 의사 결정 과정을 평가합니다.
- 그 반성에 기반하여 전략을 조정합니다. 즉, 메타인지가 실제로 작동하는 것입니다.

이는 시스템이 내부 피드백에 따라 추론 과정을 조정할 수 있는 메타인지의 간단한 형태입니다.

---

## 📝 결론

메타인지는 AI 에이전트의 기능을 크게 향상시킬 수 있는 강력한 도구입니다. 메타인지 과정을 통합함으로써 더 지능적이고, 적응력 있으며, 효율적인 에이전트를 설계할 수 있습니다. 추가 자료를 사용하여 AI 에이전트의 메타인지라는 매혹적인 세계를 더 깊이 탐구해 보시기 바랍니다.

---

## ❓ 메타인지 디자인 패턴에 대해 더 궁금한 점이 있나요?

[Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하여 다른 학습자들을 만나고, 오피스 아워에 참여하고 AI Agents에 대한 질문에 대한 답변을 받아보세요.

---

## 📚 레슨 목차

### ⬅️ 이전 레슨

[8강: 다중 에이전트 디자인 패턴](../08-multi-agent/README.md)

### ➡️ 다음 레슨

[10강: 프로덕션 환경의 AI 에이전트](../10-ai-agents-production/README.md)

---

*이 가이드가 여러분의 AI 에이전트가 스스로 생각하고 성장하는 지능적인 시스템으로 발전하는 데 도움이 되길 바랍니다!* 🧠
