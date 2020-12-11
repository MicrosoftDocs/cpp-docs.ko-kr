---
description: '자세히 알아보기: 파일 열기'
title: 파일 열기
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: cad847dc74cd32f93cc8a4a13e4bbe1bd815d815
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112884"
---
# <a name="opening-files"></a>파일 열기

MFC에서 파일을 여는 가장 일반적인 방법은 2 단계 프로세스입니다.

#### <a name="to-open-a-file"></a>파일을 열려면

1. 경로 또는 사용 권한 플래그를 지정 하지 않고 파일 개체를 만듭니다.

   일반적으로 스택 프레임에서 [CFile](reference/cfile-class.md) 변수를 선언 하 여 파일 개체를 만듭니다.

1. 경로 및 권한 플래그를 제공 하 여 파일 개체에 대해 [Open](reference/cfile-class.md#open) 멤버 함수를 호출 합니다.

   `Open`파일이 성공적으로 열린 경우의 반환 값은 0이 아니고, 지정 된 파일을 열 수 없는 경우에는 0이 됩니다. 멤버 함수는 다음과 같이 `Open` 프로토타입화 됩니다.

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   열기 플래그는 파일에 대해 원하는 읽기 전용 권한 등의 사용 권한을 지정 합니다. 가능한 플래그 값은 클래스 내에서 열거형 상수로 정의 `CFile` 되므로 `CFile::` 에서와 같이 ""로 한정 됩니다 `CFile::modeRead` . 파일을 `CFile::modeCreate` 만들려는 경우 플래그를 사용 합니다.

다음 예제에서는 읽기/쓰기 권한을 사용 하 여 새 파일을 만드는 방법을 보여 줍니다 (동일한 경로로 이전 파일 바꾸기).

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> 이 예제에서는 파일을 만들고 엽니다. 문제가 발생 하는 경우 `Open` `CFileException` 여기에 표시 된 것 처럼 호출이 마지막 매개 변수의 개체를 반환할 수 있습니다. TRACE 매크로는 파일 이름과 실패 이유를 나타내는 코드를 모두 출력 합니다. `AfxThrowFileException`자세한 오류 보고가 필요한 경우 함수를 호출할 수 있습니다.

## <a name="see-also"></a>참고 항목

[CFile 클래스](reference/cfile-class.md)<br/>
[CFile:: Open](reference/cfile-class.md#open)<br/>
[파일](files-in-mfc.md)
