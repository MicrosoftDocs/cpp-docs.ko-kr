---
description: '자세한 정보: 일반적인 인터넷 클라이언트 응용 프로그램의 단계'
title: 일반적인 인터넷 클라이언트 애플리케이션의 단계
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], general table
- WinInet classes [MFC], programming
- Internet applications [MFC], client applications
ms.assetid: 7aba135c-7c15-4e2f-8c34-bbaf792c89a6
ms.openlocfilehash: 9660687136361efb0256ecdd1fd19b577c46ab26
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216550"
---
# <a name="steps-in-a-typical-internet-client-application"></a>일반적인 인터넷 클라이언트 애플리케이션의 단계

다음 표에서는 일반적인 인터넷 클라이언트 응용 프로그램에서 수행할 수 있는 단계를 보여 줍니다.

|목표|수행할 작업|효과|
|---------------|----------------------|-------------|
|인터넷 세션을 시작 합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 만듭니다.|WinInet을 초기화하고 서버에 연결합니다.|
|인터넷 쿼리 옵션 (예: 시간 제한 또는 다시 시도 횟수)을 설정 합니다.|[Cinternetsession:: SetOption](../mfc/reference/cinternetsession-class.md#setoption)를 사용 합니다.|작업에 실패 한 경우 FALSE를 반환 합니다.|
|세션 상태를 모니터링 하는 콜백 함수를 설정 합니다.|[Cinternetsession:: EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)을 사용 합니다.|[Cinternetsession:: OnStatusCallback](../mfc/reference/cinternetsession-class.md#onstatuscallback)에 대 한 콜백을 설정 합니다. `OnStatusCallback`사용자 고유의 콜백 루틴을 만들려면를 재정의 합니다.|
|인터넷 서버, 인트라넷 서버 또는 로컬 파일에 연결 합니다.|[Cinternetsession:: OpenURL](../mfc/reference/cinternetsession-class.md#openurl)을 사용 합니다.|URL을 구문 분석 하 고 지정 된 서버에 대 한 연결을 엽니다. 로컬 파일 이름을 전달 하는 경우 [CStdioFile](../mfc/reference/cstdiofile-class.md) 를 반환 `OpenURL` 합니다. 서버 또는 파일에서 검색 된 데이터에 액세스 하는 데 사용 되는 개체입니다.|
|파일에서 읽습니다.|[Cinternetfile:: Read](../mfc/reference/cinternetfile-class.md#read)를 사용 합니다.|제공 하는 버퍼를 사용 하 여 지정 된 바이트 수를 읽습니다.|
|예외를 처리합니다.|[Cinternetexception](../mfc/reference/cinternetexception-class.md) 클래스를 사용 합니다.|모든 공용 인터넷 예외 형식을 처리합니다.|
|인터넷 세션을 종료 합니다.|[Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체를 삭제 합니다.|열린 파일 핸들 및 연결을 자동으로 정리합니다.|

## <a name="see-also"></a>참고 항목

[Win32 인터넷 확장 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[인터넷 클라이언트 클래스의 필수 구성 요소](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet 클래스를 사용 하 여 인터넷 클라이언트 응용 프로그램 작성](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
