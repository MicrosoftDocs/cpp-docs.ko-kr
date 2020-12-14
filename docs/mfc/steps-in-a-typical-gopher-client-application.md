---
description: '자세히 알아보기: 일반적인 Gopher 클라이언트 응용 프로그램의 단계'
title: 일반적인 Gopher 클라이언트 애플리케이션의 단계
ms.date: 11/04/2016
helpviewer_keywords:
- WinInet classes [MFC], gopher
- Internet applications [MFC], gopher client applications
- Gopher client applications [MFC]
- Internet client applications [MFC], gopher table
ms.assetid: 3e4e1869-5da0-453d-8ba9-b648c894bb90
ms.openlocfilehash: 23940457acf52009b6d334deec129324a53a7583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216628"
---
# <a name="steps-in-a-typical-gopher-client-application"></a>일반적인 Gopher 클라이언트 애플리케이션의 단계

다음 표에서는 일반적인 gopher 클라이언트 응용 프로그램에서 수행할 수 있는 단계를 보여 줍니다.

|목표|수행할 작업|효과|
|---------------|----------------------|-------------|
|Gopher 세션을 시작 합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 만듭니다.|WinInet을 초기화하고 서버에 연결합니다.|
|Gopher 서버에 연결 합니다.|[Cinternetsession:: GetGopherConnection](../mfc/reference/cinternetsession-class.md#getgopherconnection)를 사용 합니다.|[CGopherConnection](../mfc/reference/cgopherconnection-class.md) 개체를 반환 합니다.|
|Gopher에서 첫 번째 리소스를 찾습니다.|[CGopherFileFind:: FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)을 사용 합니다.|첫 번째 파일을 찾습니다. 파일이 발견되지 않으면 FALSE를 반환합니다.|
|Gopher에서 다음 리소스를 찾습니다.|[CGopherFileFind:: FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)을 사용 합니다.|다음 파일을 찾습니다. 파일을 찾을 수 없으면 FALSE를 반환합니다.|
|로 찾은 파일이 나 읽기용으로를 엽니다 `FindFile` `FindNextFile` .|[CGopherFileFind:: GetLocator](../mfc/reference/cgopherfilefind-class.md#getlocator)를 사용 하 여 gopher 로케이터를 가져옵니다. [CGopherConnection:: system.windows.forms.openfiledialog.openfile](../mfc/reference/cgopherconnection-class.md#openfile)를 사용 합니다.|로케이터가 지정한 파일을 엽니다. `OpenFile`[CGopherFile](../mfc/reference/cgopherfile-class.md) 개체를 반환 합니다.|
|사용자가 제공 하는 gopher 로케이터를 사용 하 여 파일을 엽니다.|[CGopherConnection:: createlocator](../mfc/reference/cgopherconnection-class.md#createlocator)를 사용 하 여 gopher 로케이터를 만듭니다. [CGopherConnection:: system.windows.forms.openfiledialog.openfile](../mfc/reference/cgopherconnection-class.md#openfile)를 사용 합니다.|로케이터가 지정한 파일을 엽니다. `OpenFile`[CGopherFile](../mfc/reference/cgopherfile-class.md) 개체를 반환 합니다.|
|파일에서 읽습니다.|[CGopherFile](../mfc/reference/cgopherfile-class.md)를 사용 합니다.|사용자가 제공 하는 버퍼를 사용 하 여 지정 된 바이트 수를 읽습니다.|
|예외를 처리합니다.|[Cinternetexception](../mfc/reference/cinternetexception-class.md) 클래스를 사용 합니다.|모든 공용 인터넷 예외 형식을 처리합니다.|
|Gopher 세션을 종료 합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 삭제 합니다.|열린 파일 핸들 및 연결을 자동으로 정리합니다.|

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet 클래스를 사용 하 여 인터넷 클라이언트 응용 프로그램 작성](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
