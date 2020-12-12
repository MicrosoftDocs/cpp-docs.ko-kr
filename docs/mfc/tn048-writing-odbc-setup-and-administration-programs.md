---
description: 'TN048: MFC 데이터베이스 응용 프로그램에 대 한 ODBC 설정 및 관리 프로그램 작성에 대해 자세히 알아보세요.'
title: 'TN048: MFC 데이터베이스 애플리케이션에 대한 ODBC 설정 및 관리 프로그램 작성'
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC, installing
- setup, ODBC setup programs
- TN048
- ODBC, and MFC
- MFC, database applications
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
ms.openlocfilehash: bca8616bae8f7243b9e66b2eccc980afa3865842
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215107"
---
# <a name="tn048-writing-odbc-setup-and-administration-programs-for-mfc-database-applications"></a>TN048: MFC 데이터베이스 애플리케이션에 대한 ODBC 설정 및 관리 프로그램 작성

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

MFC 데이터베이스 클래스를 사용 하는 응용 프로그램에는 ODBC 구성 요소를 설치 하는 설치 프로그램이 필요 합니다. 또한 사용 가능한 드라이버에 대 한 정보를 검색 하 고, 기본 드라이버를 지정 하 고, 데이터 원본을 구성 하는 ODBC 관리 프로그램이 필요할 수 있습니다. 이 정보는 ODBC 설치 관리자 API를 사용 하 여 이러한 프로그램을 작성 하는 방법을 설명 합니다.

## <a name="writing-an-odbc-setup-program"></a><a name="_mfcnotes_writing_an_odbc_setup_program"></a> ODBC 설치 프로그램 작성

MFC 데이터베이스 응용 프로그램을 사용 하려면 ODBC 드라이버 관리자 (ODBC.DLL) 및 ODBC 드라이버가 데이터 원본에 액세스할 수 있어야 합니다. 많은 ODBC 드라이버에는 추가 네트워크 및 통신 Dll도 필요 합니다. 대부분의 ODBC 드라이버는 필수 ODBC 구성 요소를 설치 하는 설치 프로그램과 함께 제공 됩니다. MFC 데이터베이스 클래스를 사용 하는 응용 프로그램 개발자는 다음을 수행 합니다.

- 드라이버 관련 설치 프로그램을 사용 하 여 ODBC 구성 요소를 설치 합니다. 이렇게 하려면 개발자 파트에 대 한 추가 작업이 필요 하지 않습니다. 드라이버의 설치 프로그램을 재배포할 수 있습니다.

- 또는 드라이버 관리자와 드라이버를 설치 하는 사용자 고유의 설치 프로그램을 작성할 수 있습니다.

ODBC 설치 관리자 API를 사용 하 여 응용 프로그램 관련 설치 프로그램을 작성할 수 있습니다. 설치 관리자 API의 함수는 ODBC 설치 관리자 DLL에서 구현 됩니다. 즉, 16 비트 Windows에서는 ODBCINST.DLL 하 고 Win32에서는 ODBCCP32.DLL 합니다. 응용 프로그램은 `SQLInstallODBC` 설치 관리자 DLL에서를 호출 하 여 odbc 드라이버 관리자, odbc 드라이버 및 필요한 모든 번역기를 설치할 수 있습니다. 그런 다음 ODBCINST.INI 파일 (또는 NT의 레지스트리)에 설치 된 드라이버와 번역기를 기록 합니다. `SQLInstallODBC` ODBC에 대 한 전체 경로가 필요 합니다. INF 파일-설치할 드라이버 목록이 포함 되어 있으며 각 드라이버를 구성 하는 파일을 설명 합니다. 또한 드라이버 관리자와 번역기에 대 한 유사한 정보를 포함 합니다. Db. INF 파일은 일반적으로 드라이버 개발자가 제공 합니다.

프로그램은 개별 ODBC 구성 요소를 설치할 수도 있습니다. 드라이버 관리자를 설치 하기 위해 프로그램은 먼저 `SQLInstallDriverManager` 설치 관리자 DLL에서를 호출 하 여 드라이버 관리자에 대 한 대상 디렉터리를 가져옵니다. 일반적으로 Windows Dll이 상주 하는 디렉터리입니다. 그런 다음이 프로그램은 ODBC의 [ODBC 드라이버 관리자] 섹션에 있는 정보를 사용 합니다. 설치 디스크의 드라이버 관리자 및 관련 파일을이 디렉터리에 복사 하는 INF 파일 개별 드라이버를 설치 하기 위해 프로그램은 먼저 `SQLInstallDriver` 설치 관리자 DLL에서를 호출 하 여 드라이버 사양을 ODBCINST.INI 파일 (또는 NT의 레지스트리)에 추가 합니다. `SQLInstallDriver` 드라이버의 대상 디렉터리 (일반적으로 Windows Dll이 있는 디렉터리)를 반환 합니다. 그러면 프로그램이 ODBC의 드라이버 섹션에 있는 정보를 사용 합니다. 설치 디스크의 드라이버 DLL 및 관련 파일을이 디렉터리에 복사 하는 INF 파일

ODBC에 대 한 자세한 내용을 보려면 INF, ODBCINST.INI 및 설치 관리자 API 사용에 대 한는 ODBC SDK *프로그래머 참조* , 19 장, Odbc 소프트웨어 설치를 참조 하세요.

## <a name="writing-an-odbc-administrator"></a><a name="_mfcnotes_writing_an_odbc_administrator"></a> ODBC 관리자 작성

MFC 데이터베이스 응용 프로그램은 다음과 같은 두 가지 방법 중 하나로 ODBC 데이터 원본을 설정 하 고 구성할 수 있습니다.

- 프로그램 또는 제어판 항목으로 사용할 수 있는 ODBC 관리자를 사용 합니다.

- 사용자 고유의 프로그램을 만들어 데이터 원본을 구성 합니다.

데이터 원본을 구성 하는 프로그램은 설치 관리자 DLL에 대 한 함수 호출을 수행 합니다. 설치 관리자 DLL이 설치 DLL을 호출 하 여 데이터 소스를 구성 합니다. 각 드라이버에 대 한 설치 DLL이 하나씩 있습니다. 드라이버 DLL 자체 이거나 별도의 DLL 일 수 있습니다. 지원 되는 경우 사용자에 게 드라이버에서 데이터 원본에 연결 하는 데 필요한 정보 및 기본 변환기를 요청 하는 메시지가 표시 됩니다. 그런 다음 설치 관리자 DLL 및 Windows Api를 호출 하 여이 정보를 ODBC.INI 파일 (또는 레지스트리)에 기록 합니다.

사용자가 데이터 원본을 추가, 수정 및 삭제할 수 있는 대화 상자를 표시 하려면 프로그램은 `SQLManageDataSources` 설치 관리자 DLL에서를 호출 합니다. 이 함수는 설치 관리자 DLL이 제어판에서 호출 될 때 호출 됩니다. 데이터 원본을 추가, 수정 또는 삭제 하려면 `SQLManageDataSources` `ConfigDSN` 해당 데이터 원본에 연결 된 드라이버에 대 한 설치 DLL에서를 호출 합니다. 데이터 원본을 직접 추가, 수정 또는 삭제 하기 위해 프로그램은 `SQLConfigDataSource` 설치 관리자 DLL에서를 호출 합니다. 프로그램은 데이터 원본의 이름과 수행할 동작을 지정 하는 옵션을 전달 합니다. `SQLConfigDataSource``ConfigDSN`설치 DLL에서를 호출 하 고에서 인수를 전달 `SQLConfigDataSource` 합니다.

자세한 내용은 ODBC SDK *프로그래머 참조,* 23 장, 설치 Dll 함수 참조 및 24 장 설치 관리자 Dll 함수 참조를 참조 하세요.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
