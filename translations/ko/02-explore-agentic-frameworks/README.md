<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "86b9c2b24da3b3e61711182ffa72601c",
  "translation_date": "2025-09-29T22:06:27+00:00",
  "source_file": "02-explore-agentic-frameworks/README.md",
  "language_code": "ko"
}
-->
[![AI 에이전트 프레임워크 탐구](../../../translated_images/lesson-2-thumbnail.c65f44c93b8558df4d5d407e29970e654629e614f357444a9c27c80feb54c79d.ko.png)](https://youtu.be/ODwF-EZo_O8?si=1xoy_B9RNQfrYdF7)

> _(위 이미지를 클릭하면 강의 영상을 볼 수 있어요)_

# AI 에이전트 프레임워크 탐구

AI 에이전트 프레임워크는 AI 에이전트의 생성, 배포, 관리를 간소화하기 위해 만들어진 소프트웨어 플랫폼이에요. 개발자에게 사전 구축된 구성 요소, 추상화, 도구를 제공해서 복잡한 AI 시스템 개발을 쉽게 해줘요.

이런 프레임워크는 AI 에이전트 개발에서 흔히 발생하는 문제에 표준화된 접근 방식을 제공해요. 덕분에 개발자가 애플리케이션의 고유한 부분에 집중할 수 있고, AI 시스템 구축의 확장성과 효율성이 높아지죠.

## 이번 강의 내용

- AI 에이전트 프레임워크란? 개발자가 뭘 할 수 있을까?
- 팀이 에이전트 기능을 빠르게 프로토타입하고 개선하는 방법
- Microsoft의 프레임워크 비교: AutoGen, Semantic Kernel, Azure AI Agent Service
- 기존 Azure 생태계 도구와의 통합 가능 여부
- Azure AI Agent Service 소개

## 학습 목표

이 강의를 마치면:

- AI 에이전트 프레임워크가 AI 개발에서 하는 역할을 이해해요
- AI 에이전트 프레임워크로 지능형 에이전트를 만드는 방법을 알게 돼요
- AI 에이전트 프레임워크의 주요 기능을 파악해요
- AutoGen, Semantic Kernel, Azure AI Agent Service의 차이를 알게 돼요

## AI 에이전트 프레임워크란?

### 기존 AI 프레임워크 vs 에이전트 프레임워크

전통적인 AI 프레임워크도 앱에 AI를 통합해서 개선하는 데 도움이 돼요:

| 기능 | 설명 | 예시 |
|------|------|------|
| **개인화** | 사용자 행동과 선호도 분석으로 맞춤 추천 | Netflix가 시청 기록 기반으로 영화 추천 |
| **자동화 및 효율성** | 반복 작업 자동화, 워크플로 간소화 | 고객 서비스 챗봇이 일반 문의 처리 |
| **향상된 UX** | 음성 인식, NLP, 예측 텍스트 등 | Siri, Google Assistant 같은 가상 비서 |

### 그런데 왜 AI 에이전트 프레임워크가 필요할까?

AI 에이전트 프레임워크는 단순한 AI 프레임워크 이상이에요. 사용자, 다른 에이전트, 환경과 상호작용해서 특정 목표를 달성하는 **지능형 에이전트**를 만들 수 있어요. 이런 에이전트는:

- 자율적으로 행동하고
- 스스로 결정하고
- 변화하는 상황에 적응할 수 있어요

| 주요 기능 | 설명 |
|-----------|------|
| **에이전트 간 협업** | 여러 AI 에이전트가 협력해서 복잡한 작업 해결 |
| **작업 자동화** | 다단계 워크플로, 작업 위임, 동적 작업 관리 |
| **맥락 이해 및 적응** | 맥락을 이해하고 실시간 정보 기반으로 결정 |

요약하면, 에이전트는 자동화를 한 단계 더 발전시키고, 환경에서 학습하고 적응하는 더 지능적인 시스템을 만들어줘요.

## 빠르게 프로토타입하고 개선하는 방법

이 분야는 빠르게 변하고 있지만, 대부분의 AI 에이전트 프레임워크에서 공통적으로 제공하는 요소들이 있어요:

| 접근 방식 | 설명 |
|-----------|------|
| **모듈 구성 요소** | AI 커넥터, 메모리 커넥터, 플러그인, 프롬프트 템플릿 등 사전 구축된 컴포넌트 |
| **협업 도구** | 특정 역할과 작업을 가진 에이전트 설계로 협업 워크플로 테스트 |
| **실시간 학습** | 상호작용에서 학습하고 동적으로 행동을 조정하는 피드백 루프 |

### 모듈 구성 요소 사용

Semantic Kernel이나 LangChain 같은 SDK는 AI 커넥터, 프롬프트 템플릿, 메모리 관리 등 사전 구축된 구성 요소를 제공해요.

**팀이 활용하는 방법**: 이런 구성 요소를 빠르게 조립해서 기능적인 프로토타입을 만들 수 있어요. 처음부터 다 만들 필요 없이 빠르게 실험하고 반복할 수 있죠.

**실제 활용**: 사용자 입력에서 정보를 추출하는 파서, 데이터를 저장/검색하는 메모리 모듈, 사용자와 상호작용하는 프롬프트 생성기 등을 직접 구축하지 않고 바로 사용할 수 있어요.

**예제 코드**: Semantic Kernel Python과 .NET에서 자동 함수 호출을 사용하는 사전 구축된 AI 커넥터 예제를 볼게요:

``` python
# Semantic Kernel Python Example

import asyncio
from typing import Annotated

from semantic_kernel.connectors.ai import FunctionChoiceBehavior
from semantic_kernel.connectors.ai.open_ai import AzureChatCompletion, AzureChatPromptExecutionSettings
from semantic_kernel.contents import ChatHistory
from semantic_kernel.functions import kernel_function
from semantic_kernel.kernel import Kernel

# Define a ChatHistory object to hold the conversation's context
chat_history = ChatHistory()
chat_history.add_user_message("I'd like to go to New York on January 1, 2025")


# Define a sample plugin that contains the function to book travel
class BookTravelPlugin:
    """A Sample Book Travel Plugin"""

    @kernel_function(name="book_flight", description="Book travel given location and date")
    async def book_flight(
        self, date: Annotated[str, "The date of travel"], location: Annotated[str, "The location to travel to"]
    ) -> str:
        return f"Travel was booked to {location} on {date}"

# Create the Kernel
kernel = Kernel()

# Add the sample plugin to the Kernel object
kernel.add_plugin(BookTravelPlugin(), plugin_name="book_travel")

# Define the Azure OpenAI AI Connector
chat_service = AzureChatCompletion(
    deployment_name="YOUR_DEPLOYMENT_NAME", 
    api_key="YOUR_API_KEY", 
    endpoint="https://<your-resource>.azure.openai.com/",
)

# Define the request settings to configure the model with auto-function calling
request_settings = AzureChatPromptExecutionSettings(function_choice_behavior=FunctionChoiceBehavior.Auto())


async def main():
    # Make the request to the model for the given chat history and request settings
    # The Kernel contains the sample that the model will request to invoke
    response = await chat_service.get_chat_message_content(
        chat_history=chat_history, settings=request_settings, kernel=kernel
    )
    assert response is not None

    """
    Note: In the auto function calling process, the model determines it can invoke the 
    `BookTravelPlugin` using the `book_flight` function, supplying the necessary arguments. 
    
    For example:

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

    Since the location and date arguments are required (as defined by the kernel function), if the 
    model lacks either, it will prompt the user to provide them. For instance:

    User: Book me a flight to New York.
    Model: Sure, I'd love to help you book a flight. Could you please specify the date?
    User: I want to travel on January 1, 2025.
    Model: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels!
    """

    print(f"`{response}`")
    # Example AI Model Response: `Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽`

    # Add the model's response to our chat history context
    chat_history.add_assistant_message(response.content)


if __name__ == "__main__":
    asyncio.run(main())
```
```csharp
// Semantic Kernel C# example

using Microsoft.SemanticKernel;
using Microsoft.SemanticKernel.ChatCompletion;
using System.ComponentModel;
using Microsoft.SemanticKernel.Connectors.AzureOpenAI;

ChatHistory chatHistory = [];
chatHistory.AddUserMessage("I'd like to go to New York on January 1, 2025");

var kernelBuilder = Kernel.CreateBuilder();
kernelBuilder.AddAzureOpenAIChatCompletion(
    deploymentName: "NAME_OF_YOUR_DEPLOYMENT",
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
Behind the scenes, the model recognizes the tool to call, what arguments it already has (location) and (date)
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

// Example AI Model Response: Your flight to New York on January 1, 2025, has been successfully booked. Safe travels! ✈️🗽

// Define a plugin that contains the function to book travel
public class BookTravelPlugin
{
    [KernelFunction("book_flight")]
    [Description("Book travel given location and date")]
    public async Task<string> BookFlight(DateTime date, string location)
    {
        return await Task.FromResult( $"Travel was booked to {location} on {date}");
    }
}
```
  
이 예제처럼 사용자 입력에서 출발지, 목적지, 날짜 같은 주요 정보를 추출하는 사전 구축된 파서를 활용할 수 있어요. 이런 모듈식 접근 방식 덕분에 고수준 로직에 집중할 수 있죠.

### 협업 도구 활용

CrewAI, Microsoft AutoGen, Semantic Kernel 같은 프레임워크는 여러 에이전트가 협력할 수 있도록 해줘요.

**팀이 활용하는 방법**: 특정 역할과 작업을 가진 에이전트를 설계해서 협업 워크플로를 테스트하고 개선하며 전체 시스템 효율성을 높일 수 있어요.

**실제 활용**: 데이터 검색, 분석, 의사 결정 같은 전문 기능을 가진 에이전트 팀을 만들 수 있어요. 이런 에이전트들은 정보를 공유하고 협력해서 사용자 질문에 답하거나 작업을 완료하죠.

**예제 코드 (AutoGen)**:

```python
# creating agents, then create a round robin schedule where they can work together, in this case in order

# Data Retrieval Agent
# Data Analysis Agent
# Decision Making Agent

agent_retrieve = AssistantAgent(
    name="dataretrieval",
    model_client=model_client,
    tools=[retrieve_tool],
    system_message="Use tools to solve tasks."
)

agent_analyze = AssistantAgent(
    name="dataanalysis",
    model_client=model_client,
    tools=[analyze_tool],
    system_message="Use tools to solve tasks."
)

# conversation ends when user says "APPROVE"
termination = TextMentionTermination("APPROVE")

user_proxy = UserProxyAgent("user_proxy", input_func=input)

team = RoundRobinGroupChat([agent_retrieve, agent_analyze, user_proxy], termination_condition=termination)

stream = team.run_stream(task="Analyze data", max_turns=10)
# Use asyncio.run(...) when running in a script.
await Console(stream)
```
  
이전 코드에서 볼 수 있듯이, 여러 에이전트가 데이터 분석 작업에 협력하는 예제예요. 각 에이전트가 특정 기능을 수행하고, 에이전트들을 조정해서 원하는 결과를 얻어요. 전문화된 역할의 에이전트를 만들면 작업 효율성과 성능이 올라가요.

### 실시간 학습

고급 프레임워크는 실시간 맥락 이해와 적응 기능을 제공해요.

**팀이 활용하는 방법**: 에이전트가 상호작용에서 학습하고 동적으로 행동을 조정하는 피드백 루프를 구현해서 지속적인 개선이 가능해요.

**실제 활용**: 에이전트가 사용자 피드백, 환경 데이터, 작업 결과를 분석해서 지식 기반을 업데이트하고, 의사 결정 알고리즘을 조정하며, 시간이 지남에 따라 성능을 개선할 수 있어요. 이런 반복 학습 덕분에 변화하는 상황과 사용자 선호도에 적응할 수 있죠.

## AutoGen, Semantic Kernel, Azure AI Agent Service 비교

이 프레임워크들을 비교하는 방법은 여러 가지가 있지만, 설계, 기능, 대상 사용 사례 측면에서 주요 차이점을 살펴볼게요.

## AutoGen

AutoGen은 Microsoft Research의 AI Frontiers Lab에서 개발한 오픈 소스 프레임워크예요. 이벤트 기반, 분산형 *에이전트* 애플리케이션을 지원하며, 여러 LLM 및 SLM, 도구, 고급 다중 에이전트 설계 패턴을 제공해요.

AutoGen은 환경을 인식하고, 결정을 내리며, 목표를 달성하기 위해 행동하는 자율적 엔터티인 에이전트를 중심으로 구축됐어요. 에이전트들은 비동기 메시지로 소통하며, 독립적이고 병렬로 작업할 수 있어서 시스템 확장성과 응답성이 높아져요.

<a href="https://en.wikipedia.org/wiki/Actor_model" target="_blank">에이전트는 액터 모델</a>을 기반으로 해요. Wikipedia에 따르면, 액터는 _동시 계산의 기본 구성 요소로, 메시지에 응답해서 로컬 결정을 내리고, 더 많은 액터를 만들고, 메시지를 보내며, 다음 메시지에 어떻게 응답할지 결정할 수 있어요_.

**사용 사례**: 코드 생성 자동화, 데이터 분석 작업, 계획 및 연구 기능을 위한 맞춤형 에이전트 구축.

AutoGen의 핵심 개념:

- **에이전트**: 다음을 수행하는 소프트웨어 엔터티:
  - **메시지를 통해 소통** (동기 또는 비동기)
  - **자신만의 상태를 유지** (들어오는 메시지로 수정 가능)
  - **행동 수행**: 메시지나 상태 변경에 응답해서 메시지 로그 업데이트, 새 메시지 전송, 코드 실행, API 호출 등

  채팅 기능을 가진 에이전트를 만드는 코드 스니펫:

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
  
  이전 코드에서 `MyAgent`는 `RoutedAgent`를 상속받아 만들었어요. 메시지 핸들러가 메시지 내용을 출력하고 `AssistantAgent` 대리자로 응답을 보내요. `self._delegate`에 `AssistantAgent` 인스턴스를 할당하는 게 핵심인데, 이건 채팅 완료를 처리하는 사전 구축된 에이전트예요.

  AutoGen에 이 에이전트 유형을 알려주고 프로그램을 시작해볼게요:

    ```python
    
    # main.py
    runtime = SingleThreadedAgentRuntime()
    await MyAgent.register(runtime, "my_agent", lambda: MyAgent())

    runtime.start()  # Start processing messages in the background.
    await runtime.send_message(MyMessageType("Hello, World!"), AgentId("my_agent", "default"))
    ```
  
  이전 코드에서 에이전트가 런타임에 등록되고, 에이전트에 메시지가 전송되어 다음과 같은 출력이 나와요:

    ```text
    # Output from the console:
    my_agent received message: Hello, World!
    my_assistant received message: Hello, World!
    my_assistant responded: Hello! How can I assist you today?
    ```
  
- **다중 에이전트**: AutoGen은 여러 에이전트가 복잡한 작업을 효율적으로 수행하도록 지원해요. 에이전트들이 정보를 공유하고 소통하며 행동을 조정해서 문제를 더 효율적으로 해결할 수 있어요. 다중 에이전트 시스템을 만들려면 데이터 검색, 분석, 의사 결정, 사용자 상호작용 같은 전문 역할의 에이전트를 정의하면 돼요:

    ```python
    editor_description = "Editor for planning and reviewing the content."

    # Example of declaring an Agent
    editor_agent_type = await EditorAgent.register(
    runtime,
    editor_topic_type,  # Using topic type as the agent type.
    lambda: EditorAgent(
        description=editor_description,
        group_chat_topic_type=group_chat_topic_type,
        model_client=OpenAIChatCompletionClient(
            model="gpt-4o-2024-08-06",
            # api_key="YOUR_API_KEY",
        ),
        ),
    )

    # remaining declarations shortened for brevity

    # Group chat
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
  
  이전 코드에서 `GroupChatManager`가 런타임에 등록됐어요. 이 매니저는 작가, 일러스트레이터, 편집자, 사용자 등 다양한 에이전트 간 상호작용을 조정하는 역할을 해요.

- **에이전트 런타임**: 프레임워크가 에이전트 간 통신을 가능하게 하고, 에이전트의 ID와 라이프사이클을 관리하며, 보안 및 개인정보 보호 경계를 강화하는 런타임 환경을 제공해요. 에이전트를 안전하고 통제된 환경에서 실행할 수 있죠. 관심 있는 두 가지 런타임:
  - **독립형 런타임**: 모든 에이전트가 같은 언어로 구현되고 같은 프로세스에서 실행되는 단일 프로세스 앱에 적합해요.
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-standalone.svg" target="_blank">독립형 런타임</a>  
    *에이전트는 런타임을 통해 메시지로 소통하며, 런타임이 에이전트 라이프사이클을 관리해요.*

  - **분산형 런타임**: 서로 다른 언어로 구현되고 다른 기기에서 실행되는 다중 프로세스 앱에 적합해요.
  
    <a href="https://microsoft.github.io/autogen/stable/_images/architecture-distributed.svg" target="_blank">분산형 런타임</a>

## Semantic Kernel + 에이전트 프레임워크

Semantic Kernel은 엔터프라이즈 준비가 된 AI 오케스트레이션 SDK예요. AI 커넥터, 메모리 커넥터, 에이전트 프레임워크로 구성돼 있어요.

핵심 구성 요소를 살펴볼게요:

- **AI 커넥터**: Python과 C#에서 외부 AI 서비스 및 데이터 소스와 인터페이스를 제공해요.

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

    // Create kernel
    var builder = Kernel.CreateBuilder();
    
    // Add a chat completion service:
    builder.Services.AddAzureOpenAIChatCompletion(
        "your-resource-name",
        "your-endpoint",
        "your-resource-key",
        "deployment-model");
    var kernel = builder.Build();
    ```
  
  여기서는 커널을 만들고 채팅 완료 서비스를 추가하는 간단한 예제예요. Semantic Kernel이 외부 AI 서비스(이 경우 Azure OpenAI Chat Completion)와 연결을 만들어요.

- **플러그인**: 앱에서 사용할 기능을 캡슐화해요. 준비된 플러그인과 직접 만드는 맞춤형 플러그인이 있어요. 관련 개념인 "프롬프트 함수"는 함수 호출을 위한 자연어 큐 대신 특정 기능을 모델에 브로드캐스트해요. 현재 채팅 컨텍스트에 따라 모델이 요청을 완료하기 위해 이 함수들 중 하나를 호출할 수 있어요:

  ```python
  from semantic_kernel.connectors.ai.open_ai.services.azure_chat_completion import AzureChatCompletion


  async def main():
      from semantic_kernel.functions import KernelFunctionFromPrompt
      from semantic_kernel.kernel import Kernel

      kernel = Kernel()
      kernel.add_service(AzureChatCompletion())

      user_input = input("User Input:> ")

      kernel_function = KernelFunctionFromPrompt(
          function_name="SummarizeText",
          prompt="""
          Summarize the provided unstructured text in a sentence that is easy to understand.
          Text to summarize: {{$user_input}}
          """,
      )

      response = await kernel_function.invoke(kernel=kernel, user_input=user_input)
      print(f"Model Response: {response}")

      """
      Sample Console Output:

      User Input:> I like dogs
      Model Response: The text expresses a preference for dogs.
      """


  if __name__ == "__main__":
    import asyncio
    asyncio.run(main())
  ```
  
    ```csharp
    var userInput = Console.ReadLine();

    // Define semantic function inline.
    string skPrompt = @"Summarize the provided unstructured text in a sentence that is easy to understand.
                        Text to summarize: {{$userInput}}";
    
    // create the function from the prompt
    KernelFunction summarizeFunc = kernel.CreateFunctionFromPrompt(
        promptTemplate: skPrompt,
        functionName: "SummarizeText"
    );

    //then import into the current kernel
    kernel.ImportPluginFromFunctions("SemanticFunctions", [summarizeFunc]);

    ```
  
  여기서는 사용자 입력을 포함할 수 있는 템플릿 프롬프트 `skPrompt`를 먼저 만들어요. 그다음 커널 함수 `SummarizeText`를 만들고 `SemanticFunctions`라는 플러그인 이름으로 커널에 가져와요. 함수 이름은 Semantic Kernel이 함수가 뭘 하는지, 언제 호출할지 이해하는 데 도움을 줘요.

- **네이티브 함수**: 프레임워크가 직접 호출해서 작업을 수행할 수 있는 함수도 있어요. 파일에서 콘텐츠를 가져오는 예제:

    ```csharp
    public class NativeFunctions {

        [SKFunction, Description("Retrieve content from local file")]
        public async Task<string> RetrieveLocalFile(string fileName, int maxSize = 5000)
        {
            string content = await File.ReadAllTextAsync(fileName);
            if (content.Length <= maxSize) return content;
            return content.Substring(0, maxSize);
        }
    }
    
    //Import native function
    string plugInName = "NativeFunction";
    string functionName = "RetrieveLocalFile";

   //To add the functions to a kernel use the following function
    kernel.ImportPluginFromType<NativeFunctions>();

    ```
  
- **메모리**: AI 앱의 컨텍스트 관리를 추상화하고 간소화해요. 메모리의 핵심은 LLM이 이 정보를 알고 있어야 한다는 거예요. 이 정보를 메모리 데이터베이스나 벡터 데이터베이스 같은 벡터 저장소에 저장할 수 있어요. *사실*을 메모리에 추가하는 간단한 시나리오:

    ```csharp
    var facts = new Dictionary<string,string>();
    facts.Add(
        "Azure Machine Learning; https://learn.microsoft.com/azure/machine-learning/",
        @"Azure Machine Learning is a cloud service for accelerating and
        managing the machine learning project lifecycle. Machine learning professionals,
        data scientists, and engineers can use it in their day-to-day workflows"
    );
    
    facts.Add(
        "Azure SQL Service; https://learn.microsoft.com/azure/azure-sql/",
        @"Azure SQL is a family of managed, secure, and intelligent products
        that use the SQL Server database engine in the Azure cloud."
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
  
이 사실들은 메모리 컬렉션 `SummarizedAzureDocs`에 저장돼요. 간단한 예제지만, LLM이 사용할 정보를 메모리에 저장하는 방법을 이해할 수 있어요.

이게 Semantic Kernel 프레임워크의 기본이에요. 그럼 에이전트 프레임워크는 어떨까요?

## Azure AI Agent Service

Azure AI Agent Service는 Microsoft Ignite 2024에서 소개된 최신 추가 기능이에요. Llama 3, Mistral, Cohere 같은 오픈소스 LLM을 직접 호출하는 등 더 유연한 모델로 AI 에이전트를 개발하고 배포할 수 있어요.

Azure AI Agent Service는 강력한 엔터프라이즈 보안 메커니즘과 데이터 저장 방법을 제공해서 기업 애플리케이션에 적합해요.

AutoGen 및 Semantic Kernel 같은 다중 에이전트 오케스트레이션 프레임워크와 바로 연동돼요.

현재 Public Preview 상태이며, Python과 C#으로 에이전트를 구축할 수 있어요.

Semantic Kernel Python으로 사용자 정의 플러그인을 통해 Azure AI Agent를 만드는 예제:

```python
import asyncio
from typing import Annotated

from azure.identity.aio import DefaultAzureCredential

from semantic_kernel.agents import AzureAIAgent, AzureAIAgentSettings, AzureAIAgentThread
from semantic_kernel.contents import ChatMessageContent
from semantic_kernel.contents import AuthorRole
from semantic_kernel.functions import kernel_function


# Define a sample plugin for the sample
class MenuPlugin:
    """A sample Menu Plugin used for the concept sample."""

    @kernel_function(description="Provides a list of specials from the menu.")
    def get_specials(self) -> Annotated[str, "Returns the specials from the menu."]:
        return """
        Special Soup: Clam Chowder
        Special Salad: Cobb Salad
        Special Drink: Chai Tea
        """

    @kernel_function(description="Provides the price of the requested menu item.")
    def get_item_price(
        self, menu_item: Annotated[str, "The name of the menu item."]
    ) -> Annotated[str, "Returns the price of the menu item."]:
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
        # Create agent definition
        agent_definition = await client.agents.create_agent(
            model=ai_agent_settings.model_deployment_name,
            name="Host",
            instructions="Answer questions about the menu.",
        )

        # Create the AzureAI Agent using the defined client and agent definition
        agent = AzureAIAgent(
            client=client,
            definition=agent_definition,
            plugins=[MenuPlugin()],
        )

        # Create a thread to hold the conversation
        # If no thread is provided, a new thread will be
        # created and returned with the initial response
        thread: AzureAIAgentThread | None = None

        user_inputs = [
            "Hello",
            "What is the special soup?",
            "How much does that cost?",
            "Thank you",
        ]

        try:
            for user_input in user_inputs:
                print(f"# User: '{user_input}'")
                # Invoke the agent for the specified thread
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

Azure AI Agent Service의 핵심 개념:

- **Agent**: Azure AI Agent Service는 Azure AI Foundry와 통합돼요. AI Foundry 내에서 AI Agent는 질문에 답변(RAG), 작업 수행, 워크플로 자동화를 할 수 있는 "스마트" 마이크로서비스 역할을 해요. 생성형 AI 모델의 힘과 실제 데이터 소스에 접근하고 상호작용하는 도구를 결합해요:

    ```python
    agent = project_client.agents.create_agent(
        model="gpt-4o-mini",
        name="my-agent",
        instructions="You are helpful agent",
        tools=code_interpreter.definitions,
        tool_resources=code_interpreter.resources,
    )
    ```

    이 예제에서는 `gpt-4o-mini` 모델, 이름 `my-agent`, 지침 `You are helpful agent`로 에이전트를 만들어요. 코드 해석 작업을 위한 도구와 리소스도 갖추고 있어요.

- **Thread와 메시지**: Thread는 에이전트와 사용자 간의 대화나 상호작용을 나타내요. 대화 진행 상황 추적, 컨텍스트 정보 저장, 상호작용 상태 관리에 사용돼요:

    ```python
    thread = project_client.agents.create_thread()
    message = project_client.agents.create_message(
        thread_id=thread.id,
        role="user",
        content="Could you please create a bar chart for the operating profit using the following data and provide the file to me? Company A: $1.2 million, Company B: $2.5 million, Company C: $3.0 million, Company D: $1.8 million",
    )
    
    # Ask the agent to perform work on the thread
    run = project_client.agents.create_and_process_run(thread_id=thread.id, agent_id=agent.id)
    
    # Fetch and log all messages to see the agent's response
    messages = project_client.agents.list_messages(thread_id=thread.id)
    print(f"Messages: {messages}")
    ```

    이전 코드에서는 Thread를 만들고 메시지를 전송해요. `create_and_process_run`을 호출해서 에이전트가 Thread에서 작업을 수행하도록 해요. 마지막으로 메시지를 가져와서 에이전트 응답을 확인해요. 메시지는 사용자와 에이전트 간의 대화 진행을 나타내며, 텍스트, 이미지, 파일 등 다양한 유형일 수 있어요. 개발자는 이 정보로 응답을 추가 처리하거나 사용자에게 보여줄 수 있어요.

- **다른 AI 프레임워크와 통합**: Azure AI Agent Service는 AutoGen이나 Semantic Kernel 같은 다른 프레임워크와 연동할 수 있어요. 앱의 일부를 이런 프레임워크로 구축하고 Agent Service를 오케스트레이터로 사용하거나, 모든 걸 Agent Service에서 구축할 수 있어요.

**사용 사례**: 안전하고 확장 가능하며 유연한 AI 에이전트 배포가 필요한 기업 애플리케이션에 적합해요.

## 어떤 프레임워크를 선택해야 할까?

이 프레임워크들 간에 중복이 많아 보이지만, 설계, 기능, 대상 사용 사례에서 주요 차이점이 있어요:

| 프레임워크 | 특징 | 적합한 경우 |
|-----------|------|------------|
| **AutoGen** | 다중 에이전트 시스템 연구를 위한 실험 프레임워크 | 복잡한 다중 에이전트 시스템 실험, 프로토타입 제작 |
| **Semantic Kernel** | 기업 에이전트 앱을 위한 프로덕션 준비 라이브러리 | 이벤트 기반, 분산 에이전트 앱, 여러 LLM/SLM 지원 |
| **Azure AI Agent Service** | Azure Foundry 내 에이전트 플랫폼 및 배포 서비스 | Azure OpenAI, AI Search, Bing, 코드 실행 등과 연결 |

### 뭘 선택해야 할지 모르겠다면?

몇 가지 시나리오를 볼게요:

> **Q**: 실험하고 배우면서 개념 증명 에이전트 앱을 빠르게 구축하고 싶어요.
>
> **A**: AutoGen이 좋아요. 이벤트 기반, 분산 에이전트 앱에 특화되어 있고 고급 다중 에이전트 설계 패턴을 지원해요.

> **Q**: Azure AI Agent Service도 여기서 작동하지 않나요? 코드 생성 도구도 있잖아요.
>
> **A**: 네, Azure AI Agent Service는 여러 모델, Azure AI Search, Bing Search, Azure Functions에 대한 내장 기능을 제공해요. Foundry Portal에서 에이전트를 쉽게 구축하고 대규모 배포할 수 있어요.

> **Q**: 아직 헷갈려요. 하나만 추천해주세요.
>
> **A**: Semantic Kernel로 먼저 앱을 구축하고 Azure AI Agent Service로 배포하는 걸 추천해요. 에이전트를 쉽게 지속 가능하게 하면서 Semantic Kernel의 강력한 다중 에이전트 기능을 활용할 수 있어요. Semantic Kernel은 AutoGen에 커넥터가 있어서 두 프레임워크를 함께 쓰기도 쉬워요.

### 비교 표

| 프레임워크 | 초점 | 핵심 개념 | 사용 사례 |
|-----------|------|----------|----------|
| AutoGen | 이벤트 기반, 분산 에이전트 앱 | 에이전트, 페르소나, 함수, 데이터 | 코드 생성, 데이터 분석 작업 |
| Semantic Kernel | 텍스트 이해 및 생성 | 에이전트, 모듈형 구성 요소, 협업 | 자연어 이해, 콘텐츠 생성 |
| Azure AI Agent Service | 유연한 모델, 엔터프라이즈 보안 | 모듈성, 협업, 프로세스 오케스트레이션 | 안전하고 확장 가능한 AI 에이전트 배포 |

## Azure 생태계 통합

기존 Azure 생태계 도구를 직접 통합할 수 있어요. Azure AI Agent Service는 다른 Azure 서비스와 원활하게 작동하도록 설계됐거든요. Bing, Azure AI Search, Azure Functions를 통합할 수 있고, Azure AI Foundry와 깊이 통합돼 있어요.

AutoGen과 Semantic Kernel도 Azure 서비스와 통합할 수 있지만, 코드에서 Azure 서비스를 호출해야 할 수도 있어요. Azure SDK를 사용해서 에이전트에서 Azure 서비스와 상호작용할 수도 있어요. 또한 AutoGen이나 Semantic Kernel로 구축한 에이전트의 오케스트레이터로 Azure AI Agent Service를 사용하면 Azure 생태계에 쉽게 접근할 수 있어요.

### 더 궁금하다면?

[Azure AI Foundry Discord](https://aka.ms/ai-agents/discord)에서 다른 학습자들과 만나고, 오피스 아워에 참석해서 AI 에이전트 관련 질문을 할 수 있어요.

## 참고 자료

- <a href="https://techcommunity.microsoft.com/blog/azure-ai-services-blog/introducing-azure-ai-agent-service/4298357" target="_blank">Azure Agent Service</a>
- <a href="https://devblogs.microsoft.com/semantic-kernel/microsofts-agentic-ai-frameworks-autogen-and-semantic-kernel/" target="_blank">Semantic Kernel 및 AutoGen</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-python" target="_blank">Semantic Kernel Python Agent Framework</a>
- <a href="https://learn.microsoft.com/semantic-kernel/frameworks/agent/?pivots=programming-language-csharp" target="_blank">Semantic Kernel .Net Agent Framework</a>
- <a href="https://learn.microsoft.com/azure/ai-services/agents/overview" target="_blank">Azure AI Agent Service</a>
- <a href="https://techcommunity.microsoft.com/blog/educatordeveloperblog/using-azure-ai-agent-service-with-autogen--semantic-kernel-to-build-a-multi-agen/4363121" target="_blank">AutoGen 및 Semantic Kernel을 사용한 Azure AI Agent Service로 다중 에이전트 솔루션 구축</a>

## 이전 강의

[AI 에이전트 및 에이전트 사용 사례 소개](../01-intro-to-ai-agents/README.md)

## 다음 강의

[에이전트 설계 패턴 이해하기](../03-agentic-design-patterns/README.md)

---

**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 최선을 다하고 있으나, 자동 번역에는 오류나 부정확성이 포함될 수 있습니다. 원본 문서의 원어 버전을 권위 있는 자료로 간주해야 합니다. 중요한 정보의 경우, 전문적인 인간 번역을 권장합니다. 이 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.