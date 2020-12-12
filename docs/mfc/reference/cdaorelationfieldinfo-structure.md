---
description: '자세히 알아보기: CDaoRelationFieldInfo Structure'
title: CDaoRelationFieldInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CDaoRelationFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Relations collection
- CDaoRelationFieldInfo structure [MFC]
ms.assetid: 47cb89ca-dc80-47ce-96fd-cc4b88512558
ms.openlocfilehash: eb470752a9e9da5f610dd59976f2716fa1c4e18a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248166"
---
# <a name="cdaorelationfieldinfo-structure"></a>CDaoRelationFieldInfo 구조체

구조에는 `CDaoRelationFieldInfo` DAO (data access objects)에 대해 정의 된 관계의 필드에 대 한 정보가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```
struct CDaoRelationFieldInfo
{
    CString m_strName;           // Primary
    CString m_strForeignName;    // Primary
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
관계의 기본 테이블에 있는 필드의 이름입니다.

*m_strForeignName*<br/>
관계의 외래 테이블에 있는 필드의 이름입니다.

## <a name="remarks"></a>설명

DAO 관계 개체는 기본 테이블의 필드와 외래 테이블에서 관계를 정의 하는 필드를 지정 합니다. 위의 구조 정의에서 주에 대 한 참조는 `m_pFieldInfos` 클래스의 [GetRelationInfo](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) 멤버 함수를 호출 하 여 가져온 [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 개체의 멤버가 정보를 반환 하는 방법을 표시 합니다 `CDaoDatabase` .

관계 개체 및 관계 필드 개체는 MFC 클래스로 표현 되지 않습니다. 대신 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 클래스의 기본 MFC 개체에 있는 DAO 개체는 relation 컬렉션 이라는 relation 개체의 컬렉션을 포함 합니다. 각 관계 개체는 관계 필드 개체의 컬렉션을 포함 합니다. 각 관계 필드 개체는 기본 테이블의 필드를 외래 테이블의 필드와 연관 시킵니다. 관계 필드 개체를 함께 사용 하 여 각 테이블에서 관계를 정의 하는 필드 그룹을 정의 합니다. `CDaoDatabase``CDaoRelationInfo`멤버 함수를 호출 하 여 개체를 사용 하 여 관계 개체에 액세스할 수 있습니다 `GetRelationInfo` . `CDaoRelationInfo`그런 다음 개체에는 `m_pFieldInfos` 개체의 배열을 가리키는 데이터 멤버가 있습니다 `CDaoRelationFieldInfo` .

[](../../mfc/reference/cdaodatabase-class.md#getrelationinfo) `CDaoDatabase` 관계 컬렉션이 관심이 있는 관계 개체를 저장 하는 포함 하는 개체의 GetRelationInfo 멤버 함수를 호출 합니다. 그런 다음 `m_pFieldInfos` [CDaoRelationInfo](../../mfc/reference/cdaorelationinfo-structure.md) 개체의 멤버에 액세스 합니다. `CDaoRelationFieldInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoRelationFieldInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoRelationInfo 구조체](../../mfc/reference/cdaorelationinfo-structure.md)
