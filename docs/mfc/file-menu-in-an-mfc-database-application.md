---
description: '자세한 정보: MFC 데이터베이스 응용 프로그램의 파일 메뉴'
title: MFC 데이터베이스 애플리케이션의 파일 메뉴
ms.date: 11/04/2016
helpviewer_keywords:
- File menu
- database applications [MFC], File menu commands
ms.assetid: 92dafb75-c1b3-4860-80a0-87a83bfc36f2
ms.openlocfilehash: d8d229ce9c53e7a79044af2de03778574c18e5dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335890"
---
# <a name="file-menu-in-an-mfc-database-application"></a>MFC 데이터베이스 애플리케이션의 파일 메뉴

MFC 데이터베이스 응용 프로그램을 만들고 serialization을 사용 하지 않는 경우이 질문에 대 한 스타일 지침이 없는 상태에서 파일 메뉴의 열기, 닫기, 저장 및 다른 이름으로 저장 명령을 해석 하는 방법은 다음과 같습니다.

- 파일 메뉴의 열기 명령을 완전히 제거 합니다.

- Open 명령을 "open database"로 해석 하 고 사용자에 게 응용 프로그램에서 인식 하는 데이터 원본 목록을 표시 합니다.

- Open 명령을 "프로필 열기"로 해석 합니다. 직렬화 된 파일을 열기 위해 열린 상태로 유지 하지만, 파일을 사용 하 여 사용자의 기본 설정과 같은 "사용자 프로필" 정보를 포함 하는 serialize 된 문서 (선택적으로 암호 제외)와 가장 최근에 작업 한 데이터 원본을 저장 합니다.

MFC 응용 프로그램 마법사는 문서 관련 파일 메뉴 명령을 사용 하지 않고 응용 프로그램을 만드는 기능을 지원 합니다. **데이터베이스 지원** 페이지에서 **파일 지원 하지 않는 데이터베이스 뷰** 옵션을 선택 합니다.

파일 메뉴 명령을 특별 한 방식으로 해석 하려면 대부분의 파생 클래스에서 하나 이상의 명령 처리기를 재정의 해야 합니다 `CWinApp` . 예를 들어 `OnFileOpen` (명령을 구현 하는)를 완전히 재정의 하 여 `ID_FILE_OPEN` "open database:"를 의미 합니다.

- `OnFileOpen`명령의 프레임 워크의 기본 구현을 완전히 바꾸기 때문에의 기본 클래스 버전을 호출 하지 마세요.

- 대신 처리기를 사용 하 여 데이터 소스를 나열 하는 대화 상자를 표시 합니다. `CDatabase::OpenEx` `CDatabase::Open` 매개 변수 **NULL** 로 또는를 호출 하 여 이러한 대화 상자를 표시할 수 있습니다. 그러면 사용자 컴퓨터에서 사용 가능한 모든 데이터 원본을 표시 하는 ODBC 대화 상자가 열립니다.

- 데이터베이스 응용 프로그램은 일반적으로 전체 문서를 저장 하지 않으므로 serialize 된 문서를 사용 하 여 프로필 정보를 저장 하지 않는 한 저장 및 저장을 구현 하지 않을 수 있습니다. 그렇지 않으면 "commit transaction"과 같은 저장 명령을 구현할 수 있습니다. 이러한 명령을 재정의 하는 방법에 대 한 자세한 내용은 [Technical Note 22](tn022-standard-commands-implementation.md) 를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[Serialization: Serialization과 데이터베이스 입/출력 비교](serialization-serialization-vs-database-input-output.md)
