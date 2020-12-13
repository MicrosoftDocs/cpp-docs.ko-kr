---
description: '다음에 대 한 자세한 정보: CObject 클래스'
title: CObject 클래스
ms.date: 11/04/2016
f1_keywords:
- CObject
- AFX/CObject
- AFX/CObject::CObject
- AFX/CObject::AssertValid
- AFX/CObject::Dump
- AFX/CObject::GetRuntimeClass
- AFX/CObject::IsKindOf
- AFX/CObject::IsSerializable
- AFX/CObject::Serialize
helpviewer_keywords:
- CObject [MFC], CObject
- CObject [MFC], AssertValid
- CObject [MFC], Dump
- CObject [MFC], GetRuntimeClass
- CObject [MFC], IsKindOf
- CObject [MFC], IsSerializable
- CObject [MFC], Serialize
ms.assetid: 95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a
ms.openlocfilehash: bd093307f159a6d7abe83d9fdd9ad6898a19e4ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331469"
---
# <a name="cobject-class"></a>CObject 클래스

MFC 라이브러리의 주체 기본 클래스입니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CObject
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CObject:: CObject](#cobject)|기본 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CObject:: AssertValid](#assertvalid)|이 개체의 무결성을 검사 합니다.|
|[CObject::Dump](#dump)|이 개체의 진단 덤프를 생성 합니다.|
|[CObject:: GetRuntimeClass](#getruntimeclass)|`CRuntimeClass`이 개체의 클래스에 해당 하는 구조체를 반환 합니다.|
|[CObject:: IsKindOf](#iskindof)|지정 된 클래스에 대 한이 개체의 관계를 테스트 합니다.|
|[CObject:: IsSerializable](#isserializable)|이 개체를 serialize 할 수 있는지 여부를 테스트 합니다.|
|[CObject:: Serialize](#serialize)|보관 파일에서 개체를 로드 하거나 저장 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CObject:: operator delete](#operator_delete)|특수 **`delete`** 연산자입니다.|
|[CObject:: operator new](#operator_new)|특수 **`new`** 연산자입니다.|

## <a name="remarks"></a>설명

및와 같은 라이브러리 클래스 뿐만 아니라 사용자가 작성 하는 클래스에 대 한 루트 역할을 합니다 `CFile` `CObList` . `CObject` 다음을 포함 하 여 기본 서비스를 제공 합니다.

- Serialization 지원

- 런타임 클래스 정보

- 개체 진단 출력

- 컬렉션 클래스와의 호환성

는 `CObject` 다중 상속을 지원 하지 않습니다. 파생 클래스 `CObject` 는 기본 클래스를 하나만 포함할 수 있으며, `CObject` 계층 구조에서 맨 왼쪽에 있어야 합니다. 그러나 `CObject` 오른쪽 다중 상속 분기에서 구조체 및 파생 클래스가 아닌 클래스를 가질 수 있습니다.

`CObject`클래스 구현 및 선언에서 선택적 매크로 중 일부를 사용 하는 경우 파생의 주요 이점을 누릴 수 있습니다.

첫 번째 수준 매크로 [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic) 및 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)는 계층에서 클래스 이름 및 해당 위치에 대 한 런타임 액세스를 허용 합니다. 그러면 의미 있는 진단 덤프를 사용할 수 있습니다.

두 번째 수준 매크로 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) 및 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)에는 첫 번째 수준 매크로의 모든 기능이 포함 되며, 개체를 "archive"로 "serialize" 할 수 있습니다.

일반적으로 및를 사용 하 여 Microsoft Foundation 클래스 및 c + + 클래스를 파생 하는 방법에 대 한 자세한 내용은 `CObject` CObject 및 [Serialization](../../mfc/serialization-in-mfc.md) [사용](../../mfc/using-cobject.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CObject`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cobjectassertvalid"></a><a name="assertvalid"></a> CObject:: AssertValid

이 개체의 무결성을 검사 합니다.

```
virtual void AssertValid() const;
```

### <a name="remarks"></a>설명

`AssertValid` 내부 상태를 확인 하 여이 개체에 대 한 유효성 검사를 수행 합니다. 라이브러리의 디버그 버전에서는 `AssertValid` 어설션이 실패 한 줄 번호와 파일 이름을 나열 하는 메시지를 사용 하 여 프로그램을 어설션 하 고 종료할 수 있습니다.

사용자 고유의 클래스를 작성 하는 경우 함수를 재정의 `AssertValid` 하 여 클래스의 사용자 및 다른 사용자에 게 진단 서비스를 제공 해야 합니다. 재정의 된는 `AssertValid` 일반적으로 `AssertValid` 파생 클래스에 고유한 데이터 멤버를 확인 하기 전에 기본 클래스의 함수를 호출 합니다.

`AssertValid`는 함수 이므로 **`const`** 테스트 중에 개체 상태를 변경할 수 없습니다. 사용자 고유의 파생 클래스 `AssertValid` 함수는 예외를 throw 해서는 안 되며, 대신 잘못 된 개체 데이터를 검색 하는지 여부를 어설션해야 합니다.

"유효성"의 정의는 개체의 클래스에 따라 다릅니다. 규칙으로 함수는 "단순 검사"를 수행 해야 합니다. 즉, 개체에 다른 개체에 대 한 포인터가 포함 된 경우 포인터가 null이 아니면 포인터가 참조 하는 개체에 대 한 유효성 테스트를 수행 하면 안 됩니다.

### <a name="example"></a>예제

모든 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#7](../../mfc/codesnippet/cpp/cobject-class_1.cpp)]

다른 예제를 보려면 [AfxDoForAllObjects](diagnostic-services.md#afxdoforallobjects)를 참조 하세요.

## <a name="cobjectcobject"></a><a name="cobject"></a> CObject:: CObject

이러한 함수는 표준 `CObject` 생성자입니다.

```
CObject();
CObject(const CObject& objectSrc);
```

### <a name="parameters"></a>매개 변수

*objectSrc*<br/>
다른에 대 한 참조 `CObject`

### <a name="remarks"></a>설명

기본 버전은 파생 클래스의 생성자에 의해 자동으로 호출 됩니다.

클래스를 serialize 할 수 있는 경우 (IMPLEMENT_SERIAL 매크로를 통합) 클래스 선언에서 기본 생성자 (인수가 없는 생성자)가 있어야 합니다. 기본 생성자가 필요 하지 않은 경우 private 또는 protected "empty" 생성자를 선언 합니다. 자세한 내용은 [CObject 사용](../../mfc/using-cobject.md)을 참조 하세요.

표준 c + + 기본 클래스 복사 생성자는 멤버 단위로 복사를 수행 합니다. `CObject`클래스의 복사 생성자가 필요 하지만 사용할 수 없는 경우 전용 복사 생성자가 있으면 컴파일러 오류 메시지가 보장 됩니다. 따라서 클래스에이 기능이 필요한 경우 복사 생성자를 제공 해야 합니다.

### <a name="example"></a>예제

예제에 사용 된 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 `CAge` `CObject` 하세요.

[!code-cpp[NVC_MFCCObjectSample#8](../../mfc/codesnippet/cpp/cobject-class_2.cpp)]

## <a name="cobjectdump"></a><a name="dump"></a> CObject::D ump

개체의 내용을 [CDumpContext](../../mfc/reference/cdumpcontext-class.md) 개체에 덤프 합니다.

```
virtual void Dump(CDumpContext& dc) const;
```

### <a name="parameters"></a>매개 변수

*dc*<br/>
일반적으로 덤프 하기 위한 진단 덤프 컨텍스트입니다 `afxDump` .

### <a name="remarks"></a>설명

사용자 고유의 클래스를 작성 하는 경우 함수를 재정의 `Dump` 하 여 클래스의 사용자 및 다른 사용자에 게 진단 서비스를 제공 해야 합니다. 재정의 된는 `Dump` 일반적으로 `Dump` 파생 클래스에 고유한 데이터 멤버를 인쇄 하기 전에 기본 클래스의 함수를 호출 합니다. `CObject::Dump` 클래스에서 또는 IMPLEMENT_SERIAL 매크로를 사용 하는 경우 클래스 이름을 인쇄 합니다 `IMPLEMENT_DYNAMIC` .

> [!NOTE]
> `Dump`함수는 출력의 끝 부분에서 줄 바꿈 문자를 인쇄 하면 안 됩니다.

`Dump` 호출은 MFC 라이브러리의 디버그 버전 에서만 의미가 있습니다.  /  `#endif` 조건부 컴파일에 대 한 #ifdef _DEBUG 문으로 호출, 함수 선언 및 함수 구현을 묶습니다.

`Dump`는 함수 이므로 **`const`** 덤프 중에 개체 상태를 변경할 수 없습니다.

[CDumpContext 삽입 (<<) 연산자](../../mfc/reference/cdumpcontext-class.md#operator_lt_lt) 는 `Dump` 포인터가 삽입 될 때를 호출 합니다 `CObject` .

`Dump` 개체의 "비순환" 덤프만 허용 합니다. 예를 들어 개체 목록을 덤프할 수 있지만 개체 중 하나가 목록 자체인 경우 스택을 오버플로 하 게 됩니다.

### <a name="example"></a>예제

모든 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#9](../../mfc/codesnippet/cpp/cobject-class_3.cpp)]

## <a name="cobjectgetruntimeclass"></a><a name="getruntimeclass"></a> CObject:: GetRuntimeClass

`CRuntimeClass`이 개체의 클래스에 해당 하는 구조체를 반환 합니다.

```
virtual CRuntimeClass* GetRuntimeClass() const;
```

### <a name="return-value"></a>반환 값

이 개체의 클래스에 해당 하는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 포인터입니다. **NULL** 이 아닙니다.

### <a name="remarks"></a>설명

`CRuntimeClass`각 파생 클래스에 대해 하나의 구조가 있습니다 `CObject` . 구조체 멤버는 다음과 같습니다.

- **Lpcstr m_lpszClassName** ASCII 클래스 이름을 포함 하는 null로 끝나는 문자열입니다.

- **int m_nObjectSize** 개체의 크기 (바이트)입니다. 개체에 할당 된 메모리를 가리키는 데이터 멤버가 있는 경우 해당 메모리의 크기는 포함 되지 않습니다.

- **UINT m_wSchema** 스키마 번호 (serialize 할 수 없는 클래스의 경우-1)입니다. 스키마 번호에 대 한 설명은 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) 매크로를 참조 하세요.

- **CObject \* (파스칼 \* m_pfnCreateObject) ()** 클래스의 개체를 만드는 기본 생성자에 대 한 함수 포인터입니다. 클래스에서 동적 생성을 지 원하는 경우에만 유효 합니다. 그렇지 않으면 **NULL** 을 반환 합니다.

- **CRuntimeClass \* (파스칼 \* m_pfn_GetBaseClass) ()** 응용 프로그램이 AFXDLL 버전의 MFC에 동적으로 연결 된 경우 `CRuntimeClass` 기본 클래스의 구조를 반환 하는 함수에 대 한 포인터입니다.

- CRuntimeClass는 응용 프로그램이 정적으로 MFC에 링크 된 경우 기본 클래스의 구조에 대 한 포인터를 **\* m_pBaseClass** `CRuntimeClass` 합니다.

이 함수를 사용 하려면 클래스 구현에서 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic), [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)또는 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) 매크로를 사용 해야 합니다. 그렇지 않으면 잘못 된 결과를 얻게 됩니다.

### <a name="example"></a>예제

모든 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#10](../../mfc/codesnippet/cpp/cobject-class_4.cpp)]

## <a name="cobjectiskindof"></a><a name="iskindof"></a> CObject:: IsKindOf

지정 된 클래스에 대 한이 개체의 관계를 테스트 합니다.

```
BOOL IsKindOf(const CRuntimeClass* pClass) const;
```

### <a name="parameters"></a>매개 변수

*pClass*<br/>
파생 클래스와 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 포인터 `CObject` 입니다.

### <a name="return-value"></a>반환 값

개체가 클래스에 해당 하는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 *Pclass* 를 테스트 하 여 (1) 지정 된 클래스의 개체 인지 (2) 지정 된 클래스에서 파생 된 클래스의 개체 인지 여부를 확인 합니다. 이 함수는 [DECLARE_DYNAMIC](run-time-object-model-services.md#declare_dynamic), [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate)또는 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) 매크로를 사용 하 여 선언 된 클래스에 대해서만 작동 합니다.

이 함수는 c + + 다형성 기능을 무효화 하므로 광범위 하 게 사용 하지 마십시오. 대신 가상 함수를 사용 해야 합니다.

### <a name="example"></a>예제

모든 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#11](../../mfc/codesnippet/cpp/cobject-class_5.cpp)]

## <a name="cobjectisserializable"></a><a name="isserializable"></a> CObject:: IsSerializable

이 개체가 직렬화에 적합 한지 여부를 테스트 합니다.

```
BOOL IsSerializable() const;
```

### <a name="return-value"></a>반환 값

이 개체를 serialize 할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

클래스를 serialize 할 수 있도록 해당 선언에는 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) 매크로가 포함 되어야 하 고, 구현에는 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) 매크로가 포함 되어야 합니다.

> [!NOTE]
> 이 함수를 재정의 하지 마십시오.

### <a name="example"></a>예제

모든 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#12](../../mfc/codesnippet/cpp/cobject-class_6.cpp)]

## <a name="cobjectoperator-delete"></a><a name="operator_delete"></a> CObject:: operator delete

라이브러리의 릴리스 버전에서 연산자는 연산자에 **`delete`** 의해 할당 된 메모리를 해제 **`new`** 합니다.

```cpp
void PASCAL operator delete(void* p);

void PASCAL operator delete(
    void* p,
    void* pPlace);

void PASCAL operator delete(
    void* p,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>설명

디버그 버전에서 연산자는 **`delete`** 메모리 누수를 감지 하도록 설계 된 할당 모니터링 체계에 참여 합니다.

코드 줄을 사용 하는 경우

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

에서 구현 하기 전에 CPP 파일의 세 번째 버전이 사용 되며 **`delete`** , 나중에 보고 하기 위해 할당 된 블록에 파일 이름 및 줄 번호를 저장 합니다. 추가 매개 변수를 제공 하는 것에 대해 걱정할 필요가 없습니다. 매크로가 사용자를 위해이 작업을 수행 합니다.

디버그 모드에서 DEBUG_NEW 사용 하지 않더라도 위에 설명 된 소스 파일 줄 번호 보고를 제외 하 고 누수 검색을 계속 받습니다.

및 연산자를 재정의 **`new`** 하 **`delete`** 는 경우이 진단 기능을 상실 합니다.

### <a name="example"></a>예제

예제에 사용 된 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 `CAge` `CObject` 하세요.

[!code-cpp[NVC_MFCCObjectSample#15](../../mfc/codesnippet/cpp/cobject-class_8.cpp)]

## <a name="cobjectoperator-new"></a><a name="operator_new"></a> CObject:: operator new

라이브러리의 릴리스 버전에서는 연산자가 **`new`** 와 비슷한 방식으로 최적의 메모리 할당을 수행 `malloc` 합니다.

```cpp
void* PASCAL operator new(size_t nSize);
void* PASCAL operator new(size_t, void* p);

void* PASCAL operator new(
    size_t nSize,
    LPCSTR lpszFileName,
    int nLine);
```

### <a name="remarks"></a>설명

디버그 버전에서 연산자는 **`new`** 메모리 누수를 감지 하도록 설계 된 할당 모니터링 체계에 참여 합니다.

코드 줄을 사용 하는 경우

[!code-cpp[NVC_MFCCObjectSample#14](../../mfc/codesnippet/cpp/cobject-class_7.cpp)]

에서 구현 하기 전에 CPP 파일의 두 번째 버전이 사용 되며 **`new`** , 나중에 보고 하기 위해 할당 된 블록에 파일 이름 및 줄 번호를 저장 합니다. 추가 매개 변수를 제공 하는 것에 대해 걱정할 필요가 없습니다. 매크로가 사용자를 위해이 작업을 수행 합니다.

디버그 모드에서 DEBUG_NEW 사용 하지 않더라도 위에 설명 된 소스 파일 줄 번호 보고를 제외 하 고 누수 검색을 계속 받습니다.

> [!NOTE]
> 이 연산자를 재정의 하는 경우도 재정의 해야 **`delete`** 합니다. 표준 라이브러리 함수를 사용 하지 마십시오 `_new_handler` .

### <a name="example"></a>예제

예제에 사용 된 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 `CAge` `CObject` 하세요.

[!code-cpp[NVC_MFCCObjectSample#16](../../mfc/codesnippet/cpp/cobject-class_9.h)]

## <a name="cobjectserialize"></a><a name="serialize"></a> CObject:: Serialize

이 개체를 보관 저장소에서 읽어오거나 보관 저장소에 씁니다.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

*ar*<br/>
`CArchive`Serialize 하거나에서 serialize 할 개체입니다.

### <a name="remarks"></a>설명

`Serialize`Serialize 하려는 각 클래스에 대해를 재정의 해야 합니다. 재정의 된는 `Serialize` 먼저 `Serialize` 기본 클래스의 함수를 호출 해야 합니다.

또한 클래스 선언에서 [DECLARE_SERIAL](run-time-object-model-services.md#declare_serial) 매크로를 사용 해야 하며, 구현에서 [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) 매크로를 사용 해야 합니다.

[Carchive:: IsLoading](../../mfc/reference/carchive-class.md#isloading) 또는 [Carchive:: isloading](../../mfc/reference/carchive-class.md#isstoring) 을 사용 하 여 보관 파일의 로드 또는 저장 여부를 확인 합니다.

`Serialize` 는 [carchive:: ReadObject](../../mfc/reference/carchive-class.md#readobject) 및 [Carchive:: WriteObject](../../mfc/reference/carchive-class.md#writeobject)에 의해 호출 됩니다. 이러한 함수는 `CArchive` 삽입 연산자 ()와 연결 됩니다 **<\<**) and extraction operator ( **>>** .

Serialization 예제는 [serialization: 개체 serialize](../../mfc/serialization-serializing-an-object.md)문서를 참조 하세요.

### <a name="example"></a>예제

모든 예제에서 사용 되는 클래스 목록은 [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) 를 참조 하세요 `CAge` `CObject` .

[!code-cpp[NVC_MFCCObjectSample#13](../../mfc/codesnippet/cpp/cobject-class_10.cpp)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)
