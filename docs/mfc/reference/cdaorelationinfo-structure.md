---
description: '자세히 알아보기: CDaoRelationInfo Structure'
title: CDaoRelationInfo 구조체
ms.date: 06/25/2018
f1_keywords:
- CDaoRelationInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationInfo structure [MFC]
ms.assetid: 92dda090-fe72-4090-84ec-429498a48aad
ms.openlocfilehash: efcc880d30dd18108005d9c4f265238b81551532
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222244"
---
# <a name="cdaorelationinfo-structure"></a>CDaoRelationInfo 구조체

`CDaoRelationInfo`구조는 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 있는 두 테이블의 필드 사이에 정의 된 관계에 대 한 정보를 포함 합니다.

## <a name="syntax"></a>구문

```cpp
struct CDaoRelationInfo
{
    CDaoRelationInfo();                     // Constructor
    CString m_strName;                      // Primary
    CString m_strTable;                     // Primary
    CString m_strForeignTable;              // Primary
    long m_lAttributes;                     // Secondary
    CDaoRelationFieldInfo* m_pFieldInfos;   // Secondary
    short m_nFields;                        // Secondary
    // Below the // Implementation comment:
    // Destructor, not otherwise documented
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
관계 개체의 이름을 고유 하 게 식별 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_strTable*<br/>
관계에 있는 기본 테이블의 이름을로 합니다.

*m_strForeignTable*<br/>
관계에서 외래 테이블의 이름을로 합니다. 외래 테이블은 외래 키를 포함 하는 데 사용 되는 테이블입니다. 일반적으로 외래 테이블을 사용 하 여 참조 무결성을 설정 하거나 적용 합니다. 외래 테이블은 일반적으로 일 대 다 관계의 다 측에 있습니다. 외래 테이블의 예로는 미국 또는 캐나다 나이 또는 고객 주문에 대 한 코드를 포함 하는 테이블이 있습니다.

*m_lAttributes*<br/>
관계 형식에 대 한 정보를 포함 합니다. 이 멤버의 값은 다음 중 하나일 수 있습니다.

- `dbRelationUnique` 일 대 일 관계입니다.

- `dbRelationDontEnforce` 관계는 적용 되지 않습니다 (참조 무결성 없음).

- `dbRelationInherited` 연결 된 두 테이블을 포함 하는 아닌 스레드의 데이터베이스에 관계가 있습니다.

- `dbRelationLeft` 왼쪽 조인입니다. 왼쪽 우선 외부 조인은 두 번째 (오른쪽) 테이블의 레코드에 대해 일치 하는 값이 없는 경우에도 두 테이블의 첫 번째 (왼쪽)에 있는 모든 레코드를 포함 합니다.

- `dbRelationRight` 관계가 올바른 조인입니다. 오른쪽 우선 외부 조인에는 첫 번째 (왼쪽) 테이블의 레코드에 대해 일치 하는 값이 없는 경우에도 두 테이블의 두 번째 (오른쪽)에 있는 모든 레코드가 포함 됩니다.

- `dbRelationUpdateCascade` 업데이트는 cascade입니다.

- `dbRelationDeleteCascade` 삭제는 cascade입니다.

*m_pFieldInfos*<br/>
[CDaoRelationFieldInfo](../../mfc/reference/cdaorelationfieldinfo-structure.md) 구조체의 배열에 대 한 포인터입니다. 배열에는 관계의 각 필드에 대 한 하나의 개체가 포함 되어 있습니다. `m_nFields`데이터 멤버는 배열 요소 수를 제공 합니다.

*m_nFields*<br/>
`CDaoRelationFieldInfo`데이터 멤버의 개체 수 `m_pFieldInfos` 입니다.

## <a name="remarks"></a>설명

위의 주 및 보조에 대 한 참조는 클래스의 [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다 `CDaoDatabase` .

관계 개체는 MFC 클래스로 표현 되지 않습니다. 대신, 클래스의 MFC 개체 내부에 있는 DAO 개체는 관계 `CDaoDatabase` 개체의 컬렉션을 유지 관리 합니다. 즉 `CDaoDatabase` , 멤버 함수를 제공 하 여 관계 정보의 일부 개별 항목에 액세스 하거나 포함 하는 `CDaoRelationInfo` `GetRelationInfo` 데이터베이스 개체의 멤버 함수를 호출 하 여 개체를 사용 하 여 한 번에 모두 액세스할 수 있습니다.

[CDaoDatabase:: GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) 멤버 함수에서 검색 된 정보는 구조체에 저장 됩니다 `CDaoRelationInfo` . `CDaoRelationInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoRelationInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[CDaoRelationFieldInfo 구조체](../../mfc/reference/cdaorelationfieldinfo-structure.md)
