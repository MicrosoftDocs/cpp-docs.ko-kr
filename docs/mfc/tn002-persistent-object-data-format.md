---
description: '자세히 알아보기: TN002: 영구 개체 데이터 형식'
title: 'TN002: 영구 개체 데이터 형식'
ms.date: 11/04/2016
helpviewer_keywords:
- VERSIONABLE_SCHEMA macro [MFC]
- persistent object data
- CArchive class [MFC], support for persistent data
- persistent C++ objects [MFC]
- TN002
ms.assetid: 553fe01d-c587-4c8d-a181-3244a15c2be9
ms.openlocfilehash: e99d54bd2624bffac4f5fea37c72bb7719e1e408
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216082"
---
# <a name="tn002-persistent-object-data-format"></a>TN002: 영구 개체 데이터 형식

이 참고는 영구 c + + 개체를 지 원하는 MFC 루틴과 파일에 저장 될 때 개체 데이터의 형식을 설명 합니다. 이는 [DECLARE_SERIAL](../mfc/reference/run-time-object-model-services.md#declare_serial) 및 [IMPLEMENT_SERIAL](../mfc/reference/run-time-object-model-services.md#implement_serial) 매크로를 사용 하는 클래스에만 적용 됩니다.

## <a name="the-problem"></a>문제

영구적 데이터에 대 한 MFC 구현은 여러 개체의 데이터를 파일의 단일 연속 부분에 저장 합니다. 개체의 `Serialize` 메서드는 개체의 데이터를 컴팩트 이진 형식으로 변환 합니다.

구현에서는 [CArchive 클래스](../mfc/reference/carchive-class.md)를 사용 하 여 모든 데이터가 같은 형식으로 저장 되도록 보장 합니다. `CArchive`개체를 번역기로 사용 합니다. 이 개체는 [CArchive:: Close](../mfc/reference/carchive-class.md#close)를 호출할 때까지 생성 된 시간부터 지속 됩니다. 이 메서드는 프로그램이를 포함 하는 범위를 종료할 때 프로그래머가 명시적으로 호출 하거나 소멸자에 의해 암시적으로 호출 될 수 있습니다 `CArchive` .

이 참고에서는 `CArchive` [carchive:: ReadObject](../mfc/reference/carchive-class.md#readobject) 및 [carchive:: WriteObject](../mfc/reference/carchive-class.md#writeobject)멤버의 구현을 설명 합니다. 이 함수에 대 한 코드는 Arcobj .cpp에서 확인할 수 있으며,이에 대 한 기본 구현은 `CArchive` Arccore .cpp에 있습니다. 사용자 코드는 `ReadObject` 및을 직접 호출 하지 않습니다 `WriteObject` . 대신 이러한 개체는 DECLARE_SERIAL 및 IMPLEMENT_SERIAL 매크로에 의해 자동으로 생성 되는 클래스 관련 형식 안전 삽입 및 추출 연산자에서 사용 됩니다. 다음 코드에서는 및를 `WriteObject` 암시적으로 호출 하는 방법을 보여 줍니다 `ReadObject` .

```
class CMyObject : public CObject
{
    DECLARE_SERIAL(CMyObject)
};

IMPLEMENT_SERIAL(CMyObj, CObject, 1)

// example usage (ar is a CArchive&)
CMyObject* pObj;
CArchive& ar;
ar <<pObj;        // calls ar.WriteObject(pObj)
ar>> pObj;        // calls ar.ReadObject(RUNTIME_CLASS(CObj))
```

## <a name="saving-objects-to-the-store-carchivewriteobject"></a>저장소에 개체 저장 (CArchive:: WriteObject)

메서드는 `CArchive::WriteObject` 개체를 다시 생성 하는 데 사용 되는 헤더 데이터를 씁니다. 이 데이터는 개체의 형식 및 개체 상태의 두 부분으로 구성 됩니다. 이 메서드는 또한 개체에 대 한 포인터 수 (순환 포인터 포함)에 관계 없이 단일 복사본만 저장 되도록 작성 되는 개체의 id를 유지 관리 합니다.

개체를 저장 (삽입) 하 고 복원 (추출) 하는 것은 몇 가지 "매니페스트 상수"에 의존 합니다. 이러한 값은 이진 파일에 저장 되며 보관에 중요 한 정보를 제공 합니다 ("w" 접두사는 16 비트 수량을 나타냄).

|태그|설명|
|---------|-----------------|
|태그|NULL 개체 포인터 (0)에 사용 됩니다.|
|wNewClassTag|이 보관 컨텍스트 (-1)의 새로운 기능을 보여 주는 클래스 설명을 나타냅니다.|
|wOldClassTag|읽을 개체의 클래스가이 컨텍스트 (0x8000)에 표시 되었음을 나타냅니다.|

개체를 저장 하는 경우 보관 파일은 [CMapPtrToPtr](../mfc/reference/cmapptrtoptr-class.md) ( *m_pStoreMap*)을 유지 관리 하며,이는 저장 된 개체에서 32 비트 PID (영구 식별자)로의 매핑입니다. PID는 모든 고유 개체 및 보관의 컨텍스트에 저장 된 모든 고유 클래스 이름에 할당 됩니다. 이러한 Pid는 1부터 순차적으로 전달 됩니다. 이러한 Pid는 보관 범위 외부에서 중요 하지 않으며 특히 레코드 번호나 다른 id 항목과 혼동 하지 않습니다.

클래스에서 `CArchive` pid는 32 비트 이지만, 0x7FFE 보다 크지 않으면 16 비트로 기록 됩니다. 대량 Pid는 0x7FFF로 작성 된 후 32 비트 PID가 됩니다. 이는 이전 버전에서 만든 프로젝트와의 호환성을 유지 합니다.

개체를 보관에 저장 하도록 요청 하는 경우 (일반적으로 global 삽입 연산자를 사용 하 여) NULL [CObject](../mfc/reference/cobject-class.md) 포인터에 대 한 검사가 수행 됩니다. 포인터가 NULL 이면 인 *태그* 는 보관 스트림에 삽입 됩니다.

포인터가 NULL이 아니고 serialize 할 수 있는 경우 (클래스가 `DECLARE_SERIAL` 클래스 임) 코드는 *m_pStoreMap* 를 확인 하 여 개체가 이미 저장 되었는지 여부를 확인 합니다. 있는 경우 코드는 해당 개체와 연결 된 32 비트 PID를 보관 스트림에 삽입 합니다.

이전에 개체를 저장 하지 않은 경우 개체의 개체와 정확한 형식 (즉, 클래스)이 모두이 보관 컨텍스트를 새로 고치거 나 개체가 이미 표시 된 정확한 형식 중 어느 것을 고려해 야 합니다. 형식이 표시 되었는지 여부를 확인 하기 위해 코드는 저장 되는 개체와 연결 된 개체와 일치 하는 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 *m_pStoreMap* 를 쿼리 합니다 `CRuntimeClass` . 일치 하는 항목이 있으면에서 `WriteObject` `OR` *wOldClassTag* 및이 인덱스의 비트 단위 태그를 삽입 합니다. `CRuntimeClass`이 보관 컨텍스트의 새 인 경우는 `WriteObject` 해당 클래스에 새 PID를 할당 하 고 *wNewClassTag* 값 앞에 보관에 삽입 합니다.

그런 다음 메서드를 사용 하 여이 클래스에 대 한 설명자를 보관에 삽입 합니다 `CRuntimeClass::Store` . `CRuntimeClass::Store` 클래스의 스키마 번호 (아래 참조)와 클래스의 ASCII 텍스트 이름을 삽입 합니다. ASCII 텍스트 이름을 사용 하면 응용 프로그램에서 아카이브의 고유성이 보장 되지 않습니다. 따라서 데이터 파일에 태그를 지정 하 여 손상을 방지 해야 합니다. 클래스 정보를 삽입 하 고 나면 archive는 개체를 *m_pStoreMap* 에 추가한 다음 메서드를 호출 하 여 `Serialize` 클래스 관련 데이터를 삽입 합니다. 를 호출 하기 전에 개체를 *m_pStoreMap* 에 배치 하면 `Serialize` 개체의 여러 복사본이 저장소에 저장 되지 않습니다.

초기 호출자 (일반적으로 개체 네트워크의 루트)로 돌아갈 때 [CArchive:: Close](../mfc/reference/carchive-class.md#close)를 호출 해야 합니다. 다른 [CFile](../mfc/reference/cfile-class.md)작업을 수행 하려는 경우에는 메서드 플러시를 호출 `CArchive` 하 [](../mfc/reference/carchive-class.md#flush) 여 보관이 손상 되지 않도록 해야 합니다.

> [!NOTE]
> 이 구현은 보관 0x3FFFFFFE 인덱스의 하드 제한을 적용 합니다. 이 숫자는 단일 아카이브에 저장할 수 있는 고유한 개체 및 클래스의 최대 수를 나타내지만 단일 디스크 파일은 보관 컨텍스트를 무제한 포함할 수 있습니다.

## <a name="loading-objects-from-the-store-carchivereadobject"></a>저장소에서 개체 로드 (CArchive:: ReadObject)

개체 로드 (추출)는 메서드를 사용 하 `CArchive::ReadObject` 고의 반대입니다 `WriteObject` . 와 마찬가지로 `WriteObject` `ReadObject` 은 사용자 코드에서 직접 호출 되지 않습니다. 사용자 코드는 예상 된를 사용 하 여를 호출 하는 형식 안전 추출 연산자를 호출 해야 합니다 `ReadObject` `CRuntimeClass` . 이렇게 하면 추출 작업의 형식 무결성을 보장 합니다.

`WriteObject`1부터 시작 하 여 (0은 NULL 개체로 미리 정의 됨) 구현에서 높은 pid를 할당 했으므로 `ReadObject` 구현은 배열을 사용 하 여 보관 컨텍스트의 상태를 유지할 수 있습니다. 저장소에서 PID를 읽을 때 PID가 *m_pLoadArray* 의 현재 상한 보다 큰 경우는 `ReadObject` 새 개체 (또는 클래스 설명)가 다음에 있음을 알고 있습니다.

## <a name="schema-numbers"></a>스키마 번호

클래스의 메서드가 발견 될 때 클래스에 할당 되는 스키마 번호는 `IMPLEMENT_SERIAL` 클래스 구현의 "버전"입니다. 스키마는 지정 된 개체가 영구적으로 설정 된 횟수 (일반적으로 개체 버전 이라고 함)가 아니라 클래스의 구현을 참조 합니다.

시간이 지남에 따라 동일한 클래스의 여러 가지 구현을 유지 하려는 경우 개체의 메서드 구현을 수정할 때 스키마를 증가 `Serialize` 시키면 이전 버전의 구현을 사용 하 여 저장 된 개체를 로드할 수 있는 코드를 작성할 수 있습니다.

`CArchive::ReadObject`이 메서드는 메모리에 있는 클래스 설명의 스키마 번호와 다른 영구 저장소의 스키마 번호를 발견 하면 [CArchiveException](../mfc/reference/carchiveexception-class.md) 를 throw 합니다. 이 예외를 복구 하는 것은 쉽지 않습니다.

`VERSIONABLE_SCHEMA`스키마 버전과 함께 (비트 **or**)를 사용 하 여이 예외가 throw 되지 않도록 할 수 있습니다. 를 사용 하면 `VERSIONABLE_SCHEMA` 코드에서 `Serialize` [CArchive:: GetObjectSchema](../mfc/reference/carchive-class.md#getobjectschema)의 반환 값을 검사 하 여 해당 함수에서 적절 한 작업을 수행할 수 있습니다.

## <a name="calling-serialize-directly"></a>직접 Serialize 호출

대부분의 경우에는 일반 개체 보관 구성표의 오버 헤드가 `WriteObject` `ReadObject` 필요 하지 않습니다. 이는 데이터를 [CDocument](../mfc/reference/cdocument-class.md)직렬화 하는 일반적인 경우입니다. 이 경우 `Serialize` 의 메서드는 `CDocument` extract 또는 insert 연산자가 아닌 직접 호출 됩니다. 문서 내용은 보다 일반적인 개체 보관 구성표를 사용할 수 있습니다.

을 `Serialize` 직접 호출 하면 다음과 같은 장단점이 있습니다.

- 개체를 직렬화 하기 전이나 후에 추가 바이트를 보관에 추가 하지 않습니다. 이렇게 하면 저장 된 데이터를 더 작게 만들 수 있을 뿐 아니라 `Serialize` 모든 파일 형식을 처리할 수 있는 루틴을 구현할 수 있습니다.

- `WriteObject` `ReadObject` 다른 용도로 더 일반적인 개체 보관 체계가 필요 하지 않는 한, 및 구현 및 관련 컬렉션은 응용 프로그램에 연결 되지 않도록 MFC가 튜닝 됩니다.

- 이전 스키마 번호에서 코드를 복구할 필요가 없습니다. 이렇게 하면 문서 serialization 코드에서 스키마 번호, 파일 형식 버전 번호 또는 데이터 파일의 시작 시 사용 하는 식별 번호를 인코딩할 책임이 있습니다.

- 에 대 한 직접 호출로 serialize 되는 개체는를 `Serialize` 사용 하지 않아야 합니다 `CArchive::GetObjectSchema` . 또는 해당 버전을 알 수 없음을 나타내는 (UINT)-1의 반환 값을 처리 해야 합니다.

`Serialize`는 문서에서 직접 호출 되기 때문에 일반적으로 문서의 하위 개체가 부모 문서에 대 한 참조를 보관할 수 없습니다. 이러한 개체는 컨테이너 문서에 대 한 포인터를 명시적으로 제공 해야 합니다. 또는 이러한 뒤로 포인터를 보관 하기 전에 [CArchive:: MapObject](../mfc/reference/carchive-class.md#mapobject) 함수를 사용 하 여 `CDocument` 포인터를 PID에 매핑해야 합니다.

앞에서 설명한 것 처럼을 직접 호출 하는 경우 버전 및 클래스 정보를 직접 인코딩하여 `Serialize` 이전 파일의 이전 버전과의 호환성을 유지 하면서 나중에 형식을 변경할 수 있도록 해야 합니다. `CArchive::SerializeClass`함수는 개체를 직접 직렬화 하거나 기본 클래스를 호출 하기 전에 명시적으로 호출할 수 있습니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
