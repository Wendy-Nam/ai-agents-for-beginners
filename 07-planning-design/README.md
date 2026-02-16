
[![계획 디자인 패턴](./images/lesson-7-thumbnail.png)](https://youtu.be/kPfJ2BrBCMY?si=9pYpPXp0sSbK91Dr)

> _(👆 이미지를 클릭하면 이번 레슨의 강의 영상을 볼 수 있어요!)_

# 🗺️ 계획(Planning) 디자인 패턴 - 복잡한 작업도 척척! AI 에이전트의 전략가

## 🧐 소개

이번 레슨에서는 다음 내용을 다룰 예정이에요:

- 명확한 전체 목표를 정의하고 복잡한 작업을 관리 가능한 하위 작업으로 나누는 방법
- 더 안정적이고 기계가 읽기 쉬운 응답을 위한 구조화된 출력 활용하기
- 동적인 작업과 예상치 못한 입력을 처리하기 위한 이벤트 기반 접근 방식 적용하기

## 📚 학습 목표

이번 레슨을 완료하면 다음을 이해하게 됩니다:

- AI 에이전트의 전체적인 목표를 식별하고 설정하여, 에이전트가 무엇을 달성해야 하는지 명확히 알 수 있습니다.
- 복잡한 작업을 관리 가능한 하위 작업으로 분해하고 논리적인 순서로 구성할 수 있습니다.
- 에이전트에게 적절한 도구(예: 검색 도구 또는 데이터 분석 도구)를 장착하고, 언제 어떻게 사용할지 결정하며, 발생하는 예상치 못한 상황을 처리할 수 있습니다.
- 하위 작업 결과를 평가하고, 성능을 측정하며, 최종 출력을 개선하기 위해 작업을 반복할 수 있습니다.

---

## 🎯 전체 목표 정의 및 작업 분해하기

![목표 및 작업 정의하기](./images/defining-goals-tasks.png)

대부분의 실제 작업은 한 단계로 처리하기에는 너무 복잡합니다. AI 에이전트는 계획과 행동을 안내할 간결한 목표가 필요합니다. 예를 들어 다음과 같은 목표를 생각해 보세요:

    "3일 여행 일정 생성하기."

말은 간단하지만, 이 목표는 더 구체화될 필요가 있습니다. 목표가 명확할수록 에이전트(및 협업하는 인간)는 항공편 옵션, 호텔 추천, 활동 제안 등이 포함된 종합적인 일정을 만드는 올바른 결과를 달성하는 데 집중할 수 있습니다.

### 작업 분해 (Task Decomposition)

크고 복잡한 작업은 더 작은 목표 지향적 하위 작업으로 나누면 관리하기가 훨씬 쉬워집니다.
여행 일정 예시의 경우, 목표를 다음과 같이 분해할 수 있습니다:

* 항공편 예약 (Flight Booking)
* 호텔 예약 (Hotel Booking)
* 렌터카 예약 (Car Rental)
* 개인화 (Personalization)

각 하위 작업은 전담 에이전트나 프로세스가 처리할 수 있습니다. 한 에이전트는 최적의 항공편 딜을 검색하는 데 특화되고, 다른 에이전트는 호텔 예약에 집중하는 식입니다. 그러면 조정 역할을 하는 "하위(downstream)" 에이전트가 이러한 결과를 하나의 응집력 있는 일정으로 모아 최종 사용자에게 전달할 수 있습니다.

이러한 모듈식 접근 방식은 점진적인 개선도 가능하게 합니다. 예를 들어, 음식 추천(Food Recommendations)이나 현지 활동 제안(Local Activity Suggestions)을 위한 특수 에이전트를 추가하여 시간이 지남에 따라 일정을 개선할 수 있습니다.

### 구조화된 출력 (Structured Output)

대규모 언어 모델(LLM)은 다운스트림 에이전트나 서비스가 파싱하고 처리하기 더 쉬운 구조화된 출력(예: JSON)을 생성할 수 있습니다. 이는 계획 출력을 받은 후 이러한 작업을 실행할 수 있는 다중 에이전트 맥락에서 특히 유용합니다. 간략한 개요는 이 `<a href="https://microsoft.github.io/autogen/stable/user-guide/core-user-guide/cookbook/structured-output-agent.html" target="_blank">`블로그 포스트 `</a>`를 참조하세요.

다음 Python 코드 조각은 간단한 계획 에이전트가 목표를 하위 작업으로 분해하고 구조화된 계획을 생성하는 방법을 보여줍니다:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union
import json
import os
from typing import Optional
from pprint import pprint
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.azure import AzureAIChatCompletionClient
from azure.core.credentials import AzureKeyCredential

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# 여행 하위 작업 모델
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum  # 작업을 할당할 에이전트

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool

client = AzureAIChatCompletionClient(
    model="gpt-4o-mini",
    endpoint="https://models.inference.ai.azure.com",
    # 모델 인증을 위해 GitHub 설정에서 개인 액세스 토큰(PAT)을 생성해야 합니다.
    # PAT 토큰 생성 방법: https://docs.github.com/ko/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens
    credential=AzureKeyCredential(os.environ["GITHUB_TOKEN"]),
    model_info={
        "json_output": False,
        "function_calling": True,
        "vision": True,
        "family": "unknown",
    },
)

# 사용자 메시지 정의
messages = [
    SystemMessage(content="""당신은 플래너 에이전트입니다.
    당신의 임무는 사용자 요청에 따라 어떤 에이전트를 실행할지 결정하는 것입니다.
    응답은 다음 구조의 JSON 형식으로 제공하세요:
{'main_task': '싱가포르에서 멜버른으로 가는 가족 여행 계획하기',
 'subtasks': [{'assigned_agent': 'flight_booking',
               'task_details': '싱가포르에서 멜버른으로 가는 왕복 항공편 예약하기'}]}
    아래는 다양한 작업에 특화된 사용 가능한 에이전트 목록입니다:
    - FlightBooking: 항공편 예약 및 항공편 정보 제공
    - HotelBooking: 호텔 예약 및 호텔 정보 제공
    - CarRental: 렌터카 예약 및 렌터카 정보 제공
    - ActivitiesBooking: 활동 예약 및 활동 정보 제공
    - DestinationInfo: 여행지 정보 제공
    - DefaultAgent: 일반 요청 처리""", source="system"),
    UserMessage(
        content="아이 둘 있는 가족의 싱가포르에서 멜버른으로 가는 여행 계획을 만들어줘", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": 'json_object'})

response_content: Optional[str] = response.content if isinstance(
    response.content, str) else None
if response_content is None:
    raise ValueError("응답 내용이 유효한 JSON 문자열이 아닙니다.")

pprint(json.loads(response_content))
```

### 다중 에이전트 오케스트레이션을 사용한 계획 에이전트

이 예시에서 시맨틱 라우터 에이전트는 사용자 요청(예: "여행 호텔 계획이 필요해요.")을 받습니다.

그러면 플래너는 다음과 같은 작업을 수행합니다:

* **호텔 계획 수신:** 플래너는 사용자의 메시지를 받고 시스템 프롬프트(사용 가능한 에이전트 세부 정보 포함)를 기반으로 구조화된 여행 계획을 생성합니다.
* **에이전트 및 해당 도구 나열:** 에이전트 레지스트리는 에이전트(예: 항공편, 호텔, 렌터카, 활동용) 목록과 함께 그들이 제공하는 기능이나 도구를 보유합니다.
* **계획을 해당 에이전트로 라우팅:** 하위 작업의 수에 따라 플래너는 단일 작업 시나리오의 경우 메시지를 전담 에이전트로 직접 보내거나 다중 에이전트 협업을 위해 그룹 채팅 관리자를 통해 조정합니다.
* **결과 요약:** 마지막으로, 플래너는 명확성을 위해 생성된 계획을 요약합니다.
  다음 Python 코드 샘플은 이러한 단계를 보여줍니다:

```python
from pydantic import BaseModel
from enum import Enum
from typing import List, Optional, Union

class AgentEnum(str, Enum):
    FlightBooking = "flight_booking"
    HotelBooking = "hotel_booking"
    CarRental = "car_rental"
    ActivitiesBooking = "activities_booking"
    DestinationInfo = "destination_info"
    DefaultAgent = "default_agent"
    GroupChatManager = "group_chat_manager"

# 여행 하위 작업 모델
class TravelSubTask(BaseModel):
    task_details: str
    assigned_agent: AgentEnum # 작업을 할당할 에이전트

class TravelPlan(BaseModel):
    main_task: str
    subtasks: List[TravelSubTask]
    is_greeting: bool
import json
import os
from typing import Optional

from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
from autogen_ext.models.openai import AzureOpenAIChatCompletionClient

# 환경 변수로 클라이언트 생성
client = AzureOpenAIChatCompletionClient(
    azure_deployment=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    model=os.getenv("AZURE_OPENAI_DEPLOYMENT_NAME"),
    api_version=os.getenv("AZURE_OPENAI_API_VERSION"),
    azure_endpoint=os.getenv("AZURE_OPENAI_ENDPOINT"),
    api_key=os.getenv("AZURE_OPENAI_API_KEY"),
)

from pprint import pprint

# 사용자 메시지 정의
messages = [
    SystemMessage(content="""당신은 플래너 에이전트입니다.
    당신의 임무는 사용자 요청에 따라 어떤 에이전트를 실행할지 결정하는 것입니다.
    아래는 다양한 작업에 특화된 사용 가능한 에이전트 목록입니다:
    - FlightBooking: 항공편 예약 및 항공편 정보 제공
    - HotelBooking: 호텔 예약 및 호텔 정보 제공
    - CarRental: 렌터카 예약 및 렌터카 정보 제공
    - ActivitiesBooking: 활동 예약 및 활동 정보 제공
    - DestinationInfo: 여행지 정보 제공
    - DefaultAgent: 일반 요청 처리""", source="system"),
    UserMessage(content="아이 둘 있는 가족의 싱가포르에서 멜버른으로 가는 여행 계획을 만들어줘", source="user"),
]

response = await client.create(messages=messages, extra_create_args={"response_format": TravelPlan})

# 응답 내용이 유효한 JSON 문자열인지 확인 후 로드
response_content: Optional[str] = response.content if isinstance(response.content, str) else None
if response_content is None:
    raise ValueError("응답 내용이 유효한 JSON 문자열이 아닙니다.")

# JSON으로 로드한 후 응답 내용 출력
pprint(json.loads(response_content))
```

위 코드의 출력 결과는 다음과 같으며, 이 구조화된 출력을 사용하여 `assigned_agent`로 라우팅하고 최종 사용자에게 여행 계획을 요약하여 전달할 수 있습니다.

```json
{
    "is_greeting": "False",
    "main_task": "싱가포르에서 멜버른으로 가는 가족 여행 계획하기",
    "subtasks": [
        {
            "assigned_agent": "flight_booking",
            "task_details": "싱가포르에서 멜버른으로 가는 왕복 항공편 예약하기"
        },
        {
            "assigned_agent": "hotel_booking",
            "task_details": "멜버른에서 가족 친화적인 호텔 찾기"
        },
        {
            "assigned_agent": "car_rental",
            "task_details": "멜버른에서 4인 가족에 적합한 렌터카 준비하기"
        },
        {
            "assigned_agent": "activities_booking",
            "task_details": "멜버른에서 가족 친화적인 활동 목록 만들기"
        },
        {
            "assigned_agent": "destination_info",
            "task_details": "여행지로서 멜버른에 대한 정보 제공하기"
        }
    ]
}
```

위 코드 샘플이 포함된 예제 노트북은 [여기](07-autogen.ipynb)에서 확인할 수 있습니다.

### 반복적 계획 (Iterative Planning)

일부 작업은 한 하위 작업의 결과가 다음 작업에 영향을 미치는 **재계획(re-planning)** 또는 **왕복(back-and-forth)** 방식이 필요합니다. 예를 들어, 에이전트가 항공편을 예약하는 동안 예상치 못한 데이터 형식을 발견하면 호텔 예약으로 넘어가기 전에 전략을 조정해야 할 수도 있습니다.

또한 사용자 피드백(예: 사용자가 더 이른 항공편을 선호한다고 결정)은 부분적인 재계획을 촉발할 수 있습니다. 이러한 동적이고 반복적인 접근 방식은 최종 솔루션이 실제 제약 조건과 변화하는 사용자 선호도에 부합하도록 보장합니다.

**예시 코드:**

```python
from autogen_core.models import UserMessage, SystemMessage, AssistantMessage
# ... 이전 코드와 동일하며 사용자 기록, 현재 계획을 전달
messages = [
    SystemMessage(content="""당신은 최적화를 위한 플래너 에이전트입니다.
    당신의 임무는 사용자 요청에 따라 어떤 에이전트를 실행할지 결정하는 것입니다.
    아래는 다양한 작업에 특화된 사용 가능한 에이전트 목록입니다:
    - FlightBooking: 항공편 예약 및 항공편 정보 제공
    - HotelBooking: 호텔 예약 및 호텔 정보 제공
    - CarRental: 렌터카 예약 및 렌터카 정보 제공
    - ActivitiesBooking: 활동 예약 및 활동 정보 제공
    - DestinationInfo: 여행지 정보 제공
    - DefaultAgent: 일반 요청 처리""", source="system"),
    UserMessage(content="아이 둘 있는 가족의 싱가포르에서 멜버른으로 가는 여행 계획을 만들어줘", source="user"),
    AssistantMessage(content=f"이전 여행 계획 - {TravelPlan}", source="assistant")
]
# .. 재계획을 수행하고 작업을 해당 에이전트로 전송
```

더 포괄적인 계획에 대해서는 복잡한 작업 해결을 위한 Magentic-One `<a href="https://www.microsoft.com/research/articles/magentic-one-a-generalist-multi-agent-system-for-solving-complex-tasks" target="_blank">`블로그 포스트 `</a>`를 확인해 보세요.

---

## 📝 요약

이 글에서는 정의된 사용 가능한 에이전트를 동적으로 선택할 수 있는 플래너를 만드는 방법에 대한 예시를 살펴보았습니다. 플래너의 출력은 작업을 분해하고 에이전트를 할당하여 실행할 수 있도록 합니다. 에이전트는 작업을 수행하는 데 필요한 함수/도구에 접근할 수 있다고 가정합니다. 에이전트 외에도 반성(reflection), 요약(summarizer), 라운드 로빈 채팅과 같은 다른 패턴을 포함하여 추가로 사용자 지정할 수 있습니다.

---

## 📚 추가 자료

**AutoGen Magentic-One** - 복잡한 작업을 해결하기 위한 일반주의 다중 에이전트 시스템으로, 여러 까다로운 에이전틱 벤치마크에서 인상적인 결과를 달성했습니다. 참고: `<a href="https://github.com/microsoft/autogen/tree/main/python/packages/autogen-magentic-one" target="_blank">`autogen-magentic-one `</a>`. 이 구현에서 오케스트레이터는 작업별 계획을 생성하고 이러한 작업을 사용 가능한 에이전트에 위임합니다. 계획 외에도 오케스트레이터는 작업 진행 상황을 모니터링하고 필요에 따라 재계획하는 추적 메커니즘도 사용합니다.

---

## ❓ 계획 디자인 패턴에 대해 더 궁금한 점이 있나요?

[Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하여 다른 학습자들을 만나고, 오피스 아워에 참여하고 AI Agents에 대한 질문에 대한 답변을 받아보세요.

---

## 📚 레슨 목차

### ⬅️ 이전 레슨

[6강: 신뢰할 수 있는 AI Agent 구축하기](../06-building-trustworthy-agents/README.md)

### ➡️ 다음 레슨

[8강: 다중 에이전트 디자인 패턴](../08-multi-agent/README.md)

---

*이 가이드가 여러분의 AI Agent가 복잡한 문제도 스스로 계획하고 해결하는 전략가로 성장하는 데 도움이 되길 바랍니다!* 🗺️
