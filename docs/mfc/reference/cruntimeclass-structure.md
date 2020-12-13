---
description: '자세히 알아보기: CRuntimeClass Structure'
title: CRuntimeClass 구조체
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: e02732ec595026f028ad4b8f9bd3d8898a40cbc0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342919"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass 구조체

에서 파생 된 각 클래스 `CObject` 는 `CRuntimeClass` 런타임에 개체 또는 해당 기본 클래스에 대 한 정보를 가져오는 데 사용할 수 있는 구조체와 연결 됩니다.

## <a name="syntax"></a>구문

```
struct CRuntimeClass
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRuntimeClass:: CreateObject](#createobject)|런타임에 개체를 만듭니다.|
|[CRuntimeClass:: FromName](#fromname)|런타임에 익숙한 클래스 이름을 사용 하 여 개체를 만듭니다.|
|[CRuntimeClass:: IsDerivedFrom](#isderivedfrom)|클래스가 지정 된 클래스에서 파생 되었는지 여부를 확인 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CRuntimeClass:: m_lpszClassName](#m_lpszclassname)|클래스의 이름입니다.|
|[CRuntimeClass:: m_nObjectSize](#m_nobjectsize)|개체의 크기(바이트)입니다.|
|[CRuntimeClass:: m_pBaseClass](#m_pbaseclass)|`CRuntimeClass`기본 클래스의 구조에 대 한 포인터입니다.|
|[CRuntimeClass:: m_pfnCreateObject](#m_pfncreateobject)|개체를 동적으로 만드는 함수에 대 한 포인터입니다.|
|[CRuntimeClass:: m_pfnGetBaseClass](#m_pfngetbaseclass)|구조체를 반환 `CRuntimeClass` 합니다 (동적으로 연결 된 경우에만 사용 가능).|
|[CRuntimeClass:: m_wSchema](#m_wschema)|클래스의 스키마 번호입니다.|

## <a name="remarks"></a>설명

`CRuntimeClass` 는 구조체 이므로 기본 클래스를 포함 하지 않습니다.

런타임에 개체의 클래스를 확인 하는 기능은 함수 인수에 대 한 추가 형식 검사가 필요 하거나 개체의 클래스를 기반으로 특수 용도의 코드를 작성 해야 하는 경우에 유용 합니다. 런타임 클래스 정보는 c + + 언어에서 직접 지원 되지 않습니다.

`CRuntimeClass` 관련 된 `CRuntimeClass` 클래스의 ASCII 클래스 이름 및 기본 클래스의에 대 한 포인터와 같은 관련 c + + 개체에 대 한 정보를 제공 합니다. 또한이 구조는 개체를 동적으로 만들고, 친숙 한 이름을 사용 하 여 개체의 형식을 지정 하 고, 관련 클래스가 특정 클래스에서 파생 되는지 여부를 확인 하는 데 사용할 수 있는 다양 한 함수를 구현 합니다.

사용에 대 한 자세한 내용은 `CRuntimeClass` [Run-Time 클래스 정보에 액세스](../../mfc/accessing-run-time-class-information.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CRuntimeClass`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a> CRuntimeClass:: CreateObject

런타임에 지정 된 클래스를 동적으로 만들려면이 함수를 호출 합니다.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
만들 클래스의 친숙 한 이름입니다.

### <a name="return-value"></a>반환 값

새로 만든 개체에 대 한 포인터 이거나, 클래스 이름이 없거나 개체를 만들기에 필요한 메모리가 부족 한 경우 NULL입니다.

### <a name="remarks"></a>설명

에서 파생 된 클래스는 `CObject` 런타임에 지정 된 클래스의 개체를 만드는 데 사용할 수 있는 동적 생성을 지원할 수 있습니다. 예를 들어 문서, 뷰 및 프레임 클래스는 동적 생성을 지원 해야 합니다. 동적 생성 및 멤버에 대 한 자세한 내용은 `CreateObject` [cobject 클래스](../../mfc/using-cobject.md) 및 [Cobject 클래스: 기능 수준 지정](../../mfc/specifying-levels-of-functionality.md)을 참조 하세요.

### <a name="example"></a>예제

  [IsDerivedFrom](#isderivedfrom)의 예제를 참조 하세요.

## <a name="cruntimeclassfromname"></a><a name="fromname"></a> CRuntimeClass:: FromName

친숙 한 이름과 연결 된 구조체를 검색 하려면이 함수를 호출 `CRuntimeClass` 합니다.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>매개 변수

*lpszClassName*<br/>
에서 파생 된 클래스의 친숙 한 이름 `CObject` 입니다.

### <a name="return-value"></a>반환 값

`CRuntimeClass` *LpszClassName* 에 전달 된 이름에 해당 하는 개체에 대 한 포인터입니다. 이 함수는 일치 하는 클래스 이름을 찾을 수 없는 경우 NULL을 반환 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a> CRuntimeClass:: IsDerivedFrom

호출 하는 클래스가 *pBaseClass* 매개 변수에 지정 된 클래스에서 파생 되는지 여부를 확인 하려면이 함수를 호출 합니다.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>매개 변수

*pBaseClass*<br/>
에서 파생 된 클래스의 친숙 한 이름 `CObject` 입니다.

### <a name="return-value"></a>반환 값

를 호출 하는 클래스가 해당 `IsDerivedFrom` 구조가 매개 변수로 지정 된 기본 클래스에서 파생 되 면 TRUE `CRuntimeClass` 이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

관계는 멤버의 클래스에서 위쪽으로 파생 된 클래스 체인 위로 "이동" 하 여 결정 됩니다. 이 함수는 기본 클래스와 일치 하는 항목이 없는 경우에만 FALSE를 반환 합니다.

> [!NOTE]
> 구조를 사용 하려면 `CRuntimeClass` 런타임 개체 정보를 검색할 클래스의 구현에 IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE 또는 IMPLEMENT_SERIAL 매크로를 포함 해야 합니다.

사용에 대 한 자세한 내용은 `CRuntimeClass` [CObject 클래스: Run-Time 클래스 정보 액세스](../../mfc/accessing-run-time-class-information.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a> CRuntimeClass:: m_lpszClassName

ASCII 클래스 이름을 포함 하는 null로 끝나는 문자열입니다.

### <a name="remarks"></a>설명

이 이름을 사용 하 여 멤버 함수를 사용 하 여 클래스의 인스턴스를 만들 수 있습니다 `FromName` .

### <a name="example"></a>예제

  [IsDerivedFrom](#isderivedfrom)의 예제를 참조 하세요.

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a> CRuntimeClass:: m_nObjectSize

개체의 크기 (바이트)입니다.

### <a name="remarks"></a>설명

개체에 할당 된 메모리를 가리키는 데이터 멤버가 있는 경우 해당 메모리의 크기는 포함 되지 않습니다.

### <a name="example"></a>예제

  [IsDerivedFrom](#isderivedfrom)의 예제를 참조 하세요.

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a> CRuntimeClass:: m_pBaseClass

응용 프로그램이 정적으로 MFC에 링크 하는 경우이 데이터 멤버는 기본 클래스의 구조에 대 한 포인터를 포함 `CRuntimeClass` 합니다.

### <a name="remarks"></a>설명

응용 프로그램이 동적으로 MFC 라이브러리에 연결 되는 경우 [m_pfnGetBaseClass](#m_pfngetbaseclass)를 참조 하세요.

### <a name="example"></a>예제

  [IsDerivedFrom](#isderivedfrom)의 예제를 참조 하세요.

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a> CRuntimeClass:: m_pfnCreateObject

클래스의 개체를 만드는 기본 생성자에 대 한 함수 포인터입니다.

### <a name="remarks"></a>설명

이 포인터는 클래스가 동적 생성을 지 원하는 경우에만 유효 합니다. 그렇지 않으면 함수는 NULL을 반환 합니다.

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a> CRuntimeClass:: m_pfnGetBaseClass

응용 프로그램에서 MFC 라이브러리를 공유 DLL로 사용 하는 경우이 데이터 멤버는 `CRuntimeClass` 기본 클래스의 구조를 반환 하는 함수를 가리킵니다.

### <a name="remarks"></a>설명

응용 프로그램이 MFC 라이브러리에 정적으로 연결 되는 경우 [m_pBaseClass](#m_pbaseclass)를 참조 하세요.

### <a name="example"></a>예제

  [IsDerivedFrom](#isderivedfrom)의 예제를 참조 하세요.

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a> CRuntimeClass:: m_wSchema

스키마 번호 (serialize 할 수 없는 클래스의 경우-1)입니다.

### <a name="remarks"></a>설명

스키마 번호에 대 한 자세한 내용은 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) 매크로를 참조 하세요.

### <a name="example"></a>예제

  [IsDerivedFrom](#isderivedfrom)의 예제를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CObject:: GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
