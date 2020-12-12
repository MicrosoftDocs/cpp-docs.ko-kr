---
description: '다음에 대 한 자세한 정보: WinInet 기본 사항'
title: WinInet 기본 사항
ms.date: 11/04/2016
helpviewer_keywords:
- OnStatusCallback method [MFC]
- WinInet classes [MFC], displaying progress
- WinInet classes [MFC], about WinInet classes
ms.assetid: 665de5ac-e80d-427d-8d91-2ae466885940
ms.openlocfilehash: 1ba8f9b898476849ca9bbb39b7850bbce3605154
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172780"
---
# <a name="wininet-basics"></a>WinInet 기본 사항

WinInet을 사용 하 여 FTP 지원을 추가 하 여 응용 프로그램 내에서 파일을 다운로드 하 고 업로드할 수 있습니다. [Onstatuscallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) 을 재정의 하 고 *dwcontext* 매개 변수를 사용 하 여 파일을 검색 하 고 다운로드 하는 동안 사용자에 게 진행률 정보를 제공할 수 있습니다.

이 문서에는 다음 항목이 포함 되어 있습니다.

- [매우 간단한 브라우저 만들기](#_core_create_a_very_simple_browser)

- [웹 페이지 다운로드](#_core_download_a_web_page)

- [FTP a 파일](#_core_ftp_a_file)

- [Gopher 디렉터리 검색](#_core_retrieve_a_gopher_directory)

- [파일을 전송 하는 동안 진행률 정보 표시](#_core_display_progress_information_while_transferring_files)

아래 발췌 한 코드에서는 간단한 브라우저를 만들고, 웹 페이지와 FTP 파일을 다운로드 하 고, gopher 파일을 검색 하는 방법을 보여 줍니다. 이는 전체 예제가 아니며 모두 예외 처리가 포함 되지 않습니다.

WinInet에 대 한 자세한 내용은 [Win32 Internet Extensions (wininet)](../mfc/win32-internet-extensions-wininet.md)를 참조 하십시오.

## <a name="create-a-very-simple-browser"></a><a name="_core_create_a_very_simple_browser"></a> 매우 간단한 브라우저 만들기

[!code-cpp[NVC_MFCWinInet#1](../mfc/codesnippet/cpp/wininet-basics_1.cpp)]

## <a name="download-a-web-page"></a><a name="_core_download_a_web_page"></a> 웹 페이지 다운로드

[!code-cpp[NVC_MFCWinInet#2](../mfc/codesnippet/cpp/wininet-basics_2.cpp)]

## <a name="ftp-a-file"></a><a name="_core_ftp_a_file"></a> FTP a 파일

[!code-cpp[NVC_MFCWinInet#3](../mfc/codesnippet/cpp/wininet-basics_3.cpp)]

## <a name="retrieve-a-gopher-directory"></a><a name="_core_retrieve_a_gopher_directory"></a> Gopher 디렉터리 검색

[!code-cpp[NVC_MFCWinInet#4](../mfc/codesnippet/cpp/wininet-basics_4.cpp)]

## <a name="use-onstatuscallback"></a>OnStatusCallback 사용

WinInet 클래스를 사용 하는 경우 응용 프로그램의 [Cinternetsession](../mfc/reference/cinternetsession-class.md) 개체의 [onstatuscallback](../mfc/reference/cinternetsession-class.md#onstatuscallback) 멤버를 사용 하 여 상태 정보를 검색할 수 있습니다. 사용자 고유의 `CInternetSession` 개체를 파생 시키고 `OnStatusCallback` 상태 콜백을 재정의 및 활성화 하는 경우 MFC는 `OnStatusCallback` 해당 인터넷 세션의 모든 활동에 대 한 진행률 정보를 사용 하 여 함수를 호출 합니다.

단일 세션은 여러 연결을 지원할 수 있기 때문에 (해당 수명 동안 여러 다른 고유 작업을 수행할 수 있음) `OnStatusCallback` 특정 연결 또는 트랜잭션으로 각 상태 변경을 식별 하는 메커니즘이 필요 합니다. 이러한 메커니즘은 WinInet 지원 클래스의 많은 멤버 함수에 제공 된 컨텍스트 ID 매개 변수에 의해 제공 됩니다. 이 매개 변수는 항상 **DWORD** 형식이 며 *dwcontext* 로 이름이 지정 됩니다.

특정 인터넷 개체에 할당 된 컨텍스트는 개체의 멤버에 의해 발생 하는 작업을 식별 하는 데만 사용 됩니다 `OnStatusCallback` `CInternetSession` . 에 대 한 호출은 `OnStatusCallback` 여러 매개 변수를 받습니다. 이러한 매개 변수는 함께 작동 하 여 트랜잭션과 연결에 대 한 진행 상황을 응용 프로그램에 알려 줍니다.

개체를 만들 때 `CInternetSession` *dwcontext* 매개 변수를 생성자에 지정할 수 있습니다. `CInternetSession` 자체는 컨텍스트 ID를 사용 하지 않습니다. 대신 고유한 컨텍스트 ID를 명시적으로 가져오지 않는 **Internetconnection** 파생 개체에 컨텍스트 id를 전달 합니다. 그러면 이러한 개체는 `CInternetConnection` `CInternetFile` 다른 컨텍스트 id를 명시적으로 지정 하지 않는 경우 생성 하는 개체와 함께 컨텍스트 id를 전달 합니다. 반면에 사용자 고유의 특정 컨텍스트 ID를 지정 하는 경우 개체 및 해당 컨텍스트 ID와 연결 되는 모든 작업입니다. 컨텍스트 Id를 사용 하 여 함수에서 제공 되는 상태 정보를 식별할 수 있습니다 `OnStatusCallback` .

## <a name="display-progress-information-while-transferring-files"></a><a name="_core_display_progress_information_while_transferring_files"></a> 파일을 전송 하는 동안 진행률 정보 표시

예를 들어 FTP 서버와 연결 하 여 파일을 읽고 웹 페이지를 가져오기 위해 HTTP 서버에 연결 하는 응용 프로그램을 작성 하는 경우에는 `CInternetSession` 개체, 개체 두 개 (a를 사용 하 고 다른 하나는 하나의 개체) `CInternetConnection` `CFtpSession` `CHttpSession` 및 두 개의 개체 `CInternetFile` (각 연결에 대해 하나씩)를 갖게 됩니다. *Dwcontext* 매개 변수에 대 한 기본값을 사용한 경우 `OnStatusCallback` FTP 연결의 진행률을 나타내는 호출과 HTTP 연결의 진행률을 나타내는 호출을 구분할 수 없습니다. 에서 나중에 테스트할 수 있는 *Dwcontext* ID를 지정 하는 경우 `OnStatusCallback` 콜백이 생성 된 작업을 알 수 있습니다.

## <a name="see-also"></a>참고 항목

[MFC 인터넷 프로그래밍 기본 사항](../mfc/mfc-internet-programming-basics.md)<br/>
[Win32 인터넷 확장 (WinInet)](../mfc/win32-internet-extensions-wininet.md)
