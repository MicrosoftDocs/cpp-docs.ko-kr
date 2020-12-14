---
description: '자세한 정보: 개체 모델 서비스 Run-Time'
title: 런타임 개체 모델 서비스
ms.date: 03/27/2019
helpviewer_keywords:
- run-time object model services macros
ms.assetid: 4a3e79df-2ee3-43a4-8193-20298828de85
ms.openlocfilehash: 5457b34b13d53a6fbf76a74b893958b03b1d63de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218890"
---
# <a name="run-time-object-model-services"></a>런타임 개체 모델 서비스

[CObject](../../mfc/reference/cobject-class.md) 및 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 클래스는 런타임 클래스 정보, serialization 및 동적 개체 만들기에 대 한 액세스를 포함 하 여 몇 가지 개체 서비스를 캡슐화 합니다. 에서 파생 된 모든 클래스는 `CObject` 이 기능을 상속 합니다.

런타임 클래스 정보에 액세스 하면 런타임에 개체의 클래스에 대 한 정보를 확인할 수 있습니다. 런타임에 개체의 클래스를 확인 하는 기능은 함수 인수에 대 한 추가 형식 검사가 필요 하 고, 개체의 클래스를 기반으로 특수 용도의 코드를 작성 해야 하는 경우에 유용 합니다. 런타임 클래스 정보는 c + + 언어에서 직접 지원 되지 않습니다.

Serialization은 개체의 콘텐츠를 파일에서 읽거나 쓰는 프로세스입니다. 응용 프로그램이 종료 된 후에도 serialization을 사용 하 여 개체의 내용을 저장할 수 있습니다. 그런 다음 응용 프로그램을 다시 시작할 때 파일에서 개체를 읽을 수 있습니다. 이러한 데이터 개체는 "영구적" 이라고 합니다.

동적 개체 만들기를 사용 하면 런타임에 지정 된 클래스의 개체를 만들 수 있습니다. 예를 들어 프레임 워크는 동적으로 만들어야 하므로 문서, 뷰 및 프레임 개체는 동적 생성을 지원 해야 합니다.

다음 표에서는 런타임 클래스 정보, serialization 및 동적 생성을 지 원하는 MFC 매크로를 보여 줍니다.

이러한 런타임 개체 서비스 및 serialization에 대 한 자세한 내용은 [CObject 클래스: Run-Time 클래스 정보 액세스](../../mfc/accessing-run-time-class-information.md)문서를 참조 하세요.

### <a name="run-time-object-model-services-macros"></a>Run-Time 개체 모델 서비스 매크로

|Name|설명|
|-|-|
|[DECLARE_DYNAMIC](#declare_dynamic)|런타임 클래스 정보에 액세스할 수 있도록 합니다 (클래스 선언에서 사용 되어야 함).|
|[DECLARE_DYNCREATE](#declare_dyncreate)|동적으로 만들고 런타임 클래스 정보에 액세스할 수 있도록 합니다 (클래스 선언에서 사용 되어야 함).|
|[DECLARE_SERIAL](#declare_serial)|Serialization 및 런타임 클래스 정보에 액세스할 수 있도록 합니다 (클래스 선언에서 사용 되어야 함).|
|[IMPLEMENT_DYNAMIC](#implement_dynamic)|런타임 클래스 정보에 액세스할 수 있도록 합니다 (클래스 구현에 사용 되어야 함).|
|[IMPLEMENT_DYNCREATE](#implement_dyncreate)|동적으로 만들고 런타임 정보에 액세스할 수 있도록 합니다 (클래스 구현에 사용 되어야 함).|
|[IMPLEMENT_SERIAL](#implement_serial)|Serialization 및 런타임 클래스 정보에 대 한 액세스를 허용 합니다 (클래스 구현에 사용 되어야 함).|
|[RUNTIME_CLASS](#runtime_class)|명명 된 `CRuntimeClass` 클래스에 해당 하는 구조체를 반환 합니다.|

OLE에서는 런타임에 개체를 동적으로 만들어야 하는 경우가 많습니다. 예를 들어 OLE 서버 응용 프로그램은 클라이언트의 요청에 대 한 응답으로 OLE 항목을 동적으로 만들 수 있어야 합니다. 마찬가지로 automation 서버는 자동화 클라이언트의 요청에 대 한 응답으로 항목을 만들 수 있어야 합니다.

MFC 라이브러리는 OLE와 관련 된 두 개의 매크로를 제공 합니다.

### <a name="dynamic-creation-of-ole-objects"></a>OLE 개체의 동적 생성

|Name|설명|
|-|-|
|[AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)|공용 컨트롤 라이브러리가 지정 된 API를 구현 하는지 여부를 확인 합니다.|
|[AFX_COMCTL32_IF_EXISTS2](#afx_comctl32_if_exists2)|공용 컨트롤 라이브러리가 지정 된 API를 구현 하는지 여부를 확인 합니다.|
|[DECLARE_OLECREATE](#declare_olecreate)|OLE 자동화를 통해 개체를 만들 수 있습니다.|
|[DECLARE_OLECTLTYPE](#declare_olectltype)|`GetUserTypeNameID` `GetMiscStatus` 컨트롤 클래스의 및 멤버 함수를 선언 합니다.|
|[DECLARE_PROPPAGEIDS](#declare_proppageids)|OLE 컨트롤이 속성 페이지 목록을 제공 하 여 속성을 표시 하도록 선언 합니다.|
|[IMPLEMENT_OLECREATE](#implement_olecreate)|OLE 시스템에서 개체를 만들 수 있도록 합니다.|
|[IMPLEMENT_OLECTLTYPE](#implement_olectltype)|`GetUserTypeNameID` `GetMiscStatus` 컨트롤 클래스의 및 멤버 함수를 구현 합니다.|
|[IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags)|이 매크로나 [IMPLEMENT_OLECREATE](#implement_olecreate) 은를 사용 하는 모든 클래스에 대 한 구현 파일에 표시 되어야 합니다 `DECLARE_OLECREATE` . |

## <a name="afx_comctl32_if_exists"></a><a name="afx_comctl32_if_exists"></a> AFX_COMCTL32_IF_EXISTS

공용 컨트롤 라이브러리가 지정 된 API를 구현 하는지 여부를 확인 합니다.

### <a name="syntax"></a>구문

```
AFX_COMCTL32_IF_EXISTS(  proc );
```

### <a name="parameters"></a>매개 변수

*proc*<br/>
함수 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터 이거나 함수의 서 수 값을 지정 합니다. 이 매개 변수가 서 수 값 이면 하위 단어 여야 합니다. 상위 단어는 0 이어야 합니다. 이 매개 변수는 유니코드 여야 합니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 공용 컨트롤이 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)를 호출 하는 대신 *proc* 에서 지정한 함수를 사용 하는지 여부를 확인 합니다.

### <a name="requirements"></a>요구 사항

afxcomctl32.h, afxcomctl32.h

## <a name="afx_comctl32_if_exists2"></a><a name="afx_comctl32_if_exists2"></a> AFX_COMCTL32_IF_EXISTS2

공용 컨트롤 라이브러리가 지정 된 API를 구현 하는지 여부를 확인 합니다 ( [AFX_COMCTL32_IF_EXISTS](#afx_comctl32_if_exists)의 유니코드 버전).

### <a name="syntax"></a>구문

```
AFX_COMCTL32_IF_EXISTS2( proc );
```

### <a name="parameters"></a>매개 변수

*proc*<br/>
함수 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터 이거나 함수의 서 수 값을 지정 합니다. 이 매개 변수가 서 수 값 이면 하위 단어 여야 합니다. 상위 단어는 0 이어야 합니다. 이 매개 변수는 유니코드 여야 합니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 공용 컨트롤이 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)를 호출 하는 대신 *proc* 에서 지정한 함수를 사용 하는지 여부를 확인 합니다. 이 매크로는 AFX_COMCTL32_IF_EXISTS의 유니코드 버전입니다.

### <a name="requirements"></a>요구 사항

afxcomctl32.h, afxcomctl32.h

## <a name="declare_dynamic"></a><a name="declare_dynamic"></a> DECLARE_DYNAMIC

에서 클래스를 파생 시킬 때 개체의 클래스에 대 한 런타임 정보에 액세스 하는 기능을 추가 `CObject` 합니다.

```
DECLARE_DYNAMIC(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

### <a name="remarks"></a>설명

클래스에 대 한 헤더 (.h) 모듈에 DECLARE_DYNAMIC 매크로를 추가 하 고이 클래스의 개체에 액세스 해야 하는 모든 .cpp 모듈에 해당 모듈을 포함 합니다.

설명 된 대로 DECLARE_ 동적 및 IMPLEMENT_DYNAMIC 매크로를 사용 하는 경우 RUNTIME_CLASS 매크로와 함수를 사용 하 여 `CObject::IsKindOf` 런타임에 개체의 클래스를 확인할 수 있습니다.

클래스 선언에 DECLARE_DYNAMIC 포함 된 경우 IMPLEMENT_DYNAMIC 클래스 구현에 포함 되어야 합니다.

DECLARE_DYNAMIC 매크로에 대 한 자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

### <a name="example"></a>예제

[IMPLEMENT_DYNAMIC](#implement_dynamic)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="declare_dyncreate"></a><a name="declare_dyncreate"></a> DECLARE_DYNCREATE

`CObject`파생 클래스의 개체를 런타임에 동적으로 만들 수 있도록 합니다.

```
DECLARE_DYNCREATE(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

### <a name="remarks"></a>설명

프레임 워크에서는이 기능을 사용 하 여 새 개체를 동적으로 만듭니다. 예를 들어 새 문서를 열 때 생성 되는 새 뷰입니다. 프레임 워크는 동적으로 만들어야 하므로 문서, 뷰 및 프레임 클래스는 동적 생성을 지원 해야 합니다.

클래스에 대 한 .h 모듈에 DECLARE_DYNCREATE 매크로를 추가 하 고이 클래스의 개체에 액세스 해야 하는 모든 .cpp 모듈에 해당 모듈을 포함 합니다.

클래스 선언에 DECLARE_DYNCREATE 포함 된 경우 IMPLEMENT_DYNCREATE 클래스 구현에 포함 되어야 합니다.

DECLARE_DYNCREATE 매크로에 대 한 자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

> [!NOTE]
> DECLARE_DYNCREATE 매크로에는 DECLARE_DYNAMIC의 모든 기능이 포함 되어 있습니다.

### <a name="example"></a>예제

[IMPLEMENT_DYNCREATE](#implement_dyncreate)의 예제를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="declare_olectltype"></a><a name="declare_olectltype"></a> DECLARE_OLECTLTYPE

`GetUserTypeNameID` `GetMiscStatus` 컨트롤 클래스의 및 멤버 함수를 선언 합니다.

### <a name="syntax"></a>구문

```
DECLARE_OLECTLTYPE( class_name )
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
컨트롤 클래스의 이름입니다.

### <a name="remarks"></a>설명

`GetUserTypeNameID` 및 `GetMiscStatus` 는에 선언 된 순수 가상 함수 `COleControl` 입니다. 이러한 함수는 순수 가상 함수 이므로 컨트롤 클래스에서 재정의 해야 합니다. DECLARE_OLECTLTYPE 외에도 IMPLEMENT_OLECTLTYPE 매크로를 컨트롤 클래스 선언에 추가 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="declare_proppageids"></a><a name="declare_proppageids"></a> DECLARE_PROPPAGEIDS

OLE 컨트롤이 속성 페이지 목록을 제공 하 여 속성을 표시 하도록 선언 합니다.

### <a name="syntax"></a>구문

```
DECLARE_PROPPAGEIDS( class_name )
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
속성 페이지를 소유 하는 컨트롤 클래스의 이름입니다.

### <a name="remarks"></a>설명

`DECLARE_PROPPAGEIDS`클래스 선언 끝에서 매크로를 사용 합니다. 그런 다음 클래스의 멤버 함수를 정의 하는 .cpp 파일에서 `BEGIN_PROPPAGEIDS` 매크로, 각 컨트롤의 속성 페이지에 대 한 매크로 항목, 매크로를 사용 `END_PROPPAGEIDS` 하 여 속성 페이지 목록의 끝을 선언 합니다.

속성 페이지에 대 한 자세한 내용은 [ActiveX 컨트롤: 속성 페이지](../mfc-activex-controls-property-pages.md)를 참조 하세요.

### <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="declare_serial"></a><a name="declare_serial"></a> DECLARE_SERIAL

Serialize 할 수 있는 파생 클래스에 필요한 c + + 헤더 코드를 생성 `CObject` 합니다.

```
DECLARE_SERIAL(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

### <a name="remarks"></a>설명

Serialization은 파일에 대 한 개체의 콘텐츠를 쓰거나 읽는 프로세스입니다.

.H 모듈의 DECLARE_SERIAL 매크로를 사용 하 고이 클래스의 개체에 액세스 해야 하는 모든 .cpp 모듈에 해당 모듈을 포함 합니다.

클래스 선언에 DECLARE_SERIAL 포함 된 경우 IMPLEMENT_SERIAL 클래스 구현에 포함 되어야 합니다.

DECLARE_SERIAL 매크로에는 DECLARE_DYNAMIC 및 DECLARE_DYNCREATE의 모든 기능이 포함 되어 있습니다.

AFX_API 매크로를 사용 하 여 `CArchive` DECLARE_SERIAL 및 IMPLEMENT_SERIAL 매크로를 사용 하는 클래스에 대 한 추출 연산자를 자동으로 내보낼 수 있습니다. 다음 코드를 사용 하 여 클래스 선언 (.h 파일에 있음)을 묶습니다.

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

DECLARE_SERIAL 매크로에 대 한 자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#21](../../mfc/codesnippet/cpp/run-time-object-model-services_2.h)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="implement_dynamic"></a><a name="implement_dynamic"></a> IMPLEMENT_DYNAMIC

`CObject`계층 내에서 클래스 이름 및 위치에 대 한 런타임 액세스 권한이 있는 동적 파생 클래스에 필요한 c + + 코드를 생성 합니다.

```
IMPLEMENT_DYNAMIC(class_name, base_class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

*base_class_name*<br/>
기본 클래스의 이름입니다.

### <a name="remarks"></a>설명

.Cpp 모듈의 IMPLEMENT_DYNAMIC 매크로를 사용 하 여 결과 개체 코드를 한 번만 연결 합니다.

자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#2](../../mfc/codesnippet/cpp/run-time-object-model-services_3.h)]

[!code-cpp[NVC_MFCCObjectSample#3](../../mfc/codesnippet/cpp/run-time-object-model-services_4.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="implement_dyncreate"></a><a name="implement_dyncreate"></a> IMPLEMENT_DYNCREATE

`CObject`DECLARE_DYNCREATE 매크로와 함께 사용 하는 경우 파생 클래스의 개체를 런타임에 동적으로 만들 수 있도록 합니다.

```
IMPLEMENT_DYNCREATE(class_name, base_class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

*base_class_name*<br/>
기본 클래스의 실제 이름입니다.

### <a name="remarks"></a>설명

프레임 워크는이 기능을 사용 하 여 serialization 중에 디스크에서 개체를 읽을 때와 같이 새 개체를 동적으로 만듭니다. 클래스 구현 파일에 IMPLEMENT_DYNCREATE 매크로를 추가 합니다. 자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

DECLARE_DYNCREATE 및 IMPLEMENT_DYNCREATE 매크로를 사용 하는 경우 런타임에 RUNTIME_CLASS 매크로와 `CObject::IsKindOf` 멤버 함수를 사용 하 여 개체의 클래스를 확인할 수 있습니다.

클래스 선언에 DECLARE_DYNCREATE 포함 된 경우 IMPLEMENT_DYNCREATE 클래스 구현에 포함 되어야 합니다.

이 매크로 정의는 클래스에 대 한 기본 생성자를 호출 합니다. 특수 생성자를 클래스에서 명시적으로 구현 하는 경우 기본 생성자도 명시적으로 구현 해야 합니다. 클래스의 또는 멤버 섹션에 기본 생성자를 추가 하 여 **`private`** **`protected`** 클래스 구현 외부에서 호출 되는 것을 방지할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#22](../../mfc/codesnippet/cpp/run-time-object-model-services_5.h)]

[!code-cpp[NVC_MFCCObjectSample#23](../../mfc/codesnippet/cpp/run-time-object-model-services_6.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="implement_olecreate_flags"></a><a name="implement_olecreate_flags"></a> IMPLEMENT_OLECREATE_FLAGS

이 매크로나 [IMPLEMENT_OLECREATE](#implement_olecreate) 은 DECLARE_OLECREATE를 사용 하는 모든 클래스에 대 한 구현 파일에 표시 되어야 합니다.

### <a name="syntax"></a>구문

```
IMPLEMENT_OLECREATE_FLAGS( class_name, external_name, nFlags,
    l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

*external_name*<br/>
다른 응용 프로그램에 노출 되는 개체 이름입니다 (따옴표로 묶).

*nFlags*<br/>
다음 플래그 중 하나 이상을 포함 합니다.

- `afxRegInsertable` OLE 개체에 대 한 개체 삽입 대화 상자에 컨트롤을 표시할 수 있습니다.
- `afxRegApartmentThreading` 레지스트리의 스레딩 모델을 ThreadingModel = 아파트로 설정 합니다.
- `afxRegFreeThreading` 레지스트리의 스레딩 모델을 ThreadingModel = Free로 설정 합니다.

두 플래그를 결합 하 `afxRegApartmentThreading` 고 `afxRegFreeThreading` ThreadingModel =를 설정할 수 있습니다. 스레딩 모델 등록에 대 한 자세한 내용은 Windows SDK의 [InprocServer32](/windows/win32/com/inprocserver32) 를 참조 하세요.

클래스 CLSID의 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* 구성 요소입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> IMPLEMENT_OLECREATE_FLAGS 사용 하는 경우 *Nflags* 매개 변수를 사용 하 여 개체에서 지 원하는 스레딩 모델을 지정할 수 있습니다. 단일 treading 모델만 지원 하려면 IMPLEMENT_OLECREATE을 사용 합니다.

외부 이름은 다른 응용 프로그램에 노출 되는 식별자입니다. 클라이언트 응용 프로그램은 외부 이름을 사용 하 여 자동화 서버에서이 클래스의 개체를 요청 합니다.

OLE 클래스 ID는 개체의 고유한 128 비트 식별자입니다. 이는 **`long`** 구문 설명에서 *l*, *w1*, *w2* 및 *b1* 에서 *b8* 로 표시 되는 1, 2 개의 **단어** 및 8 **바이트** s로 구성 됩니다. 응용 프로그램 마법사 및 코드 마법사는 필요에 따라 고유한 OLE 클래스 Id를 만듭니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="implement_olectltype"></a><a name="implement_olectltype"></a> IMPLEMENT_OLECTLTYPE

`GetUserTypeNameID` `GetMiscStatus` 컨트롤 클래스의 및 멤버 함수를 구현 합니다.

### <a name="syntax"></a>구문

```
DECLARE_OLECTLTYPE( class_name, idsUserTypeName, dwOleMisc )
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
컨트롤 클래스의 이름입니다.

*idsUserTypeName*<br/>
컨트롤의 외부 이름을 포함 하는 문자열의 리소스 ID입니다.

*dwOleMisc*<br/>
하나 이상의 플래그를 포함 하는 열거형입니다. 이 열거형에 대 한 자세한 내용은 Windows SDK의 [Olemisc](/windows/win32/api/oleidl/ne-oleidl-olemisc) 를 참조 하십시오.

### <a name="remarks"></a>설명

IMPLEMENT_OLECTLTYPE 외에도 DECLARE_OLECTLTYPE 매크로를 컨트롤 클래스 선언에 추가 해야 합니다.

`GetUserTypeNameID`멤버 함수는 컨트롤 클래스를 식별 하는 리소스 문자열을 반환 합니다. `GetMiscStatus` 컨트롤에 대 한 OLEMISC 비트를 반환 합니다. 이 열거형은 컨트롤의 기타 특성을 설명 하는 설정의 컬렉션을 지정 합니다. OLEMISC 설정에 대 한 자세한 설명은 Windows SDK의 [Olemisc](/windows/win32/api/oleidl/ne-oleidl-olemisc) 를 참조 하십시오.

> [!NOTE]
> ActiveX ControlWizard에서 사용 하는 기본 설정은 OLEMISC_ACTIVATEWHENVISIBLE, OLEMISC_SETCLIENTSITEFIRST, OLEMISC_INSIDEOUT, OLEMISC_CANTLINKINSIDE 및 OLEMISC_RECOMPOSEONRESIZE입니다.

### <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="implement_serial"></a><a name="implement_serial"></a> IMPLEMENT_SERIAL

`CObject`계층 내에서 클래스 이름 및 위치에 대 한 런타임 액세스 권한이 있는 동적 파생 클래스에 필요한 c + + 코드를 생성 합니다.

```
IMPLEMENT_SERIAL(class_name, base_class_name, wSchema)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

*base_class_name*<br/>
기본 클래스의 이름입니다.

*wSchema*<br/>
역직렬화 프로그램에서 이전 프로그램 버전에서 생성 된 데이터를 식별 하 고 처리할 수 있도록 archive로 인코딩될 UINT "버전 번호"입니다. 클래스 스키마 번호는-1이 아니어야 합니다.

### <a name="remarks"></a>설명

.Cpp 모듈의 IMPLEMENT_SERIAL 매크로를 사용 합니다. 그런 다음 결과 개체 코드를 한 번만 연결 합니다.

AFX_API 매크로를 사용 하 여 `CArchive` DECLARE_SERIAL 및 IMPLEMENT_SERIAL 매크로를 사용 하는 클래스에 대 한 추출 연산자를 자동으로 내보낼 수 있습니다. 다음 코드를 사용 하 여 클래스 선언 (.h 파일에 있음)을 묶습니다.

[!code-cpp[NVC_MFCCObjectSample#20](../../mfc/codesnippet/cpp/run-time-object-model-services_1.h)]

자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#24](../../mfc/codesnippet/cpp/run-time-object-model-services_7.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="runtime_class"></a><a name="runtime_class"></a> RUNTIME_CLASS

C + + 클래스의 이름에서 런타임 클래스 구조를 가져옵니다.

```
RUNTIME_CLASS(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름 (따옴표로 묶여 있지 않음)입니다.

### <a name="remarks"></a>설명

RUNTIME_CLASS *class_name* 에서 지정한 클래스의 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조에 대 한 포인터를 반환 합니다. `CObject`DECLARE_DYNAMIC, DECLARE_DYNCREATE 또는 DECLARE_SERIAL으로 선언 된 파생 클래스만 구조체에 대 한 포인터를 반환 `CRuntimeClass` 합니다.

자세한 내용은 [CObject 클래스 항목](../../mfc/using-cobject.md)을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#25](../../mfc/codesnippet/cpp/run-time-object-model-services_8.cpp)]

### <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="declare_olecreate"></a><a name="declare_olecreate"></a> DECLARE_OLECREATE

`CCmdTarget`OLE 자동화를 통해 파생 클래스의 개체를 만들 수 있도록 합니다.

```
DECLARE_OLECREATE(class_name)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

### <a name="remarks"></a>설명

이 매크로를 사용 하 여 다른 OLE 지원 응용 프로그램에서이 유형의 개체를 만들 수 있습니다.

클래스에 대 한 .h 모듈에 DECLARE_OLECREATE 매크로를 추가 하 고이 클래스의 개체에 액세스 해야 하는 모든 .cpp 모듈에 해당 모듈을 포함 합니다.

클래스 선언에 DECLARE_OLECREATE 포함 된 경우 IMPLEMENT_OLECREATE 클래스 구현에 포함 되어야 합니다. DECLARE_OLECREATE를 사용 하는 클래스 선언에는 DECLARE_DYNCREATE 또는 DECLARE_SERIAL도 사용 해야 합니다.

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="implement_olecreate"></a><a name="implement_olecreate"></a> IMPLEMENT_OLECREATE

이 매크로나 [IMPLEMENT_OLECREATE_FLAGS](#implement_olecreate_flags) 은를 사용 하는 모든 클래스에 대 한 구현 파일에 표시 되어야 합니다 `DECLARE_OLECREATE` .

```
IMPLEMENT_OLECREATE(class_name, external_name, l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
클래스의 실제 이름입니다.

*external_name*<br/>
다른 응용 프로그램에 노출 되는 개체 이름입니다 (따옴표로 묶).

클래스 CLSID의 *l*, *w1*, *w2*, *b1*, *b2*, *b3*, *b4*, *b5*, *b6*, *b7*, *b8* 구성 요소입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> IMPLEMENT_OLECREATE 사용 하는 경우 기본적으로 단일 스레딩 모델만 지원 합니다. IMPLEMENT_OLECREATE_FLAGS 사용 하는 경우 *Nflags* 매개 변수를 사용 하 여 개체에서 지 원하는 스레딩 모델을 지정할 수 있습니다.

외부 이름은 다른 응용 프로그램에 노출 되는 식별자입니다. 클라이언트 응용 프로그램은 외부 이름을 사용 하 여 자동화 서버에서이 클래스의 개체를 요청 합니다.

OLE 클래스 ID는 개체의 고유한 128 비트 식별자입니다. 이는 **`long`** 구문 설명에서 *l*, *w1*, *w2* 및 *b1* 에서 *b8* 로 표시 되는 1, 2 개의 **단어** 및 8 **바이트** s로 구성 됩니다. 응용 프로그램 마법사 및 코드 마법사는 필요에 따라 고유한 OLE 클래스 Id를 만듭니다.

### <a name="requirements"></a>요구 사항

**헤더**: afxdisp.h

## <a name="see-also"></a>참고 항목

[매크로 및 전역](mfc-macros-and-globals.md)<br/>
[MFC 공용 컨트롤 라이브러리 격리](../isolation-of-the-mfc-common-controls-library.md)<br/>
[CLSID 키](/windows/win32/com/clsid-key-hklm)
