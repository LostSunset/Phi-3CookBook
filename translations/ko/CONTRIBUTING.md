# 기여하기

이 프로젝트는 기여와 제안을 환영합니다. 대부분의 기여는 Contributor License Agreement (CLA)에 동의해야 합니다. 이는 귀하가 기여에 대한 권리를 가지고 있으며 실제로 우리에게 사용 권리를 부여한다는 것을 선언하는 것입니다. 자세한 내용은 [https://cla.opensource.microsoft.com](https://cla.opensource.microsoft.com)를 방문하십시오.

풀 리퀘스트를 제출하면 CLA 봇이 자동으로 CLA를 제공해야 하는지 여부를 결정하고 PR을 적절하게 장식합니다 (예: 상태 확인, 댓글). 봇이 제공하는 지침을 따르기만 하면 됩니다. CLA를 사용하는 모든 리포지토리에 대해 한 번만 이 작업을 수행하면 됩니다.

## 행동 강령

이 프로젝트는 [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)를 채택했습니다. 자세한 내용은 [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/)를 읽거나 [opencode@microsoft.com](mailto:opencode@microsoft.com)으로 추가 질문이나 의견을 보내주십시오.

## 이슈 생성 시 주의사항

일반 지원 질문에 대해 GitHub 이슈를 열지 마십시오. GitHub 목록은 기능 요청 및 버그 보고에 사용되어야 합니다. 이렇게 하면 실제 코드의 문제나 버그를 더 쉽게 추적하고 일반적인 논의를 실제 코드와 분리할 수 있습니다.

## 기여 방법

### 풀 리퀘스트 가이드라인

Phi-3 CookBook 리포지토리에 풀 리퀘스트 (PR)를 제출할 때는 다음 가이드라인을 사용하십시오:

- **리포지토리 포크**: 수정하기 전에 항상 리포지토리를 자신의 계정으로 포크하십시오.

- **별도의 풀 리퀘스트 (PR)**:
  - 각 유형의 변경 사항을 별도의 풀 리퀘스트로 제출하십시오. 예를 들어, 버그 수정과 문서 업데이트는 별도의 PR로 제출해야 합니다.
  - 오타 수정 및 사소한 문서 업데이트는 적절한 경우 단일 PR로 결합할 수 있습니다.

- **병합 충돌 처리**: 풀 리퀘스트에 병합 충돌이 표시되면 수정하기 전에 로컬 `main` 브랜치를 메인 리포지토리와 동기화하십시오.

- **번역 제출**: 번역 PR을 제출할 때는 번역 폴더에 원본 폴더의 모든 파일에 대한 번역이 포함되어 있는지 확인하십시오.

### 번역 가이드라인

> [!IMPORTANT]
>
> 이 리포지토리의 텍스트를 번역할 때 기계 번역을 사용하지 마십시오. 능숙한 언어로만 번역에 자원하십시오.

비영어권 언어에 능숙하다면 콘텐츠 번역에 도움을 줄 수 있습니다. 번역 기여가 올바르게 통합되도록 하기 위해 다음 단계를 따르십시오:

- **번역 폴더 생성**: 적절한 섹션 폴더로 이동하여 기여하는 언어에 대한 번역 폴더를 생성하십시오. 예를 들어:
  - 소개 섹션: `Phi-3CookBook/md/01.Introduce/translations/<language_code>/`
  - 빠른 시작 섹션: `Phi-3CookBook/md/02.QuickStart/translations/<language_code>/`
  - 다른 섹션(03.Inference, 04.Finetuning 등)에 대해서도 이 패턴을 계속 따르십시오.

- **상대 경로 업데이트**: 번역할 때, 폴더 구조를 조정하여 markdown 파일 내 상대 경로의 시작 부분에 `../../`를 추가하여 링크가 올바르게 작동하도록 하십시오. 예를 들어, 다음과 같이 변경하십시오:
  - `(../../imgs/01/phi3aisafety.png)`를 `(../../../../imgs/01/phi3aisafety.png)`로 변경하십시오.

- **번역 정리**: 각 번역 파일은 해당 섹션의 번역 폴더에 배치해야 합니다. 예를 들어, 소개 섹션을 스페인어로 번역하는 경우 다음과 같이 생성하십시오:
  - `Phi-3CookBook/md/01.Introduce/translations/es/`

- **완전한 PR 제출**: 섹션의 모든 번역 파일이 하나의 PR에 포함되어 있는지 확인하십시오. 섹션의 부분 번역은 허용되지 않습니다. 번역 PR을 제출할 때 번역 폴더에 원본 폴더의 모든 파일에 대한 번역이 포함되어 있는지 확인하십시오.

### 작성 가이드라인

모든 문서에서 일관성을 유지하기 위해 다음 가이드라인을 사용하십시오:

- **URL 형식**: 모든 URL을 괄호로 감싸고 그 뒤에 괄호를 붙여 추가 공백 없이 작성하십시오. 예: `[example](https://example.com)`.

- **상대 링크**: 현재 디렉토리의 파일이나 폴더를 가리키는 상대 링크에는 `./`를 사용하고, 상위 디렉토리의 경우 `../`를 사용하십시오. 예: `[example](../../path/to/file)` 또는 `[example](../../../path/to/file)`.

- **국가별 로케일 사용 금지**: 링크에 국가별 로케일이 포함되지 않도록 하십시오. 예를 들어, `/en-us/` 또는 `/en/`를 피하십시오.

- **이미지 저장**: 모든 이미지는 `./imgs` 폴더에 저장하십시오.

- **설명적인 이미지 이름**: 이미지는 영어 문자, 숫자, 대시를 사용하여 설명적으로 이름을 지정하십시오. 예: `example-image.jpg`.

## GitHub 워크플로우

풀 리퀘스트를 제출하면 변경 사항을 검증하기 위해 다음 워크플로우가 실행됩니다. 워크플로우 검사를 통과하기 위해 아래 지침을 따르십시오:

- [깨진 상대 경로 확인](../..)
- [URL에 로케일이 포함되지 않았는지 확인](../..)

### 깨진 상대 경로 확인

이 워크플로우는 파일의 모든 상대 경로가 올바른지 확인합니다.

1. 링크가 제대로 작동하는지 확인하려면 VS Code를 사용하여 다음 작업을 수행하십시오:
    - 파일의 링크 위에 커서를 올려 놓습니다.
    - **Ctrl + 클릭**하여 링크로 이동합니다.
    - 링크를 클릭했을 때 로컬에서 작동하지 않으면 워크플로우가 트리거되고 GitHub에서도 작동하지 않습니다.

1. 이 문제를 해결하려면 VS Code에서 제공하는 경로 제안을 사용하여 다음 작업을 수행하십시오:
    - `./` 또는 `../`를 입력합니다.
    - VS Code는 입력한 내용을 기반으로 사용 가능한 옵션을 선택하도록 프롬프트를 제공합니다.
    - 올바른 경로를 확인하기 위해 원하는 파일이나 폴더를 클릭하여 경로를 따릅니다.

올바른 상대 경로를 추가한 후 변경 사항을 저장하고 푸시하십시오.

### URL에 로케일이 포함되지 않았는지 확인

이 워크플로우는 웹 URL에 국가별 로케일이 포함되지 않았는지 확인합니다. 이 리포지토리는 전 세계적으로 접근 가능하므로 URL에 국가 로케일이 포함되지 않도록 하는 것이 중요합니다.

1. URL에 국가 로케일이 포함되지 않았는지 확인하려면 다음 작업을 수행하십시오:

    - URL에서 `/en-us/`, `/en/` 또는 기타 언어 로케일과 같은 텍스트를 확인하십시오.
    - URL에 이러한 내용이 포함되지 않았다면 이 검사를 통과합니다.

1. 이 문제를 해결하려면 다음 작업을 수행하십시오:
    - 워크플로우에서 강조 표시된 파일 경로를 엽니다.
    - URL에서 국가 로케일을 제거합니다.

국가 로케일을 제거한 후 변경 사항을 저장하고 푸시하십시오.

### 깨진 URL 확인

이 워크플로우는 파일의 웹 URL이 작동하고 200 상태 코드를 반환하는지 확인합니다.

1. URL이 올바르게 작동하는지 확인하려면 다음 작업을 수행하십시오:
    - 파일의 URL 상태를 확인합니다.

2. 깨진 URL을 수정하려면 다음 작업을 수행하십시오:
    - 깨진 URL이 포함된 파일을 엽니다.
    - URL을 올바른 것으로 업데이트합니다.

URL을 수정한 후 변경 사항을 저장하고 푸시하십시오.

> [!NOTE]
>
> 링크가 접근 가능함에도 불구하고 URL 검사가 실패하는 경우가 있을 수 있습니다. 이는 여러 가지 이유로 발생할 수 있습니다:
>
> - **네트워크 제한**: GitHub 액션 서버는 특정 URL에 대한 접근을 제한할 수 있습니다.
> - **타임아웃 문제**: 응답 시간이 너무 긴 URL은 워크플로우에서 타임아웃 오류를 발생시킬 수 있습니다.
> - **일시적인 서버 문제**: 가끔 서버 다운타임이나 유지 보수로 인해 검증 중에 URL이 일시적으로 사용할 수 없게 될 수 있습니다.

**면책 조항**:
이 문서는 기계 기반 AI 번역 서비스를 사용하여 번역되었습니다. 정확성을 위해 노력하고 있지만, 자동 번역에는 오류나 부정확한 내용이 포함될 수 있습니다. 원본 문서의 원어가 권위 있는 출처로 간주되어야 합니다. 중요한 정보의 경우, 전문적인 인간 번역을 권장합니다. 이 번역 사용으로 인한 오해나 잘못된 해석에 대해 당사는 책임을 지지 않습니다.