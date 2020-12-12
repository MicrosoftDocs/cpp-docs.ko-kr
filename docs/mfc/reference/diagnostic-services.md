---
description: '자세한 정보: 진단 서비스'
title: 진단 서비스
ms.date: 11/04/2016
helpviewer_keywords:
- diagnosi [MFC]s, diagnostic services
- diagnostic macros [MFC], list of general MFC
- services [MFC], diagnostic
- MFC, diagnostic services
- general diagnostic functions and variables [MFC]
- diagnostics [MFC], diagnostic functions and variables
- diagnostics [MFC], list of general MFC
- diagnosis [MFC], diagnostic functions and variables
- diagnosis [MFC], list of general MFC
- general diagnostic macros in MFC
- diagnostic macros [MFC]
- diagnostic services [MFC]
- object diagnostic functions in MFC
- diagnostics [MFC], diagnostic services
- diagnostic functions and variables [MFC]
ms.assetid: 8d78454f-9fae-49c2-88c9-d3fabd5393e8
ms.openlocfilehash: 3d2b7bd303fc062aa520497e649430f53f7667c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220073"
---
# <a name="diagnostic-services"></a>진단 서비스

MFC 라이브러리는 프로그램을 더 쉽게 디버그할 수 있는 많은 진단 서비스를 제공합니다. 이러한 진단 서비스에는 매크로 및 전역 함수가 포함되며, 이러한 함수를 통해 프로그램의 메모리 할당을 추적하고 런타임 중 개체의 내용을 덤프하고 런타임 중 디버깅 메시지를 인쇄할 수 있습니다. 진단 서비스의 매크로 및 전역 함수는 다음과 같은 범주로 그룹화됩니다.

- 일반 진단 매크로

- 일반 진단 함수 및 변수

- 개체 진단 함수

이러한 매크로 및 함수는 MFC 디버그 및 릴리스 버전의 `CObject` 에서 파생된 모든 클래스에서 사용할 수 있습니다. 그러나 DEBUG_NEW 및 VERIFY를 제외한 모든는 릴리스 버전에서 아무 작업도 수행 하지 않습니다.

디버그 라이브러리에서, 할당된 모든 메모리 블록은 일련의 "보호 바이트"와 함께 묶입니다. 이러한 바이트가 잘못된 메모리 쓰기로 인해 교란되면 진단 루틴이 문제를 보고할 수 있습니다. 다음 줄을 포함하는 경우

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

구현 파일에서에 대 한 모든 호출에는 **`new`** 메모리 할당이 발생 한 파일 이름 및 줄 번호가 저장 됩니다. [Cmemorystate::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) 함수는이 추가 정보를 표시 하 여 메모리 누수를 식별할 수 있도록 합니다. 진단 출력에 대 한 추가 정보는 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 클래스를 참조 하세요.

또한 C 런타임 라이브러리는 애플리케이션을 디버그하는 데 사용할 수 있는 진단 함수 집합도 지원합니다. 자세한 내용은 Run-Time 라이브러리 참조에서 [루틴 디버그](../../c-runtime-library/debug-routines.md) 를 참조 하세요.

### <a name="mfc-general-diagnostic-macros"></a>MFC 일반 진단 매크로

|Name|설명|
|-|-|
|[어설션하](#assert)|라이브러리의 디버그 버전에서 지정된 식의 값이 FALSE로 계산된 경우 메시지를 출력한 후 프로그램을 중단합니다.|
|[ASSERT_KINDOF](#assert_kindof)|개체가 지정된 클래스의 개체인지 아니면 지정된 클래스에서 파생된 클래스의 개체인지 테스트합니다.|
|[ASSERT_VALID](#assert_valid)|해당 `AssertValid` 멤버 함수를 호출하여 개체의 내부 유효성을 테스트합니다. 일반적으로 `CObject`에서 재정의됩니다.|
|[DEBUG_NEW](#debug_new)|메모리 누수를 쉽게 찾을 수 있도록 디버그 모드에서 모든 개체 할당에 파일 이름과 줄 번호를 제공합니다.|
|[DEBUG_ONLY](#debug_only)|ASSERT와 비슷하지만, 식의 값을 테스트하지는 않습니다. 디버그 모드에서만 실행해야 하는 코드에 유용합니다.|
|[및 ENSURE_VALID 확인](#ensure)|를 사용 하 여 데이터 정확성의 유효성을 검사 합니다.|
|[THIS_FILE](#this_file)|는 컴파일되는 파일의 이름으로 확장 됩니다.|
|[TRACE](#trace)|라이브러리의 디버그 버전에서 `printf`와 유사한 기능을 제공합니다.|
|[올바른지](#verify)|ASSERT와 비슷하지만, 라이브러리의 릴리스 버전뿐만 아니라 디버그 버전에서도 식을 계산합니다.|

### <a name="mfc-general-diagnostic-variables-and-functions"></a>MFC 일반 진단 변수 및 함수

|Name|설명|
|-|-|
|[afxDump](#afxdump)|[CDumpContext](../../mfc/reference/cdumpcontext-class.md) 정보를 디버거 출력 창 또는 디버그 터미널에 보내는 전역 변수입니다.|
|[afxMemDF](#afxmemdf)|디버깅 메모리 할당자의 동작을 제어하는 전역 변수입니다.|
|[AfxCheckError](#afxcheckerror)|전달된 SCODE를 테스트하여 오류인지 알아보고 오류인 경우 적절한 오류를 throw하는 데 사용하는 전역 변수입니다.|
|[AfxCheckMemory](#afxcheckmemory)|현재 할당된 모든 메모리의 무결성을 검사합니다.|
|[AfxDebugBreak](#afxdebugbreak)|실행을 중단 시킵니다.|
|[afxDump](#cdumpcontext_in_mfc)|디버거 내에 있는 동안 호출되는 경우 디버그하는 동안 개체의 상태를 덤프합니다.|
|[afxDump](#afxdump)|디버깅 하는 동안 개체의 상태를 덤프 하는 내부 함수입니다.|
|[AfxDumpStack](#afxdumpstack)|현재 스택의 이미지를 생성합니다. 이 함수는 항상 정적으로 연결됩니다.|
|[AfxEnableMemoryLeakDump](#afxenablememoryleakdump)|메모리 누수 덤프를 사용하도록 설정합니다.|
|[AfxEnableMemoryTracking](#afxenablememorytracking)|메모리 추적을 켜고 끕니다.|
|[AfxIsMemoryBlock](#afxismemoryblock)|메모리 블록이 제대로 할당되었는지 확인합니다.|
|[AfxIsValidAddress](#afxisvalidaddress)|메모리 주소 범위가 프로그램의 경계 내에 있는지 확인합니다.|
|[AfxIsValidString](#afxisvalidstring)|문자열에 대한 포인터가 유효한지 여부를 결정합니다.|
|[AfxSetAllocHook](#afxsetallochook)|각 메모리 할당에서 함수 호출을 사용하도록 설정합니다.|

### <a name="mfc-object-diagnostic-functions"></a>MFC 개체 진단 함수

|Name|설명|
|-|-|
|[AfxDoForAllClasses](#afxdoforallclasses)|런타임 형식 검사를 지원하는 모든 `CObject`파생 클래스에서 지정된 함수를 실행합니다.|
|[AfxDoForAllObjects](#afxdoforallobjects)|로 할당 된 모든 파생 개체에서 지정 된 함수를 수행 `CObject` **`new`** 합니다.|

### <a name="mfc-compilation-macros"></a>MFC 컴파일 매크로

|Name|설명|
|-|-|
|[_AFX_SECURE_NO_WARNINGS](#afx_secure_no_warnings)|사용 되지 않는 MFC 함수 사용에 대 한 컴파일러 경고를 표시 하지 않습니다.|

## <a name="_afx_secure_no_warnings"></a><a name="afx_secure_no_warnings"></a> _AFX_SECURE_NO_WARNINGS

사용 되지 않는 MFC 함수 사용에 대 한 컴파일러 경고를 표시 하지 않습니다.

### <a name="syntax"></a>구문

```
_AFX_SECURE_NO_WARNINGS
```

### <a name="example"></a>예제

_AFX_SECURE_NO_WARNINGS 정의 되지 않은 경우이 코드 샘플에서 컴파일러 경고가 발생 합니다.

```cpp
// define this before including any afx files in *pch.h* (*stdafx.h* in Visual Studio 2017 and earlier)
#define _AFX_SECURE_NO_WARNINGS
```

```cpp
CRichEditCtrl* pRichEdit = new CRichEditCtrl;
pRichEdit->Create(WS_CHILD|WS_VISIBLE|WS_BORDER|ES_MULTILINE,
   CRect(10,10,100,200), pParentWnd, 1);
char sz[256];
pRichEdit->GetSelText(sz);
```

## <a name="afxdebugbreak"></a><a name="afxdebugbreak"></a> AfxDebugBreak

`AfxDebugBreak`MFC 응용 프로그램의 디버그 버전을 실행할 때이 함수를 호출 하 여에 대 한 호출 위치에서 중단을 발생 시킵니다.

### <a name="syntax"></a>구문

```cpp
void AfxDebugBreak( );
```

### <a name="remarks"></a>설명

`AfxDebugBreak` 는 MFC 응용 프로그램의 릴리스 버전에는 영향을 주지 않으며 제거 해야 합니다. 이 함수는 MFC 응용 프로그램 에서만 사용 해야 합니다. `DebugBreak`MFC가 아닌 응용 프로그램에서 중단을 발생 시키려면 Win32 API 버전를 사용 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxver_. h

## <a name="assert"></a><a name="assert"></a> 어설션하

해당 인수를 계산 합니다.

```
ASSERT(booleanExpression)
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
0이 아닌 값 또는 0으로 계산 되는 식 (포인터 값 포함)을 지정 합니다.

### <a name="remarks"></a>설명

결과가 0 이면 매크로는 진단 메시지를 출력 하 고 프로그램을 중단 합니다. 조건이 0이 아닌 경우 아무 작업도 수행 하지 않습니다.

진단 메시지의 형식은 다음과 같습니다.

`assertion failed in file <name> in line <num>`

여기서 *name* 은 소스 파일의 이름이 고, *num* 은 소스 파일에서 실패 한 어설션의 줄 번호입니다.

MFC의 릴리스 버전에서 ASSERT는 식을 계산 하지 않으므로 프로그램을 중단 하지 않습니다. 환경에 관계 없이 식을 평가 해야 하는 경우 ASSERT 대신 VERIFY 매크로를 사용 합니다.

> [!NOTE]
> 이 함수는 MFC의 디버그 버전 에서만 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#44](../../mfc/codesnippet/cpp/diagnostic-services_2.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="assert_kindof"></a><a name="assert_kindof"></a> ASSERT_KINDOF

이 매크로는 가리키는 개체가 지정 된 클래스의 개체 이거나 지정 된 클래스에서 파생 된 클래스의 개체 임을 어설션 합니다.

```
ASSERT_KINDOF(classname, pobject)
```

### <a name="parameters"></a>매개 변수

*classname*<br/>
파생 클래스의 이름 `CObject` 입니다.

*pobject*<br/>
클래스 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*Pobject* 매개 변수는 개체에 대 한 포인터 여야 하며 일 수 있습니다 **`const`** . 및 클래스가 가리키는 개체는 런타임 클래스 정보를 지원 해야 합니다 `CObject` . 예를 들어 `pDocument` 가 클래스의 개체 또는 파생 클래스의 개체에 대 한 포인터 인지 확인 하려면 `CMyDoc` 다음 코드를 사용할 수 있습니다.

[!code-cpp[NVC_MFCDocView#194](../../mfc/codesnippet/cpp/diagnostic-services_3.cpp)]

매크로를 사용 하는 `ASSERT_KINDOF` 것은 코딩의 경우와 동일 합니다.

[!code-cpp[NVC_MFCDocView#195](../../mfc/codesnippet/cpp/diagnostic-services_4.cpp)]

이 함수는 [DECLARE_DYNAMIC] (런타임-개체-declare_dynamic 또는 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) 매크로를 사용 하 여 선언 된 클래스에 대해서만 작동 합니다.

> [!NOTE]
> 이 함수는 MFC의 디버그 버전 에서만 사용할 수 있습니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="assert_valid"></a><a name="assert_valid"></a> ASSERT_VALID

를 사용 하 여 개체의 내부 상태에 대 한 가정을 테스트할 수 있습니다.

```
ASSERT_VALID(pObject)
```

### <a name="parameters"></a>매개 변수

*pObject*<br/>
에서 파생 된 클래스의 개체를 지정 합니다 .이 개체는 `CObject` 재정의 버전의 `AssertValid` 멤버 함수를 포함 합니다.

### <a name="remarks"></a>설명

ASSERT_VALID는 `AssertValid` 인수로 전달 되는 개체의 멤버 함수를 호출 합니다.

MFC의 릴리스 버전에서 ASSERT_VALID은 아무 작업도 수행 하지 않습니다. 디버그 버전에서는 포인터의 유효성을 검사 하 고, NULL에 대해 확인 하 고, 개체의 고유한 `AssertValid` 멤버 함수를 호출 합니다. 이러한 테스트 중 하나라도 실패 하면 [ASSERT](#assert)와 동일한 방식으로 경고 메시지가 표시 됩니다.

> [!NOTE]
> 이 함수는 MFC의 디버그 버전 에서만 사용할 수 있습니다.

자세한 내용 및 예제는 [MFC 응용 프로그램 디버깅](/visualstudio/debugger/mfc-debugging-techniques)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#19](../../mfc/codesnippet/cpp/diagnostic-services_5.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="debug_new"></a><a name="debug_new"></a> DEBUG_NEW

는 메모리 누수를 찾는 데 도움이 됩니다.

```
#define  new DEBUG_NEW
```

### <a name="remarks"></a>설명

일반적으로 연산자를 사용 하 여 힙 저장소를 할당 하는 프로그램의 모든 위치에서 DEBUG_NEW를 사용할 수 있습니다 **`new`** .

디버그 모드에서 ( **_DEBUG** 기호가 정의 된 경우) DEBUG_NEW은 할당 된 각 개체의 파일 이름과 줄 번호를 추적 합니다. 그런 다음 [Cmemorystate::D umpallobjectssince](cmemorystate-structure.md#dumpallobjectssince) 멤버 함수를 사용 하는 경우 DEBUG_NEW로 할당 된 각 개체에는 할당 된 파일 이름 및 줄 번호가 표시 됩니다.

DEBUG_NEW를 사용 하려면 다음 지시문을 소스 파일에 삽입 합니다.

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

이 지시문을 삽입 하면 전처리기에서 사용 하는 모든 위치에 DEBUG_NEW을 삽입 **`new`** 하 고 MFC는 나머지를 수행 합니다. 프로그램의 릴리스 버전을 컴파일할 때 DEBUG_NEW 간단한 작업으로 확인 되 **`new`** 고 파일 이름 및 줄 번호 정보가 생성 되지 않습니다.

> [!NOTE]
> 이전 버전의 MFC (4.1 및 이전 버전)에서는 `#define` IMPLEMENT_DYNCREATE 또는 IMPLEMENT_SERIAL 매크로를 호출한 모든 문 뒤에 문을 배치 해야 했습니다. 이것이 더 이상 필요 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="debug_only"></a><a name="debug_only"></a> DEBUG_ONLY

디버그 모드 ( **_DEBUG** 기호가 정의 된 경우)는 DEBUG_ONLY 인수를 계산 합니다.

```
DEBUG_ONLY(expression)
```

### <a name="remarks"></a>설명

릴리스 빌드에서는 DEBUG_ONLY 인수를 계산 하지 않습니다. 이 기능은 디버그 빌드에서만 실행 되어야 하는 코드가 있는 경우에 유용 합니다.

DEBUG_ONLY 매크로는 and를 사용 하는 주변 *식* 에 해당 `#ifdef _DEBUG` `#endif` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#32](../../mfc/codesnippet/cpp/diagnostic-services_6.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

### <a name="ensure-and-ensure_valid"></a><a name="ensure"></a> 및 ENSURE_VALID 확인

를 사용 하 여 데이터 정확성의 유효성을 검사 합니다.

### <a name="syntax"></a>구문

```
ENSURE(  booleanExpression )
ENSURE_VALID( booleanExpression  )
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
테스트할 부울 식을 지정 합니다.

### <a name="remarks"></a>설명

이러한 매크로의 목적은 매개 변수의 유효성 검사를 개선 하는 것입니다. 매크로를 통해 코드에서 잘못 된 매개 변수를 추가로 처리할 수 없습니다. ASSERT 매크로와 달리 매크로는 어설션을 생성 하는 것 외에도 예외를 throw 합니다.

매크로는 프로젝트 구성에 따라 두 가지 방법으로 동작 합니다. 매크로는 ASSERT를 호출한 다음 어설션이 실패할 경우 예외를 throw 합니다. 따라서 디버그 구성에서 (즉, _DEBUG 정의 된 경우) 매크로는 릴리스 구성에서 어설션 및 예외를 생성 하 고, 매크로는 예외만 생성 합니다 (ASSERT는 릴리스 구성에서 식을 평가 하지 않음).

매크로 ENSURE_ARG 매크로와 동일 하 게 작동 합니다.

ENSURE_VALID는 디버그 빌드에서만 영향을 주는 ASSERT_VALID 매크로를 호출 합니다. 또한 포인터가 NULL 인 경우에는 ENSURE_VALID 예외를 throw 합니다. NULL 테스트는 디버그 구성과 릴리스 구성에서 모두 수행 됩니다.

이러한 테스트 중 하나라도 실패 하면 ASSERT와 동일한 방식으로 경고 메시지가 표시 됩니다. 필요한 경우 매크로에서 잘못 된 인수 예외를 throw 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="this_file"></a><a name="this_file"></a> THIS_FILE

는 컴파일되는 파일의 이름으로 확장 됩니다.

### <a name="syntax"></a>구문

```
THIS_FILE
```

### <a name="remarks"></a>설명

이 정보는 ASSERT 및 VERIFY 매크로에 사용 됩니다. 응용 프로그램 마법사 및 코드 마법사는 생성 하는 소스 코드 파일에 매크로를 저장 합니다.

### <a name="example"></a>예제

```cpp
#ifdef _DEBUG
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif

// __FILE__ is one of the six predefined ANSI C macros that the
// compiler recognizes.
```

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="trace"></a><a name="trace"></a> 추적

지정 된 문자열을 현재 응용 프로그램의 디버거로 보냅니다.

```
TRACE(exp)
TRACE(DWORD  category,  UINT  level, LPCSTR lpszFormat, ...)
```

### <a name="remarks"></a>설명

추적에 대 한 설명은 [ATLTRACE2](../../atl/reference/debugging-and-error-reporting-macros.md#atltrace2) 를 참조 하세요. 추적과 ATLTRACE2는 동일한 동작을 포함 합니다.

MFC의 디버그 버전에서이 매크로는 지정 된 문자열을 현재 응용 프로그램의 디버거로 보냅니다. 릴리스 빌드에서는이 매크로가 아무것도 컴파일되지 않습니다 (코드는 전혀 생성 되지 않음).

자세한 내용은 [MFC 응용 프로그램 디버깅](/visualstudio/debugger/mfc-debugging-techniques)을 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="verify"></a><a name="verify"></a> 올바른지

MFC의 디버그 버전에서은 해당 인수를 계산 합니다.

```
VERIFY(booleanExpression)
```

### <a name="parameters"></a>매개 변수

*booleanExpression*<br/>
0이 아닌 값 또는 0으로 계산 되는 식 (포인터 값 포함)을 지정 합니다.

### <a name="remarks"></a>설명

결과가 0 이면 매크로가 진단 메시지를 출력 하 고 프로그램을 중단 합니다. 조건이 0이 아닌 경우 아무 작업도 수행 하지 않습니다.

진단 메시지의 형식은 다음과 같습니다.

`assertion failed in file <name> in line <num>`

여기서 *name* 은 소스 파일의 이름이 고, *num* 은 소스 파일에서 실패 한 어설션의 줄 번호입니다.

MFC의 릴리스 버전에서 확인은 식을 계산 하지만 프로그램을 인쇄 하거나 중단 하지는 않습니다. 예를 들어 식이 함수 호출인 경우 호출이 수행 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#198](../../mfc/codesnippet/cpp/diagnostic-services_7.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxdump-cdumpcontext-in-mfc"></a><a name="cdumpcontext_in_mfc"></a> afxDump (MFC의 CDumpContext)

응용 프로그램에서 기본 개체 덤프 기능을 제공 합니다.

```
CDumpContext  afxDump;
```

### <a name="remarks"></a>설명

`afxDump`는 디버거 출력 창 또는 디버그 터미널에 `CDumpContext` 정보를 보낼 수 있도록 하는 미리 정의 된 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 개체입니다. 일반적으로 `afxDump` 에 대 한 매개 변수로를 제공 `CObject::Dump` 합니다.

Windows NT 및 모든 버전의 Windows에서 `afxDump` 응용 프로그램을 디버그할 때 출력은 Visual C++ Output-Debug 창으로 전송 됩니다.

이 변수는 MFC의 디버그 버전에만 정의 됩니다. 에 대 한 자세한 내용은 `afxDump` [MFC 응용 프로그램 디버깅](/visualstudio/debugger/mfc-debugging-techniques)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#23](../../mfc/codesnippet/cpp/diagnostic-services_8.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxdump-internal"></a><a name="afxdump"></a> AfxDump (내부)

디버깅 하는 동안 MFC에서 개체의 상태를 덤프 하는 데 사용 하는 내부 함수입니다.

### <a name="syntax"></a>구문

```cpp
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>매개 변수

*pOb*<br/>
에서 파생 된 클래스의 개체에 대 한 포인터입니다 `CObject` .

### <a name="remarks"></a>설명

`AfxDump` 개체의 `Dump` 멤버 함수를 호출 하 고 해당 정보를 변수에 의해 지정 된 위치로 보냅니다 `afxDump` . `AfxDump` 는 MFC의 디버그 버전 에서만 사용할 수 있습니다.

프로그램 코드는를 호출 해서는 안 되며 `AfxDump` , 대신 `Dump` 적절 한 개체의 멤버 함수를 호출 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxmemdf"></a><a name="afxmemdf"></a> afxMemDF

이 변수는 디버거 또는 프로그램에서 액세스할 수 있으며 할당 진단을 튜닝할 수 있습니다.

```
int  afxMemDF;
```

### <a name="remarks"></a>설명

`afxMemDF` 는 열거형에 지정 된 대로 다음과 같은 값을 가질 수 있습니다 `afxMemDF` .

- `allocMemDF` 디버깅 할당자 (디버그 라이브러리의 기본 설정)를 설정 합니다.

- `delayFreeMemDF` 메모리가 확보 될 때까지 지연 됩니다. 프로그램에서 메모리 블록을 해제 하는 동안 할당자는 해당 메모리를 기본 운영 체제에 반환 하지 않습니다. 이렇게 하면 프로그램에 최대 메모리 스트레스가 발생 합니다.

- `checkAlwaysMemDF``AfxCheckMemory`메모리를 할당 하거나 해제할 때마다를 호출 합니다. 이렇게 하면 메모리 할당 및 할당 해제가 상당히 느려집니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#30](../../mfc/codesnippet/cpp/diagnostic-services_9.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxcheckerror"></a><a name="afxcheckerror"></a> AfxCheckError

이 함수는 전달 된를 테스트 하 여 오류 인지 여부를 확인 합니다.

```cpp
void AFXAPI AfxCheckError(SCODE sc);
throw CMemoryException*
throw COleException*
```

### <a name="remarks"></a>설명

오류가 발생 하는 경우 함수는 예외를 throw 합니다. 전달 된를 E_OUTOFMEMORY 하는 경우이 함수는 [AfxThrowMemoryException](exception-processing.md#afxthrowmemoryexception)를 호출 하 여 [cmemoryexception](../../mfc/reference/cmemoryexception-class.md) 을 throw 합니다. 그렇지 않으면이 함수는 [AfxThrowOleException](exception-processing.md#afxthrowoleexception)를 호출 하 여 [coleexception](../../mfc/reference/coleexception-class.md) 을 throw 합니다.

이 함수를 사용 하 여 응용 프로그램에서 OLE 함수 호출의 반환 값을 확인할 수 있습니다. 응용 프로그램에서이 함수를 사용 하 여 반환 값을 테스트 하면 최소한의 코드로 오류 조건에 적절 하 게 대응할 수 있습니다.

> [!NOTE]
> 이 함수는 디버그 빌드와 비 디버그 빌드에서 동일한 효과를 가집니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCOleContainer#33](../../mfc/codesnippet/cpp/diagnostic-services_10.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxcheckmemory"></a><a name="afxcheckmemory"></a> AfxCheckMemory

이 함수는 사용 가능한 메모리 풀의 유효성을 검사 하 고 필요에 따라 오류 메시지를 출력 합니다.

```
BOOL  AfxCheckMemory();
```

### <a name="return-value"></a>반환 값

메모리 오류가 없으면 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

함수가 메모리 손상을 발견 하지 못하면 아무것도 출력 하지 않습니다.

에 의해 할당 된 모든 메모리 블록을 포함 하 여 현재 힙에 할당 된 모든 메모리 블록을 검사 하 고, **`new`** **malloc** 함수 또는 Windows 함수와 같은 기본 메모리 할당자에 대 한 직접 호출로 할당 된 블록을 포함 하지 않습니다 `GlobalAlloc` . 손상 된 블록이 발견 되 면 디버거 출력에 메시지가 출력 됩니다.

줄을 포함 하는 경우

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/diagnostic-services_1.cpp)]

프로그램 모듈에서 후속 호출은 `AfxCheckMemory` 메모리가 할당 된 파일 이름과 줄 번호를 표시 합니다.

> [!NOTE]
> 모듈에 serialize 할 수 있는 클래스의 구현이 하나 이상 포함 되어 있는 경우 `#define` 마지막 IMPLEMENT_SERIAL 매크로 호출 뒤에 줄을 삽입 해야 합니다.

이 함수는 MFC의 디버그 버전 에서만 작동 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#26](../../mfc/codesnippet/cpp/diagnostic-services_11.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxdump-mfc"></a><a name="afxdump"></a> AfxDump (MFC)

디버깅 하는 동안 개체의 상태를 덤프 하는 동안 디버거에서이 함수를 호출 합니다.

```cpp
void AfxDump(const CObject* pOb);
```

### <a name="parameters"></a>매개 변수

*pOb*<br/>
에서 파생 된 클래스의 개체에 대 한 포인터입니다 `CObject` .

### <a name="remarks"></a>설명

`AfxDump` 개체의 `Dump` 멤버 함수를 호출 하 고 해당 정보를 변수에 의해 지정 된 위치로 보냅니다 `afxDump` . `AfxDump` 는 MFC의 디버그 버전 에서만 사용할 수 있습니다.

프로그램 코드는를 호출 해서는 안 되며 `AfxDump` , 대신 `Dump` 적절 한 개체의 멤버 함수를 호출 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxdumpstack"></a><a name="afxdumpstack"></a> AfxDumpStack

이 전역 함수는 현재 스택의 이미지를 생성 하는 데 사용할 수 있습니다.

```cpp
void AFXAPI AfxDumpStack(DWORD dwTarget = AFX_STACK_DUMP_TARGET_DEFAULT);
```

### <a name="parameters"></a>매개 변수

*dwTarget*<br/>
덤프 출력의 대상을 나타냅니다. 비트 or ( **&#124;**) 연산자를 사용 하 여 결합할 수 있는 가능한 값은 다음과 같습니다.

- AFX_STACK_DUMP_TARGET_TRACE는 [추적](#trace) 매크로를 통해 출력을 보냅니다. TRACE 매크로는 디버그 빌드에서만 출력을 생성 합니다. 릴리스 빌드에서 출력을 생성 하지 않습니다. 또한 추적을 디버거 외의 다른 대상으로 리디렉션할 수 있습니다.

- AFX_STACK_DUMP_TARGET_DEFAULT는 덤프 출력을 기본 대상으로 보냅니다. 디버그 빌드의 경우 output은 TRACE 매크로로 이동 합니다. 릴리스 빌드에서 출력이 클립보드로 이동 합니다.

- AFX_STACK_DUMP_TARGET_CLIPBOARD 출력을 클립보드로만 보냅니다. 데이터는 클립보드에 CF_TEXT 클립보드 형식을 사용 하 여 일반 텍스트로 저장 됩니다.

- AFX_STACK_DUMP_TARGET_BOTH은 출력을 클립보드와 추적 매크로에 동시에 보냅니다.

- AFX_STACK_DUMP_TARGET_ODS는 Win32 함수를 통해 출력을 디버거로 직접 보냅니다 `OutputDebugString()` . 이 옵션은 디버거가 프로세스에 연결 될 때 디버그 빌드와 릴리스 빌드에서 디버거 출력을 생성 합니다. AFX_STACK_DUMP_TARGET_ODS 항상 디버거 (연결 된 경우)에 도달 하 여 리디렉션할 수 없습니다.

### <a name="remarks"></a>설명

아래 예제에서는 `AfxDumpStack` MFC 대화 상자 응용 프로그램의 단추 처리기에서를 호출 하 여 생성 된 출력의 한 줄을 반영 합니다.

```Output
=== begin AfxDumpStack output ===
00427D55: DUMP2\DEBUG\DUMP2.EXE! void AfxDumpStack(unsigned long) + 181 bytes
0040160B: DUMP2\DEBUG\DUMP2.EXE! void CDump2Dlg::OnClipboard(void) + 14 bytes
0044F884: DUMP2\DEBUG\DUMP2.EXE! int _AfxDispatchCmdMsg(class CCmdTarget *,
unsigned int,int,void ( CCmdTarget::*)(void),void *,unsigned int,struct
AFX_CMDHANDLE
0044FF7B: DUMP2\DEBUG\DUMP2.EXE! virtual int CCmdTarget::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 626 bytes
00450C71: DUMP2\DEBUG\DUMP2.EXE! virtual int CDialog::OnCmdMsg(unsigned
int,int,void *,struct AFX_CMDHANDLERINFO *) + 36 bytes
00455B27: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnCommand(unsigned
int,long) + 312 bytes
00454D3D: DUMP2\DEBUG\DUMP2.EXE! virtual int CWnd::OnWndMsg(unsigned
int,unsigned int,long,long *) + 83 bytes
00454CC0: DUMP2\DEBUG\DUMP2.EXE! virtual long CWnd::WindowProc(unsigned
int,unsigned int,long) + 46 bytes
004528D9: DUMP2\DEBUG\DUMP2.EXE! long AfxCallWndProc(class CWnd *,struct
HWND__ *,unsigned int,unsigned int,long) + 237 bytes
00452D34: DUMP2\DEBUG\DUMP2.EXE! long AfxWndProc(struct HWND__ *,unsigned
int,unsigned int,long) + 129 bytes
BFF73663: WINDOWS\SYSTEM\KERNEL32.DLL! ThunkConnect32 + 2148 bytes
BFF928E0: WINDOWS\SYSTEM\KERNEL32.DLL! UTUnRegister + 2492 bytes
=== end AfxDumpStack() output ===
```

위의 출력에서 각 줄은 마지막 함수 호출의 주소, 함수 호출이 포함 된 모듈의 전체 경로 이름 및 호출 된 함수 프로토타입을 나타냅니다. 스택의 함수 호출이 정확한 함수 주소에서 발생 하지 않는 경우 바이트의 오프셋이 표시 됩니다.

예를 들어 다음 표에서는 위의 출력의 첫 번째 줄을 설명 합니다.

|출력|Description|
|------------|-----------------|
|`00427D55:`|마지막 함수 호출의 반환 주소입니다.|
|`DUMP2\DEBUG\DUMP2.EXE!`|함수 호출이 포함 된 모듈의 전체 경로 이름입니다.|
|`void AfxDumpStack(unsigned long)`|호출 된 함수 프로토타입입니다.|
|`+ 181 bytes`|함수 프로토타입 주소 (이 경우 `void AfxDumpStack(unsigned long)` )에서 반환 주소 (이 경우) 까지의 오프셋 (바이트 `00427D55` )입니다.|

`AfxDumpStack` 는 MFC 라이브러리의 디버그 및 nondebug 버전에서 사용할 수 있습니다. 그러나 실행 파일이 공유 DLL에서 MFC를 사용 하는 경우에도 함수는 항상 정적으로 연결 됩니다. 공유 라이브러리 구현에서 함수는 MFCS42에서 찾을 수 있습니다. LIB 라이브러리 및 해당 변형

이 함수를 성공적으로 사용 하려면 다음을 수행 합니다.

- 파일 IMAGEHLP.DLL는 경로에 있어야 합니다. 이 DLL이 없으면 함수는 오류 메시지를 표시 합니다. 데 필요한 IMAGEHLP.DLL에서 제공 하는 함수 집합에 대 한 자세한 내용은 [이미지 도움말 라이브러리](/windows/win32/Debug/image-help-library) 를 참조 하세요.

- 스택에 프레임이 있는 모듈에는 디버깅 정보가 포함 되어야 합니다. 디버깅 정보가 포함 되어 있지 않은 경우 함수는 스택 추적을 생성 하지만 추적은 더 자세히 설명 하지 않습니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxenablememoryleakdump"></a><a name="afxenablememoryleakdump"></a> AfxEnableMemoryLeakDump

AFX_DEBUG_STATE 소멸자에서 메모리 누수 덤프를 사용 하거나 사용 하지 않도록 설정 합니다.

```
BOOL AFXAPI AfxEnableMemoryLeakDump(BOOL bDump);
```

### <a name="parameters"></a>매개 변수

*bDump*<br/>
진행 TRUE는 메모리 누수 덤프가 사용 됨을 나타냅니다. FALSE는 메모리 누수 덤프가 사용 되지 않음을 나타냅니다.

### <a name="return-value"></a>반환 값

이 플래그에 대한 이전 값입니다.

### <a name="remarks"></a>설명

애플리케이션이 MFC 라이브러리를 언로드하면 MFC 라이브러리는 메모리 누수를 확인합니다. 이 시점에서 Visual Studio의 **디버그** 창을 통해 모든 메모리 누수가 사용자에 게 보고 됩니다.

애플리케이션이 MFC 라이브러리 전에 다른 라이브러리를 로드하는 경우, 해당 라이브러리의 일부 메모리 할당이 메모리 누수로 잘못 보고됩니다. 거짓 메모리 누수가 발생하면 MFC 라이브러리에서 이를 보고하므로 애플리케이션이 느리게 종료될 수 있습니다. 이 경우 메모리 누수 덤프를 사용하지 않으려면 `AfxEnableMemoryLeakDump` 를 사용합니다.

> [!NOTE]
> 이 방법을 사용하여 메모리 누수 덤프를 끄는 경우, 애플리케이션에서 발생하는 유효한 메모리 누수의 보고서를 받지 못합니다. 메모리 누수 보고서에 거짓 메모리 누수가 포함되어 있다고 확신하는 경우에만 이 방법을 사용해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxenablememorytracking"></a><a name="afxenablememorytracking"></a> AfxEnableMemoryTracking

진단 메모리 추적은 일반적으로 MFC의 디버그 버전에서 사용 하도록 설정 됩니다.

```
BOOL AfxEnableMemoryTracking(BOOL bTrack);
```

### <a name="parameters"></a>매개 변수

*bTrack*<br/>
이 값을 TRUE로 설정 하면 메모리 추적이 설정 됩니다. FALSE로 설정 합니다.

### <a name="return-value"></a>반환 값

추적-사용 플래그의 이전 설정입니다.

### <a name="remarks"></a>설명

블록을 올바르게 할당 하는 코드 섹션에서 추적을 사용 하지 않도록 설정 하려면이 함수를 사용 합니다.

에 대 한 자세한 내용은 `AfxEnableMemoryTracking` [MFC 응용 프로그램 디버깅](/visualstudio/debugger/mfc-debugging-techniques)을 참조 하세요.

> [!NOTE]
> 이 함수는 MFC의 디버그 버전 에서만 작동 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#24](../../mfc/codesnippet/cpp/diagnostic-services_12.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxismemoryblock"></a><a name="afxismemoryblock"></a> AfxIsMemoryBlock

메모리 주소를 테스트 하 여의 진단 버전에 의해 할당 된 현재 활성 메모리 블록을 나타내는지 확인 **`new`** 합니다.

```
BOOL AfxIsMemoryBlock(
    const void* p,
    UINT nBytes,
    LONG* plRequestNumber = NULL);
```

### <a name="parameters"></a>매개 변수

*®*<br/>
테스트할 메모리 블록을 가리킵니다.

*nBytes*<br/>
메모리 블록의 길이 (바이트)를 포함 합니다.

*plRequestNumber*<br/>
는 **`long`** 메모리 블록의 할당 시퀀스 번호를 사용 하 여 채워질 정수를 가리키거나, 현재 활성 메모리 블록을 나타내지 않는 경우 0을 반환 합니다.

### <a name="return-value"></a>반환 값

메모리 블록이 현재 할당 되어 있고 길이가 올바른 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

또한 지정 된 크기를 원래 할당 된 크기와 비교 하 여 확인 합니다. 함수가 0이 아닌 값을 반환 하는 경우 할당 시퀀스 번호는 *Plrequestnumber* 로 반환 됩니다. 이 숫자는 다른 모든 할당을 기준으로 블록이 할당 된 순서를 나타냅니다 **`new`** .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#27](../../mfc/codesnippet/cpp/diagnostic-services_13.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxisvalidaddress"></a><a name="afxisvalidaddress"></a> AfxIsValidAddress

모든 메모리 주소가 프로그램의 메모리 공간 내에 완전히 포함 되는지 테스트 합니다.

```
BOOL AfxIsValidAddress(
    const void* lp,
    UINT nBytes,
    BOOL bReadWrite = TRUE);
```

### <a name="parameters"></a>매개 변수

*lp*<br/>
테스트할 메모리 주소를 가리킵니다.

*nBytes*<br/>
테스트할 메모리의 바이트 수를 포함 합니다.

*bReadWrite*<br/>
메모리의 읽기 및 쓰기 (TRUE) 또는 읽기 (FALSE)를 모두 수행할지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

디버그 빌드에서 지정 된 메모리 블록이 프로그램의 메모리 공간 내에 완전히 포함 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

디버그가 아닌 빌드에서는 *lp* 가 NULL이 아닌 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

주소는에 의해 할당 된 블록으로 제한 되지 않습니다 **`new`** .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#28](../../mfc/codesnippet/cpp/diagnostic-services_14.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxisvalidstring"></a><a name="afxisvalidstring"></a> AfxIsValidString

이 함수를 사용 하 여 문자열에 대 한 포인터가 유효한 지 여부를 확인 합니다.

```
BOOL  AfxIsValidString(
    LPCSTR lpsz,
    int nLength = -1);
```

### <a name="parameters"></a>매개 변수

*lpsz*<br/>
테스트할 포인터입니다.

*nLength*<br/>
테스트할 문자열의 길이 (바이트)를 지정 합니다. 값-1은 문자열이 null로 종료 됨을 나타냅니다.

### <a name="return-value"></a>반환 값

디버그 빌드에서 지정 된 포인터가 지정 된 크기의 문자열을 가리키는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

비 디버그 빌드에서 *lpsz* 가 NULL이 아닌 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#29](../../mfc/codesnippet/cpp/diagnostic-services_15.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxsetallochook"></a><a name="afxsetallochook"></a> AfxSetAllocHook

각 메모리 블록을 할당 하기 전에 지정 된 함수를 호출할 수 있도록 하는 후크를 설정 합니다.

```
AFX_ALLOC_HOOK AfxSetAllocHook(AFX_ALLOC_HOOK pfnAllocHook);
```

### <a name="parameters"></a>매개 변수

*pfnAllocHook*<br/>
호출할 함수의 이름을 지정 합니다. 할당 함수의 프로토타입에 대 한 설명을 참조 하십시오.

### <a name="return-value"></a>반환 값

할당을 허용 하려는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

MFC 라이브러리 디버그 메모리 할당자는 사용자 정의 후크 함수를 호출 하 여 사용자가 메모리 할당을 모니터링 하 고 할당이 허용 되는지 여부를 제어할 수 있습니다. 할당 후크 함수는 다음과 같이 프로토타입화 됩니다.

**BOOL AFXAPI AllocHook( size_t** `nSize`**, BOOL** `bObject`**, LONG** `lRequestNumber` **);**

*nSize*<br/>
제안 된 메모리 할당의 크기입니다.

*bObject*<br/>
파생 개체에 대 한 할당이 면 TRUE `CObject` 이 고, 그렇지 않으면 FALSE입니다.

*lRequestNumber*<br/>
메모리 할당의 시퀀스 번호입니다.

AFXAPI 호출 규칙은 호출 수신자가 스택에서 매개 변수를 제거 해야 함을 의미 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxdoforallclasses"></a><a name="afxdoforallclasses"></a> AfxDoForAllClasses

`CObject`응용 프로그램의 메모리 공간에서 serialize 할 수 있는 모든 파생 클래스에 대해 지정 된 반복 함수를 호출 합니다.

```cpp
void
AFXAPI AfxDoForAllClasses(
    void (* pfn)(const CRuntimeClass* pClass, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>매개 변수

*pfn*<br/>
각 클래스에 대해 호출할 반복 함수를 가리킵니다. 함수 인수는 개체에 대 한 포인터 `CRuntimeClass` 이며 호출자가 함수에 제공 하는 추가 데이터에 대 한 void 포인터입니다.

*pContext*<br/>
호출자가 반복 함수에 제공할 수 있는 선택적 데이터를 가리킵니다. 이 포인터는 NULL 일 수 있습니다.

### <a name="remarks"></a>설명

Serializable `CObject` 파생 클래스는 DECLARE_SERIAL 매크로를 사용 하 여 파생 된 클래스입니다. PContext에서에 전달 되는 포인터는 `AfxDoForAllClasses` 호출 될 때마다 지정 된 반복 함수에 전달 됩니다. 

> [!NOTE]
> 이 함수는 MFC의 디버그 버전 에서만 작동 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#113](../../mfc/codesnippet/cpp/diagnostic-services_16.cpp)]

[!code-cpp[NVC_MFCCollections#114](../../mfc/codesnippet/cpp/diagnostic-services_17.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="afxdoforallobjects"></a><a name="afxdoforallobjects"></a> AfxDoForAllObjects

로 할당 된에서 파생 된 모든 개체에 대해 지정 된 반복 함수를 실행 `CObject` **`new`** 합니다.

```cpp
void AfxDoForAllObjects(
    void (* pfn)(CObject* pObject, void* pContext),
    void* pContext);
```

### <a name="parameters"></a>매개 변수

*pfn*<br/>
각 개체에 대해 실행할 반복 함수를 가리킵니다. 함수 인수는에 대 한 포인터 `CObject` 이며 호출자가 함수에 제공 하는 추가 데이터에 대 한 void 포인터입니다.

*pContext*<br/>
호출자가 반복 함수에 제공할 수 있는 선택적 데이터를 가리킵니다. 이 포인터는 NULL 일 수 있습니다.

### <a name="remarks"></a>설명

스택, 전역 또는 포함 된 개체는 열거 되지 않습니다. PContext에서에 전달 된 포인터는 호출 될 때마다 `AfxDoForAllObjects` 지정 된 반복 함수에 전달 됩니다. 

> [!NOTE]
> 이 함수는 MFC의 디버그 버전 에서만 작동 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCollections#115](../../mfc/codesnippet/cpp/diagnostic-services_18.cpp)]

[!code-cpp[NVC_MFCCollections#116](../../mfc/codesnippet/cpp/diagnostic-services_19.cpp)]

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[CObject::Dump](cobject-class.md#dump)
