---
description: '자세히 알아보기: CDaoDatabaseInfo Structure'
title: CDaoDatabaseInfo 구조체
ms.date: 09/17/2019
f1_keywords:
- CDaoDatabaseInfo
helpviewer_keywords:
- CDaoDatabaseInfo structure [MFC]
- DAO (Data Access Objects), Databases collection
ms.assetid: 68e9e0da-8382-4fc6-8115-1b1519392ddb
ms.openlocfilehash: 9c516821ce401f390538537233ec465f3f520458
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250987"
---
# <a name="cdaodatabaseinfo-structure"></a>CDaoDatabaseInfo 구조체

구조에는 `CDaoDatabaseInfo` DAO (data access objects)에 대해 정의 된 데이터베이스 개체에 대 한 정보가 포함 되어 있습니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
struct CDaoDatabaseInfo
{
    CString m_strName;       // Primary
    BOOL m_bUpdatable;       // Primary
    BOOL m_bTransactions;    // Primary
    CString m_strVersion;    // Secondary
    long m_lCollatingOrder;  // Secondary
    short m_nQueryTimeout;   // Secondary
    CString m_strConnect;    // All
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
데이터베이스 개체의 이름을 고유 하 게 합니다. 이 속성을 직접 검색 하려면 [CDaoDatabase:: GetName](../../mfc/reference/cdaodatabase-class.md#getname)를 호출 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_bUpdatable*<br/>
데이터베이스에 대 한 변경 내용을 적용할 수 있는지 여부를 나타냅니다. 이 속성을 직접 검색 하려면 [CDaoDatabase:: CanUpdate](../../mfc/reference/cdaodatabase-class.md#canupdate)를 호출 합니다. 자세한 내용은 DAO 도움말의 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

*m_bTransactions*<br/>
데이터 원본이 트랜잭션을 지원 하는지 여부를 나타냅니다 .이는 나중에 롤백 (취소) 또는 커밋 (저장) 할 수 있는 일련의 변경 내용에 대 한 기록입니다. 데이터베이스가 Microsoft Jet 데이터베이스 엔진을 기반으로 하는 경우 트랜잭션 속성은 0이 아니며 트랜잭션을 사용할 수 있습니다. 다른 데이터베이스 엔진은 트랜잭션을 지원 하지 않을 수 있습니다. 이 속성을 직접 검색 하려면 [CDaoDatabase:: CanTransact](../../mfc/reference/cdaodatabase-class.md#cantransact)을 호출 합니다. 자세한 내용은 DAO 도움말의 "트랜잭션 속성" 항목을 참조 하십시오.

*m_strVersion*<br/>
Microsoft Jet 데이터베이스 엔진의 버전을 나타냅니다. 이 속성의 값을 직접 검색 하려면 데이터베이스 개체의 [GetVersion](../../mfc/reference/cdaodatabase-class.md#getversion) 멤버 함수를 호출 합니다. 자세한 내용은 DAO 도움말의 "버전 속성" 항목을 참조 하십시오.

*m_lCollatingOrder*<br/>
텍스트에서 문자열 비교 또는 정렬 순서를 지정 합니다. 가능한 값은 다음과 같습니다.

- `dbSortGeneral` 일반 (영어, 프랑스어, 독일어, 포르투갈어, 이탈리아어 및 현대 스페인어) 정렬 순서를 사용 합니다.

- `dbSortArabic` 아랍어 정렬 순서를 사용 합니다.

- `dbSortCyrillic` 러시아어 정렬 순서를 사용 합니다.

- `dbSortCzech` 체코어 정렬 순서를 사용 합니다.

- `dbSortDutch` 네덜란드어 정렬 순서를 사용 합니다.

- `dbSortGreek` 그리스어 정렬 순서를 사용 합니다.

- `dbSortHebrew` 히브리어 정렬 순서를 사용 합니다.

- `dbSortHungarian` 헝가리어 정렬 순서를 사용 합니다.

- `dbSortIcelandic` 아이슬란드어 정렬 순서를 사용 합니다.

- `dbSortNorwdan` 노르웨이어 또는 덴마크어 정렬 순서를 사용 합니다.

- `dbSortPDXIntl` Paradox 국제 정렬 순서를 사용 합니다.

- `dbSortPDXNor` Paradox 노르웨이어 또는 덴마크어 정렬 순서를 사용 합니다.

- `dbSortPDXSwe` Paradox 스웨덴어 또는 핀란드어 정렬 순서를 사용 합니다.

- `dbSortPolish` 폴란드어 정렬 순서를 사용 합니다.

- `dbSortSpanish` 스페인어 정렬 순서를 사용 합니다.

- `dbSortSwedFin` 스웨덴어 또는 핀란드어 정렬 순서를 사용 합니다.

- `dbSortTurkish` 터키어 정렬 순서를 사용 합니다.

- `dbSortUndefined` 정렬 순서가 정의 되지 않았거나 알 수 없습니다.

자세한 내용은 DAO 도움말의 "데이터 액세스에 대 한 Windows 레지스트리 설정 사용자 지정" 항목을 참조 하십시오.

*m_nQueryTimeout*<br/>
Microsoft Jet 데이터베이스 엔진이 ODBC 데이터베이스에서 쿼리를 실행할 때 시간 초과 오류가 발생 하기 전까지 대기 하는 시간 (초)입니다. 기본 시간 제한 값은 60 초입니다. QueryTimeout을 0으로 설정 하면 시간 제한이 발생 하지 않습니다. 이로 인해 프로그램의 응답이 중지 될 수 있습니다. 이 속성의 값을 직접 검색 하려면 데이터베이스 개체의 [GetQueryTimeout](../../mfc/reference/cdaodatabase-class.md#getquerytimeout) 멤버 함수를 호출 합니다. 자세한 내용은 DAO 도움말의 "QueryTimeout 속성" 항목을 참조 하십시오.

*m_strConnect*<br/>
열려 있는 데이터베이스의 원본에 대 한 정보를 제공 합니다. 연결 문자열에 대 한 자세한 내용과이 속성의 값을 직접 검색 하는 방법에 대 한 자세한 내용은 [CDaoDatabase:: GetConnect](../../mfc/reference/cdaodatabase-class.md#getconnect) 멤버 함수를 참조 하세요. 자세한 내용은 DAO 도움말의 "연결 속성" 항목을 참조 하십시오.

## <a name="remarks"></a>설명

데이터베이스는 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)클래스의 MFC 개체 내부에 있는 DAO 개체입니다. 위의 기본, 보조 및 모든에 대 한 참조는 [CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다.

[CDaoWorkspace:: GetDatabaseInfo](../../mfc/reference/cdaoworkspace-class.md#getdatabaseinfo) 멤버 함수에서 검색 된 정보는 구조체에 저장 됩니다 `CDaoDatabaseInfo` . `GetDatabaseInfo` `CDaoWorkspace` 데이터베이스 컬렉션 데이터베이스 개체가 저장 된 개체에 대해를 호출 합니다. `CDaoDatabaseInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoDatabaseInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 클래스](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)
