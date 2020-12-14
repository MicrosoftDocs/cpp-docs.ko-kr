---
description: '자세한 정보: ODBC 및 MFC'
title: ODBC 및 MFC
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], MFC
- connections [C++], databases
- connections [C++], data source
- databases [C++], connecting to
- data sources [C++], connecting to
- MFC [C++], ODBC and
- database connections [C++], MFC ODBC classes
ms.assetid: 98f02fd7-1235-437b-89a9-edfd0fc797f7
ms.openlocfilehash: 32cc3f9a023a4b965e8872fde27291bf8df3f1a4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195101"
---
# <a name="odbc-and-mfc"></a>ODBC 및 MFC

> [!NOTE]
> MFC 데이터베이스 클래스를 사용 하려면 데이터 원본에 적합 한 ODBC 드라이버가 있어야 합니다. 최신 Microsoft ODBC driver for SQL Server은 [SQL Server 용 MICROSOFT Odbc driver 13](https://www.microsoft.com/download/details.aspx?id=50420)입니다. 대부분의 데이터베이스 공급 업체는 Windows 용 ODBC 드라이버를 제공 합니다.

이 항목에서는 MFC (Microsoft Foundation Classes) 라이브러리의 ODBC 기반 데이터베이스 클래스에 대 한 주요 개념을 소개 하 고 클래스가 함께 작동 하는 방법에 대 한 개요를 제공 합니다. ODBC 및 MFC에 대 한 자세한 내용은 다음 항목을 참조 하십시오.

- [데이터 소스에 연결](connecting-to-a-data-source.md)

- [레코드 선택 및 조작](selecting-and-manipulating-records.md)

- [폼에서 데이터 표시 및 조작](displaying-and-manipulating-data-in-a-form.md)

- [문서 및 뷰 작업](working-with-documents-and-views.md)

- [ODBC 및 SQL 액세스](access-to-odbc-and-sql.md)

- [MFC ODBC 클래스에 대 한 추가 정보](further-reading-about-the-mfc-odbc-classes.md)

ODBC를 기반으로 하는 MFC 데이터베이스 클래스는 ODBC 드라이버를 사용할 수 있는 모든 데이터베이스에 대 한 액세스를 제공 하도록 설계 되었습니다. 클래스가 ODBC를 사용 하기 때문에 응용 프로그램은 다양 한 데이터 형식 및 다른 로컬/원격 구성의 데이터에 액세스할 수 있습니다. 다른 Dbms (데이터베이스 관리 시스템)를 처리 하는 특별 한 사례 코드를 작성할 필요가 없습니다. 사용자에 게 액세스 하려는 데이터에 적합 한 ODBC 드라이버가 있는 경우 프로그램을 사용 하 여 거기에 저장 된 테이블의 데이터를 조작할 수 있습니다.

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](open-database-connectivity-odbc.md)
