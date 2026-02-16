# Azure AI Search 설정 가이드

안녕하세요! 이 가이드는 Azure Portal을 이용해 Azure AI Search를 설정하는 과정을 차근차근 도와드립니다. 처음 사용하시는 분들도 쉽게 따라 하실 수 있도록 준비했어요. 그럼 함께 시작해볼까요?

## 시작하기 전에 준비할 것

먼저 아래 항목이 준비되었는지 확인해주세요.

- **Azure 구독** – 아직 구독이 없으시다면 [Azure 무료 계정](https://azure.microsoft.com/free/?wt.mc_id=studentamb_258691)에서 무료로 만들 수 있습니다. (신용카드 등록이 필요하지만, 체험 크레딧을 제공해요.)

---

## 1단계: Azure Storage 계정 만들기

Azure AI Search에서 사용할 데이터를 저장할 Storage 계정을 먼저 만들어 보겠습니다.

1. [Azure Storage 계정 만들기](https://learn.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal) 가이드를 따라 새 Storage 계정을 만들어주세요.
   **❗주의**: Storage 계정 유형은 반드시 **‘표준 범용 V2’**를 선택해야 해요.

> 💡 **팁**: Storage 계정은 나중에 데이터를 업로드하고 인덱싱할 때 필요하니 꼭 생성해 주세요.

---

## 2단계: Azure AI Search 서비스 만들기

이제 본격적으로 Azure AI Search 서비스를 만들어볼게요.

1. [Azure Portal](https://portal.azure.com/?wt.mc_id=studentamb_258691)에 로그인합니다.
2. 왼쪽 메뉴에서 **‘리소스 만들기’**를 클릭해주세요.
3. 검색창에 **“Azure AI Search”**를 입력하고, 나타난 결과에서 **‘Azure AI Search’**를 선택합니다.
4. **‘만들기’** 버튼을 누르면 설정 화면으로 이동해요.
5. **‘기본 사항’** 탭에서 아래 정보를 입력해 주세요.
   - **구독**: 사용 중인 Azure 구독을 선택합니다.
   - **리소스 그룹**: 새로 만들거나 기존 리소스 그룹을 선택합니다. (처음이라면 새로 만드는 걸 추천해요.)
   - **리소스 이름**: 서비스의 고유한 이름을 입력합니다. (예: `my-ai-search-service`)
   - **지역**: 사용자와 가장 가까운 지역을 선택하세요. 한국 지역이 있다면 ‘Korea Central’을 추천합니다.
   - **가격 책정 계층**: 테스트 목적이라면 **무료(Free) 계층**으로 시작할 수 있어요. 나중에 필요에 따라 업그레이드하면 됩니다.
6. 입력이 끝나면 **‘검토 + 만들기’**를 클릭하세요.
7. 설정 내용을 확인한 후 **‘만들기’** 버튼을 누르면 서비스 배포가 시작됩니다. 배포까지 1~2분 정도 소요돼요.

---

## 3단계: Azure AI Search 사용해보기

서비스가 준비되면 간단한 검색 인덱스를 만들고 데이터를 업로드해 볼 거예요.

1. 배포가 완료되면 **‘리소스로 이동’** 버튼을 클릭해 새로 만든 검색 서비스 페이지로 이동합니다.
2. **‘개요’** 페이지에서 **URL**을 복사해 두세요. URL 형식은 `https://<서비스이름>.search.windows.net`과 같습니다.
3. 왼쪽 메뉴에서 **‘설정’ > ‘키’** 로 이동한 후, **‘쿼리 키’** 중 하나를 복사해 둡니다. (이 키는 검색할 때 사용돼요.)
4. 이제 [Azure AI Search 빠른 시작 가이드](https://learn.microsoft.com/azure/search/search-get-started-portal?pivots=import-data-new)를 따라 실제로 인덱스를 만들고, 데이터를 업로드하고, 검색을 해보세요. 포털에서 직접 해볼 수 있어 아주 쉽답니다.

---

## 4단계: 다양한 도구로 더 편리하게 사용하기

Azure AI Search는 포털뿐 아니라 명령줄 도구나 프로그래밍 언어 SDK로도 다룰 수 있어요. 여기서는 Azure CLI, Python, .NET을 이용하는 방법을 소개할게요.

### 🔹 Azure CLI로 사용하기

터미널에서 간편하게 명령어로 검색 서비스를 제어할 수 있어요.

1. **Azure CLI 설치**아직 설치하지 않으셨다면 [Azure CLI 설치 가이드](https://learn.microsoft.com/cli/azure/install-azure-cli?wt.mc_id=studentamb_258691)를 참고해 설치해 주세요.
2. **로그인**터미널에서 아래 명령어를 입력해 Azure에 로그인합니다.

   ```bash
   az login
   ```
3. **환경 변수에 엔드포인트와 API 키 저장**
   아래 명령어를 실행하면 환경 변수에 엔드포인트와 관리 키가 자동으로 저장됩니다.
   (`<리소스-그룹>`과 `<서비스-이름>`은 실제 값으로 바꿔주세요.)

   **macOS/Linux (bash/zsh)**

   ```bash
   export AZURE_SEARCH_SERVICE_ENDPOINT=$(az search service show -g <리소스-그룹> -n <서비스-이름> --query "endpoint" -o tsv)
   export AZURE_SEARCH_API_KEY=$(az search service admin-key list -g <리소스-그룹> --search-service-name <서비스-이름> --query "primaryKey" -o tsv)
   ```

   **Windows PowerShell**

   ```powershell
   $env:AZURE_SEARCH_SERVICE_ENDPOINT = az search service show -g <리소스-그룹> -n <서비스-이름> --query "endpoint" -o tsv
   $env:AZURE_SEARCH_API_KEY = $(az search service admin-key list -g <리소스-그룹> --search-service-name <서비스-이름> --query "primaryKey" -o tsv)
   ```

### 🔹 Python SDK로 사용하기

Python을 좋아하시는 분들은 아래 방법으로 쉽게 인덱스를 만들고 문서를 업로드할 수 있어요.

1. **라이브러리 설치**

   ```bash
   pip install azure-search-documents
   ```
2. **Python 코드 작성**
   아래 코드를 실행하면 `sample-index`라는 인덱스가 생성되고 두 개의 문서가 업로드됩니다.

   ```python
   import os
   from azure.core.credentials import AzureKeyCredential
   from azure.search.documents import SearchClient
   from azure.search.documents.indexes import SearchIndexClient
   from azure.search.documents.indexes.models import SearchIndex, SimpleField, SearchFieldDataType

   service_endpoint = os.getenv("AZURE_SEARCH_SERVICE_ENDPOINT")
   api_key = os.getenv("AZURE_SEARCH_API_KEY")
   index_name = "sample-index"

   credential = AzureKeyCredential(api_key)
   index_client = SearchIndexClient(service_endpoint, credential)

   fields = [
       SimpleField(name="id", type=SearchFieldDataType.String, key=True),
       SimpleField(name="content", type=SearchFieldDataType.String, searchable=True),
   ]

   index = SearchIndex(name=index_name, fields=fields)
   index_client.create_index(index)
   print("인덱스가 생성되었어요!")

   search_client = SearchClient(service_endpoint, index_name, credential)

   documents = [
       {"id": "1", "content": "Hello world"},
       {"id": "2", "content": "Azure Cognitive Search"}
   ]

   search_client.upload_documents(documents)
   print("문서 업로드 완료!")
   ```

### 🔹 .NET SDK로 사용하기

C# 개발자라면 이 코드를 참고하세요.

1. **콘솔 애플리케이션에서 실행**아래 명령어로 실행합니다.

   ```bash
   dotnet run ./AzureSearch.cs
   ```
2. **AzureSearch.cs 파일 내용**

   ```csharp
   #:package Azure.Search.Documents@11.*
   #:property PublishAot=false

   using Azure;
   using Azure.Search.Documents;
   using Azure.Search.Documents.Indexes;
   using Azure.Search.Documents.Indexes.Models;

   var serviceEndpoint = new Uri(Environment.GetEnvironmentVariable("AZURE_SEARCH_SERVICE_ENDPOINT")!);
   var apiKey = Environment.GetEnvironmentVariable("AZURE_SEARCH_API_KEY")!;
   var indexName = "sample-index";

   var credential = new AzureKeyCredential(apiKey);
   var indexClient = new SearchIndexClient(serviceEndpoint, credential);

   var fields = new List<SearchField>()
   {
       new SimpleField("id", SearchFieldDataType.String) { IsKey = true },
       new SearchableField("content")
   };

   var index = new SearchIndex(name: indexName, fields: fields);

   var response = await indexClient.CreateOrUpdateIndexAsync(index);
   Console.WriteLine($"인덱스 '{response.Value.Name}' 준비 완료!");

   var searchClient = new SearchClient(serviceEndpoint, indexName, credential);

   var documents = new[]
   {
       new { id = "1", content = "Hello world" },
       new { id = "2", content = "Azure Cognitive Search" }
   };

   var result = await searchClient.UploadDocumentsAsync(documents);
   Console.WriteLine($"인덱스 '{response.Value.Name}'에 {result.Value.Results.Count}개 문서 업로드 완료!");
   ```

---

## 더 알아보기

이 외에도 다양한 기능과 도구가 준비되어 있어요. 아래 공식 문서들을 참고하시면 더 많은 것을 배울 수 있습니다.

- [Azure Cognitive Search 서비스 만들기 (공식 문서)](https://learn.microsoft.com/azure/search/search-create-service-portal?wt.mc_id=studentamb_258691)
- [Azure Cognitive Search 시작하기 - 포털](https://learn.microsoft.com/azure/search/search-get-started-portal?wt.mc_id=studentamb_258691)
- [Azure AI Search 도구 (CLI, Python 등)](https://learn.microsoft.com/azure/ai-services/agents/how-to/tools/azure-ai-search?tabs=azurecli%2Cpython&pivots=code-examples?wt.mc_id=studentamb_258691)

---

## 마무리

축하합니다! 🎉 Azure AI Search를 성공적으로 설정하고 간단한 검색 기능까지 사용해 보셨어요. 이제 여러분의 애플리케이션에 강력한 검색 기능을 추가할 준비가 되었습니다.
