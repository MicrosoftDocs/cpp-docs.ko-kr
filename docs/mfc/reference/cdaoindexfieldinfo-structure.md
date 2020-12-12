---
description: '자세히 알아보기: CDaoIndexFieldInfo Structure'
title: CDaoIndexFieldInfo 구조체
ms.date: 09/17/2019
f1_keywords:
- CDaoIndexFieldInfo
helpviewer_keywords:
- CDaoIndexFieldInfo structure [MFC]
- DAO (Data Access Objects), Index Fields collection
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
ms.openlocfilehash: fe2d6bef3ce44e7418474b7f2c004942935968c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250792"
---
# <a name="cdaoindexfieldinfo-structure"></a>CDaoIndexFieldInfo 구조체

구조에는 `CDaoIndexFieldInfo` DAO (data access objects)에 대해 정의 된 인덱스 필드 개체에 대 한 정보가 포함 되어 있습니다.

DAO는 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
struct CDaoIndexFieldInfo
{
    CString m_strName;          // Primary
    BOOL m_bDescending;         // Primary
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
인덱스 필드 개체의 이름을 고유 하 게 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_bDescending*<br/>
인덱스 개체에서 정의한 인덱스 순서를 나타냅니다. 순서가 내림차순 이면 TRUE입니다.

## <a name="remarks"></a>설명

인덱스 개체는 여러 필드를 가질 수 있습니다 .이 필드에는 테이블 형식 (또는 테이블 기반 레코드 집합)이 인덱싱되는 필드가 표시 됩니다. 위의 주에 대 한 참조는 `m_pFieldInfos` [](../../mfc/reference/cdaoindexinfo-structure.md) `GetIndexInfo` [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getindexinfo) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getindexinfo)클래스의 멤버 함수를 호출 하 여 가져온 CDaoIndexInfo 개체의 멤버가 정보를 반환 하는 방법을 표시 합니다.

인덱스 개체와 인덱스 필드 개체는 MFC 클래스로 표현 되지 않습니다. 대신 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 클래스의 기본 MFC 개체에 있는 DAO 개체는 Indexes 컬렉션 이라는 인덱스 개체의 컬렉션을 포함 합니다. 각 인덱스 개체는 field 개체의 컬렉션을 포함 합니다. 이러한 클래스는 인덱스 정보의 개별 항목에 액세스 하는 멤버 함수를 제공 하거나, 포함 하는 `CDaoIndexInfo` `GetIndexInfo` 개체의 멤버 함수를 호출 하 여 개체를 사용 하 여 한 번에 모두 액세스할 수 있습니다. `CDaoIndexInfo`그런 다음 개체에는 `m_pFieldInfos` 개체의 배열을 가리키는 데이터 멤버가 있습니다 `CDaoIndexFieldInfo` .

`GetIndexInfo`인덱스 컬렉션이 관심이 있는 인덱스 개체를 저장 하는 테이블을 포함 하는 테이블 형식이 나 레코드 집합 개체의 멤버 함수를 호출 합니다. 그런 다음 `m_pFieldInfos` [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 개체의 멤버에 액세스 합니다. 배열의 길이는 `m_pFieldInfos` 에 저장 됩니다 `m_nFields` . `CDaoIndexFieldInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoIndexFieldInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef:: GetIndexInfo](../../mfc/reference/cdaotabledef-class.md#getindexinfo)<br/>
[CDaoRecordset:: GetIndexInfo](../../mfc/reference/cdaorecordset-class.md#getindexinfo)
