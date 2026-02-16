
[![AI Agent 프레임워크 탐험](./images/lesson-2-thumbnail.png)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(👆 이미지를 클릭하면 이번 레슨의 강의 영상을 볼 수 있어요!)_

# 🛠️ AI Agent 프레임워크 탐험하기

AI Agent 프레임워크는 AI Agent의 생성, 배포, 관리를 간소화하도록 설계된 소프트웨어 플랫폼이에요. 이러한 프레임워크는 개발자에게 미리 구축된 구성 요소, 추상화, 도구를 제공하여 복잡한 AI 시스템 개발을 간소화합니다.

이 프레임워크들은 AI Agent 개발의 일반적인 과제에 대한 표준화된 접근 방식을 제공함으로써 개발자가 애플리케이션의 고유한 측면에 집중할 수 있도록 도와줘요. AI 시스템 구축 시 확장성, 접근성, 효율성을 향상시킵니다.

## 🎯 소개

이번 레슨에서는 다음 내용을 다룰 예정이에요:

- AI Agent 프레임워크란 무엇이며, 개발자들이 이를 통해 무엇을 할 수 있을까요?
- 팀에서 이를 사용하여 Agent의 기능을 빠르게 프로토타이핑하고, 반복하고, 개선하려면 어떻게 해야 할까요?
- Microsoft에서 만든 프레임워크와 도구들(`<a href="https://aka.ms/ai-agents/autogen" target="_blank">`AutoGen `</a>`, `<a href="https://aka.ms/ai-agents-beginners/semantic-kernel" target="_blank">`Semantic Kernel `</a>`, `<a href="https://aka.ms/ai-agents-beginners/ai-agent-service" target="_blank">`Azure AI Agent Service `</a>`)의 차이점은 무엇인가요?
- 기존 Azure 생태계 도구를 직접 통합할 수 있나요, 아니면 독립형 솔루션이 필요한가요?
- Azure AI Agent 서비스란 무엇이며, 어떻게 도움이 될까요?

## 📚 학습 목표

이번 레슨의 목표는 다음을 이해하는 데 도움을 주는 것입니다:

- AI 개발에서 AI Agent 프레임워크의 역할
- AI Agent 프레임워크를 활용하여 지능형 Agent를 구축하는 방법
- AI Agent 프레임워크가 제공하는 주요 기능
- AutoGen, Semantic Kernel, Azure AI Agent Service의 차이점

---

## 🤔 AI Agent 프레임워크란 무엇이며, 개발자들이 무엇을 할 수 있게 해줄까요?

기존의 AI 프레임워크는 AI를 앱에 통합하고 다음과 같은 방식으로 앱을 더 좋게 만드는 데 도움을 줄 수 있어요:

- **개인화(Personalization)**: AI는 사용자 행동과 선호도를 분석하여 개인화된 추천, 콘텐츠, 경험을 제공할 수 있습니다.
  예시: Netflix와 같은 스트리밍 서비스는 AI를 사용하여 시청 기록을 기반으로 영화와 쇼를 추천하여 사용자 참여와 만족도를 높입니다.
- **자동화 및 효율성(Automation and Efficiency)**: AI는 반복적인 작업을 자동화하고, 워크플로우를 간소화하며, 운영 효율성을 개선할 수 있습니다.
  예시: 고객 서비스 앱은 AI 기반 챗봇을 사용하여 일반적인 문의를 처리하여 응답 시간을 줄이고, 인간 상담원이 더 복잡한 문제에 집중할 수 있도록 합니다.
- **향상된 사용자 경험(Enhanced User Experience)**: AI는 음성 인식, 자연어 처리, 예측 텍스트와 같은 지능형 기능을 제공하여 전반적인 사용자 경험을 개선할 수 있습니다.
  예시: Siri나 Google Assistant와 같은 가상 비서는 AI를 사용하여 음성 명령을 이해하고 응답함으로써 사용자가 기기와 더 쉽게 상호작용할 수 있도록 합니다.

### 🧐 다 좋아 보이는데, 그럼 왜 AI Agent 프레임워크가 필요할까요?

AI Agent 프레임워크는 단순한 AI 프레임워크 그 이상을 의미합니다. 이는 사용자, 다른 Agent, 환경과 상호작용하여 특정 목표를 달성할 수 있는 지능형 Agent를 생성할 수 있도록 설계되었습니다. 이러한 Agent는 자율적인 동작을 나타내고, 결정을 내리고, 변화하는 조건에 적응할 수 있습니다. AI Agent 프레임워크가 제공하는 몇 가지 주요 기능을 살펴보겠습니다:

- **Agent 협업 및 조정(Agent Collaboration and Coordination)**: 함께 작업하고, 소통하고, 복잡한 작업을 해결하기 위해 조정하는 여러 AI Agent를 생성할 수 있습니다.
- **작업 자동화 및 관리(Task Automation and Management)**: 여러 단계의 워크플로우 자동화, 작업 위임, Agent 간의 동적 작업 관리를 위한 메커니즘을 제공합니다.
- **상황 인식 및 적응(Contextual Understanding and Adaptation)**: Agent에게 상황을 이해하고, 변화하는 환경에 적응하며, 실시간 정보를 기반으로 결정을 내릴 수 있는 능력을 부여합니다.

요약하자면, Agent는 더 많은 일을 할 수 있게 하고, 자동화를 다음 수준으로 끌어올리며, 환경으로부터 학습하고 적응할 수 있는 더 지능적인 시스템을 만들 수 있게 해줍니다.

---

## 🚀 Agent의 기능을 빠르게 프로토타이핑, 반복 및 개선하는 방법은 무엇일까요?

이 분야는 빠르게 변화하고 있지만, 대부분의 AI Agent 프레임워크에서 공통적으로 빠른 프로토타이핑과 반복을 도와줄 수 있는 몇 가지 요소, 즉 **모듈식 구성 요소, 협업 도구, 실시간 학습**이 있습니다. 자세히 알아볼까요?

- **모듈식 구성 요소 사용하기**: AI SDK는 AI 및 메모리 커넥터, 자연어 또는 코드 플러그인을 사용한 함수 호출, 프롬프트 템플릿 등과 같은 미리 구축된 구성 요소를 제공합니다.
- **협업 도구 활용하기**: 특정 역할과 작업을 가진 Agent를 설계하여 협업 워크플로우를 테스트하고 개선할 수 있습니다.
- **실시간으로 학습하기**: Agent가 상호작용에서 학습하고 동작을 동적으로 조정하는 피드백 루프를 구현합니다.

### 🔧 모듈식 구성 요소 사용하기

Microsoft Semantic Kernel, LangChain과 같은 SDK는 AI 커넥터, 프롬프트 템플릿, 메모리 관리와 같은 미리 구축된 구성 요소를 제공합니다.

**팀에서 어떻게 사용할 수 있을까요?**: 팀은 이러한 구성 요소를 빠르게 조합하여 처음부터 시작하지 않고도 기능적인 프로토타입을 만들 수 있으며, 이를 통해 신속한 실험과 반복이 가능합니다.

**실제로 어떻게 작동할까요?**: 사용자 입력에서 정보를 추출하는 미리 구축된 파서, 데이터를 저장하고 검색하는 메모리 모듈, 사용자와 상호작용하는 프롬프트 생성기를 사용할 수 있습니다. 이러한 구성 요소를 처음부터 직접 구축할 필요가 없습니다.

**코드 예제**. Semantic Kernel Python 및 .NET에서 미리 구축된 AI 커넥터를 사용하여 자동 함수 호출을 통해 모델이 사용자 입력에 응답하도록 하는 방법을 살펴보겠습니다:

```python
# Semantic Kernel Python 예제

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# 대화의 맥락을 저장할 ChatHistory 객체 정의
chat_history = ChatHistory()
chat_history.add_user_message("2025년 1월 1일에 뉴욕에 가고 싶어요")


# 여행을 예약하는 함수를 포함하는 샘플 플러그인 정의
class BookTravelPlugin:
    """샘플 여행 예약 플러그인"""

    @kernel_function(name="book_flight", description="위치와 날짜가 주어지면 여행을 예약합니다")
    async def book_flight(
        self, date: Annotated[str, "여행 날짜"], location: Annotated[str, "여행할 위치"]
    ) -> str:
        return f"{date}에 {location}으로 여행이 예약되었습니다."

# Kernel 생성
kernel = Kernel()

# 샘플 플러그인을 Kernel 객체에 추가
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Azure OpenAI AI 커넥터 정의
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME",
    api_key="YOUR_API_KEY",
    endpoint="https://<your-resource>.azure.openai.com/",
)

# 자동 함수 호출로 모델을 구성하기 위한 요청 설정 정의
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # 주어진 채팅 기록 및 요청 설정으로 모델에 요청
    # Kernel에는 모델이 호출을 요청할 샘플이 포함되어 있음
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    참고: 자동 함수 호출 과정에서 모델은 `BookTravelPlugin`을 `book_flight` 함수를 사용하여 호출할 수 있다고 판단하고 필요한 인수를 제공합니다.

    예시:

    "tool_calls": [
        {
            "id": "call_abc123",
            "type": "function",
            "function": {
                "name": "BookTravelPlugin-book_flight",
                "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
            }
        }
    ]

    위치와 날짜 인수는 (커널 함수에 의해 정의된 대로) 필수이므로, 모델이 둘 중 하나라도 가지고 있지 않으면 사용자에게 제공하도록 요청합니다. 예를 들어:

    사용자: 뉴욕행 비행기 예약해줘.
    모델: 네, 비행기 예약을 도와드리고 싶어요. 날짜를 알려주시겠어요?
    사용자: 2025년 1월 1일에 여행하고 싶어요.
    모델: 2025년 1월 1일자 뉴욕행 비행기가 성공적으로 예약되었습니다. 안전한 여행 되세요!
    """

    print(f"`{response}`")
    # 예시 AI 모델 응답: `2025년 1월 1일자 뉴욕행 비행기가 성공적으로 예약되었습니다. 안전한 여행 되세요! ✈️🗽`

    # 모델의 응답을 채팅 기록 컨텍스트에 추가
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```

```csharp
// Semantic Kernel C# 예제

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("2025년 1월 1일에 뉴욕에 가고 싶어요");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "YOUR_DEPLOYMENT_NAME",
    apiKey: "YOUR_API_KEY",
    endpoint: "YOUR_AZURE_ENDPOINT"
);
kernelBuilder.Plugins.AddFromType<BookTravelPlugin>("BookTravel");
var kernel = kernelBuilder.Build();

var settings = new AzureOpenAIPromptExecutionSettings()
{
    FunctionChoiceBehavior = FunctionChoiceBehavior.Auto()
};

var chatCompletion = kernel.GetRequiredService<IChatCompletionService>();

var response = await chatCompletion.GetChatMessageContentAsync(chatHistory, settings, kernel);

/*
내부적으로 모델은 호출할 도구와 이미 가지고 있는 인수(위치)와 (날짜)를 인식합니다.
{

"tool_calls": [
    {
        "id": "call_abc123",
        "type": "function",
        "function": {
            "name": "BookTravelPlugin-book_flight",
            "arguments": "{'location': 'New York', 'date': '2025-01-01'}"
        }
    }
]
*/

Console.WriteLine(response.Content);
chatHistory.AddMessage(response!.Role, response!.Content!);

// 예시 AI 모델 응답: 2025년 1월 1일자 뉴욕행 비행기가 성공적으로 예약되었습니다. 안전한 여행 되세요! ✈️🗽

// 여행 예약 함수를 포함하는 플러그인 정의
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("위치와 날짜가 주어지면 여행을 예약합니다")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"{date}에 {location}으로 여행이 예약되었습니다.");
    }
}
```

이 예제를 통해 사용자 입력(예: 항공편 예약 요청의 출발지, 도착지, 날짜)에서 핵심 정보를 추출하기 위해 미리 구축된 파서를 어떻게 활용할 수 있는지 확인할 수 있습니다. 이러한 모듈식 접근 방식을 통해 높은 수준의 로직에 집중할 수 있습니다.

### 🤝 협업 도구 활용하기

CrewAI, Microsoft AutoGen, Semantic Kernel과 같은 프레임워크는 함께 작업할 수 있는 여러 Agent의 생성을 용이하게 합니다.

**팀에서 어떻게 사용할 수 있을까요?**: 팀은 특정 역할과 작업을 가진 Agent를 설계하여 협업 워크플로우를 테스트하고 개선하며 전반적인 시스템 효율성을 향상시킬 수 있습니다.

**실제로 어떻게 작동할까요?**: 각각 데이터 검색, 분석, 의사 결정과 같은 특화된 기능을 가진 Agent 팀을 만들 수 있습니다. 이러한 Agent는 통신하고 정보를 공유하여 사용자 쿼리에 응답하거나 작업을 완료하는 것과 같은 공통 목표를 달성할 수 있습니다.

**코드 예제 (AutoGen)**:

```python
# Agent 생성 후, 함께 작업할 수 있는 라운드 로빈 일정 생성 (이 경우 순서대로)

# 데이터 검색 Agent
# 데이터 분석 Agent
# 의사 결정 Agent

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="도구를 사용하여 작업을 해결하세요."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="도구를 사용하여 작업을 해결하세요."
)

# 사용자가 "APPROVE"라고 말하면 대화 종료
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="데이터 분석", max_turns=10)
# 스크립트에서 실행할 때는 asyncio.run(...)을 사용하세요.
await Console(stream)
```

위 코드에서는 여러 Agent가 협력하여 데이터를 분석하는 작업을 생성하는 방법을 보여줍니다. 각 Agent는 특정 기능을 수행하며, 원하는 결과를 얻기 위해 Agent들을 조정하여 작업이 실행됩니다. 전문화된 역할을 가진 전용 Agent를 생성하면 작업 효율성과 성능을 향상시킬 수 있습니다.

### ⚡ 실시간 학습하기

고급 프레임워크는 실시간 컨텍스트 이해 및 적응 기능을 제공합니다.

**팀에서 어떻게 사용할 수 있을까요?**: 팀은 Agent가 상호작용에서 학습하고 동작을 동적으로 조정하는 피드백 루프를 구현하여 지속적인 개선과 기능 개선을 이끌어낼 수 있습니다.

**실제로 어떻게 작동할까요?**: Agent는 사용자 피드백, 환경 데이터, 작업 결과를 분석하여 지식 베이스를 업데이트하고, 의사 결정 알고리즘을 조정하며, 시간이 지남에 따라 성능을 개선할 수 있습니다. 이 반복적인 학습 프로세스를 통해 Agent는 변화하는 조건과 사용자 선호도에 적응하여 전반적인 시스템 효율성을 향상시킬 수 있습니다.

---

## 🆚 AutoGen, Semantic Kernel, Azure AI Agent Service 프레임워크의 차이점은 무엇인가요?

이 프레임워크들을 비교하는 방법은 많지만, 설계, 기능, 대상 사용 사례 측면에서 몇 가지 주요 차이점을 살펴보겠습니다.

### AutoGen

AutoGen은 Microsoft Research의 AI Frontiers Lab에서 개발한 오픈 소스 프레임워크입니다. 이벤트 기반의 분산형 *agentic* 애플리케이션에 중점을 두며, 여러 LLM 및 SLM, 도구, 고급 다중 Agent 설계 패턴을 가능하게 합니다.

AutoGen은 Agent라는 핵심 개념을 기반으로 구축되었습니다. Agent는 환경을 인식하고, 결정을 내리고, 특정 목표를 달성하기 위해 행동을 취할 수 있는 자율적인 엔터티입니다. Agent는 비동기 메시지를 통해 통신하므로 독립적으로 병렬로 작업할 수 있어 시스템 확장성과 응답성이 향상됩니다.

`<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">`Agent는 액터 모델을 기반으로 합니다 `</a>`. Wikipedia에 따르면 액터는 _동시성 계산의 기본 구성 요소입니다. 수신한 메시지에 대한 응답으로 액터는 로컬 결정을 내리고, 더 많은 액터를 생성하고, 더 많은 메시지를 보내고, 다음에 수신할 메시지에 응답하는 방법을 결정할 수 있습니다_.

**사용 사례**: 코드 생성 자동화, 데이터 분석 작업, 계획 및 연구 기능을 위한 맞춤형 Agent 구축.

AutoGen의 중요한 핵심 개념은 다음과 같습니다:

- **Agent(에이전트)**. Agent는 다음과 같은 소프트웨어 엔터티입니다:

  - **메시지를 통해 통신**하며, 이러한 메시지는 동기식 또는 비동기식일 수 있습니다.
  - **자체 상태를 유지**하며, 수신 메시지에 의해 수정될 수 있습니다.
  - 수신된 메시지 또는 상태 변경에 대한 응답으로 **작업을 수행**합니다. 이러한 작업은 Agent의 상태를 수정하고 메시지 로그 업데이트, 새 메시지 전송, 코드 실행, API 호출과 같은 외부 효과를 생성할 수 있습니다.

  다음은 채팅 기능으로 자신만의 Agent를 생성하는 짧은 코드 조각입니다:

  ```python
  from autogen_agentchat.agents import AssistantAgent
  from autogen_agentchat.messages import TextMessage
  from autogen_ext.models.openai import OpenAIChatCompletionClient


  class MyAgent(RoutedAgent):
      def __init__(self, name: str) -> None:
          super().__init__(name)
          model_client = OpenAIChatCompletionClient(model="gpt-4o")
          self._delegate = AssistantAgent(name, model_client=model_client)

      @message_handler
      async def handle_my_message_type(self, message: MyMessageType, ctx: MessageContext) -> None:
          print(f"{self.id.type} received message: {message.content}")
          response = await self._delegate.on_messages(
              [TextMessage(content=message.content, source="user")], ctx.cancellation_token
          )
          print(f"{self.id.type} responded: {response.chat_message.content}")
  ```

  위 코드에서는 `RoutedAgent`를 상속받는 `MyAgent`가 생성되었습니다. 여기에는 메시지 내용을 출력한 다음 `AssistantAgent` 대리자를 사용하여 응답을 보내는 메시지 핸들러가 있습니다. 특히 `self._delegate`에 채팅 완료를 처리할 수 있는 미리 구축된 Agent인 `AssistantAgent`의 인스턴스를 할당하는 방법에 주목하세요.

  다음으로 AutoGen에 이 Agent 유형을 알리고 프로그램을 시작해 보겠습니다:

  ```python
  # main.py
  runtime = SingleThreadedAgentRuntime()
  await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

  runtime.start()  # 백그라운드에서 메시지 처리 시작
  await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
  ```

  위 코드에서 Agent는 런타임에 등록된 다음 Agent로 메시지가 전송되어 다음과 같은 출력이 생성됩니다:

  ```text
  # 콘솔 출력:
  my_agent received message: Hello, World!
  my_assistant received message: Hello, World!
  my_assistant responded: Hello! How can I assist you today?
  ```
- **다중 Agent(Multi agents)**. AutoGen은 복잡한 작업을 달성하기 위해 함께 작업할 수 있는 여러 Agent의 생성을 지원합니다. Agent는 통신하고, 정보를 공유하고, 작업을 조정하여 문제를 더 효율적으로 해결할 수 있습니다. 다중 Agent 시스템을 생성하려면 데이터 검색, 분석, 의사 결정, 사용자 상호 작용과 같은 특화된 기능과 역할을 가진 다양한 유형의 Agent를 정의할 수 있습니다. 이러한 생성이 어떻게 보이는지 살펴보겠습니다:

  ```python
  editor_description = "콘텐츠 계획 및 검토를 위한 편집자."

  # Agent 선언 예시
  editor_agent_type = await EditorAgent.register(
      runtime,
      editor_topic_type,  # 주제 유형을 Agent 유형으로 사용
      lambda: EditorAgent(
          description=editor_description,
          group_chat_topic_type=group_chat_topic_type,
          model_client=OpenAIChatCompletionClient(
              model="gpt-4o-2024-08-06",
              # api_key="YOUR_API_KEY",
          ),
      ),
  )

  # 나머지 선언은 간략하게 생략

  # 그룹 채팅
  group_chat_manager_type = await GroupChatManager.register(
      runtime,
      "group_chat_manager",
      lambda: GroupChatManager(
          participant_topic_types=[writer_topic_type, illustrator_topic_type, editor_topic_type, user_topic_type],
          model_client=OpenAIChatCompletionClient(
              model="gpt-4o-2024-08-06",
              # api_key="YOUR_API_KEY",
          ),
          participant_descriptions=[
              writer_description,
              illustrator_description,
              editor_description,
              user_description
          ],
      ),
  )
  ```

  위 코드에서는 `GroupChatManager`가 런타임에 등록됩니다. 이 관리자는 작성자, 일러스트레이터, 편집자, 사용자와 같은 다양한 유형의 Agent 간의 상호 작용을 조정하는 역할을 합니다.
- **Agent 런타임(Agent Runtime)**. 프레임워크는 런타임 환경을 제공하여 Agent 간의 통신을 가능하게 하고, ID와 라이프사이클을 관리하며, 보안 및 개인 정보 보호 경계를 적용합니다. 즉, 안전하고 통제된 환경에서 Agent를 실행하여 안전하고 효율적으로 상호 작용할 수 있습니다. 관심 있는 두 가지 런타임이 있습니다:

  - **독립형 런타임(Stand-alone runtime)**. 모든 Agent가 동일한 프로그래밍 언어로 구현되고 동일한 프로세스에서 실행되는 단일 프로세스 애플리케이션에 적합한 선택입니다. 작동 방식은 다음과 같습니다:

    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">독립형 런타임 다이어그램 보기</a>

애플리케이션 스택
    *Agent는 런타임을 통해 메시지를 통해 통신하며, 런타임은 Agent의 라이프사이클을 관리합니다*

- **분산 Agent 런타임(Distributed agent runtime)**. Agent가 다른 프로그래밍 언어로 구현되고 다른 머신에서 실행될 수 있는 다중 프로세스 애플리케이션에 적합합니다. 작동 방식은 다음과 같습니다:

  <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">분산 런타임 다이어그램 보기</a>

### Semantic Kernel + Agent Framework

Semantic Kernel은 엔터프라이즈에 적합한 AI 오케스트레이션 SDK입니다. AI 및 메모리 커넥터와 Agent 프레임워크로 구성됩니다.

먼저 몇 가지 핵심 구성 요소를 살펴보겠습니다:

- **AI 커넥터(AI Connectors)**: Python과 C# 모두에서 사용할 수 있는 외부 AI 서비스 및 데이터 소스와의 인터페이스입니다.

  ```python
  # Semantic Kernel Python
  from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion
  from semantic_kernel.kernel import Kernel

  kernel = Kernel()
  kernel.add_service(
    AzureChatCompletion(
        deployment_name="your-deployment-name",
        api_key="your-api-key",
        endpoint="your-endpoint",
    )
  )
  ```

  ```csharp
  // Semantic Kernel C#
  using Microsoft.SemanticKernel;

  // 커널 생성
  var builder = Kernel.CreateBuilder();

  // 채팅 완료 서비스 추가:
  builder.Services.AddAzureOpenAIChatCompletion(
      "your-resource-name",
      "your-endpoint",
      "your-resource-key",
      "deployment-model");
  var kernel = builder.Build();
  ```

  여기서는 커널을 생성하고 채팅 완료 서비스를 추가하는 간단한 예를 보여줍니다. Semantic Kernel은 외부 AI 서비스(이 경우 Azure OpenAI 채팅 완료)에 대한 연결을 생성합니다.
- **플러그인(Plugins)**: 애플리케이션이 사용할 수 있는 함수를 캡슐화합니다. 바로 사용할 수 있는 플러그인과 직접 생성할 수 있는 사용자 지정 플러그인이 있습니다. 관련 개념으로 "프롬프트 함수(prompt functions)"가 있습니다. 함수 호출을 위한 자연어 단서를 제공하는 대신, 특정 함수를 모델에 브로드캐스트합니다. 현재 채팅 컨텍스트를 기반으로 모델은 요청이나 쿼리를 완료하기 위해 이러한 함수 중 하나를 호출하도록 선택할 수 있습니다. 예는 다음과 같습니다:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("사용자 입력:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          제공된 구조화되지 않은 텍스트를 이해하기 쉬운 한 문장으로 요약하세요.
          요약할 텍스트: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"모델 응답: {response}")

      """
      샘플 콘솔 출력:

      사용자 입력:> 나는 개를 좋아해요
      모델 응답: 텍스트는 개에 대한 선호를 표현합니다.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```

  ```csharp
  var userInput = Console.ReadLine();

  // 의미론적 함수 인라인 정의
  string skPrompt = @"제공된 구조화되지 않은 텍스트를 이해하기 쉬운 한 문장으로 요약하세요.
                      요약할 텍스트: {{$userInput}}";

  // 프롬프트에서 함수 생성
  KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
      promptTemplate: skPrompt,
      functionName: "SummarizeText"
  );

  // 그런 다음 현재 커널로 가져오기
  kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

  ```

  여기서는 먼저 사용자가 텍스트를 입력할 수 있는 공간 `$userInput`을 남겨둔 템플릿 프롬프트 `skPrompt`가 있습니다. 그런 다음 커널 함수 `SummarizeText`를 생성하고 플러그인 이름 `SemanticFunctions`로 커널에 가져옵니다. 함수의 이름은 Semantic Kernel이 함수의 기능과 호출 시기를 이해하는 데 도움이 됩니다.
- **네이티브 함수(Native function)**: 프레임워크가 작업을 수행하기 위해 직접 호출할 수 있는 네이티브 함수도 있습니다. 다음은 파일에서 콘텐츠를 검색하는 이러한 함수의 예입니다:

  ```csharp
  public class NativeFunctions {

      [SKFunction, Description("로컬 파일에서 콘텐츠 검색")]
      public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
      {
          string content = await File.ReadAllTextAsync(fileName);
          if (content.Length <= maxSize) return content;
          return content.Substring(0, maxSize);
      }
  }

  // 네이티브 함수 가져오기
  string plugInName = "NativeFunction";
  string functionName = "RetrieveLocalFile";

  // 함수를 커널에 추가하려면 다음 함수를 사용하세요
  kernel.ImportPluginFromType<NativeFunctions>();

  ```
- **메모리(Memory)**: AI 앱을 위한 컨텍스트 관리를 추상화하고 단순화합니다. 메모리의 개념은 LLM이 알아야 할 정보라는 것입니다. 이 정보는 벡터 저장소(인메모리 데이터베이스, 벡터 데이터베이스 등)에 저장할 수 있습니다. 다음은 *사실(facts)* 이 메모리에 추가되는 매우 간소화된 시나리오의 예입니다:

  ```csharp
  var facts = new Dictionary<string,string>();
  facts.Add(
      "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
      @"Azure Machine Learning은 기계 학습 프로젝트 수명 주기를 가속화하고 관리하기 위한 클라우드 서비스입니다.
      기계 학습 전문가, 데이터 과학자, 엔지니어는 일상적인 워크플로우에서 이를 사용할 수 있습니다."
  );

  facts.Add(
      "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
      @"Azure SQL은 Azure 클라우드에서 SQL Server 데이터베이스 엔진을 사용하는 관리형, 보안 및 지능형 제품군입니다."
  );

  string memoryCollectionName = "SummarizedAzureDocs";

  foreach (var fact in facts) {
      await memoryBuilder.SaveReferenceAsync(
          collection: memoryCollectionName,
          description: fact.Key.Split(";")[1].Trim(),
          text: fact.Value,
          externalId: fact.Key.Split(";")[2].Trim(),
          externalSourceName: "Azure Documentation"
      );
  }
  ```

  이러한 사실은 메모리 컬렉션 `SummarizedAzureDocs`에 저장됩니다. 매우 간단한 예이지만, LLM이 사용할 정보를 메모리에 저장하는 방법을 확인할 수 있습니다.

이것이 Semantic Kernel 프레임워크의 기본 사항입니다. 그렇다면 Agent 프레임워크는 어떨까요?

### Azure AI Agent Service

Azure AI Agent Service는 Microsoft Ignite 2024에서 소개된 비교적 최근에 추가된 서비스입니다. Llama 3, Mistral, Cohere와 같은 오픈 소스 LLM을 직접 호출하는 등 더 유연한 모델로 AI Agent를 개발하고 배포할 수 있습니다.

Azure AI Agent Service는 더 강력한 엔터프라이즈 보안 메커니즘과 데이터 저장 방법을 제공하므로 엔터프라이즈 애플리케이션에 적합합니다.

AutoGen 및 Semantic Kernel과 같은 다중 Agent 오케스트레이션 프레임워크와 즉시 호환됩니다.

이 서비스는 현재 공개 미리 보기(Public Preview) 상태이며 Agent 구축을 위해 Python과 C#을 지원합니다.

Semantic Kernel Python을 사용하여 사용자 정의 플러그인으로 Azure AI Agent를 생성할 수 있습니다:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# 샘플을 위한 샘플 플러그인 정의
class MenuPlugin:
    """개념 샘플에 사용되는 샘플 메뉴 플러그인입니다."""

    @kernel_function(description="메뉴에서 특별 메뉴 목록을 제공합니다.")
    def get_specials(self) -> Annotated[str, "메뉴의 특별 메뉴를 반환합니다."]:
        return """
        특별 스프: 뉴잉글랜드 클램 차우더
        특별 샐러드: 콥 샐러드
        특별 음료: 차이 티
        """

    @kernel_function(description="요청한 메뉴 항목의 가격을 제공합니다.")
    def get_item_price(
        self, menu_item: Annotated[str, "메뉴 항목의 이름"]
    ) -> Annotated[str, "메뉴 항목의 가격을 반환합니다."]:
        return "$9.99"


async def main() -> None:
    ai_agent_settings = AzureAIAgentSettings.create()

    async with (
        DefaultAzureCredential() as creds,
        AzureAIAgent.create_client(
            credential=creds,
            conn_str=ai_agent_settings.project_connection_string.get_secret_value(),
        ) as client,
    ):
        # Agent 정의 생성
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="메뉴에 관한 질문에 답변하세요.",
        )

        # 정의된 클라이언트와 Agent 정의를 사용하여 AzureAI Agent 생성
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # 대화를 유지할 스레드 생성
        # 스레드가 제공되지 않으면 초기 응답과 함께 새 스레드가 생성되어 반환됩니다.
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "안녕하세요",
            "오늘의 특별 스프는 뭐예요?",
            "그거 얼마예요?",
            "감사합니다",
        ]

        try:
            for user_input in user_inputs:
                print(f"# 사용자: '{user_input}'")
                # 지정된 스레드에 대해 Agent 호출
                response = await agent.get_response(
                    messages=user_input,
                    thread_id=thread,
                )
                print(f"# {response.name}: {response.content}")
                thread = response.thread
        finally:
            await thread.delete() if thread else None
            await client.agents.delete_agent(agent.id)


if __name__ == "__main__":
    asyncio.run(main())
```

### 핵심 개념

Azure AI Agent Service에는 다음과 같은 핵심 개념이 있습니다:

- **Agent(에이전트)**. Azure AI Agent Service는 Azure AI Foundry와 통합됩니다. AI Foundry 내에서 AI Agent는 질문에 답변하거나(RAG), 작업을 수행하거나, 워크플로우를 완전히 자동화하는 데 사용할 수 있는 "스마트" 마이크로서비스 역할을 합니다. 이는 생성형 AI 모델의 성능과 실제 데이터 소스에 액세스하고 상호 작용할 수 있는 도구를 결합하여 달성합니다. 다음은 Agent의 예입니다:

  ```python
  agent = project_client.agents.create_agent(
      model="gpt-4o-mini",
      name="my-agent",
      instructions="You are helpful agent",
      tools=code_interpreter.definitions,
      tool_resources=code_interpreter.resources,
  )
  ```

  이 예에서는 `gpt-4o-mini` 모델, 이름 `my-agent`, 지침 `You are helpful agent`로 Agent가 생성됩니다. Agent는 코드 해석 작업을 수행할 수 있는 도구와 리소스를 갖추고 있습니다.
- **스레드 및 메시지(Thread and messages)**. 스레드는 또 다른 중요한 개념입니다. 이는 Agent와 사용자 간의 대화 또는 상호 작용을 나타냅니다. 스레드는 대화 진행 상황을 추적하고, 컨텍스트 정보를 저장하며, 상호 작용 상태를 관리하는 데 사용할 수 있습니다. 다음은 스레드의 예입니다:

  ```python
  thread = project_client.agents.create_thread()
  message = project_client.agents.create_message(
      thread_id=thread.id,
      role="user",
      content="다음 데이터를 사용하여 영업 이익에 대한 막대 차트를 만들고 파일을 제공해 주시겠어요? A사: 120만 달러, B사: 250만 달러, C사: 300만 달러, D사: 180만 달러",
  )

  # 스레드에서 작업을 수행하도록 Agent에 요청
  run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)

  # 모든 메시지를 가져와서 Agent의 응답을 확인
  messages = project_client.agents.list_messages(thread_id=thread.id)
  print(f"메시지: {messages}")
  ```

  위 코드에서는 스레드가 생성됩니다. 그런 다음 스레드로 메시지가 전송됩니다. `create_and_process_run`을 호출하여 Agent가 스레드에서 작업을 수행하도록 요청합니다. 마지막으로 메시지를 가져와서 기록하여 Agent의 응답을 확인합니다. 메시지는 사용자와 Agent 간의 대화 진행 상황을 나타냅니다. 메시지는 텍스트, 이미지, 파일 등 다양한 유형일 수 있으며, 이는 Agent의 작업 결과로 예를 들어 이미지나 텍스트 응답이 생성되었음을 의미합니다. 개발자는 이 정보를 사용하여 응답을 추가로 처리하거나 사용자에게 표시할 수 있습니다.
- **다른 AI 프레임워크와 통합(Integrates with other AI frameworks)**. Azure AI Agent 서비스는 AutoGen, Semantic Kernel과 같은 다른 프레임워크와 상호 작용할 수 있습니다. 즉, 이러한 프레임워크 중 하나로 앱의 일부를 빌드하고 예를 들어 Agent 서비스를 오케스트레이터로 사용하거나 Agent 서비스에서 모든 것을 빌드할 수 있습니다.

**사용 사례**: Azure AI Agent Service는 안전하고 확장 가능하며 유연한 AI Agent 배포가 필요한 엔터프라이즈 애플리케이션을 위해 설계되었습니다.

---

## 🆚 이 프레임워크들의 차이점은 무엇인가요?

이러한 프레임워크 간에 상당한 중복이 있는 것처럼 들릴 수 있지만, 설계, 기능, 대상 사용 사례 측면에서 몇 가지 주요 차이점이 있습니다:

- **AutoGen**: 다중 Agent 시스템에 대한 최첨단 연구에 중점을 둔 실험 프레임워크입니다. 정교한 다중 Agent 시스템을 실험하고 프로토타입을 만드는 데 가장 적합한 곳입니다.
- **Semantic Kernel**: 엔터프라이즈 에이전틱(agentic) 애플리케이션을 구축하기 위한 프로덕션 준비 Agent 라이브러리입니다. 이벤트 기반의 분산형 에이전틱 애플리케이션에 중점을 두며, 여러 LLM 및 SLM, 도구, 단일/다중 Agent 설계 패턴을 가능하게 합니다.
- **Azure AI Agent Service**: Azure Foundry의 Agent를 위한 플랫폼이자 배포 서비스입니다. Azure OpenAI, Azure AI Search, Bing Search, 코드 실행과 같이 Azure Foundry에서 지원하는 서비스에 대한 연결 기능을 제공합니다.

여전히 어떤 것을 선택해야 할지 모르시겠나요?

### 🤷‍♀️ 사용 사례

일반적인 사용 사례를 살펴보면서 결정을 도와드리겠습니다:

> 질문: 저는 실험하고, 배우고, 개념 증명 에이전트 애플리케이션을 구축하는 중이며, 빠르게 구축하고 실험할 수 있기를 원합니다.

> 답변: 이 시나리오에서는 AutoGen이 좋은 선택이 될 수 있습니다. 이벤트 기반의 분산형 에이전틱 애플리케이션에 중점을 두고 고급 다중 Agent 설계 패턴을 지원하기 때문입니다.

> 질문: 이 사용 사례에서 AutoGen이 Semantic Kernel이나 Azure AI Agent Service보다 더 나은 선택인 이유는 무엇인가요?
>
> 답변: AutoGen은 특히 이벤트 기반의 분산형 에이전틱 애플리케이션을 위해 설계되어 코드 생성 및 데이터 분석 작업을 자동화하는 데 매우 적합합니다. 복잡한 다중 Agent 시스템을 효율적으로 구축하는 데 필요한 도구와 기능을 제공합니다.

> 질문: Azure AI Agent Service도 여기서 작동할 수 있을 것 같은데요? 코드 생성을 위한 도구 등 더 많은 기능이 있는 것 같아요.

> 답변: 네, Azure AI Agent Service는 Agent를 위한 플랫폼 서비스이며 여러 모델, Azure AI Search, Bing Search, Azure Functions에 대한 내장 기능을 추가합니다. Foundry Portal에서 Agent를 쉽게 구축하고 대규모로 배포할 수 있습니다.

> 질문: 아직 혼란스러워요. 그냥 하나만 알려주세요.
>
> 답변: 좋은 선택은 먼저 Semantic Kernel로 애플리케이션을 빌드한 다음 Azure AI Agent Service를 사용하여 Agent를 배포하는 것입니다. 이 접근 방식을 사용하면 Semantic Kernel에서 다중 Agent 시스템을 구축하는 강력한 기능을 활용하면서 Agent를 쉽게 유지할 수 있습니다. 또한 Semantic Kernel에는 AutoGen용 커넥터가 있어 두 프레임워크를 함께 쉽게 사용할 수 있습니다.

표로 주요 차이점을 요약해 보겠습니다:

| 프레임워크             | 초점                                                 | 핵심 개념                             | 사용 사례                                   |
| ---------------------- | ---------------------------------------------------- | ------------------------------------- | ------------------------------------------- |
| AutoGen                | 이벤트 기반, 분산형 에이전틱 애플리케이션            | Agent, 페르소나, 함수, 데이터         | 코드 생성, 데이터 분석 작업                 |
| Semantic Kernel        | 인간과 유사한 텍스트 콘텐츠 이해 및 생성             | Agent, 모듈식 구성 요소, 협업         | 자연어 이해, 콘텐츠 생성                    |
| Azure AI Agent Service | 유연한 모델, 엔터프라이즈 보안, 코드 생성, 도구 호출 | 모듈성, 협업, 프로세스 오케스트레이션 | 안전하고 확장 가능하며 유연한 AI Agent 배포 |

각 프레임워크의 이상적인 사용 사례는 무엇일까요?

---

## 🔗 기존 Azure 생태계 도구를 직접 통합할 수 있나요, 아니면 독립형 솔루션이 필요한가요?

정답은 '네, 통합할 수 있습니다'입니다. 특히 Azure AI Agent Service는 다른 Azure 서비스와 원활하게 작동하도록 구축되었기 때문에 기존 Azure 생태계 도구를 직접 통합할 수 있습니다. 예를 들어 Bing, Azure AI Search, Azure Functions를 통합할 수 있습니다. Azure AI Foundry와도 깊게 통합되어 있습니다.

AutoGen과 Semantic Kernel의 경우 Azure 서비스와 통합할 수도 있지만, 코드에서 Azure 서비스를 직접 호출해야 할 수 있습니다. 통합하는 또 다른 방법은 Azure SDK를 사용하여 Agent 내에서 Azure 서비스와 상호 작용하는 것입니다. 또한 앞서 언급했듯이 Azure AI Agent Service를 AutoGen 또는 Semantic Kernel로 구축된 Agent의 오케스트레이터로 사용하면 Azure 생태계에 쉽게 액세스할 수 있습니다.

---

## 💻 샘플 코드

- Python: [Agent 프레임워크](./code_samples/02-python-agent-framework.ipynb)
- .NET: [Agent 프레임워크](./code_samples/02-dotnet-agent-framework.md)

---

## ❓ AI Agent 프레임워크에 대해 더 궁금한 점이 있나요?

[Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하여 다른 학습자들을 만나고, 오피스 아워에 참여하고 AI Agents에 대한 질문에 대한 답변을 받아보세요.

---

## 📚 참고 자료

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service 소개</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Microsoft의 에이전틱 AI 프레임워크: AutoGen과 Semantic Kernel</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent 프레임워크</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .NET Agent 프레임워크</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent 서비스 개요</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">AutoGen / Semantic Kernel과 함께 Azure AI Agent Service를 사용하여 다중 Agent 솔루션 구축하기</a>

---

## 📚 다른 레슨들

### ⬅️ 이전 레슨

[1강: AI Agents 소개 및 활용 사례](../01-intro-to-ai-agents/README.md)

### ➡️ 다음 레슨

[3강: Agentic 디자인 패턴 이해하기](../03-agentic-design-patterns/README.md)

---

*이 가이드는 여러분의 성공적인 학습을 응원합니다! 💪*
