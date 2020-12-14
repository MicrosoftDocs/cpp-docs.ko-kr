---
description: '자세히 알아보기: CDaoErrorInfo Structure'
title: CDaoErrorInfo 구조체
ms.date: 09/17/2019
f1_keywords:
- CDaoErrorInfo
helpviewer_keywords:
- CDaoErrorInfo structure [MFC]
- DAO (Data Access Objects), Errors collection
ms.assetid: cd37ef71-b0b3-401d-bc2b-540c9147f532
ms.openlocfilehash: 3d8ae4bd133c96ef1853c8d087904c7c6eba810d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250961"
---
# <a name="cdaoerrorinfo-structure"></a>CDaoErrorInfo 구조체

구조에는 `CDaoErrorInfo` DAO (data access objects)에 대해 정의 된 오류 개체에 대 한 정보가 포함 되어 있습니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
struct CDaoErrorInfo
{
    long m_lErrorCode;
    CString m_strSource;
    CString m_strDescription;
    CString m_strHelpFile;
    long m_lHelpContext;
};
```

#### <a name="parameters"></a>매개 변수

*m_lErrorCode*<br/>
숫자 DAO 오류 코드입니다. DAO 도움말의 "잡을 수 있는 데이터 액세스 오류" 항목을 참조 하십시오.

*m_strSource*<br/>
원래 오류를 생성 한 개체 또는 응용 프로그램의 이름입니다. Source 속성은 원래 오류를 생성 한 개체를 나타내는 문자열 식을 지정 합니다. 식은 일반적으로 개체의 클래스 이름입니다. 자세한 내용은 DAO 도움말의 "원본 속성" 항목을 참조 하십시오.

*m_strDescription*<br/>
오류와 관련 된 설명이 포함 된 문자열입니다. 자세한 내용은 DAO 도움말의 "Description Property" 항목을 참조 하십시오.

*m_strHelpFile*<br/>
Microsoft Windows 도움말 파일의 정규화 된 경로입니다. 자세한 내용은 DAO 도움말에서 "HelpContext, HelpFile Properties" 항목을 참조 하십시오.

*m_lHelpContext*<br/>
Microsoft Windows 도움말 파일의 항목에 대 한 컨텍스트 ID입니다. 자세한 내용은 DAO 도움말에서 "HelpContext, HelpFile Properties" 항목을 참조 하십시오.

## <a name="remarks"></a>설명

MFC는 클래스의 DAO 오류 개체를 캡슐화 하지 않습니다. 대신, [CDaoException](../../mfc/reference/cdaoexception-class.md) 클래스는 `DBEngine` 모든 작업 영역을 포함 하는 개체인 DAO 개체에 포함 된 Errors 컬렉션에 액세스 하기 위한 인터페이스를 제공 합니다. MFC DAO 작업에서 catch 한 개체를 throw 하는 경우 `CDaoException` mfc는 구조체를 채우고 `CDaoErrorInfo` 예외 개체의 [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) 멤버에 저장 합니다. DAO를 직접 호출 하도록 선택 하는 경우 예외 개체의 [Geterrorinfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) 멤버 함수를 직접 호출 하 여 채워야 합니다 `m_pErrorInfo` .

DAO 오류를 처리 하는 방법에 대 한 자세한 내용은 [예외: 데이터베이스 예외](../../mfc/exceptions-database-exceptions.md)문서를 참조 하세요. 관련 내용은 DAO 도움말의 "오류 개체" 항목을 참조 하십시오.

[CDaoException:: GetErrorInfo](../../mfc/reference/cdaoexception-class.md#geterrorinfo) 멤버 함수에서 검색 된 정보는 구조체에 저장 됩니다 `CDaoErrorInfo` . 예외 처리기에서 catch 한 `CDaoException` 개체에서 [m_pErrorInfo](../../mfc/reference/cdaoexception-class.md#m_perrorinfo) 데이터 멤버를 검사하거나 직접 호출 중에 발생했을 수 있는 오류를 확인하기 위해 명시적으로 만든 `CDaoException` 개체에서 `GetErrorInfo`를 호출합니다. DAO 인터페이스를 대상으로 합니다. `CDaoErrorInfo` 또한 `Dump` 디버그 빌드에서 멤버 함수를 정의 합니다. `Dump`를 사용 하 여 개체의 콘텐츠를 덤프할 수 있습니다 `CDaoErrorInfo` .

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoException 클래스](../../mfc/reference/cdaoexception-class.md)
