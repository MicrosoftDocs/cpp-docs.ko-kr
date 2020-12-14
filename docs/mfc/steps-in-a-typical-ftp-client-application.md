---
description: '자세한 정보: 일반적인 FTP 클라이언트 응용 프로그램의 단계'
title: 일반적인 FTP 클라이언트 애플리케이션의 단계
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: caac613adf3ad886c4b36ae567a3b8c5c928ee10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216641"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>일반적인 FTP 클라이언트 애플리케이션의 단계

일반적인 FTP 클라이언트 응용 프로그램은 [Cinternetsession](../mfc/reference/cinternetsession-class.md) 및 [cinternetsession](../mfc/reference/cftpconnection-class.md) 개체를 만듭니다. 이러한 MFC WinInet 클래스는 실제로 프록시 형식 설정을 제어 하지 않습니다. IIS는

다음 표에서는 일반적인 FTP 클라이언트 응용 프로그램에서 수행할 수 있는 단계를 보여 줍니다.

|목표|수행할 작업|효과|
|---------------|----------------------|-------------|
|FTP 세션을 시작합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 만듭니다.|WinInet을 초기화하고 서버에 연결합니다.|
|FTP 서버에 연결합니다.|[Cinternetsession:: GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection)을 사용 합니다.|[Cftpconnection](../mfc/reference/cftpconnection-class.md) 개체를 반환 합니다.|
|서버의 새로운 FTP 디렉터리로 변경합니다.|[CSetCurrentDirectory connection::](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)를 사용 합니다.|서버에서 현재 연결된 디렉터리를 변경합니다.|
|FTP 디렉터리에서 첫 번째 파일을 찾습니다.|[Cftpfilefind:: FindFile](../mfc/reference/cftpfilefind-class.md#findfile)을 사용 합니다.|첫 번째 파일을 찾습니다. 파일이 발견되지 않으면 FALSE를 반환합니다.|
|FTP 디렉터리에서 다음 파일을 찾습니다.|[Cftpfilefind:: FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)을 사용 합니다.|다음 파일을 찾습니다. 파일을 찾을 수 없으면 FALSE를 반환합니다.|
|에서 찾은 파일이 `FindFile` 나 `FindNextFile` 읽기 또는 쓰기에 대 한 파일을 엽니다.|[Findfile](../mfc/reference/cftpfilefind-class.md#findfile) 또는 [findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)에서 반환 된 파일 이름을 사용 하 여 [Csystem.windows.forms.openfiledialog.openfile connection::](../mfc/reference/cftpconnection-class.md#openfile)를 사용 합니다.|읽기 또는 쓰기를 위해 서버에서 파일을 엽니다. [Cinternetfile](../mfc/reference/cinternetfile-class.md) 개체를 반환 합니다.|
|파일에서 읽거나 파일에 씁니다.|[Cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read) 또는 [Cinternetfile:: Write](../mfc/reference/cinternetfile-class.md#write)를 사용 합니다.|사용자가 제공 하는 버퍼를 사용 하 여 지정 된 바이트 수를 읽거나 씁니다.|
|예외를 처리합니다.|[Cinternetexception](../mfc/reference/cinternetexception-class.md) 클래스를 사용 합니다.|모든 공용 인터넷 예외 형식을 처리합니다.|
|FTP 세션을 종료합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 삭제 합니다.|열린 파일 핸들 및 연결을 자동으로 정리합니다.|

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet 클래스를 사용 하 여 인터넷 클라이언트 응용 프로그램 작성](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
