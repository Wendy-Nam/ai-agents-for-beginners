
# AGENTS.md

## 프로젝트 개요

이 저장소는 "AI Agents for Beginners" – AI Agent 구축에 필요한 모든 것을 가르치는 포괄적인 교육 과정입니다. 이 과정은 AI Agent의 기초, 디자인 패턴, 프레임워크, 프로덕션 배포까지 다루는 15개 이상의 강의로 구성되어 있습니다.

**주요 기술:**

- Python 3.12+
- 대화형 학습을 위한 Jupyter Notebook
- AI 프레임워크: Semantic Kernel, AutoGen, Microsoft Agent Framework (MAF)
- Azure AI 서비스: Azure AI Foundry, Azure AI Agent Service
- GitHub Models Marketplace (무료 티어 제공)

**구조:**

- 강의 기반 디렉토리 구성 (00-15+ 폴더)
- 각 강의는 README 문서, 코드 샘플(Jupyter 노트북), 이미지 포함
- 자동 번역 시스템을 통한 다국어 지원
- 강의별 여러 프레임워크 옵션 (Semantic Kernel, AutoGen, Azure AI Agent Service)

---

## 설정 명령어

### 사전 요구사항

- Python 3.12 이상
- GitHub 계정 (GitHub Models 무료 티어 사용 시)
- Azure 구독 (선택 사항, Azure AI 서비스 사용 시)

### 초기 설정

1. **저장소 포크 또는 클론:**

   ```bash
   gh repo fork microsoft/ai-agents-for-beginners --clone
   # 또는
   git clone https://github.com/microsoft/ai-agents-for-beginners.git
   cd ai-agents-for-beginners
   ```
2. **Python 가상 환경 생성 및 활성화:**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # Windows: venv\Scripts\activate
   ```
3. **의존성 설치:**

   ```bash
   pip install -r requirements.txt
   ```
4. **환경 변수 설정:**

   ```bash
   cp .env.example .env
   # .env 파일을 편집하여 API 키와 엔드포인트 입력
   ```

### 필요한 환경 변수

**GitHub Models (무료) 사용 시:**

- `GITHUB_TOKEN` – GitHub에서 발급한 개인 액세스 토큰

**Azure AI 서비스 사용 시 (선택 사항):**

- `PROJECT_ENDPOINT` – Azure AI Foundry 프로젝트 엔드포인트
- `AZURE_OPENAI_API_KEY` – Azure OpenAI API 키
- `AZURE_OPENAI_ENDPOINT` – Azure OpenAI 엔드포인트 URL
- `AZURE_OPENAI_CHAT_DEPLOYMENT_NAME` – 채팅 모델 배포 이름
- `AZURE_OPENAI_EMBEDDING_DEPLOYMENT_NAME` – 임베딩 모델 배포 이름
- `.env.example`에 명시된 추가 Azure 구성 변수들

---

## 개발 워크플로우

### Jupyter Notebook 실행하기

각 강의에는 여러 프레임워크를 위한 Jupyter 노트북이 포함되어 있습니다:

1. **Jupyter 시작:**

   ```bash
   jupyter notebook
   ```
2. **강의 디렉토리로 이동** (예: `01-intro-to-ai-agents/code_samples/`)
3. **노트북 열고 실행:**

   - `*-semantic-kernel.ipynb` – Semantic Kernel 프레임워크 사용
   - `*-autogen.ipynb` – AutoGen 프레임워크 사용
   - `*-python-agent-framework.ipynb` – Microsoft Agent Framework (Python)
   - `*-dotnet-agent-framework.ipynb` – Microsoft Agent Framework (.NET)
   - `*-azureaiagent.ipynb` – Azure AI Agent Service 사용

### 다양한 프레임워크 활용하기

**Semantic Kernel + GitHub Models:**

- GitHub 계정으로 무료 티어 사용 가능
- 학습 및 실험에 적합
- 파일 패턴: `*-semantic-kernel*.ipynb`

**AutoGen + GitHub Models:**

- GitHub 계정으로 무료 티어 사용 가능
- 다중 에이전트 오케스트레이션 기능
- 파일 패턴: `*-autogen.ipynb`

**Microsoft Agent Framework (MAF):**

- Microsoft의 최신 프레임워크
- Python과 .NET 모두 지원
- 파일 패턴: `*-agent-framework.ipynb`

**Azure AI Agent Service:**

- Azure 구독 필요
- 프로덕션에 적합한 기능 제공
- 파일 패턴: `*-azureaiagent.ipynb`

---

## 테스트 방법

이 저장소는 교육용으로, 자동화된 테스트보다는 예제 코드에 중점을 둡니다. 설정과 변경 사항을 확인하려면:

### 수동 테스트

1. **Python 환경 확인:**

   ```bash
   python --version  # 3.12+이어야 함
   pip list | grep -E "(autogen|semantic-kernel|azure-ai)"
   ```
2. **노트북 실행 테스트:**

   ```bash
   # 노트북을 스크립트로 변환하여 실행 (import 확인)
   jupyter nbconvert --to script <lesson-folder>/code_samples/<notebook>.ipynb --stdout | python
   ```
3. **환경 변수 확인:**

   ```bash
   python -c "import os; from dotenv import load_dotenv; load_dotenv(); print('✓ GITHUB_TOKEN' if os.getenv('GITHUB_TOKEN') else '✗ GITHUB_TOKEN 없음')"
   ```

### 개별 노트북 실행

Jupyter에서 노트북을 열고 셀을 순서대로 실행하세요. 각 노트북은 독립적으로 구성되어 있으며 다음을 포함합니다:

- import 문
- 구성 로드
- 예제 에이전트 구현
- 마크다운 셀에 예상 출력

---

## 코드 스타일

### Python 규칙

- **Python 버전**: 3.12+
- **코드 스타일**: 표준 Python PEP 8 규칙 준수
- **노트북**: 개념을 설명하는 명확한 마크다운 셀 사용
- **import문**: 표준 라이브러리, 서드파티, 로컬 import 순서로 그룹화

### Jupyter Notebook 규칙

- 코드 셀 앞에 설명적인 마크다운 셀 포함
- 참고용으로 노트북에 출력 예제 포함
- 강의 개념과 일치하는 명확한 변수명 사용
- 노트북 실행 순서를 선형적으로 유지 (셀 1 → 2 → 3 ...)

### 파일 구성

```
<lesson-number>-<lesson-name>/
├── README.md                     # 강의 문서
├── code_samples/
│   ├── <number>-semantic-kernel.ipynb
│   ├── <number>-autogen.ipynb
│   ├── <number>-python-agent-framework.ipynb
│   └── <number>-azureaiagent.ipynb
└── images/
    └── *.png
```

---

## 빌드 및 배포

### 문서 빌드

이 저장소는 문서화에 Markdown을 사용합니다:

- 각 강의 폴더의 README.md 파일
- 저장소 루트의 메인 README.md
- GitHub Actions를 통한 자동 번역 시스템

### CI/CD 파이프라인

`.github/workflows/`에 위치:

1. **co-op-translator.yml** – 50개 이상 언어로 자동 번역
2. **welcome-issue.yml** – 새 이슈 작성자 환영
3. **welcome-pr.yml** – 새 풀 리퀘스트 기여자 환영

### 배포

교육용 저장소이므로 별도의 배포 과정이 없습니다. 사용자는:

1. 저장소를 포크하거나 클론
2. 로컬 또는 GitHub Codespaces에서 노트북 실행
3. 예제를 수정하고 실험하며 학습

---

## 풀 리퀘스트 가이드라인

### 제출 전 확인 사항

1. **변경 사항 테스트:**

   - 관련 노트북 전체 실행
   - 모든 셀이 오류 없이 실행되는지 확인
   - 출력이 적절한지 확인
2. **문서 업데이트:**

   - 새 개념을 추가한 경우 README.md 업데이트
   - 복잡한 코드에는 노트북에 주석 추가
   - 마크다운 셀이 목적을 설명하는지 확인
3. **파일 변경:**

   - `.env` 파일은 커밋하지 말 것 (`.env.example` 사용)
   - `venv/` 또는 `__pycache__/` 디렉토리 커밋 금지
   - 개념을 보여줄 때는 노트북 출력 유지
   - 임시 파일 및 백업 노트북(`*-backup.ipynb`) 제거

### PR 제목 형식

설명적인 제목을 사용하세요:

- `[Lesson-XX] <개념>에 대한 새 예제 추가`
- `[Fix] lesson-XX README 오타 수정`
- `[Update] lesson-XX 코드 샘플 개선`
- `[Docs] 설정 지침 업데이트`

### 필요한 확인 사항

- 노트북이 오류 없이 실행되어야 함
- README 파일이 명확하고 정확해야 함
- 저장소의 기존 코드 패턴을 따라야 함
- 다른 강의와 일관성 유지

---

## 추가 참고 사항

### 자주 발생하는 문제

1. **Python 버전 불일치:**

   - Python 3.12+ 사용 확인
   - 일부 패키지는 구버전에서 동작하지 않을 수 있음
   - `python3 -m venv`로 Python 버전을 명시적으로 지정
2. **환경 변수:**

   - 항상 `.env.example`에서 `.env` 생성
   - `.env` 파일은 커밋 금지 (`.gitignore`에 포함됨)
   - GitHub 토큰에 적절한 권한 필요
3. **패키지 충돌:**

   - 새 가상 환경 사용
   - 개별 패키지보다 `requirements.txt`에서 설치
   - 일부 노트북은 마크다운 셀에 언급된 추가 패키지가 필요할 수 있음
4. **Azure 서비스:**

   - Azure AI 서비스는 활성 구독 필요
   - 일부 기능은 특정 지역에서만 사용 가능
   - GitHub Models 무료 티어에는 제한 사항 있음

### 학습 경로

권장 진도:

1. **00-course-setup** – 환경 설정부터 시작
2. **01-intro-to-ai-agents** – AI Agent 기초 이해
3. **02-explore-agentic-frameworks** – 다양한 프레임워크 학습
4. **03-agentic-design-patterns** – 핵심 디자인 패턴
5. 이후 번호 순서대로 강의 진행

### 프레임워크 선택

목표에 따라 프레임워크 선택:

- **학습/프로토타입**: Semantic Kernel + GitHub Models (무료)
- **다중 에이전트 시스템**: AutoGen
- **최신 기능**: Microsoft Agent Framework (MAF)
- **프로덕션 배포**: Azure AI Agent Service

### 도움 받기

- [Azure AI Foundry Community Discord](https://aka.ms/ai-agents/discord) 참여
- 강의 README 파일에서 구체적인 지침 확인
- 메인 [README.md](./README.md)에서 과정 개요 확인
- 자세한 설정 방법은 [Course Setup](./00-course-setup/README.md) 참조

### 기여하기

이 프로젝트는 오픈 교육 프로젝트입니다. 기여를 환영합니다:

- 코드 예제 개선
- 오타나 오류 수정
- 명확한 주석 추가
- 새 강의 주제 제안
- 추가 언어 번역

현재 필요한 작업은 [GitHub Issues](https://github.com/microsoft/ai-agents-for-beginners/issues)에서 확인하세요.

---

## 프로젝트별 컨텍스트

### 다국어 지원

이 저장소는 자동 번역 시스템을 사용합니다:

- 50개 이상 언어 지원
- 번역본은 `/translations/<lang-code>/` 디렉토리에 위치
- GitHub Actions 워크플로우가 번역 업데이트 처리
- 원본 파일은 저장소 루트에 영어로 유지

### 강의 구조

각 강의는 일관된 패턴을 따릅니다:

1. 링크가 포함된 비디오 썸네일
2. 서면 강의 내용 (README.md)
3. 여러 프레임워크의 코드 샘플
4. 학습 목표 및 사전 요구사항
5. 추가 학습 자료 링크

### 코드 샘플 명명 규칙

형식: `<lesson-number>-<framework-name>.ipynb`

- `04-semantic-kernel.ipynb` – 4강, Semantic Kernel
- `07-autogen.ipynb` – 7강, AutoGen
- `14-python-agent-framework.ipynb` – 14강, MAF Python
- `14-dotnet-agent-framework.ipynb` – 14강, MAF .NET

### 특수 디렉토리

- `translated_images/` – 번역을 위한 지역화된 이미지
- `images/` – 영어 콘텐츠용 원본 이미지
- `.devcontainer/` – VS Code 개발 컨테이너 구성
- `.github/` – GitHub Actions 워크플로우 및 템플릿

### 의존성

`requirements.txt`의 주요 패키지:

- `autogen-agentchat`, `autogen-core`, `autogen-ext` – AutoGen 프레임워크
- `semantic-kernel` – Semantic Kernel 프레임워크
- `agent-framework` – Microsoft Agent Framework
- `azure-ai-inference`, `azure-ai-projects` – Azure AI 서비스
- `azure-search-documents` – Azure AI Search 통합
- `chromadb` – RAG 예제용 벡터 데이터베이스
- `chainlit` – 채팅 UI 프레임워크
- `browser_use` – 에이전트용 브라우저 자동화
- `mcp[cli]` – Model Context Protocol 지원
- `mem0ai` – 에이전트 메모리 관리

---

이 가이드가 저장소에 기여하고 학습하는 데 도움이 되길 바랍니다! 😊 궁금한 점이 있다면 언제든지 이슈나 디스코드를 통해 물어보세요.
