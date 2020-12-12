---
description: '자세한 정보: 방법: 컴파일 타임에 리소스 포함 (c + +)'
title: '방법: 컴파일 타임에 리소스 포함 (c + +)'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: 18c391351c3a97a8adbbd79691f9c0e3ec07abae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329356"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>방법: 컴파일 타임에 리소스 포함 (c + +)

기본적으로 모든 리소스는 하나의 리소스 스크립트 (.rc) 파일에 있지만 기본 .rc 파일이 아닌 다른 파일에 리소스를 배치 하는 이유는 여러 가지가 있습니다.

- .Rc 파일을 저장할 때 삭제 되지 않는 주석을 리소스 문에 추가 합니다.

- 이미 개발 되 고 테스트 된 리소스를 포함 하 고 추가 수정이 필요 하지 않습니다. 포함 되었지만 .rc 확장명이 없는 모든 파일은 리소스 편집기에서 편집할 수 없습니다.

- 다른 프로젝트에서 사용 중이거나 소스 코드 버전 제어 시스템의 일부인 리소스를 포함 하려면입니다. 이러한 리소스는 수정 내용이 모든 프로젝트에 영향을 주는 중앙 위치에 있어야 합니다.

- 사용자 지정 형식인 리소스 (예: RCDATA 리소스)를 포함 합니다. RCDATA 리소스에는 식을 필드 값으로 사용할 수 없는 특별 한 요구 사항이 있습니다 `nameID` .

이러한 조건을 충족 하는 기존 .rc 파일에 섹션이 있는 경우이 섹션을 하나 이상의 개별 .rc 파일에 놓고 **리소스 내용** 대화 상자를 사용 하 여 프로젝트에 포함 합니다.

## <a name="resource-includes"></a>리소스 포함

**리소스 내용** 대화 상자의 **컴파일 시간 지시문** 상자에 나열 하 여 컴파일 타임에 다른 파일의 리소스를 프로젝트에 추가할 수 있습니다. **리소스 내용** 대화 상자를 사용 하 여 프로젝트의 기본 작업 정렬을 수정할 수 있습니다 .이를 통해 프로젝트 .rc 파일 및의 모든 [기호](../windows/symbols-resource-identifiers.md) 에 모든 리소스를 저장할 수 `Resource.h` 있습니다.

시작 하려면 [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources)에서 .rc 파일을 마우스 오른쪽 단추로 클릭 하 여 **리소스 내용** 대화 상자를 열고 **리소스 포함** 을 선택 하 고 다음 속성을 확인 합니다.

| 속성 | 설명 |
|---|---|
| **기호 헤더 파일** | 리소스 파일에 대 한 기호 정의가 저장 되는 헤더 파일의 이름을 변경할 수 있습니다.<br/><br/>자세한 내용은 [기호 헤더 파일의 이름 변경](./changing-a-symbol-or-symbol-name-id.md)을 참조 하세요. |
| **읽기 전용 기호 지시문** | 수정할 수 없는 기호가 포함 된 헤더 파일을 포함할 수 있습니다.<br/><br/>예를 들어 다른 프로젝트와 공유할 기호 파일입니다. 여기에는 MFC .h 파일도 포함 될 수 있습니다. 자세한 내용은 [공유 (읽기 전용) 또는 계산 된 기호 포함](./changing-a-symbol-or-symbol-name-id.md)을 참조 하세요. |
| **컴파일 타임 지시문** | 기본 리소스 파일의 리소스와 별도로 생성 및 편집 되는 리소스 파일을 포함 하거나, 컴파일 타임 지시문 (예: 조건에 따라 리소스를 포함 하는 지시문)을 포함 하거나, 사용자 지정 형식의 리소스를 포함할 수 있습니다.<br/><br/>**컴파일 시간 지시문 상자** 를 사용 하 여 표준 MFC 리소스 파일을 포함할 수도 있습니다. |

> [!NOTE]
> 이러한 텍스트 상자의 항목은 `TEXTINCLUDE 1` 각각, 및로 표시 된 .rc 파일에 표시 됩니다 `TEXTINCLUDE 2` `TEXTINCLUDE 3` . 자세한 내용은 [TN035: Visual C++에서 여러 리소스 파일 및 헤더 파일 사용](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md)을 참조 하세요.

**리소스** 내용 대화 상자를 사용 하 여 리소스 파일을 변경한 후 변경 내용을 적용 하려면 *.rc* 파일을 닫았다가 다시 열어야 합니다.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>컴파일 시간에 프로젝트에 리소스를 포함하려면

1. 고유한 파일 이름으로 리소스 스크립트 파일에 리소스를 배치합니다. 기본 리소스 스크립트 파일에 사용 되는 파일의 이름 이므로 *projectname .rc* 를 사용 하지 마세요.

1. [리소스 뷰](how-to-create-a-resource-script-file.md#create-resources) 에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 **리소스 포함** 을 선택 합니다.

1. **컴파일 타임 지시문** 상자에 개발 환경의 주 리소스 파일에 새 리소스 파일을 포함 하는 [#include](../preprocessor/hash-include-directive-c-cpp.md) 컴파일러 지시문을 추가 합니다.

이러한 방식으로 포함 된 파일의 리소스는 컴파일 시간에 실행 파일의 일부에만 적용 되며 프로젝트의 기본 .rc 파일에서 작업 하는 경우 편집 또는 수정에 사용할 수 없습니다. 포함 된 .rc 파일은 별도로 열어야 하며 .rc 확장명 없이 포함 된 모든 파일은 리소스 편집기에서 편집할 수 없습니다.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>특정 리소스 (.rc) 파일에 대 한 포함 디렉터리를 지정 하려면

1. **솔루션 탐색기** 에서 *.rc* 파일을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.

1. 왼쪽 창에서 **리소스** 노드를 선택 하 고 **추가 포함** 디렉터리 속성에 추가 포함 디렉터리를 지정 합니다.

### <a name="to-find-symbols-in-resources"></a>리소스에서 기호를 찾으려면

1. 메뉴로 이동 하 여  >  [기호 찾기](/visualstudio/ide/go-to)를 편집 합니다.

   > [!TIP]
   > 검색에서 [정규식](/visualstudio/ide/using-regular-expressions-in-visual-studio) 을 사용 하려면 **기호 찾기** 대신 **편집** 메뉴에서 [파일에서 찾기](/visualstudio/ide/reference/find-command) 를 선택 합니다. [찾기 대화 상자](/visualstudio/ide/finding-and-replacing-text) 에서 **사용: 정규식** 확인란을 선택 하 고 **찾을 내용** 상자에서 드롭다운 목록에서 일반 검색 식을 선택할 수 있습니다. 이 목록에서 식을 선택 하면 **찾을 내용** 상자에 검색 텍스트로 대체 됩니다.

1. **찾을 내용** 상자의 드롭다운 목록에서 이전 검색 문자열을 선택 하거나 찾으려는 액셀러레이터 키를 입력 합니다 (예:) `ID_ACCEL1` .

1. **찾기** 옵션을 선택 하 고 **다음 찾기** 를 선택 합니다.

> [!NOTE]
> 문자열, 액셀러레이터 또는 이진 리소스에서 기호를 검색할 수 없습니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[리소스 파일](../windows/resource-files-visual-studio.md)<br/>
[방법: 리소스 만들기](../windows/how-to-create-a-resource-script-file.md)<br/>
[방법: 리소스 관리](../windows/how-to-copy-resources.md)<br/>
