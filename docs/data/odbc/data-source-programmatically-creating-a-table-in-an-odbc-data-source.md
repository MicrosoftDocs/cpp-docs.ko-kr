---
description: '자세한 정보: 데이터 소스: ODBC 데이터 소스에서 프로그래밍 방식으로 테이블 작성'
title: ODBC 데이터 원본에서 프로그래밍 방식으로 테이블 만들기
ms.date: 11/04/2016
helpviewer_keywords:
- programmatically creating ODBC tables [C++]
- tables [C++]
- ODBC data sources, creating tables in
- tables [C++], creating programmatically
ms.assetid: 9ca68fb5-c3df-424a-a75c-e3fb01cc1b18
ms.openlocfilehash: b195cc4fb81f1caed0b280c5df6a2032f4944ddf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155711"
---
# <a name="data-source-programmatically-creating-a-table-in-an-odbc-data-source"></a>데이터 소스: ODBC 데이터 소스에서 프로그래밍 방식으로 테이블 작성

이 항목에서는 `ExecuteSQL` 클래스의 멤버 함수를 사용 하 여 `CDatabase` 함수를 **CREATE TABLE** SQL 문을 포함 하는 문자열에 전달 하 여 데이터 원본에 대 한 테이블을 만드는 방법에 대해 설명 합니다.

MFC의 ODBC 데이터 원본에 대 한 일반 정보는 [데이터 원본 (odbc)](../../data/odbc/data-source-odbc.md)을 참조 하세요. 항목 [데이터 원본: 프로그래밍 방식으로 ODBC 데이터 소스를 구성](../../data/odbc/data-source-programmatically-configuring-an-odbc-data-source.md) 하는 방법에 대해서는 데이터 원본 만들기를 설명 합니다.

데이터 원본을 설정 하면 `ExecuteSQL` 멤버 함수 및 **CREATE TABLE** SQL 문을 사용 하 여 테이블을 쉽게 만들 수 있습니다. 예를 들어 라는 개체가 있는 경우 `CDatabase` `myDB` 다음 MFC 코드를 사용 하 여 테이블을 만들 수 있습니다.

```
myDB.ExecuteSQL("CREATE TABLE OFFICES (OfficeID TEXT(4)" ",
                         OfficeName TEXT(10))");
```

이 코드 예제에서는에 의해 유지 관리 되는 Microsoft Access 데이터 원본 연결에서 "사무실" 이라는 테이블을 만듭니다 .이 테이블에는 `myDB` "OfficeName id" 및 "" 라는 두 개의 필드가 있습니다.

> [!NOTE]
> **CREATE TABLE** SQL 문에 지정 된 필드 형식은 사용 하는 ODBC 드라이버에 따라 달라질 수 있습니다. Microsoft Query program (Visual C++ 1.5과 함께 배포)은 데이터 원본에 사용할 수 있는 필드 형식을 검색 하는 한 가지 방법입니다. Microsoft Query에서 **파일**, **Table_Definition** 을 차례로 클릭 하 고 데이터 원본에서 테이블을 선택 하 고 **유형** 콤보 상자에 표시 된 유형을 확인 합니다. 인덱스를 만드는 데에도 SQL 구문이 있습니다.

## <a name="see-also"></a>참고 항목

[데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md)
