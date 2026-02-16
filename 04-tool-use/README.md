
[![좋은 AI Agent 디자인 방법](./images/lesson-4-thumbnail.png)](https://youtu.be/vieRiPRx-gI?si=cEZ8ApnT6Sus9rhn)

> _(👆 이미지를 클릭하면 이번 레슨의 강의 영상을 볼 수 있어요!)_

# 🛠️ 도구 사용(Tool Use) 디자인 패턴 - AI Agent에게 날개를 달아주다

도구는 정말 흥미로운 주제예요. 왜냐하면 AI Agent가 훨씬 더 다양한 능력을 발휘할 수 있게 해주기 때문이죠! Agent가 수행할 수 있는 동작이 제한되어 있을 때는 한계가 명확하지만, 도구를 추가하는 순간 Agent는 무한한 가능성을 가지게 됩니다. 이번 장에서는 AI Agent가 특정 도구를 사용하여 목표를 달성하는 방법을 설명하는 **도구 사용 디자인 패턴**에 대해 자세히 알아볼 거예요.

## 🎯 소개

이번 레슨에서는 다음 질문들에 대한 답을 찾아보려고 해요:

- 도구 사용 디자인 패턴이란 정확히 무엇인가요?
- 어떤 상황(사용 사례)에 적용할 수 있을까요?
- 이 디자인 패턴을 구현하는 데 필요한 요소/구성 요소는 무엇인가요?
- 신뢰할 수 있는 AI Agent를 만들기 위해 도구 사용 디자인 패턴을 사용할 때 특별히 고려해야 할 사항은 무엇인가요?

## 📚 학습 목표

이번 레슨을 완료하면 여러분은 다음을 할 수 있게 됩니다:

- 도구 사용 디자인 패턴과 그 목적을 명확하게 정의할 수 있습니다.
- 도구 사용 디자인 패턴을 적용할 수 있는 적절한 사용 사례를 스스로 찾아낼 수 있습니다.
- 디자인 패턴을 구현하는 데 필요한 핵심 요소들을 이해하고 설명할 수 있습니다.
- 이 패턴을 사용하여 신뢰할 수 있는 AI Agent를 구축할 때 반드시 고려해야 할 사항들을 인지하게 됩니다.

---

## 🤔 도구 사용 디자인 패턴이란 무엇인가요?

**도구 사용 디자인 패턴**은 LLM(대규모 언어 모델)이 특정 목표를 달성하기 위해 외부 도구와 상호작용할 수 있는 능력을 부여하는 데 초점을 맞춥니다. 여기서 '도구'란 Agent가 작업을 수행하기 위해 실행할 수 있는 코드 조각을 의미해요. 도구는 계산기처럼 아주 간단한 함수일 수도 있고, 주식 가격을 조회하거나 일기 예보를 가져오는 것과 같은 외부 서비스 API 호출처럼 복잡할 수도 있습니다. AI Agent의 세계에서 도구는 **모델이 생성한 함수 호출(model-generated function calls)** 에 대한 응답으로 Agent가 실행하도록 설계됩니다.

## 💡 어떤 사용 사례에 적용할 수 있나요?

AI Agent는 도구를 활용하여 복잡한 작업을 완료하고, 필요한 정보를 찾고, 스스로 결정을 내릴 수 있습니다. 도구 사용 디자인 패턴은 주로 데이터베이스, 웹 서비스, 코드 해석기 등 외부 시스템과 동적으로 상호작용해야 하는 시나리오에서 사용됩니다. 이 능력은 정말 다양한 분야에서 유용하게 쓰일 수 있어요:

- **실시간 정보 검색:** Agent가 외부 API나 데이터베이스에 직접 질의하여 최신 데이터를 가져올 수 있습니다. (예: 데이터 분석을 위해 SQLite 데이터베이스에 질의하거나, 실시간 주식 가격이나 날씨 정보를 가져오기)
- **코드 실행 및 해석:** Agent가 코드나 스크립트를 직접 실행하여 수학 문제를 풀거나, 보고서를 생성하거나, 시뮬레이션을 수행할 수 있습니다.
- **워크플로우 자동화:** 작업 스케줄러, 이메일 서비스, 데이터 파이프라인과 같은 도구를 통합하여 지루하고 반복적인 작업이나 여러 단계로 구성된 업무 흐름을 자동화합니다.
- **고객 지원:** Agent가 CRM 시스템, 티켓 발행 플랫폼, 지식 베이스(FAQ)와 직접 상호작용하여 사용자 문의를 신속하고 정확하게 해결합니다.
- **콘텐츠 생성 및 편집:** Agent가 맞춤법 검사기, 텍스트 요약기, 콘텐츠 안전 평가기와 같은 도구를 활용하여 블로그 글 작성, 보고서 요약 등 콘텐츠 제작 업무를 도와줄 수 있습니다.

---

## 🧩 이 디자인 패턴을 구현하는 데 필요한 요소(구성 요소)는 무엇인가요?

이러한 구성 요소들은 마치 레고 블록처럼 조립되어 AI Agent가 거의 모든 종류의 작업을 수행할 수 있게 해줍니다. 도구 사용 디자인 패턴을 구현하는 데 필요한 핵심 요소들을 하나씩 살펴보겠습니다:

- **함수/도구 스키마 (Function/Tool Schemas)**: Agent가 사용할 수 있는 도구들에 대한 상세한 설명서입니다. 함수 이름, 기능 설명, 필요한 입력값(매개변수), 그리고 기대되는 출력 결과가 포함됩니다. 이 스키마 덕분에 LLM은 어떤 도구가 있는지, 그리고 그 도구를 사용하려면 어떻게 요청을 구성해야 하는지 정확히 이해할 수 있습니다.
- **함수 실행 로직 (Function Execution Logic)**: 사용자의 의도와 대화 맥락에 따라 어떤 도구를, 언제 호출할지 결정하는 규칙과 절차입니다. 여기에는 작업을 계획하는 플래너 모듈, 요청을 적절한 도구로 안내하는 라우팅 메커니즘, 상황에 따라 도구 사용을 동적으로 결정하는 조건부 흐름 등이 포함될 수 있습니다.
- **메시지 처리 시스템 (Message Handling System)**: 사용자 입력, LLM 응답, 도구 호출, 도구 실행 결과 등 대화의 모든 흐름을 관리하는 시스템입니다. 모든 구성 요소 간의 원활한 소통을 책임집니다.
- **도구 통합 프레임워크 (Tool Integration Framework)**: Agent를 다양한 도구(간단한 함수부터 복잡한 외부 서비스까지)에 연결해주는 인프라입니다. Agent가 도구를 쉽게 찾고 사용할 수 있도록 돕는 연결고리 역할을 합니다.
- **오류 처리 및 유효성 검사 (Error Handling & Validation)**: 도구 실행 중 발생할 수 있는 오류(예: API 서버 다운, 잘못된 입력값)를 처리하고, 매개변수가 올바른지 확인하며, 예상치 못한 응답을 우아하게 처리하는 메커니즘입니다.
- **상태 관리 (State Management)**: 여러 번의 대화에 걸쳐 일관성을 유지하기 위해 대화 맥락, 이전에 사용한 도구와 그 결과, 그리고 지속적으로 필요한 데이터를 추적하고 관리합니다.

이제 이 중에서도 가장 핵심이라고 할 수 있는 **함수/도구 호출**에 대해 더 자세히 알아보겠습니다.

### 📞 함수/도구 호출 (Function/Tool Calling)

함수 호출은 LLM이 도구와 상호작용할 수 있게 하는 핵심 메커니즘입니다. 실제로 개발자들 사이에서는 '함수'와 '도구'라는 용어를 혼용해서 사용하는 경우가 많아요. 왜냐하면 재사용 가능한 코드 블록인 '함수'가 바로 Agent가 작업을 수행하는 '도구'이기 때문입니다. 함수의 코드가 실행되려면, LLM이 사용자의 요청과 함수의 기능 설명을 비교하는 과정이 필요합니다. 이를 위해 사용 가능한 모든 함수에 대한 설명이 담긴 스키마가 LLM으로 전송됩니다. 그러면 LLM은 주어진 작업에 가장 적합한 함수를 선택하고, 그 함수의 이름과 필요한 인수(arguments)를 반환합니다. 이후 선택된 함수가 실제로 호출되고, 그 실행 결과는 다시 LLM으로 보내져 사용자 요청에 대한 최종 응답을 생성하는 데 사용됩니다.

개발자가 Agent를 위한 함수 호출을 구현하려면 다음 세 가지가 반드시 필요합니다:

1. **함수 호출을 지원하는 LLM 모델**: 모든 LLM이 이 기능을 지원하는 것은 아니니, 사용하려는 모델의 사양을 꼭 확인해야 합니다.
2. **함수 설명을 담은 스키마**: 각 함수가 무엇이고, 어떤 입력을 받고, 어떤 출력을 내는지에 대한 명확한 설명이 담긴 JSON 형태의 문서입니다.
3. **각 함수의 실제 코드**: 함수 스키마에 설명된 대로 실제로 동작하는 코드입니다.

자, 그럼 '도시의 현재 시간을 알려주는' 간단한 예제를 통해 함수 호출이 실제로 어떻게 이루어지는지 단계별로 살펴보겠습니다.

1. **함수 호출을 지원하는 LLM 초기화:**

   먼저 함수 호출을 지원하는 LLM 클라이언트를 초기화합니다. 여기서는 `<a href="https://learn.microsoft.com/azure/ai-services/openai/how-to/function-calling" target="_blank">`Azure OpenAI `</a>`를 사용할게요.

   ```python
   # Azure OpenAI 클라이언트 초기화
   client = AzureOpenAI(
       azure_endpoint = os.getenv("AZURE_OPENAI_ENDPOINT"),
       api_key=os.getenv("AZURE_OPENAI_API_KEY"),
       api_version="2024-05-01-preview"
   )
   ```
2. **함수 스키마 생성:**

   다음으로, LLM에게 우리가 제공할 수 있는 도구가 무엇인지 알려주기 위한 함수 스키마를 정의합니다. `get_current_time`이라는 함수가 있고, 이 함수는 `location`이라는 도시 이름을 입력받아 현재 시간을 알려준다는 정보를 담고 있습니다.

   ```python
   # 모델이 읽을 함수 설명 (스키마)
   tools = [
       {
           "type": "function",
           "function": {
               "name": "get_current_time",
               "description": "주어진 위치의 현재 시간을 가져옵니다",
               "parameters": {
                   "type": "object",
                   "properties": {
                       "location": {
                           "type": "string",
                           "description": "도시 이름 (예: San Francisco)",
                       },
                   },
                   "required": ["location"], # location은 반드시 필요한 입력값입니다.
               },
           }
       }
   ]
   ```

   이제 사용자의 메시지("What's the current time in San Francisco")와 함께 이 스키마를 LLM에 전송합니다. 여기서 중요한 점은 LLM이 반환하는 것은 질문에 대한 **최종 답변이 아니라, 어떤 도구를 어떻게 사용해야 할지에 대한 정보, 즉 '도구 호출(tool call)'** 이라는 것입니다.

   ```python
   # 초기 사용자 메시지
   messages = [{"role": "user", "content": "What's the current time in San Francisco"}]

   # 첫 번째 API 호출: 모델에게 함수를 사용하도록 요청
   response = client.chat.completions.create(
       model=deployment_name, # 사용할 모델 이름
       messages=messages,
       tools=tools,           # 생성한 함수 스키마 전달
       tool_choice="auto",    # 모델이 자동으로 도구 사용 여부를 결정하도록 설정
   )

   # 모델의 응답 처리
   response_message = response.choices[0].message
   messages.append(response_message)

   print("모델 응답:")
   print(response_message)
   ```

   ```bash
   # 출력 결과
   모델 응답:
   ChatCompletionMessage(content=None, role='assistant', function_call=None, tool_calls=[ChatCompletionMessageToolCall(id='call_pOsKdUlqvdyttYB67MOj434b', function=Function(arguments='{"location":"San Francisco"}', name='get_current_time'), type='function')])
   ```

   보시는 것처럼 `content`는 `None`이고, 대신 `tool_calls` 항목에 LLM이 선택한 함수 이름(`get_current_time`)과 함께 함수에 전달할 인수(`arguments: {"location":"San Francisco"}`)가 담겨 있습니다.
3. **작업을 수행할 함수 코드 실행:**

   이제 LLM이 선택한 함수를 실제로 실행할 차례입니다. `get_current_time` 함수의 코드를 구현하고, 앞서 받은 응답에서 함수 이름과 인수를 추출하여 이 함수를 호출합니다.

   ```python
   # 실제로 현재 시간을 가져오는 함수 코드
   def get_current_time(location):
       """주어진 위치의 현재 시간을 가져옵니다"""
       print(f"get_current_time 함수가 location: {location}로 호출됨")
       location_lower = location.lower()

       # TIMEZONE_DATA 딕셔너리에서 해당 도시의 시간대를 찾아 현재 시간 계산 (예시 코드)
       for key, timezone in TIMEZONE_DATA.items():
           if key in location_lower:
               print(f"{key}에 대한 시간대를 찾음")
               current_time = datetime.now(ZoneInfo(timezone)).strftime("%I:%M %p")
               return json.dumps({
                   "location": location,
                   "current_time": current_time
               })

       print(f"{location_lower}에 대한 시간대 데이터를 찾을 수 없음")
       return json.dumps({"location": location, "current_time": "unknown"})
   ```

   ```python
   # 함수 호출 처리 및 최종 응답 생성
   if response_message.tool_calls:
       for tool_call in response_message.tool_calls:
           if tool_call.function.name == "get_current_time":

               function_args = json.loads(tool_call.function.arguments) # 인수 추출
               time_response = get_current_time(                         # 함수 실행
                   location=function_args.get("location")
               )

               # 함수 실행 결과를 메시지에 추가 (대화 맥락 유지)
               messages.append({
                   "tool_call_id": tool_call.id,
                   "role": "tool",
                   "name": "get_current_time",
                   "content": time_response,
               })
   else:
       print("모델이 도구 호출을 수행하지 않았습니다.")

   # 두 번째 API 호출: 함수 실행 결과를 포함하여 모델에게 최종 응답 생성 요청
   final_response = client.chat.completions.create(
       model=deployment_name,
       messages=messages, # 함수 실행 결과가 추가된 메시지 전달
   )

   print(final_response.choices[0].message.content)
   ```

   ```bash
   # 최종 출력 결과
   get_current_time 함수가 location: San Francisco로 호출됨
   san francisco에 대한 시간대를 찾음
   The current time in San Francisco is 09:24 AM.
   ```

   드디어 사용자가 원했던 최종 답변("The current time in San Francisco is 09:24 AM.")을 얻었습니다!

함수 호출은 대부분의 Agent 도구 사용 디자인의 핵심이지만, 이 모든 과정을 매번 직접 구현하는 것은 상당히 번거롭고 복잡할 수 있습니다. 다행히도 [2강](../02-explore-agentic-frameworks/)에서 배웠듯이, Agent 프레임워크들은 이러한 복잡한 과정을 추상화하고 미리 만들어진 구성 요소를 제공하여 훨씬 쉽게 도구 사용 패턴을 구현할 수 있도록 도와줍니다.

---

## 🚀 Agent 프레임워크를 활용한 도구 사용 예제

그럼 지금부터 인기 있는 Agent 프레임워크들을 사용하여 도구 사용 디자인 패턴을 얼마나 쉽고 간편하게 구현할 수 있는지 살펴보겠습니다.

### Semantic Kernel

`<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">`Semantic Kernel `</a>`은 .NET, Python, Java 개발자를 위한 오픈 소스 AI 프레임워크입니다. Semantic Kernel의 가장 큰 장점 중 하나는 함수 호출 과정을 극도로 단순화한다는 점이에요. 개발자가 함수와 파라미터를 정의하면, 프레임워크가 자동으로 이를 LLM이 이해할 수 있는 스키마로 **직렬화(serializing)** 하고, LLM과 코드 간의 모든 통신을 알아서 처리해줍니다. 또한, `<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step4_assistant_tool_file_search.py" target="_blank">`파일 검색 `</a>`이나 `<a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">`코드 인터프리터 `</a>`와 같이 자주 사용되는 강력한 도구들을 기본적으로 제공합니다.

다음 다이어그램은 Semantic Kernel에서 함수 호출이 어떻게 이루어지는지 보여줍니다.

![함수 호출 다이어그램](./images/functioncalling-diagram.png)

Semantic Kernel에서는 함수/도구를 **`플러그인(Plugins)`** 이라는 개념으로 관리합니다. 앞서 만들었던 `get_current_time` 함수를 Semantic Kernel 스타일의 플러그인으로 만들어 보겠습니다. 함수를 클래스 안에 넣고, `@kernel_function` 데코레이터를 사용하여 함수에 대한 설명을 추가하기만 하면 됩니다.

```python
from semantic_kernel.functions import kernel_function

class GetCurrentTimePlugin:

    @kernel_function(
        description="주어진 위치의 현재 시간을 가져옵니다"
    )
    def get_current_time(self, location: str) -> str:
        # ... (실제 시간을 가져오는 함수 구현)
        return f"The current time in {location} is ..."
```

그리고 이 플러그인을 커널에 추가하기만 하면 모든 준비가 끝납니다. 커널이 나머지 복잡한 과정(스키마 생성, LLM과의 통신 등)을 모두 자동으로 처리해 줍니다.

```python
from semantic_kernel import Kernel

# 커널 생성
kernel = Kernel()

# 플러그인 생성 및 커널에 추가
get_current_time_plugin = GetCurrentTimePlugin()
kernel.add_plugin(get_current_time_plugin, plugin_name="time_plugin")

# 이후 사용자 요청이 들어오면 커널이 알아서 함수를 호출하고 결과를 반환합니다.
```

### Azure AI Agent Service

`<a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">`Azure AI Agent Service `</a>`는 Microsoft Ignite 2024에서 발표된 비교적 최신의 Agent 프레임워크입니다. 이 서비스의 가장 큰 특징은 개발자가 인프라(서버, 스토리지 등) 관리에 신경 쓸 필요 없이 안전하고 확장 가능한 AI Agent를 구축하고 배포할 수 있도록 도와준다는 점입니다. 특히 엔터프라이즈급 보안을 갖춘 완전 관리형 서비스이기 때문에 기업 환경에서 매우 유용하게 사용될 수 있습니다.

LLM API를 직접 사용하는 것과 비교했을 때, Azure AI Agent Service는 다음과 같은 강력한 이점을 제공합니다:

- **자동 도구 호출 (Automatic tool calling)**: 도구 호출을 파싱하고, 도구를 실행하고, 응답을 처리하는 등의 모든 과정이 서버 측에서 자동으로 처리됩니다. 개발자는 비즈니스 로직에만 집중할 수 있습니다.
- **안전하게 관리되는 데이터 (Securely managed data)**: 대화 상태(컨텍스트)를 직접 관리할 필요 없이, '스레드(threads)'라는 기능을 통해 모든 대화 정보를 안전하게 저장하고 관리할 수 있습니다.
- **즉시 사용 가능한 도구 (Out-of-the-box tools)**: Bing 검색, Azure AI Search, Azure Functions 등 자주 사용되는 엔터프라이즈급 도구들을 기본적으로 제공합니다.

Azure AI Agent Service에서 제공하는 도구는 크게 두 가지 범주로 나눌 수 있습니다:

1. **지식 도구 (Knowledge Tools)**: 외부 데이터 소스로부터 정보를 가져와 Agent의 응답을 풍부하게 만듭니다.
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/bing-grounding?tabs=python&pivots=overview" target="_blank">Bing 검색 기반 근거 확인 (Grounding with Bing Search)</a>`
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/file-search?tabs=python&pivots=overview" target="_blank">파일 검색 (File Search)</a>`
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=overview-azure-ai-search" target="_blank">Azure AI Search</a>`
2. **액션 도구 (Action Tools)**: Agent가 특정 작업을 직접 수행할 수 있게 합니다.
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/function-calling?tabs=python&pivots=overview" target="_blank">함수 호출 (Function Calling)</a>`
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/code-interpreter?tabs=python&pivots=overview" target="_blank">코드 인터프리터 (Code Interpreter)</a>`
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/openapi-spec?tabs=python&pivots=overview" target="_blank">OpenAPI 정의 도구</a>`
   - `<a href="https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-functions?pivots=overview" target="_blank">Azure Functions</a>`

이러한 도구들은 `toolset`으로 묶어서 Agent에 한 번에 제공할 수 있으며, `threads`를 통해 대화의 맥락을 유지할 수 있습니다.

예를 들어, 여러분이 Contoso라는 회사의 영업 사원이고, 영업 데이터에 대해 질문하면 답변해주는 대화형 Agent를 개발한다고 가정해 보겠습니다. 아래 그림은 Azure AI Agent Service를 사용하여 이러한 Agent를 구현하는 개념을 보여줍니다.

![Agentic Service In Action](./images/agent-service-in-action.jpg)

이를 실제 Python 코드로 구현하면 다음과 같습니다. 사용자 요청에 따라 LLM이 `toolset`을 보고, 직접 만든 함수(`fetch_sales_data_using_sqlite_query`)를 사용할지, 아니면 기본 제공되는 코드 인터프리터를 사용할지 결정하게 됩니다.

```python
import os
from azure.ai.projects import AIProjectClient
from azure.identity import DefaultAzureCredential
# 사용자 정의 함수 import (fetch_sales_data_functions.py 파일에 있다고 가정)
from fetch_sales_data_functions import fetch_sales_data_using_sqlite_query
from azure.ai.projects.models import ToolSet, FunctionTool, CodeInterpreterTool

# 프로젝트 클라이언트 생성
project_client = AIProjectClient.from_connection_string(
    credential=DefaultAzureCredential(),
    conn_str=os.environ["PROJECT_CONNECTION_STRING"],
)

# Toolset 초기화
toolset = ToolSet()

# 사용자 정의 함수(Function Tool)를 toolset에 추가
fetch_data_function = FunctionTool(fetch_sales_data_using_sqlite_query)
toolset.add(fetch_data_function)

# 코드 인터프리터(Code Interpreter)를 toolset에 추가
code_interpreter = CodeInterpreterTool()
toolset.add(code_interpreter)

# Agent 생성 (toolset을 함께 전달)
agent = project_client.agents.create_agent(
    model="gpt-4o-mini",
    name="sales-data-agent",
    instructions="당신은 영업 데이터를 분석하는 도우미입니다. 주어진 도구를 활용하여 질문에 답변하세요.",
    toolset=toolset # 정의한 toolset 전달
)
```

---

## 🔒 신뢰할 수 있는 AI Agent 구축을 위한 특별 고려 사항

LLM이 동적으로 생성하는 SQL과 관련하여 항상 따라다니는 우려는 바로 **보안**입니다. 특히 SQL 인젝션 공격이나, 악의적인 사용자가 데이터베이스를 삭제(drop)하거나 변조(tampering)할 위험에 대한 걱정이 많습니다. 이러한 우려는 충분히 타당하지만, 다행히도 데이터베이스 접근 권한을 적절하게 설정함으로써 효과적으로 완화할 수 있습니다.

가장 기본적이고 강력한 방법은 Agent가 사용하는 데이터베이스 계정에 **읽기 전용(read-only) 권한만 부여**하는 것입니다. 대부분의 데이터베이스 시스템(PostgreSQL, Azure SQL 등)에서는 애플리케이션에 `SELECT` 권한만 있는 역할(role)을 할당하면 됩니다. 이렇게 하면 LLM이 아무리 창의적인(?) SQL을 생성하더라도 데이터를 조회하는 것 외에는 어떤 변경도 가할 수 없습니다.

또한, 애플리케이션 자체를 안전한 환경(예: 가상 네트워크 내부)에서 실행하면 보안이 한층 더 강화됩니다. 실제 엔터프라이즈 환경에서는 운영 시스템의 데이터를 추출하여, 분석에 최적화되고 사용하기 쉬운 스키마를 가진 별도의 읽기 전용 데이터베이스나 데이터 웨어하우스로 복제하여 사용합니다. 이렇게 함으로써 원본 데이터의 안전을 보장하고, Agent의 접근을 필요한 만큼만(읽기 전용) 엄격하게 제한할 수 있습니다.

---

## 💻 샘플 코드

- Python: [Agent 프레임워크](./code_samples/04-python-agent-framework.ipynb)
- .NET: [Agent 프레임워크](./code_samples/04-dotnet-agent-framework.md)

---

## ❓ 도구 사용 디자인 패턴에 대해 더 궁금한 점이 있나요?

[Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)에 참여하여 전 세계의 다른 학습자 및 전문가들과 함께 이야기 나누고, 정기적으로 열리는 오피스 아워에 참여하여 궁금증을 해결하세요!

---

## 📚 추가 학습 자료

- <a href="https://microsoft.github.io/build-your-first-agent-with-azure-ai-agent-service-workshop/" target="_blank">Azure AI Agents Service 워크샵 (영문)</a>
- <a href="https://github.com/Azure-Samples/contoso-creative-writer/tree/main/docs/workshop" target="_blank">Contoso Creative Writer 다중 Agent 워크샵 (영문)</a>
- <a href="https://learn.microsoft.com/semantic-kernel/concepts/ai-services/chat-completion/function-calling/?pivots=programming-language-python#1-serializing-the-functions" target="_blank">Semantic Kernel 함수 호출 공식 튜토리얼 (영문)</a>
- <a href="https://github.com/microsoft/semantic-kernel/blob/main/python/samples/getting_started_with_agents/openai_assistant/step3_assistant_tool_code_interpreter.py" target="_blank">Semantic Kernel 코드 인터프리터 예제 코드 (영문)</a>
- <a href="https://microsoft.github.io/autogen/dev/user-guide/core-user-guide/components/tools.html" target="_blank">Autogen 도구 사용 가이드 (영문)</a>

---

## 📚 레슨 목차

### ⬅️ 이전 레슨

[3강: Agentic 디자인 패턴 이해하기](../03-agentic-design-patterns/README.md)

### ➡️ 다음 레슨

[5강: Agentic RAG (검색 증강 생성)](../05-agentic-rag/README.md)

---

*이 가이드가 여러분의 AI Agent 개발 여정에 날개를 달아주길 바랍니다!* 🚀
