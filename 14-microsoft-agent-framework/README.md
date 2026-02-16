# 🚀 Microsoft Agent Framework 탐험하기 - 차세대 AI 에이전트 구축의 모든 것

[![Microsoft Agent Framework](./images/lesson-14-thumbnail.png)]

> _(👆 이미지를 클릭하면 이번 레슨의 강의 영상을 볼 수 있어요!)_

## 🧐 소개

이번 레슨에서는 다음 내용을 다룹니다:

- **Microsoft Agent Framework 이해하기**: 주요 기능과 가치
- **Microsoft Agent Framework의 핵심 개념** 탐구하기
- **MAF와 Semantic Kernel 및 AutoGen 비교**: 마이그레이션 가이드

## 📚 학습 목표

이번 레슨을 완료하면 다음을 할 수 있게 됩니다:

- Microsoft Agent Framework를 사용하여 **프로덕션에 바로 투입할 수 있는 AI 에이전트**를 구축할 수 있습니다.
- Microsoft Agent Framework의 핵심 기능을 자신의 **에이전틱 사용 사례에 적용**할 수 있습니다.
- 기존 에이전틱 프레임워크와 도구를 **마이그레이션하고 통합**할 수 있습니다.

## 💻 코드 샘플

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok)에 대한 코드 샘플은 이 저장소의 `xx-python-agent-framework` 및 `xx-dotnet-agent-framework` 파일에서 찾을 수 있습니다.

---

## 🤔 Microsoft Agent Framework 이해하기

![프레임워크 소개](./images/framework-intro.png)

[Microsoft Agent Framework (MAF)](https://aka.ms/ai-agents-beginners/agent-framewrok)는 Semantic Kernel과 AutoGen의 경험과 학습을 바탕으로 구축되었습니다. 프로덕션 환경과 연구 환경 모두에서 볼 수 있는 다양한 에이전틱 사용 사례를 해결할 수 있는 유연성을 제공합니다. 여기에는 다음이 포함됩니다:

- **순차적 에이전트 오케스트레이션(Sequential Agent orchestration)**: 단계별 워크플로우가 필요한 시나리오
- **동시적 오케스트레이션(Concurrent orchestration)**: 에이전트가 동시에 작업을 완료해야 하는 시나리오
- **그룹 채팅 오케스트레이션(Group chat orchestration)**: 에이전트가 하나의 작업에 대해 함께 협력할 수 있는 시나리오
- **핸드오프 오케스트레이션(Handoff Orchestration)**: 하위 작업이 완료됨에 따라 에이전트가 서로에게 작업을 넘기는 시나리오
- **마그네틱 오케스트레이션(Magnetic Orchestration)**: 관리자 에이전트가 작업 목록을 생성 및 수정하고 하위 에이전트의 조정을 처리하여 작업을 완료하는 시나리오

프로덕션에서 AI 에이전트를 제공하기 위해 MAF에는 다음과 같은 기능도 포함되어 있습니다:

- **관찰 가능성(Observability)**: OpenTelemetry를 사용하여 AI 에이전트의 모든 작업(도구 호출, 오케스트레이션 단계, 추론 흐름)을 추적하고 Azure AI Foundry 대시보드를 통해 성능을 모니터링할 수 있습니다.
- **보안(Security)**: Azure AI Foundry에 에이전트를 기본적으로 호스팅하여 역할 기반 액세스, 프라이빗 데이터 처리, 내장된 콘텐츠 안전과 같은 보안 제어 기능을 제공합니다.
- **내구성(Durability)**: 에이전트 스레드와 워크플로우가 일시 중지, 재개 및 오류로부터 복구될 수 있어 장기 실행 프로세스를 지원합니다.
- **제어(Control)**: 인간 개입 루프(Human-in-the-loop) 워크플로우를 지원하여 특정 작업에 인간의 승인이 필요하도록 표시할 수 있습니다.

Microsoft Agent Framework는 또한 상호 운용성에 중점을 둡니다:

- **클라우드에 구애받지 않음(Cloud-agnostic)**: 에이전트는 컨테이너, 온프레미스 및 여러 다른 클라우드에서 실행될 수 있습니다.
- **공급자에 구애받지 않음(Provider-agnostic)**: Azure OpenAI 및 OpenAI를 포함한 선호하는 SDK를 통해 에이전트를 생성할 수 있습니다.
- **개방형 표준 통합(Integrating Open Standards)**: 에이전트는 A2A(Agent-to-Agent) 및 MCP(Model Context Protocol)와 같은 프로토콜을 활용하여 다른 에이전트와 도구를 검색하고 사용할 수 있습니다.
- **플러그인 및 커넥터(Plugins and Connectors)**: Microsoft Fabric, SharePoint, Pinecone, Qdrant와 같은 데이터 및 메모리 서비스에 연결할 수 있습니다.

이러한 기능들이 Microsoft Agent Framework의 핵심 개념에 어떻게 적용되는지 살펴보겠습니다.

---

## 🧩 Microsoft Agent Framework의 핵심 개념

### 에이전트 (Agents)

![에이전트 구성 요소](./images/agent-components.png)

**에이전트 생성하기**

에이전트 생성은 추론 서비스(LLM 제공자), AI 에이전트가 따라야 할 지침 세트, 그리고 할당된 `이름`을 정의하여 수행됩니다:

```python
# Azure OpenAI 클라이언트를 사용한 에이전트 생성
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent(
    instructions="당신은 고객의 선호도에 따라 여행지를 추천하는 데 능숙합니다.",
    name="TripRecommender"
)
```

위 예시는 `Azure OpenAI`를 사용했지만, `Azure AI Foundry Agent Service`를 포함한 다양한 서비스를 사용하여 에이전트를 생성할 수 있습니다:

```python
# Azure AI Foundry Agent Service를 사용한 에이전트 생성
async with AzureAIAgentClient(async_credential=credential).create_agent(
    name="HelperAgent",
    instructions="당신은 도움이 되는 어시스턴트입니다."
) as agent:
    # 에이전트 사용
```

OpenAI `Responses`, `ChatCompletion` API를 사용할 수도 있습니다:

```python
# OpenAI Responses API 사용
agent = OpenAIResponsesClient().create_agent(
    name="WeatherBot",
    instructions="당신은 도움이 되는 날씨 어시스턴트입니다.",
)
```

```python
# OpenAI ChatCompletion API 사용
agent = OpenAIChatClient().create_agent(
    name="HelpfulAssistant",
    instructions="당신은 도움이 되는 어시스턴트입니다.",
)
```

또는 A2A 프로토콜을 사용하여 원격 에이전트를 생성할 수도 있습니다:

```python
# A2A 프로토콜을 통한 원격 에이전트
agent = A2AAgent(
    name=agent_card.name,
    description=agent_card.description,
    agent_card=agent_card,
    url="https://your-a2a-agent-host"
)
```

**에이전트 실행하기**

에이전트는 비스트리밍 또는 스트리밍 응답을 위해 `.run` 또는 `.run_stream` 메서드를 사용하여 실행됩니다.

```python
# 일반 실행
result = await agent.run("암스테르담에서 가볼 만한 좋은 곳은 어디인가요?")
print(result.text)
```

```python
# 스트리밍 실행
async for update in agent.run_stream("암스테르담에서 가볼 만한 좋은 곳은 어디인가요?"):
    if update.text:
        print(update.text, end="", flush=True)
```

각 에이전트 실행은 에이전트가 사용하는 `max_tokens`, 에이전트가 호출할 수 있는 `tools`, 심지어 에이전트에 사용되는 `model` 자체와 같은 매개변수를 사용자 지정하는 옵션을 가질 수 있습니다.

이는 사용자의 작업을 완료하는 데 특정 모델이나 도구가 필요한 경우에 유용합니다.

**도구 (Tools)**

도구는 에이전트를 정의할 때 정의할 수 있습니다:

```python
def get_attractions(
    location: Annotated[str, Field(description="최고의 관광 명소를 가져올 위치")],
) -> str:
    """주어진 위치에 대한 최고의 관광 명소를 가져옵니다."""
    return f"{location}의 주요 명소는..."

# ChatAgent를 직접 생성할 때
agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="당신은 도움이 되는 어시스턴트입니다.",
    tools=[get_attractions]  # 도구 목록 전달
)
```

또한 에이전트를 실행할 때 도구를 정의할 수도 있습니다:

```python
# 이번 실행에만 도구 제공
result1 = await agent.run(
    "시애틀에서 가장 가볼 만한 곳은 어디인가요?",
    tools=[get_attractions]  # 이 실행에만 제공되는 도구
)
```

**에이전트 스레드 (Agent Threads)**

에이전트 스레드는 다중 턴 대화를 처리하는 데 사용됩니다. 스레드는 다음 두 가지 방법 중 하나로 생성할 수 있습니다:

- 시간이 지남에 따라 스레드를 저장할 수 있게 해주는 `get_new_thread()` 사용
- 에이전트를 실행할 때 자동으로 스레드를 생성하고 현재 실행 중에만 스레드가 지속되도록 함

스레드를 생성하는 코드는 다음과 같습니다:

```python
# 새 스레드 생성
thread = agent.get_new_thread()

# 스레드로 에이전트 실행
response = await agent.run("안녕하세요, 여행 예약을 도와드리러 왔습니다. 어디로 가고 싶으신가요?", thread=thread)
```

그런 다음 스레드를 직렬화하여 나중에 사용할 수 있도록 저장할 수 있습니다:

```python
# 새 스레드 생성
thread = agent.get_new_thread()

# 스레드로 에이전트 실행
response = await agent.run("안녕하세요, 어떻게 지내세요?", thread=thread)

# 저장을 위해 스레드 직렬화
serialized_thread = await thread.serialize()

# 저장소에서 로드한 후 스레드 상태 역직렬화
resumed_thread = await agent.deserialize_thread(serialized_thread)
```

**에이전트 미들웨어 (Agent Middleware)**

에이전트는 사용자의 작업을 완료하기 위해 도구 및 LLM과 상호작용합니다. 특정 시나리오에서는 이러한 상호작용 사이에 작업을 실행하거나 추적하려고 할 수 있습니다. 에이전트 미들웨어를 통해 이를 수행할 수 있습니다:

*함수 미들웨어 (Function Middleware)*

이 미들웨어를 사용하면 에이전트와 호출할 함수/도구 사이에서 작업을 실행할 수 있습니다. 예를 들어 함수 호출에 대한 로깅을 수행하려는 경우에 사용됩니다.

아래 코드에서 `next`는 다음 미들웨어 또는 실제 함수를 호출해야 하는지 정의합니다.

```python
async def logging_function_middleware(
    context: FunctionInvocationContext,
    next: Callable[[FunctionInvocationContext], Awaitable[None]],
) -> None:
    """함수 실행을 기록하는 함수 미들웨어"""
    # 사전 처리: 함수 실행 전 로깅
    print(f"[함수] {context.function.name} 호출 중")

    # 다음 미들웨어 또는 함수 실행으로 계속 진행
    await next(context)

    # 사후 처리: 함수 실행 후 로깅
    print(f"[함수] {context.function.name} 완료됨")
```

*채팅 미들웨어 (Chat Middleware)*

이 미들웨어를 사용하면 에이전트와 LLM 간의 요청 사이에서 작업을 실행하거나 기록할 수 있습니다.

여기에는 AI 서비스로 전송되는 `messages`와 같은 중요한 정보가 포함됩니다.

```python
async def logging_chat_middleware(
    context: ChatContext,
    next: Callable[[ChatContext], Awaitable[None]],
) -> None:
    """AI 상호작용을 기록하는 채팅 미들웨어"""
    # 사전 처리: AI 호출 전 로깅
    print(f"[채팅] AI에 {len(context.messages)}개의 메시지 전송 중")

    # 다음 미들웨어 또는 AI 서비스로 계속 진행
    await next(context)

    # 사후 처리: AI 응답 후 로깅
    print("[채팅] AI 응답 수신됨")
```

**에이전트 메모리 (Agent Memory)**

`에이전틱 메모리` 강의에서 다루었듯이, 메모리는 에이전트가 다양한 컨텍스트에서 작동할 수 있도록 하는 중요한 요소입니다. MAF는 여러 가지 다양한 유형의 메모리를 제공합니다:

*인메모리 저장소 (In-Memory Storage)*

애플리케이션 런타임 중에 스레드에 저장되는 메모리입니다.

```python
# 새 스레드 생성
thread = agent.get_new_thread()

# 스레드로 에이전트 실행
response = await agent.run("안녕하세요, 여행 예약을 도와드리러 왔습니다. 어디로 가고 싶으신가요?", thread=thread)
```

*영구 메시지 (Persistent Messages)*

이 메모리는 여러 세션에 걸쳐 대화 기록을 저장할 때 사용됩니다. `chat_message_store_factory`를 사용하여 정의합니다:

```python
from agent_framework import ChatMessageStore

# 사용자 정의 메시지 저장소 생성
def create_message_store():
    return ChatMessageStore()

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="당신은 여행 어시스턴트입니다.",
    chat_message_store_factory=create_message_store  # 메시지 저장소 팩토리
)
```

*동적 메모리 (Dynamic Memory)*

이 메모리는 에이전트가 실행되기 전에 컨텍스트에 추가됩니다. 이러한 메모리는 mem0과 같은 외부 서비스에 저장될 수 있습니다:

```python
from agent_framework.mem0 import Mem0Provider

# 고급 메모리 기능을 위해 Mem0 사용
memory_provider = Mem0Provider(
    api_key="your-mem0-api-key",
    user_id="user_123",
    application_id="my_app"
)

agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="메모리를 가진 도움이 되는 어시스턴트입니다.",
    context_providers=memory_provider  # 메모리 제공자 추가
)
```

**에이전트 관찰 가능성 (Agent Observability)**

관찰 가능성은 안정적이고 유지 관리 가능한 에이전틱 시스템을 구축하는 데 중요합니다. MAF는 OpenTelemetry와 통합하여 더 나은 관찰 가능성을 위한 트레이싱 및 메트릭을 제공합니다.

```python
from agent_framework.observability import get_tracer, get_meter

tracer = get_tracer()
meter = get_meter()

# 사용자 정의 스팬 생성
with tracer.start_as_current_span("my_custom_span"):
    # 작업 수행
    pass

# 사용자 정의 카운터 생성
counter = meter.create_counter("my_custom_counter")
counter.add(1, {"key": "value"})
```

### 워크플로우 (Workflows)

MAF는 작업을 완료하기 위한 사전 정의된 단계인 워크플로우를 제공하며, 이러한 단계의 구성 요소로 AI 에이전트를 포함합니다.

워크플로우는 더 나은 제어 흐름을 허용하는 다양한 구성 요소로 구성됩니다. 또한 워크플로우는 **다중 에이전트 오케스트레이션**과 워크플로우 상태를 저장하는 **체크포인팅**을 가능하게 합니다.

워크플로우의 핵심 구성 요소는 다음과 같습니다:

**실행기 (Executors)**

실행기는 입력 메시지를 수신하고 할당된 작업을 수행한 다음 출력 메시지를 생성합니다. 이는 더 큰 작업 완료를 위해 워크플로우를 앞으로 진행시킵니다. 실행기는 AI 에이전트이거나 사용자 정의 로직일 수 있습니다.

**엣지 (Edges)**

엣지는 워크플로우에서 메시지의 흐름을 정의하는 데 사용됩니다. 다음과 같은 유형이 있습니다:

*직접 엣지 (Direct Edges)* - 실행기 간의 단순한 일대일 연결:

```python
from agent_framework import WorkflowBuilder

builder = WorkflowBuilder()
builder.add_edge(source_executor, target_executor)
builder.set_start_executor(source_executor)
workflow = builder.build()
```

*조건부 엣지 (Conditional Edges)* - 특정 조건이 충족된 후 활성화됩니다. 예를 들어, 호텔 객실을 이용할 수 없는 경우 실행기가 다른 옵션을 제안할 수 있습니다.

*스위치-케이스 엣지 (Switch-case Edges)* - 정의된 조건에 따라 메시지를 다른 실행기로 라우팅합니다. 예를 들어, 여행 고객이 우선 액세스 권한을 가지고 있어 그들의 작업이 다른 워크플로우를 통해 처리되어야 하는 경우입니다.

*팬-아웃 엣지 (Fan-out Edges)* - 하나의 메시지를 여러 대상으로 보냅니다.

*팬-인 엣지 (Fan-in Edges)* - 다른 실행기에서 여러 메시지를 수집하여 하나의 대상으로 보냅니다.

**이벤트 (Events)**

워크플로우에 더 나은 관찰 가능성을 제공하기 위해 MAF는 실행을 위한 내장 이벤트를 제공합니다. 여기에는 다음이 포함됩니다:

- `WorkflowStartedEvent` - 워크플로우 실행 시작
- `WorkflowOutputEvent` - 워크플로우 출력 생성
- `WorkflowErrorEvent` - 워크플로우 오류 발생
- `ExecutorInvokeEvent` - 실행기 처리 시작
- `ExecutorCompleteEvent` - 실행기 처리 완료
- `RequestInfoEvent` - 요청 발행

---

## 🔄 다른 프레임워크에서 마이그레이션하기 (Semantic Kernel 및 AutoGen)

### MAF와 Semantic Kernel의 차이점

**간소화된 에이전트 생성**

Semantic Kernel은 모든 에이전트에 대해 Kernel 인스턴스를 생성해야 합니다. MAF는 주요 제공자에 대한 확장을 사용하여 더 간소화된 접근 방식을 사용합니다.

```python
# MAF: 직접 클라이언트에서 에이전트 생성
agent = AzureOpenAIChatClient(credential=AzureCliCredential()).create_agent(
    instructions="당신은 고객의 선호도에 따라 여행지를 추천하는 데 능숙합니다.",
    name="TripRecommender"
)
```

**에이전트 스레드 생성**

Semantic Kernel은 스레드를 수동으로 생성해야 합니다. MAF에서는 에이전트에 직접 스레드가 할당됩니다.

```python
# MAF: 에이전트에서 직접 스레드 생성
thread = agent.get_new_thread()
```

**도구 등록**

Semantic Kernel에서는 도구가 Kernel에 등록되고 Kernel이 에이전트에 전달됩니다. MAF에서는 에이전트 생성 과정 중에 도구가 직접 등록됩니다.

```python
# MAF: 에이전트 생성 시 도구 직접 등록
agent = ChatAgent(
    chat_client=OpenAIChatClient(),
    instructions="당신은 도움이 되는 어시스턴트입니다.",
    tools=[get_attractions]  # 도구 직접 전달
)
```

### MAF와 AutoGen의 차이점

**팀(Teams) vs 워크플로우(Workflows)**

`Teams`는 AutoGen에서 에이전트와의 이벤트 기반 활동을 위한 구조입니다. MAF는 그래프 기반 아키텍처를 통해 데이터를 실행기로 라우팅하는 `Workflows`를 사용합니다.

**도구 생성**

AutoGen은 에이전트가 호출할 함수를 래핑하기 위해 `FunctionTool`을 사용합니다. MAF는 유사하게 작동하지만 각 함수에 대한 스키마를 자동으로 추론하는 `@ai_function` 데코레이터를 사용합니다.

**에이전트 동작**

AutoGen에서 에이전트는 `max_tool_iterations`가 더 높게 설정되지 않는 한 기본적으로 단일 턴 에이전트입니다. MAF 내에서 `ChatAgent`는 기본적으로 다중 턴입니다. 즉, 사용자의 작업이 완료될 때까지 계속 도구를 호출합니다.

---

## 💻 코드 샘플

Microsoft Agent Framework에 대한 코드 샘플은 이 저장소의 `xx-python-agent-framework` 및 `xx-dotnet-agent-framework` 파일에서 찾을 수 있습니다.

---

## ❓ Microsoft Agent Framework에 대해 더 궁금한 점이 있나요?

[Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하여 다른 학습자들을 만나고, 오피스 아워에 참여하고 AI Agents에 대한 질문에 대한 답변을 받아보세요.

---

*이 가이드가 여러분의 AI 에이전트 개발 여정에 강력한 새로운 도구를 제공했기를 바랍니다!* 🚀