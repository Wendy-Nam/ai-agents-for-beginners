# 🚀 AI Agents 학습 시작하기 - 완벽한 셋업 가이드

안녕하세요! AI Agents의 세계에 오신 것을 진심으로 환영합니다! 😊

이 가이드는 Microsoft의 "AI Agents for Beginners" 코스를 시작하기 위한 모든 준비 과정을 친절하게 안내해드릴게요. 더 이상 복잡한 설정에 지치지 마세요! 저희가 차근차근 도와드릴게요.

---

## 🤝 함께 배우기 (혼자 하지 마세요!)

시작하기 전에 **AI Agents 커뮤니티**에 참여하세요! 혼자 공부하다가 막히면 언제든지 도움을 받을 수 있어요.

**🎯 Discord 채널 참여하기**: [AI Agents For Beginners Discord](https://aka.ms/ai-agents/discord)

- 설정 문제, 코스 질문, 다른 학습자들과 소통 모두 가능!
- 전 세계 사람들과 함께 배우면 2배 빨라져요!

---

## 📥 코스 자료 받기 (나만의 버전 만들기)

### 왜 Fork 해야 할까요?

- **나만의 공간**: 자유롭게 코드 수정하고 실험할 수 있어요
- **실습 결과 저장**: 내 학습 진행 상황을 기록할 수 있어요
- **안전한 실험**: 원본 코드를 망가뜨릴 걱정 없어요!

### 쉬운 Fork 방법

1. **[여기 클릭해서 Fork](https://github.com/microsoft/ai-agents-for-beginners/fork)**
2. 자동으로 당신의 GitHub에 복사될 거예요

이제 아래처럼 여러분만의 저장소가 생겼을 거예요!

![Fork된 저장소](./images/forked-repo.png)

### ⚡ 빠른 다운로드 (워크숍/코드스페이스용)

전체 리포지토리는 크기가 커요 (약 3GB!). 몇 개의 레슨만 필요하다면 **Shallow Clone**으로 용량을 아낄 수 있어요.

#### 🔥 가장 빠른 방법 - 최신 버전만

```bash
# 본인 GitHub 이름으로 변경해주세요!
git clone --depth 1 https://github.com/본인-이름/ai-agents-for-beginners.git
```

#### 🎯 특정 레슨만 다운로드

```bash
git clone --depth 1 --branch 브랜치이름 https://github.com/본인-이름/ai-agents-for-beginners.git
```

#### 💾 부분 다운로드 - 내가 필요한 폴더만!

```bash
# Git 2.25+ 버전 필요
git clone --depth 1 --filter=blob:none --sparse https://github.com/본인-이름/ai-agents-for-beginners.git
cd ai-agents-for-beginners

# 필요한 폴더만 선택 (예: 2개 폴더만)
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

#### 🌟 GitHub Codespaces 추천

- 로컬 다운로드 없이 바로 시작!
- [GitHub Codespaces](https://github.com/codespaces)에서 새 Codespace 생성
- 위의 shallow/sparse clone 명령어 실행해서 필요한 폴더만 가져오기

> 💡 **팁**: 다운로드 후 `.git` 폴더를 지우면 공간을 더 확보할 수 있어요. (단, 이 경우 Git 기능은 사라집니다)
>
> ```bash
> rm -rf .git
> ```

---

## 🎮 코드 실행하기 (실제 시작!)

이 코스는 **Jupyter Notebook**으로 실습합니다. 클릭만 하면 바로 AI Agent를 만들 수 있어요!

### 🆓 무료로 시작하기 (GitHub 계정만 필요)

1. **Semantic Kernel + GitHub Models** (`*semantic-kernel.ipynb`)

   - 가장 쉬운 입문용
   - Microsoft의 최신 프레임워크
2. **AutoGen + GitHub Models** (`*autogen.ipynb`)

   - 여러 Agent가 협력하는 기술
   - 복잡한 시나리오에 좋아요

### 💼 전문가용 (Azure 구독 필요)

3. **Azure AI Foundry + Azure AI Agent Service** (`*azureaiagent.ipynb`)
   - 실제 서비스 출시용
   - Production 환경에서 사용

**💡 팁**: 세 가지 모두 체험해보고 나한테 맞는 것 선택하세요!

---

## ⚙️ 필요한 도구 설치하기

### Python 3.12+

- **Python 3.12**가 필요해요. 아직 없으면 [python.org](https://www.python.org/downloads/)에서 설치해 주세요.
- 가상 환경을 만들고 활성화하는 걸 추천해요:

  ```bash
  python -m venv venv
  # Windows
  venv\Scripts\activate
  # macOS/Linux
  source venv/bin/activate
  ```

### .NET 10+ (선택사항)

.NET 예제를 실행하려면 [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0)를 설치해 주세요.

```bash
dotnet --list-sdks   # 설치 확인
```

### 필수 패키지 설치

저장소 루트에서 아래 명령어를 실행하면 필요한 Python 패키지가 모두 설치됩니다:

```bash
pip install -r requirements.txt
```

---

## 💻 VSCode 설정

VSCode를 사용한다면, Python 인터프리터를 올바른 버전(3.12)으로 설정해 주세요.

![올바른 Python 버전 선택](./images/vscode-python-version.png)

---

## 🆓 GitHub Models 샘플 실행 준비하기

### Step 1: GitHub Personal Access Token (PAT) 발급받기

이 코스는 GitHub Models Marketplace를 통해 무료로 LLM을 사용할 수 있어요. 토큰이 필요합니다.

1. [GitHub 개인 액세스 토큰 설정](https://github.com/settings/personal-access-tokens)으로 이동
2. **Fine-grained tokens** 선택 → **Generate new token** 클릭
3. 토큰 이름과 만료일 입력 (보안을 위해 30일 이하 권장)
4. 저장소 접근 범위를 **방금 Fork한 자신의 저장소**로 제한
5. 권한(Permissions)에서 **Account** 탭 → **Models** 추가
6. 토큰 생성 후 **안전한 곳에 저장** (비밀번호 관리자 추천)

![토큰 생성 과정](./images/token-creation-steps.png)

### Step 2: `.env` 파일 만들기

```bash
# Windows PowerShell
Copy-Item .env.example .env
# macOS/Linux
cp .env.example .env
```

`.env` 파일을 열고 `GITHUB_TOKEN=` 부분에 발급받은 토큰을 붙여넣으세요.

![GitHub 토큰 입력](./images/github_token_field.png)

이제 GitHub Models를 사용하는 샘플을 실행할 준비가 되었어요!

---

## 💼 Azure AI Foundry 샘플 실행 준비하기

### Step 1: Azure Project Endpoint 가져오기

1. [Azure AI Foundry](https://ai.azure.com)에서 프로젝트를 생성하세요. (도움이 필요하면 [허브 및 프로젝트 생성 가이드](https://learn.microsoft.com/azure/ai-foundry/concepts/ai-resources) 참고)
2. 프로젝트의 **개요(Overview)** 페이지에서 **프로젝트 연결 문자열(Connection string)**을 복사하세요.

![프로젝트 연결 문자열](./images/project-endpoint.png)

### Step 2: `.env` 파일에 프로젝트 엔드포인트 추가

`.env` 파일을 열고 `PROJECT_ENDPOINT=` 부분에 복사한 연결 문자열을 붙여넣으세요.

### Step 3: Azure에 로그인 (키 없는 인증)

보안을 위해 Azure CLI로 로그인하여 키 없이 인증할 거예요.

```bash
az login --use-device-code
```

화면의 지시에 따라 로그인하고, 구독을 선택하세요.

---

## 🧩 추가 환경 변수 (Agentic RAG 레슨용)

5단원(Agentic RAG)에서는 Azure Search와 Azure OpenAI를 사용하는 예제가 있어요. 필요한 정보를 `.env` 파일에 추가해 주세요.

| 변수명                                     | 설명                     | 찾는 위치                                                                                                    |
| ------------------------------------------ | ------------------------ | ------------------------------------------------------------------------------------------------------------ |
| `AZURE_SUBSCRIPTION_ID`                  | 구독 ID                  | 프로젝트 개요의**프로젝트 세부 정보**                                                                  |
| `AZURE_AI_PROJECT_NAME`                  | 프로젝트 이름            | 프로젝트 개요 상단                                                                                           |
| `AZURE_OPENAI_SERVICE`                   | OpenAI 서비스 이름       | 프로젝트 개요의**포함된 기능** 탭                                                                      |
| `AZURE_OPENAI_RESOURCE_GROUP`            | 리소스 그룹              | 관리 센터 > 프로젝트 속성                                                                                    |
| `GLOBAL_LLM_SERVICE`                     | AI Services 연결 이름    | 관리 센터 > 연결된 리소스                                                                                    |
| `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` | 임베딩 모델 배포명       | 모델 + 엔드포인트 페이지                                                                                     |
| `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME`      | 채팅 모델 배포명         | 모델 + 엔드포인트 페이지                                                                                     |
| `AZURE_OPENAI_ENDPOINT`                  | OpenAI 엔드포인트        | Azure Portal > AI Services > 키 및 엔드포인트                                                                |
| `AZURE_OPENAI_API_KEY`                   | OpenAI API 키            | Azure Portal > AI Services > 키 및 엔드포인트                                                                |
| `AZURE_SEARCH_SERVICE_ENDPOINT`          | Search 서비스 엔드포인트 | Azure Portal > Search 서비스 > 개요                                                                          |
| `AZURE_SEARCH_API_KEY`                   | Search API 키            | Azure Portal > Search 서비스 > 설정 > 키                                                                     |
| `AZURE_OPENAI_API_VERSION`               | API 버전                 | [공식 문서](https://learn.microsoft.com/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release) |

### 키 없는 인증 코드 예시 (Python)

```python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
credential = DefaultAzureCredential()
```

---

## 🆘 도움이 필요하신가요?

설정 중에 막히는 부분이 있다면, 주저하지 말고 커뮤니티에 물어보세요!

- 💬 [Azure AI Community Discord](https://discord.gg/kzRShWzttr)
- 🐛 [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues)

---

## 📚 다음 레슨으로 고고!

이제 모든 준비가 끝났어요! 본격적으로 AI Agents의 세계로 떠나볼까요?

👉 [1강: AI Agents 소개 및 활용 사례](../01-intro-to-ai-agents/README.md)

행복한 코딩 되세요! 🎉
