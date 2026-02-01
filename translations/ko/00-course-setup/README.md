<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "96eb7f95375daa3e91778ca0295a55d9",
  "translation_date": "2025-10-15T08:33:11+00:00",
  "source_file": "00-course-setup/README.md",
  "language_code": "ko"
}
-->
# 코스 설정

## 소개

이번 강의에서는 코스의 코드 샘플을 어떻게 실행하는지 알아볼게요.

## 다른 학습자들과 소통하기

저장소를 복제하기 전에 [AI Agents For Beginners Discord 채널](https://aka.ms/ai-agents/discord)에 먼저 가입해보세요. 설정 관련 도움도 받고, 질문도 하고, 다른 학습자들과 교류할 수 있어요.

## 저장소 복제 또는 포크

GitHub 저장소를 복제하거나 포크해서 시작하면 돼요. 이렇게 하면 코스 자료의 개인 버전을 만들어서 코드를 직접 실행하고 수정할 수 있어요.

포크하려면 <a href="https://github.com/microsoft/ai-agents-for-beginners/fork" target="_blank">여기를 클릭</a>하세요.

포크가 완료되면 아래처럼 확인할 수 있어요:

![포크된 저장소](../../../translated_images/forked-repo.33f27ca1901baa6a5e13ec3eb1f0ddd3a44d936d91cc8cfb19bfdb9688bd2c3d.ko.png)

### 얕은 복제 (워크숍 / Codespaces 추천)

  >전체 저장소는 약 3GB 정도로 꽤 커요. 워크숍에 참석하거나 몇 개 강의 폴더만 필요하다면 얕은 복제(또는 희소 복제)로 다운로드 용량을 줄일 수 있어요.

#### 빠른 얕은 복제 — 최소 기록, 모든 파일

아래 명령어에서 `<your-username>`을 자신의 포크 URL로 바꿔주세요.

최신 커밋만 복제하려면 (용량이 작아요):

```bash|powershell
git clone --depth 1 https://github.com/<your-username>/ai-agents-for-beginners.git
```

특정 브랜치만 복제하려면:

```bash|powershell
git clone --depth 1 --branch <branch-name> https://github.com/<your-username>/ai-agents-for-beginners.git
```

#### 부분(희소) 복제 — 최소 블롭 + 선택한 폴더만

부분 복제와 희소 체크아웃을 사용해요 (Git 2.25 이상 필요):

```bash|powershell
git clone --depth 1 --filter=blob:none --sparse https://github.com/<your-username>/ai-agents-for-beginners.git
```

저장소 폴더로 이동:

bash의 경우:

```bash
cd ai-agents-for-beginners
```

Powershell의 경우:

```powershell
Set-Location ai-agents-for-beginners
```

필요한 폴더를 지정해요 (예시로 두 개 폴더):

```bash|powershell
git sparse-checkout set 00-course-setup 01-intro-to-ai-agents
```

파일만 필요하고 용량을 확보하고 싶다면 저장소 메타데이터를 삭제할 수 있어요. 단, 💀복구가 안 되니까 주의하세요 — 커밋, 풀, 푸시 같은 Git 기능을 쓸 수 없게 돼요.

Linux/macOS의 경우:

```bash
rm -rf .git
```

Windows의 경우:

```powershell
Remove-Item -Recurse -Force .git
```

#### GitHub Codespaces 사용 (로컬 다운로드 없이 작업 가능)

- [GitHub UI](https://github.com/codespaces)에서 새 Codespace를 생성하세요.
- Codespace 터미널에서 위의 얕은/희소 복제 명령을 실행해서 필요한 폴더만 가져오세요.
- 선택사항: 복제 후 .git을 삭제하면 용량을 확보할 수 있어요.
- 참고: Codespaces에서 저장소를 직접 열면 devcontainer 환경이 구성되어 필요 이상의 리소스가 할당될 수 있어요. Codespace 내부에서 얕은 복제를 하면 디스크 사용량을 더 잘 제어할 수 있어요.

#### 팁

- 편집하고 커밋하려면 복제 URL을 자신의 포크로 바꿔야 해요.
- 나중에 더 많은 기록이나 파일이 필요하면 희소 체크아웃을 조정해서 폴더를 추가할 수 있어요.

## 코드 실행

AI 에이전트 구축 실습을 위한 Jupyter 노트북을 제공해요.

코드 샘플 종류는 이렇게 있어요:

**GitHub 계정 필요 (무료)**:
1) Semantic Kernel Agent Framework + GitHub Models Marketplace (semantic-kernel.ipynb)
2) AutoGen Framework + GitHub Models Marketplace (autogen.ipynb)

**Azure 구독 필요**:
3) Azure AI Foundry + Azure AI Agent Service (azureaiagent.ipynb)

세 가지 모두 시도해보고 자신에게 맞는 걸 찾아보세요!

선택한 옵션에 따라 아래 설정 단계를 따라주세요:

## 요구 사항

- Python 3.12+
  - **참고**: Python 3.12가 설치되어 있지 않다면 먼저 설치하고, python3.12로 venv를 생성하세요.
  
    >예시

    Python venv 생성:

    ``` bash
    python3 -m venv venv
    ```

    venv 활성화:

    macOS 및 Linux

    ```bash
    source venv/bin/activate
    ```
  
    Windows

    ```bash
    venv\Scripts\activate
    ```

- GitHub 계정 - GitHub Models Marketplace 이용에 필요
- Azure 구독 - Azure AI Foundry 이용에 필요
- Azure AI Foundry 계정 - Azure AI Agent Service 이용에 필요

저장소 루트의 `requirements.txt`에 필요한 Python 패키지가 모두 포함되어 있어요.

설치 명령어:

```bash
pip install -r requirements.txt
```
충돌을 방지하려면 Python 가상 환경을 사용하는 걸 권장해요.

## VSCode 설정
VSCode에서 올바른 Python 버전을 사용하고 있는지 확인하세요.

![image](https://github.com/user-attachments/assets/a85e776c-2edb-4331-ae5b-6bfdfb98ee0e)

## GitHub Models 샘플 설정 

### 1단계: GitHub 개인 액세스 토큰(PAT) 가져오기

GitHub Models Marketplace에서 무료 LLM을 제공하고 있어요.

사용하려면 [GitHub 개인 액세스 토큰](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)을 생성해야 해요.

<a href="https://github.com/settings/personal-access-tokens" target="_blank">개인 액세스 토큰 설정</a>에서 생성할 수 있어요.

[최소 권한 원칙](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)을 따라서 코스 실행에 필요한 권한만 부여하세요.

1. **개발자 설정**으로 가서 왼쪽에서 `세분화된 토큰`을 선택하세요.
   ![](../../../translated_images/profile_developer_settings.410a859fe749c755c859d414294c5908e307222b2c61819c3203bbeed4470e25.ko.png)

    그리고 `새 토큰 생성`을 선택하세요.

    ![토큰 생성](../../../translated_images/fga_new_token.1c1a234afe202ab37483944a291ee80c1868e1e78082fd6bd4180fea5d5a15b4.ko.png)

2. 나중에 알아보기 쉽도록 토큰 이름을 입력하세요.

    🔐 토큰 기간 추천

    추천: 30일. 더 안전하게 하려면 7일도 괜찮아요 🛡️
    학습 동기 부여에도 좋아요 🚀

    ![토큰 이름 및 만료 날짜](../../../translated_images/token-name-expiry-date.a095fb0de63868640a4c82d6b1bbc92b482930a663917a5983a3c7cd1ef86b77.ko.png)

3. 토큰 범위를 이 저장소의 포크로 제한하세요.

    ![저장소 범위 제한](../../../translated_images/token_repository_limit.924ade5e11d9d8bb6cd21293987e4579dea860e2ba66d607fb46e49524d53644.ko.png)

4. 권한 제한: **권한** → **계정** 탭 → "+ 권한 추가" → **모델** 검색해서 체크
    ![모델 권한 추가](../../../translated_images/add_models_permissions.c0c44ed8b40fc143dc87792da9097d715b7de938354e8f771d65416ecc7816b8.ko.png)

5. 생성 전에 권한을 확인하세요.
    ![권한 확인](../../../translated_images/verify_permissions.06bd9e43987a8b219f171bbcf519e45ababae35b844f5e9757e10afcb619b936.ko.png)

6. 토큰은 생성 후 다시 볼 수 없으니까 안전한 곳에 저장할 준비를 해두세요.
    ![토큰 안전하게 저장](../../../translated_images/store_token_securely.08ee2274c6ad6caf3482f1cd1bad7ca3fdca1ce737bc485bfa6499c84297c789.ko.png)

생성한 토큰을 복사해서 `.env` 파일에 추가하세요.


### 2단계: `.env` 파일 생성

```bash
cp .env.example .env
```

예제 파일을 복사해서 `.env`를 만들고 환경 변수를 채워넣으세요.

`.env` 파일을 열고 `GITHUB_TOKEN` 필드에 토큰을 붙여넣으세요.
![GitHub 토큰 필드](../../../translated_images/github_token_field.20491ed3224b5f4ab24d10ced7a68c4aba2948fe8999cfc8675edaa16f5e5681.ko.png)

이제 코드 샘플을 실행할 수 있어요!

## Azure AI Foundry 및 Azure AI Agent Service 샘플 설정

### 1단계: Azure 프로젝트 엔드포인트 가져오기

Azure AI Foundry에서 허브와 프로젝트를 만드는 방법은 [허브 리소스 개요](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/ai-resources)를 참고하세요.

프로젝트를 만든 후에는 연결 문자열이 필요해요. Azure AI Foundry 포털에서 프로젝트 **개요** 페이지로 가면 확인할 수 있어요.

![프로젝트 연결 문자열](../../../translated_images/project-endpoint.8cf04c9975bbfbf18f6447a599550edb052e52264fb7124d04a12e6175e330a5.ko.png)

### 2단계: `.env` 파일 생성

```bash
cp .env.example .env
```

`.env` 파일을 열고 `PROJECT_ENDPOINT` 필드에 연결 문자열을 붙여넣으세요.

### 3단계: Azure 로그인

보안을 위해 Microsoft Entra ID로 [키 없는 인증](https://learn.microsoft.com/azure/developer/ai/keyless-connections?tabs=csharp%2Cazure-cli?WT.mc_id=academic-105485-koreyst)을 사용해요.

터미널에서 `az login --use-device-code`를 실행한 다음 구독을 선택하세요.


## 추가 환경 변수 - Azure Search 및 Azure OpenAI 

Lesson 5 (Agentic RAG)에서는 Azure Search와 Azure OpenAI를 사용해요.

`.env`에 다음 환경 변수를 추가하세요:

### Azure AI Foundry 포털에서 찾기

| 변수명 | 위치 |
|--------|------|
| `AZURE_SUBSCRIPTION_ID` | **개요** → **프로젝트 세부 정보** |
| `AZURE_AI_PROJECT_NAME` | **개요** 페이지 상단 |
| `AZURE_OPENAI_SERVICE` | **개요** → **포함된 기능** → **Azure OpenAI Service** |
| `AZURE_OPENAI_RESOURCE_GROUP` | **관리 센터** → **개요** → **프로젝트 속성** |
| `GLOBAL_LLM_SERVICE` | **관리 센터** → **연결된 리소스** → **Azure AI Services** 연결 이름 |
| `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` | **모델 + 엔드포인트** → 임베딩 모델 선택 → **배포 이름** |
| `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` | **모델 + 엔드포인트** → 채팅 모델 선택 → **배포 이름** |

### Azure 포털에서 찾기

| 변수명 | 위치 |
|--------|------|
| `AZURE_OPENAI_ENDPOINT` | **Azure AI Services** → **키 및 엔드포인트** → "언어 API" |
| `AZURE_OPENAI_API_KEY` | 위와 동일 → KEY 1 또는 KEY 2 |
| `AZURE_SEARCH_SERVICE_ENDPOINT` | **Azure AI Search** → **개요** |
| `AZURE_SEARCH_API_KEY` | **Azure AI Search** → **설정** → **키** |

### 외부 참조

| 변수명 | 참조 |
|--------|------|
| `AZURE_OPENAI_API_VERSION` | [API 버전 문서](https://learn.microsoft.com/en-us/azure/ai-services/openai/api-version-deprecation#latest-ga-api-release)에서 최신 GA 버전 확인 |

### 키 없는 인증 설정

자격 증명을 하드코딩하는 대신 `DefaultAzureCredential`로 키 없는 연결을 사용해요.

```python
from azure.identity import DefaultAzureCredential, InteractiveBrowserCredential
```

## 막혔을 때

<a href="https://discord.gg/kzRShWzttr" target="_blank">Azure AI 커뮤니티 Discord</a>에 참여하거나 <a href="https://github.com/microsoft/ai-agents-for-beginners/issues?WT.mc_id=academic-105485-koreyst" target="_blank">이슈를 생성</a>해주세요.

## 다음 강의

이제 코드 실행 준비가 끝났어요. AI 에이전트의 세계로 출발!

[AI 에이전트와 에이전트 사용 사례 소개](../01-intro-to-ai-agents/README.md)

---

**면책 조항**:  
이 문서는 AI 번역 서비스 [Co-op Translator](https://github.com/Azure/co-op-translator)를 사용하여 번역되었습니다. 정확성을 위해 최선을 다하고 있으나, 자동 번역에는 오류나 부정확성이 포함될 수 있습니다. 원본 문서의 원어 버전을 권위 있는 자료로 간주해야 합니다. 중요한 정보의 경우, 전문적인 인간 번역을 권장합니다. 이 번역 사용으로 인해 발생하는 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.