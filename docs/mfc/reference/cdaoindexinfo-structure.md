---
description: '자세히 알아보기: CDaoIndexInfo Structure'
title: CDaoIndexInfo 구조체
ms.date: 06/25/2018
f1_keywords:
- CDaoIndexInfo
helpviewer_keywords:
- DAO (Data Access Objects), Indexes collection
- CDaoIndexInfo structure [MFC]
ms.assetid: 251d8285-78ce-4716-a0b3-ccc3395fc437
ms.openlocfilehash: 2e09846789dc91e4d0df67665f3e975b557c07c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250766"
---
# <a name="cdaoindexinfo-structure"></a>CDaoIndexInfo 구조체

구조에는 `CDaoIndexInfo` DAO (data access objects)에 대해 정의 된 인덱스 개체에 대 한 정보가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```cpp
struct CDaoIndexInfo {
    CDaoIndexInfo();                    // Constructor
    CString m_strName;                  // Primary
    CDaoIndexFieldInfo* m_pFieldInfos;  // Primary
    short m_nFields;                    // Primary
    BOOL m_bPrimary;                    // Secondary
    BOOL m_bUnique;                     // Secondary
    BOOL m_bClustered;                  // Secondary
    BOOL m_bIgnoreNulls;                // Secondary
    BOOL m_bRequired;                   // Secondary
    BOOL m_bForeign;                    // Secondary
    long m_lDistinctCount;              // All

    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

### <a name="parameters"></a>매개 변수

*m_strName*<br/>
필드 개체의 이름을 고유 하 게 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_pFieldInfos*<br/>
인덱스의 키 필드에 해당 하는 테이블 또는 레코드 집합 필드를 나타내는 [CDaoIndexFieldInfo](../../mfc/reference/cdaoindexfieldinfo-structure.md) 개체의 배열에 대 한 포인터입니다. 각 개체는 인덱스의 필드 하나를 식별 합니다. 기본 인덱스 순서는 오름차순입니다. 인덱스 개체는 각 레코드에 대 한 인덱스 키를 나타내는 하나 이상의 필드를 가질 수 있습니다. 이는 오름차순, 내림차순 또는 조합일 수 있습니다.

*m_nFields*<br/>
에 저장 된 필드의 수 `m_pFieldInfos` 입니다.

*m_bPrimary*<br/>
Primary 속성이 TRUE 이면 index 개체가 기본 인덱스를 나타냅니다. 주 인덱스는 테이블의 모든 레코드를 미리 정의 된 순서로 고유 하 게 식별 하는 하나 이상의 필드로 구성 됩니다. 인덱스 필드는 고유 해야 하므로 DAO에서 Index 개체의 Unique 속성도 TRUE로 설정 되어 있습니다. 주 인덱스가 두 개 이상의 필드로 구성 된 경우 각 필드는 중복 값을 포함할 수 있지만 모든 인덱싱된 필드의 각 값 조합은 고유 해야 합니다. 주 인덱스는 테이블의 키로 구성 되며 일반적으로 기본 키와 동일한 필드를 포함 합니다.

테이블에 대 한 기본 키를 설정 하면 기본 키는 테이블의 기본 인덱스로 자동으로 정의 됩니다. 자세한 내용은 DAO 도움말의 "기본 속성" 및 "고유 속성" 항목을 참조 하십시오.

> [!NOTE]
> 테이블에는 최대 하나의 기본 인덱스가 있을 수 있습니다.

*m_bUnique*<br/>
인덱스 개체가 테이블의 고유 인덱스를 나타내는지 여부를 나타냅니다. 이 속성이 TRUE 이면 index 개체가 고유한 인덱스를 나타냅니다. 고유 인덱스는 고유 하 고 미리 정의 된 순서로 테이블의 모든 레코드를 논리적으로 정렬 하는 하나 이상의 필드로 구성 됩니다. 인덱스가 하나의 필드로 구성 된 경우 해당 필드의 값은 전체 테이블에 대해 고유 해야 합니다. 인덱스가 둘 이상의 필드로 구성 된 경우 각 필드는 중복 값을 포함할 수 있지만 모든 인덱싱된 필드의 각 값 조합은 고유 해야 합니다.

Index 개체의 Unique 및 Primary 속성이 모두 TRUE로 설정 된 경우 인덱스는 unique 및 primary입니다 .이 인덱스는 테이블의 모든 레코드를 미리 정의 된 논리적 순서로 고유 하 게 식별 합니다. Primary 속성이 FALSE로 설정 된 경우 인덱스는 보조 인덱스입니다. 보조 인덱스 (키와 키가 아닌 키)는 테이블의 레코드에 대 한 식별자 역할을 하지 않고 레코드를 미리 정의 된 순서로 논리적으로 정렬 합니다.

자세한 내용은 DAO 도움말의 "기본 속성" 및 "고유 속성" 항목을 참조 하십시오.

*m_bClustered*<br/>
인덱스 개체가 테이블의 클러스터형 인덱스를 나타내는지 여부를 나타냅니다. 이 속성이 TRUE 이면 index 개체가 클러스터형 인덱스를 나타냅니다. 그렇지 않은 경우에는 그렇지 않습니다. 클러스터형 인덱스는 함께 사용 되는 하나 이상의 키가 아닌 필드로 구성 되며 테이블의 모든 레코드는 미리 정의 된 순서에 따라 정렬 됩니다. 클러스터형 인덱스의 경우 테이블의 데이터는 클러스터형 인덱스에 지정 된 순서에 따라 그대로 저장 됩니다. 클러스터형 인덱스는 테이블의 레코드에 대 한 효율적인 액세스를 제공 합니다. 자세한 내용은 DAO 도움말의 "클러스터형 속성" 항목을 참조 하십시오.

> [!NOTE]
> Jet 데이터베이스 엔진은 클러스터형 인덱스를 지원 하지 않으므로 Microsoft Jet 데이터베이스 엔진을 사용 하는 데이터베이스에 대해서는 클러스터형 속성이 무시 됩니다.

*m_bIgnoreNulls*<br/>
인덱스 필드에 Null 값이 있는 레코드에 대 한 인덱스 항목이 있는지 여부를 나타냅니다. 이 속성이 TRUE 이면 Null 값을 포함 하는 필드에 인덱스 항목이 없습니다. 필드를 사용 하 여 레코드를 빠르게 검색 하려면 필드에 대 한 인덱스를 정의 하면 됩니다. 인덱싱된 필드에서 Null 항목을 허용 하 고 많은 항목이 Null 일 것으로 간주 되는 경우 인덱스 개체의 IgnoreNulls 속성을 TRUE로 설정 하 여 인덱스에서 사용 하는 저장소 공간의 크기를 줄일 수 있습니다. IgnoreNulls 속성 설정 및 필수 속성 설정은 다음 표와 같이 인덱스 값이 Null 인 레코드에 인덱스 항목이 있는지 여부를 확인 합니다.

|IgnoreNulls|필수|인덱스 필드의 Null|
|-----------------|--------------|-------------------------|
|참|거짓|Null 값이 허용 됩니다. 인덱스 항목이 추가 되지 않았습니다.|
|False|False|Null 값이 허용 됩니다. 인덱스 항목이 추가 되었습니다.|
|True 또는 False|참|Null 값은 허용 되지 않습니다. 인덱스 항목이 추가 되지 않았습니다.|

자세한 내용은 DAO 도움말의 "IgnoreNulls 속성" 항목을 참조 하십시오.

*m_bRequired*<br/>
DAO 인덱스 개체에 Null이 아닌 값이 필요한 지 여부를 나타냅니다. 이 속성이 TRUE 이면 index 개체는 Null 값을 허용 하지 않습니다. 자세한 내용은 DAO 도움말의 "필수 속성" 항목을 참조 하십시오.

> [!TIP]
> 테이블 정의, 레코드 집합 또는 querydef 개체에 포함 된 필드 개체 또는 DAO 인덱스 개체에 대해이 속성을 설정할 수 있는 경우 필드 개체에 대해이 속성을 설정 합니다. Field 개체의 속성 설정에 대 한 유효성은 인덱스 개체의 앞에서 확인 됩니다.

*m_bForeign*<br/>
인덱스 개체가 테이블의 외래 키를 나타내는지 여부를 나타냅니다. 이 속성이 TRUE 이면 인덱스는 테이블의 외래 키를 나타냅니다. 외래 키는 외래 테이블에서 기본 테이블의 행을 고유 하 게 식별 하는 하나 이상의 필드로 구성 됩니다. Microsoft Jet 데이터베이스 엔진은 외부 테이블에 대 한 인덱스 개체를 만들고 참조 무결성을 적용 하는 관계를 만들 때 외래 속성을 설정 합니다. 자세한 내용은 DAO 도움말의 "외래 속성" 항목을 참조 하십시오.

*m_lDistinctCount*<br/>
연결 된 테이블에 포함 된 인덱스 개체의 고유 값 수를 나타냅니다. DistinctCount 속성을 확인 하 여 인덱스의 고유 값 또는 키 수를 확인 합니다. 인덱스에서 중복 값을 허용 하는 경우에도 해당 값이 여러 번 나타날 수 있지만 키는 한 번만 계산 됩니다. 이 정보는 인덱스 정보를 평가 하 여 데이터 액세스를 최적화 하려는 응용 프로그램에서 유용 합니다. 고유 값 수는 인덱스 개체의 카디널리티 라고도 합니다. DistinctCount 속성은 항상 특정 시간에 실제 키 수를 반영 하지 않습니다. 예를 들어 트랜잭션 롤백으로 인 한 변경 내용은 DistinctCount 속성에 즉시 반영 되지 않습니다. 자세한 내용은 DAO 도움말의 "DistinctCount 속성" 항목을 참조 하십시오.

## <a name="remarks"></a>설명

위의 기본, 보조 및 모든에 대 한 참조는 `GetIndexInfo` [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) 및 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)클래스의 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다.

인덱스 개체는 MFC 클래스로 표현 되지 않습니다. 대신 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 클래스의 기본 MFC 개체인 DAO 개체는 Indexes 컬렉션 이라는 인덱스 개체의 컬렉션을 포함 합니다. 이러한 클래스는 인덱스 정보의 개별 항목에 액세스 하는 멤버 함수를 제공 하거나, 포함 하는 `CDaoIndexInfo` `GetIndexInfo` 개체의 멤버 함수를 호출 하 여 개체를 사용 하 여 한 번에 모두 액세스할 수 있습니다.

`CDaoIndexInfo` 에는에서 인덱스 필드 정보를 올바르게 할당 및 할당 취소 하기 위해 생성자와 소멸자가 있습니다 `m_pFieldInfos` .

`GetIndexInfo`테이블 정의 개체의 멤버 함수에 의해 검색 된 정보는 구조체에 저장 됩니다 `CDaoIndexInfo` . `GetIndexInfo`인덱스 컬렉션이 인덱스 개체를 저장 하는을 포함 하는 테이블 형식의 개체에 대 한 멤버 함수를 호출 합니다. `CDaoIndexInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoIndexInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef:: GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)
