---
title: '연습: 오류에 대 한 C/c + + 코드 분석'
description: Visual Studio에서 Microsoft c + +를 사용 하 여 코드 분석을 사용 하는 방법을 보여 줍니다.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: bb81ca376651c17c760ee776510303efaa13fd9a
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924780"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>연습: 오류에 대 한 C/c + + 코드 분석

이 연습에서는 C/c + + 코드에서 잠재적 코드 오류를 분석 하는 방법을 보여 줍니다. C/c + + 코드에 대 한 코드 분석 도구를 사용 합니다.

이 연습에서는 다음을 수행 합니다.

- 네이티브 코드에 대해 코드 분석을 실행 합니다.
- 코드 오류 경고를 분석 합니다.
- 경고를 오류로 처리 합니다.
- 코드 오류 분석을 향상 시키기 위해 소스 코드에 주석을 추가 합니다.

## <a name="prerequisites"></a>사전 요구 사항

- [CppDemo 샘플](../code-quality/demo-sample.md)의 복사본입니다.
- C/c + +에 대 한 기본적인 이해

## <a name="run-code-analysis-on-native-code"></a>네이티브 코드에 대해 코드 분석 실행

### <a name="to-run-code-defect-analysis-on-native-code"></a>네이티브 코드에 대 한 코드 오류 분석을 실행 하려면

::: moniker range=">=msvc-160"

1. Visual Studio에서 CppDemo 솔루션을 엽니다.

     CppDemo 솔루션은 이제 **솔루션 탐색기** 를 채웁니다.

1. **빌드** 메뉴에서 **솔루션 다시 빌드** 를 선택 합니다.

     솔루션이 오류 또는 경고 없이 빌드됩니다.

1. **솔루션 탐색기** 에서 codedefects 있는 프로젝트를 선택 합니다.

1. **프로젝트** 메뉴에서 **속성** 을 선택합니다.

     **Codedefects 속성 페이지** 대화 상자가 표시 됩니다.

1. **코드 분석** 속성 페이지를 선택 합니다.

1. **빌드 시 코드 분석 사용** 속성을 **예** 로 변경 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

1. CodeDefects 있는 프로젝트를 다시 빌드합니다.

     코드 분석 경고는 **오류 목록** 창에 표시 됩니다.

::: moniker-end

::: moniker range="<=msvc-150"

1. Visual Studio에서 CppDemo 솔루션을 엽니다.

     CppDemo 솔루션은 이제 **솔루션 탐색기** 를 채웁니다.

1. **빌드** 메뉴에서 **솔루션 다시 빌드** 를 선택 합니다.

     솔루션이 오류 또는 경고 없이 빌드됩니다.

     > [!NOTE]
     > Visual Studio 2017에서는 IntelliSense 엔진에 의사 경고가 표시 될 수 있습니다 `E1097 unknown attribute "no_init_all"` . 이 경고는 무시해도 됩니다.

1. **솔루션 탐색기** 에서 codedefects 있는 프로젝트를 선택 합니다.

1. **프로젝트** 메뉴에서 **속성** 을 선택합니다.

     **Codedefects 속성 페이지** 대화 상자가 표시 됩니다.

1. **코드 분석** 속성 페이지를 선택 합니다.

1. **빌드 시 코드 분석 사용** 확인란을 선택 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

1. CodeDefects 있는 프로젝트를 다시 빌드합니다.

     코드 분석 경고는 **오류 목록** 창에 표시 됩니다.

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>코드 오류 경고를 분석 하려면

1. **보기** 메뉴에서 **오류 목록** 를 선택 합니다.

     이 메뉴 항목이 표시 되지 않을 수 있습니다. Visual Studio에서 선택한 개발자 프로필에 따라 다릅니다. **보기** 메뉴에서 **다른 창을** 가리킨 다음 **오류 목록** 를 선택 해야 할 수도 있습니다.

1. **오류 목록** 창에서 다음 경고를 두 번 클릭 합니다.

     C6230: 의미 체계가 다른 형식 간의 암시적 캐스트입니다. 부울 컨텍스트에서 HRESULT를 사용 합니다.

     코드 편집기는 함수 내에서 경고를 발생 시킨 줄을 표시 합니다 `bool ProcessDomain()` . 이 경고는가 `HRESULT` 부울 결과가 필요한 ' if ' 문에서를 사용 하 고 있음을 나타냅니다. 일반적으로 `S_OK` HRESULT는 함수에서 반환 되는 경우 success를 나타내지만이 값은로 계산 되는 부울 값으로 변환 되기 때문 **`false`** 입니다.

1. 매크로를 사용 하 여이 경고를 수정 `SUCCEEDED` 합니다 .이 매크로는 **`true`** 반환 값이 success를 나타내는 경우로 변환 `HRESULT` 됩니다. 코드는 다음 코드와 유사 해야 합니다.

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. **오류 목록** 에서 다음 경고를 두 번 클릭 합니다.

     C6282: 잘못 된 연산자: 부울 컨텍스트에서 상수를 할당 했습니다. 대신 ' = = '를 사용 하십시오.

1. 같은지 테스트 하 여이 경고를 수정 합니다. 코드는 다음 코드와 유사 하 게 표시 됩니다.

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. **Error List** `i` 및 `j` 를 0으로 초기화 하 여 오류 목록에서 남은 C6001 경고를 수정 합니다.

1. CodeDefects 있는 프로젝트를 다시 빌드합니다.

     프로젝트는 경고 또는 오류 없이 빌드됩니다.

## <a name="correct-source-code-annotation-warnings"></a>소스 코드 주석 경고 수정

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>주석에서 소스 코드 주석 경고를 사용 하도록 설정 하려면

::: moniker range=">=msvc-160"

1. 솔루션 탐색기에서 주석 프로젝트를 선택 합니다.

1. **프로젝트** 메뉴에서 **속성** 을 선택합니다.

     **주석 속성 페이지** 대화 상자가 표시 됩니다.

1. **코드 분석** 속성 페이지를 선택 합니다.

1. **빌드 시 코드 분석 사용** 속성을 **예** 로 변경 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

::: moniker-end

::: moniker range="<=msvc-150"

1. 솔루션 탐색기에서 주석 프로젝트를 선택 합니다.

1. **프로젝트** 메뉴에서 **속성** 을 선택합니다.

     **주석 속성 페이지** 대화 상자가 표시 됩니다.

1. **코드 분석** 속성 페이지를 선택 합니다.

1. **빌드 시 코드 분석 사용** 확인란을 선택 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>주석에서 소스 코드 주석 경고를 수정 하려면

1. 주석 프로젝트를 다시 빌드합니다.

1. **빌드** 메뉴에서 **주석에 대해 코드 분석 실행** 을 선택 합니다.

1. **오류 목록** 에서 다음 경고를 두 번 클릭 합니다.

     C6011: NULL 포인터 ' newNode '를 역참조 하 고 있습니다.

     이 경고는 호출자가 반환 값을 확인 하는 데 실패 했음을 나타냅니다. 이 경우에 대 한 호출은 `AllocateNode` NULL 값을 반환할 수 있습니다. 의 함수 선언에 대 한 annotation 헤더 파일을 참조 하세요 `AllocateNode` .

1. 커서는 경고가 발생 한 annotation .cpp 파일의 위치에 있습니다.

1. 이 경고를 해결 하려면 ' if ' 문을 사용 하 여 반환 값을 테스트 합니다. 코드는 다음 코드와 유사 해야 합니다.

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. 주석 프로젝트를 다시 빌드합니다.

     프로젝트는 경고 또는 오류 없이 빌드됩니다.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>소스 코드 주석을 사용 하 여 더 많은 문제 검색

### <a name="to-use-source-code-annotation"></a>소스 코드 주석을 사용 하려면

1. 형식 매개 변수와 함수의 반환 값에 주석을 추가 `AddTail` 하 여 포인터 값이 null 일 수 있음을 표시 합니다.

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. **빌드** 메뉴에서 **솔루션에서 코드 분석 실행** 을 선택합니다.

1. **오류 목록** 에서 다음 경고를 두 번 클릭 합니다.

     C6011: NULL 포인터 ' node '를 역참조 하 고 있습니다.

     이 경고는 함수에 전달 된 노드가 null 일 수 있음을 나타냅니다.

1. 이 경고를 해결 하려면 함수 시작 부분에 ' if ' 문을 사용 하 여 전달 된 값을 테스트 합니다. 코드는 다음 코드와 유사 해야 합니다.

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. **빌드** 메뉴에서 **솔루션에서 코드 분석 실행** 을 선택합니다.

     이제 프로젝트는 경고 또는 오류 없이 빌드됩니다.

## <a name="see-also"></a>참고 항목

[연습: 관리 코드의 코드 오류 분석](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[C/C++용 코드 분석](../code-quality/code-analysis-for-c-cpp-overview.md)
