---
title: 일반적인 FTP 클라이언트 응용 프로그램의 단계
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: ef772438558e5d587962242fdd7f1230cc2b2f25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50560188"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>일반적인 FTP 클라이언트 응용 프로그램의 단계

일반적인 FTP 클라이언트 응용 프로그램을 만듭니다는 [CInternetSession](../mfc/reference/cinternetsession-class.md) 와 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 개체입니다. 이러한 MFC WinInet 클래스 실제로 프록시 형식 설정을 제어 하 고 하지 않습니다 참고 IIS는 다음 작업을 수행 하지 않습니다.

다음 표에서 일반적인 FTP 클라이언트 응용 프로그램에서 수행할 수 있는 단계를 보여 줍니다.

|목표|수행할 작업|효과|
|---------------|----------------------|-------------|
|FTP 세션을 시작합니다.|만들기는 [CInternetSession](../mfc/reference/cinternetsession-class.md) 개체입니다.|WinInet을 초기화하고 서버에 연결합니다.|
|FTP 서버에 연결합니다.|사용 하 여 [cinternetsession:: Getftpconnection](../mfc/reference/cinternetsession-class.md#getftpconnection)합니다.|반환 된 [CFtpConnection](../mfc/reference/cftpconnection-class.md) 개체입니다.|
|서버의 새로운 FTP 디렉터리로 변경합니다.|사용 하 여 [:: Setcurrentdirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)합니다.|서버에서 현재 연결된 디렉터리를 변경합니다.|
|FTP 디렉터리에서 첫 번째 파일을 찾습니다.|사용 하 여 [:: Findfile](../mfc/reference/cftpfilefind-class.md#findfile)합니다.|첫 번째 파일을 찾습니다. 파일이 발견되지 않으면 FALSE를 반환합니다.|
|FTP 디렉터리에서 다음 파일을 찾습니다.|사용 하 여 [:: Findnextfile](../mfc/reference/cftpfilefind-class.md#findnextfile)합니다.|다음 파일을 찾습니다. 파일을 찾을 수 없으면 FALSE를 반환합니다.|
|찾은 파일을 엽니다 `FindFile` 또는 `FindNextFile` 읽기 또는 쓰기에 대 한 합니다.|사용 하 여 [CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile), 파일 이름을 사용 하 여 반환한 [FindFile](../mfc/reference/cftpfilefind-class.md#findfile) 하거나 [FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)합니다.|읽기 또는 쓰기에 대 한 서버에서 파일을 엽니다. 반환 된 [CInternetFile](../mfc/reference/cinternetfile-class.md) 개체입니다.|
|읽거나 파일에 기록 합니다.|사용 하 여 [cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read) 하거나 [CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)합니다.|읽거나 지정한 수가 제공한 버퍼를 사용 하 여 바이트를 씁니다.|
|예외 처리|사용 된 [CInternetException](../mfc/reference/cinternetexception-class.md) 클래스입니다.|모든 공용 인터넷 예외 형식을 처리합니다.|
|FTP 세션을 종료합니다.|삭제 합니다 [CInternetSession](../mfc/reference/cinternetsession-class.md) 개체입니다.|열린 파일 핸들 및 연결을 자동으로 정리합니다.|

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장(WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet 클래스를 사용하여 인터넷 클라이언트 응용 프로그램 작성](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
