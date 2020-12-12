---
description: '자세히 알아보기: CGopherFile 클래스'
title: CGopherFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CGopherFile
- AFXINET/CGopherFile
- AFXINET/CGopherFile::CGopherFile
helpviewer_keywords:
- CGopherFile [MFC], CGopherFile
ms.assetid: 3ca9898f-8cdb-4495-bbde-46d40100feda
ms.openlocfilehash: 8f511bdaf3ae6417972ea19465c0392832a2b408
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184077"
---
# <a name="cgopherfile-class"></a>CGopherFile 클래스

Gopher 서버에서 파일을 찾고 읽는 기능을 제공합니다.

> [!NOTE]
> 클래스 `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` 및 해당 멤버는 Windows XP 플랫폼에서 작동 하지 않으므로 더 이상 사용 되지 않지만 이전 플랫폼에서는 계속 작동 합니다.

## <a name="syntax"></a>구문

```
class CGopherFile : public CInternetFile
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CGopherFile:: CGopherFile](#cgopherfile)|`CGopherFile` 개체를 생성합니다.|

## <a name="remarks"></a>설명

이 서비스는 주로 정보를 찾기 위한 메뉴 기반 인터페이스로 작동 하기 때문에 gopher 서비스에서 사용자가 gopher 파일에 데이터를 쓸 수 없습니다. `CGopherFile`멤버 함수 `Write` , 및는 `WriteString` `Flush` 에 대해 구현 되지 않습니다 `CGopherFile` . 개체에서 이러한 함수 `CGopherFile` 를 호출 하면 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)이 반환 됩니다.

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CGopherFile` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CGopherFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cgopherfilecgopherfile"></a><a name="cgopherfile"></a> CGopherFile:: CGopherFile

이 멤버 함수를 호출 하 여 개체를 생성 `CGopherFile` 합니다.

```
CGopherFile(
    HINTERNET hFile,
    CGopherLocator& refLocator,
    CGopherConnection* pConnection);

CGopherFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrLocator,
    DWORD dwLocLen,
    DWORD_PTR dwContext);
```

### <a name="parameters"></a>매개 변수

*hFile*<br/>
HINTERNET 파일에 대 한 핸들입니다.

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md) 개체에 대 한 참조입니다.

*pConnection*<br/>
[CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 개체에 대 한 포인터입니다.

*hSession*<br/>
현재 인터넷 세션에 대 한 핸들입니다.

*pstrLocator*<br/>
Gopher 서버를 찾는 데 사용 되는 문자열에 대 한 포인터입니다. Gopher 로케이터에 대 한 자세한 내용은 [Gopher 세션](cgopherlocator-class.md) 을 참조 하세요.

*dwLocLen*<br/>
*Pstrlocator* 의 바이트 수를 포함 하는 DWORD입니다.

*dwContext*<br/>
열려는 파일의 컨텍스트 식별자에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CGopherFile`Gopher 인터넷 세션 중에 파일에서 읽을 개체가 필요 합니다.

개체를 직접 만들지는 않습니다 `CGopherFile` . 대신 [CGopherConnection:: system.windows.forms.openfiledialog.openfile](../../mfc/reference/cgopherconnection-class.md#openfile) 를 호출 하 여 gopher 서버에서 파일을 엽니다.

## <a name="see-also"></a>참고 항목

[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile 클래스](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherLocator 클래스](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFileFind 클래스](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CGopherConnection 클래스](../../mfc/reference/cgopherconnection-class.md)
