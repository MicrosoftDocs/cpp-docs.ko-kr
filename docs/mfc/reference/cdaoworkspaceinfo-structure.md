---
description: '자세히 알아보기: CDaoWorkspaceInfo Structure'
title: CDaoWorkspaceInfo 구조체
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: b89e8787c2103244535e9458650f1f104478b748
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222205"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo 구조체

구조에는 `CDaoWorkspaceInfo` DAO (data access objects) 데이터베이스 액세스에 대해 정의 된 작업 영역에 대 한 정보가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```
struct CDaoWorkspaceInfo
{
    CString m_strName;           // Primary
    CString m_strUserName;       // Secondary
    BOOL m_bIsolateODBCTrans;    // All
};
```

#### <a name="parameters"></a>매개 변수

*m_strName*<br/>
작업 영역 개체의 이름을 고유 하 게 합니다. 이 속성의 값을 직접 검색 하려면 querydef 개체의 [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) 멤버 함수를 호출 합니다. 자세한 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*m_strUserName*<br/>
작업 영역 개체의 소유자를 나타내는 값입니다. 관련 정보는 DAO 도움말의 "UserName 속성" 항목을 참조 하십시오.

*m_bIsolateODBCTrans*<br/>
동일한 ODBC 데이터베이스를 포함 하는 여러 트랜잭션이 격리 되어 있는지 여부를 나타내는 값입니다. 자세한 내용은 [CDaoWorkspace:: SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans)를 참조 하세요. 관련 내용은 DAO 도움말의 "IsolateODBCTrans 속성" 항목을 참조 하십시오.

## <a name="remarks"></a>설명

작업 영역은 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)클래스의 개체입니다. 위의 기본, 보조 및 모든에 대 한 참조는 클래스의 [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) 멤버 함수에서 정보를 반환 하는 방법을 표시 합니다 `CDaoWorkspace` .

[CDaoWorkspace:: GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) 멤버 함수에서 검색 된 정보는 구조체에 저장 됩니다 `CDaoWorkspaceInfo` . `CDaoWorkspaceInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoWorkspaceInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace 클래스](../../mfc/reference/cdaoworkspace-class.md)
