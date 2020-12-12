---
description: '자세한 정보: 디버깅 및 오류 보고 매크로'
title: 디버깅 및 오류 보고 매크로
ms.date: 05/06/2019
f1_keywords:
- atldef/ATL::_ATL_DEBUG_INTERFACES
- atldef/ATL::_ATL_DEBUG_QI
- atldef/ATL::ATLASSERT
- afx/ATL::ATLENSURE
- atltrace/ATL::ATLTRACENOTIMPL
- atltrace/ATL::ATLTRACE
helpviewer_keywords:
- macros, error reporting
ms.assetid: 4da9b87f-ec5c-4a32-ab93-637780909b9d
ms.openlocfilehash: 573c3f341ff9f9df58337b75e1080dde960d232c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139947"
---
# <a name="debugging-and-error-reporting-macros"></a>디버깅 및 오류 보고 매크로

이러한 매크로는 유용한 디버깅 및 추적 기능을 제공 합니다.

|Name|설명|
|-|-|
|[_ATL_DEBUG_INTERFACES](#_atl_debug_interfaces)|가 호출 될 때 검색 되는 인터페이스 누수를 출력 창에 씁니다 `_Module.Term` .|
|[_ATL_DEBUG_QI](#_atl_debug_qi)|모든 호출을 `QueryInterface` 출력 창에 씁니다.|
|[가 나 어설션](#atlassert)|C 런타임 라이브러리에 있는 [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 매크로와 동일한 기능을 수행 합니다.|
|[It 확인](#atlensure)|매개 변수 유효성 검사를 수행 합니다. `AtlThrow`필요한 경우 호출|
|[ATLTRACENOTIMPL](#atltracenotimpl)|지정 된 함수가 구현 되지 않은 메시지를 덤프 장치로 보냅니다.|
|[이 추적](#atltrace)|표시 된 플래그 및 수준에 따라 디버거 창과 같은 출력 장치에 대 한 경고를 보고 합니다. 이전 버전과의 호환성을 위해 포함 되었습니다.|
|[ATLTRACE2](#atltrace2)|표시 된 플래그 및 수준에 따라 디버거 창과 같은 출력 장치에 대 한 경고를 보고 합니다.|

## <a name="_atl_debug_interfaces"></a><a name="_atl_debug_interfaces"></a> _ATL_DEBUG_INTERFACES

`AddRef` `Release` 출력 창에 대 한 구성 요소 인터페이스에 대 한 모든 및 호출을 추적 하려면 ATL 헤더 파일을 포함 하기 전에이 매크로를 정의 합니다.

```
#define _ATL_DEBUG_INTERFACES
```

### <a name="remarks"></a>설명

추적 출력은 아래와 같이 표시 됩니다.

`ATL: QIThunk - 2008         AddRef  :   Object = 0x00d81ba0   Refcount = 1   CBug - IBug`

각 추적의 첫 번째 부분은 항상 `ATL: QIThunk` 입니다. 다음은 사용 되는 특정 *인터페이스 썽크* 를 식별 하는 값입니다. 인터페이스 썽크는 참조 횟수를 유지 관리 하 고 여기에 사용 되는 추적 기능을 제공 하는 데 사용 되는 개체입니다. 인터페이스에 대 한 요청을 제외 하 고에 대 한 모든 호출에 새 인터페이스 썽크를 만듭니다 `QueryInterface` `IUnknown` .이 경우에는 COM의 id 규칙을 준수할 때마다 동일한 썽크를 반환 합니다.

다음으로 `AddRef` 호출 된 메서드를 표시 하거나 표시 `Release` 합니다. 다음에는 인터페이스 참조 개수가 변경 된 개체를 식별 하는 값이 표시 됩니다. 추적 되는 값은 **`this`** 개체의 포인터입니다.

추적 되는 참조 횟수는 `AddRef` 또는가 호출 된 후 해당 썽크의 참조 횟수입니다 `Release` . 이 참조 수는 개체에 대 한 참조 횟수와 일치 하지 않을 수 있습니다. 각 썽크는 COM의 참조 횟수 규칙을 완벽 하 게 준수할 수 있도록 자체 참조 횟수를 유지 관리 합니다.

마지막으로 추적 되는 정보는 개체의 이름과 또는 호출의 영향을 받는 인터페이스입니다 `AddRef` `Release` .

서버가 종료 되 고가 호출 될 때 검색 되는 모든 인터페이스 누수는 `_Module.Term` 다음과 같이 기록 됩니다.

`ATL: QIThunk - 2005         LEAK    :   Object = 0x00d81ca0   Refcount = 1   MaxRefCount = 1   CBug - IBug`

여기에 제공 된 정보는 이전 추적 문에 제공 된 정보에 직접 매핑되므로 인터페이스 썽크의 전체 수명 동안 참조 횟수를 검사할 수 있습니다. 또한 해당 인터페이스 썽크의 최대 참조 수를 나타냅니다.

> [!NOTE]
> _ATL_DEBUG_INTERFACES는 소매점 빌드에서 사용할 수 있습니다.

## <a name="_atl_debug_qi"></a><a name="_atl_debug_qi"></a> _ATL_DEBUG_QI

모든 호출을 `QueryInterface` 출력 창에 씁니다.

```
#define _ATL_DEBUG_QI
```

### <a name="remarks"></a>설명

에 대 한 호출이 `QueryInterface` 실패 하면 출력 창에 다음이 표시 됩니다.

*인터페이스 이름* - `failed`

## <a name="atlassert"></a><a name="atlassert"></a> 가 나 어설션

C # ASSERT 매크로는 C 런타임 라이브러리에 있는 [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 매크로와 동일한 기능을 수행 합니다.

```
ATLASSERT(booleanExpression);
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
0이 아닌 값 또는 0으로 계산되는 식(포인터 포함)입니다.

### <a name="remarks"></a>설명

디버그 빌드에서 *booleanExpression* 는 결과가 false 인 경우 디버그 보고서를 생성 하 고 생성 합니다.

### <a name="requirements"></a>요구 사항

**헤더:**

## <a name="atlensure"></a><a name="atlensure"></a> It 확인

이 매크로는 함수에 전달 된 매개 변수의 유효성을 검사 하는 데 사용 됩니다.

```
ATLENSURE(booleanExpression);
ATLENSURE_THROW(booleanExpression, hr);
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
테스트할 부울 식을 지정 합니다.

*시간*<br/>
반환할 오류 코드를 지정 합니다.

### <a name="remarks"></a>설명

이러한 매크로는 잘못 된 매개 변수 사용을 검색 하 고 사용자에 게 알리는 메커니즘을 제공 합니다.

매크로가 호출에 실패 하는 경우 매크로는이를 호출 `AtlThrow` 합니다.

이 경우에는 E_FAIL를 `AtlThrow` 사용 하 여가 호출 됩니다.

ATLENSURE_THROW 경우에 `AtlThrow` 는 지정 된 HRESULT를 사용 하 여가 호출 됩니다.

이에 대 한 두 번째 ASSERT의 차이점은,이는 디버그 빌드에서 뿐만 아니라 릴리스 빌드에서 예외를 throw 한다는 것입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#108](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_1.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="atltracenotimpl"></a><a name="atltracenotimpl"></a> ATLTRACENOTIMPL

ATL의 디버그 빌드에서는 덤프 장치에 " *funcname* 이 구현 되지 않았습니다" 라는 문자열을 보내고 E_NOTIMPL 반환 합니다.

```
ATLTRACENOTIMPL(funcname);
```

### <a name="parameters"></a>매개 변수

*funcname*<br/>
진행 구현 되지 않은 함수의 이름을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

릴리스 빌드에서는 E_NOTIMPL 반환 하기만 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#127](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_2.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:**

## <a name="atltrace"></a><a name="atltrace"></a> 이 추적

표시 된 플래그 및 수준에 따라 디버거 창과 같은 출력 장치에 대 한 경고를 보고 합니다. 이전 버전과의 호환성을 위해 포함 되었습니다.

```
ATLTRACE(exp);

ATLTRACE(
    DWORD category,
    UINT  level,
    LPCSTR lpszFormat, ...);
```

### <a name="parameters"></a>매개 변수

*exp*<br/>
진행 출력 창 또는 이러한 메시지를 트래핑 하는 응용 프로그램에 보낼 문자열 및 변수입니다.

*category*<br/>
진행 보고할 이벤트 또는 메서드의 유형입니다. 범주 목록은 설명 부분을 참조 하십시오.

*level*<br/>
진행 보고할 추적 수준입니다. 자세한 내용은 설명 부분을 참조 하십시오.

*lpszFormat*<br/>
진행 덤프 장치로 보낼 형식이 지정 된 문자열입니다.

### <a name="remarks"></a>설명

정보 추적에 대 한 설명은 [ATLTRACE2](#atltrace2) 를 참조 하십시오. 가 나 추적과 ATLTRACE2는 동일한 동작을 가지 며, 이전 버전과의 호환성을 위해이 추적 기능이 포함 되어 있습니다.

## <a name="atltrace2"></a><a name="atltrace2"></a> ATLTRACE2

표시 된 플래그 및 수준에 따라 디버거 창과 같은 출력 장치에 대 한 경고를 보고 합니다.

```
ATLTRACE2(exp);

ATLTRACE2(
    DWORD category,
    UINT level,
    LPCSTR lpszFormat,  ...);
```

### <a name="parameters"></a>매개 변수

*exp*<br/>
진행 출력 창 또는 이러한 메시지를 트래핑 하는 응용 프로그램에 보낼 문자열입니다.

*category*<br/>
진행 보고할 이벤트 또는 메서드의 유형입니다. 범주 목록은 설명 부분을 참조 하십시오.

*level*<br/>
진행 보고할 추적 수준입니다. 자세한 내용은 설명 부분을 참조 하십시오.

*lpszFormat*<br/>
진행 `printf`덤프 장치로 보낼 문자열을 만드는 데 사용할 스타일 서식 문자열입니다.

### <a name="remarks"></a>설명

ATLTRACE2의 약식 형태는 디버거의 출력 창에 문자열을 씁니다. 또한 두 번째 형식의 ATLTRACE2는 디버거의 출력 창에 출력을 작성 하지만 ATL/MFC 추적 도구의 설정이 적용 됩니다 ( [ATLTraceTool 샘플](../../overview/visual-cpp-samples.md)참조). 예를 들어 *수준* 을 4로 설정 하 고 ATL/MFC 추적 도구를 수준 0으로 설정 하면 메시지가 표시 되지 않습니다. *수준은* 0, 1, 2, 3 또는 4가 될 수 있습니다. 기본값인 0은 가장 심각한 문제만 보고 합니다.

*Category* 매개 변수는 설정할 추적 플래그를 나열 합니다. 이러한 플래그는 보고 하려는 메서드의 유형에 해당 합니다. 아래 표에서는 *category* 매개 변수에 사용할 수 있는 유효한 추적 플래그를 나열 합니다.

### <a name="atl-trace-flags"></a>ATL 추적 플래그

|ATL 범주|설명|
|------------------|-----------------|
|`atlTraceGeneral`|모든 ATL 응용 프로그램에 대 한 보고서입니다. 기본값입니다.|
|`atlTraceCOM`|COM 메서드를 보고 합니다.|
|`atlTraceQI`|QueryInterface 호출을 보고 합니다.|
|`atlTraceRegistrar`|개체의 등록에 대 한 보고서입니다.|
|`atlTraceRefcount`|참조 횟수 변경에 대 한 보고서입니다.|
|`atlTraceWindowing`|Windows 메서드에 대 한 보고서 예를 들어는 잘못 된 메시지 맵 ID를 보고 합니다.|
|`atlTraceControls`|컨트롤에 대 한 보고서 예를 들어, 컨트롤 또는 해당 창이 소멸 되는 경우를 보고 합니다.|
|`atlTraceHosting`|메시지를 호스트 하는 보고서 예를 들어, 컨테이너의 클라이언트가 활성화 되는 경우를 보고 합니다.|
|`atlTraceDBClient`|OLE DB Consumer Template에 대 한 보고서 예를 들어 GetData에 대 한 호출이 실패 하면 출력에 HRESULT가 포함 될 수 있습니다.|
|`atlTraceDBProvider`|OLE DB 공급자 템플릿에 대 한 보고서 예를 들어 열 생성이 실패 한 경우를 보고 합니다.|
|`atlTraceSnapin`|MMC 스냅인 응용 프로그램에 대 한 보고서입니다.|
|`atlTraceNotImpl`|표시 된 함수가 구현 되지 않은 것을 보고 합니다.|
|`atlTraceAllocation`|Atldbgmem의 메모리 디버깅 도구에서 인쇄 한 메시지를 보고 합니다.|

### <a name="mfc-trace-flags"></a>MFC 추적 플래그

|MFC 범주|설명|
|------------------|-----------------|
|`traceAppMsg`|일반적인 목적의 MFC 메시지입니다. 항상 권장 됩니다.|
|`traceDumpContext`|[CDumpContext](../../mfc/reference/cdumpcontext-class.md)의 메시지입니다.|
|`traceWinMsg`|MFC 메시지 처리 코드의 메시지입니다.|
|`traceMemory`|MFC의 메모리 관리 코드의 메시지입니다.|
|`traceCmdRouting`|MFC의 Windows 명령 라우팅 코드의 메시지입니다.|
|`traceHtml`|MFC의 DHTML 대화 상자에서 메시지를 지원 합니다.|
|`traceSocket`|MFC의 소켓 지원 메시지입니다.|
|`traceOle`|MFC의 OLE 지원 메시지입니다.|
|`traceDatabase`|MFC 데이터베이스 지원의 메시지입니다.|
|`traceInternet`|MFC의 인터넷 지원 메시지입니다.|

사용자 지정 추적 범주를 선언 하려면 클래스의 전역 인스턴스를 다음과 `CTraceCategory` 같이 선언 합니다.

[!code-cpp[NVC_ATL_Utilities#109](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_3.cpp)]

이 예에서 MY_CATEGORY 범주 이름은 *category* 매개 변수에 지정 하는 이름입니다. 첫 번째 매개 변수는 ATL/MFC 추적 도구에 표시 되는 범주 이름입니다. 두 번째 매개 변수는 기본 추적 수준입니다. 이 매개 변수는 선택 사항이 며 기본 추적 수준은 0입니다.

사용자 정의 범주를 사용 하려면 다음을 수행 합니다.

[!code-cpp[NVC_ATL_Utilities#110](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_4.cpp)]

추적 메시지를 필터링 하도록 지정 하려면 문 앞의 Stdafx.h에 이러한 매크로에 대 한 정의를 삽입 `#include <atlbase.h>` 합니다.

또는 **속성 페이지** 대화 상자의 전처리기 지시문에서 필터를 설정할 수 있습니다. **전처리기** 탭을 클릭 한 다음 **전처리기 정의** 편집 상자에 전역을 삽입 합니다.

이 기본 .h에는 ATLTRACE2 매크로의 기본 정의가 포함 되어 있으며,이 정의를 사용 하 여 이러한 기호를 정의 하지 않으면 해당 정의가 사용 됩니다.

릴리스 빌드에서는 ATLTRACE2를로 컴파일합니다 `(void) 0` .

ATLTRACE2는 서식 지정 후 덤프 장치로 보낼 문자열의 내용을 1023 자 이하로 제한 합니다.

가 나 추적과 ATLTRACE2는 동일한 동작을 가지 며, 이전 버전과의 호환성을 위해이 추적 기능이 포함 되어 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#111](../../atl/codesnippet/cpp/debugging-and-error-reporting-macros_5.cpp)]

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)<br/>
[디버깅 및 오류 보고 전역 함수](../../atl/reference/debugging-and-error-reporting-global-functions.md)
