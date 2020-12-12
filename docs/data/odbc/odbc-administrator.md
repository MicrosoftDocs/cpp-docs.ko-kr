---
description: '자세한 정보: ODBC 관리자'
title: ODBC 관리자
ms.date: 11/04/2016
helpviewer_keywords:
- installing ODBC
- ODBC data sources [C++], ODBC Administrator
- ODBC drivers [C++], installing
- ODBC [C++], ODBC Administrator
- Administrator in ODBC
- administration ODBC Administrator
- ODBC Administrator [C++]
- drivers [C++], ODBC
ms.assetid: b8652790-3437-4e7d-bc83-6ea6981f008b
ms.openlocfilehash: bbcb0d93884f29a04f20c130f25bee9a5e2556ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317833"
---
# <a name="odbc-administrator"></a>ODBC 관리자

ODBC 관리자는 로컬에서 또는 네트워크를 통해 사용할 수 있는 [데이터 원본을](../../data/odbc/data-source-odbc.md) 등록 하 고 구성 합니다. 마법사는 ODBC 관리자가 제공 하는 정보를 사용 하 여 사용자를 데이터 원본에 연결 하는 코드를 응용 프로그램에 만듭니다.

MFC ODBC 클래스 또는 MFC DAO (Data Access Object) 클래스에서 사용할 ODBC 데이터 원본을 설정 하려면 먼저 데이터 소스를 등록 하 고 구성 해야 합니다. ODBC 관리자를 사용 하 여 데이터 원본을 추가 하 고 제거 합니다. ODBC 드라이버에 따라 새 데이터 원본을 만들 수도 있습니다.

ODBC 관리자는 설치 중에 설치 됩니다. **사용자 지정** 설치를 선택 하 고 **데이터베이스 옵션** 대화 상자에서 ODBC 드라이버를 선택 하지 않은 경우 설치 프로그램을 다시 실행 하 여 필요한 파일을 설치 해야 합니다.

설치 하는 동안 설치 하려는 ODBC 드라이버를 선택 합니다. 나중에 Visual C++ 설치 프로그램을 사용 하 여 Visual C++와 함께 제공 되는 추가 드라이버를 설치할 수 있습니다.

Visual C++와 함께 제공 되지 않는 ODBC 드라이버를 설치 하려면 드라이버와 함께 제공 되는 설치 프로그램을 실행 해야 합니다.

#### <a name="to-install-odbc-drivers-that-ship-with-visual-c"></a>Visual C++와 함께 제공 되는 ODBC 드라이버를 설치 하려면

1. Visual C++ 배포 CD에서 설치 프로그램을 실행 합니다.

   설치 프로그램에서 열기 대화 상자가 나타납니다.

1. **설치 옵션** 대화 상자에 도달할 때까지 각 대화 상자에서 **다음** 을 클릭 합니다. **사용자 지정** 을 선택 하 고 **다음** 을 클릭 합니다.

1. **데이터베이스 옵션** 확인란을 제외 하 고 **Microsoft Visual C++ 설정** 대화 상자에서 모든 확인란의 선택을 취소 한 다음 **세부 정보** 를 클릭 하 여 **데이터베이스 옵션** 대화 상자를 표시 합니다.

1. **Microsoft Data Access Objects** 확인란의 선택을 취소 하 고 **microsoft ODBC Drivers** 확인란을 선택한 다음 **세부 정보** 를 클릭 합니다.

   **MICROSOFT ODBC 드라이버** 대화 상자가 나타납니다.

1. 설치 하려는 드라이버를 선택 하 고 **확인** 을 두 번 클릭 합니다.

1. 나머지 대화 상자에서 **다음** 을 클릭 하 여 설치를 시작 합니다. 설치가 완료 되 면 설치 프로그램이 사용자에 게 알려 줍니다.

드라이버가 설치 되 면 ODBC 관리자를 사용 하 여 데이터 원본을 구성할 수 있습니다. 제어판에서 ODBC 아이콘을 찾을 수 있습니다.

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md)
