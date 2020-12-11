---
description: '자세한 정보: 데이터 소스: 프로그래밍 방식으로 ODBC 데이터 소스 구성'
title: '데이터 소스: 프로그래밍 방식으로 ODBC 데이터 소스 구성'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 4d3cab3de1a3b65bd8df9aee2b91bbaf243926d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155724"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>데이터 소스: 프로그래밍 방식으로 ODBC 데이터 소스 구성

이 항목에서는 ODBC (Open Database Connectivity) 데이터 원본 이름을 프로그래밍 방식으로 구성할 수 있는 방법에 대해 설명 합니다. 이렇게 하면 사용자가 ODBC 관리자 또는 다른 프로그램을 명시적으로 사용 하 여 데이터 원본의 이름을 지정 하지 않고도 데이터에 유연 하 게 액세스할 수 있습니다.

일반적으로 연결 된 DBMS (데이터베이스 관리 시스템)가이 작업을 지 원하는 경우 사용자는 ODBC 관리자를 실행 하 여 데이터 원본을 만듭니다.

ODBC 관리자를 통해 Microsoft Access ODBC 데이터 원본을 만들 때 기존 .mdb 파일을 선택 하거나 새 .mdb 파일을 만들 수 있습니다. MFC ODBC 응용 프로그램에서 .mdb 파일을 프로그래밍 방식으로 만들 수 있는 방법은 없습니다. 따라서 응용 프로그램에서 Microsoft Access 데이터 원본 (.mdb 파일)에 데이터를 저장 해야 하는 경우 필요할 때마다 사용 하거나 복사할 수 있는 빈 .mdb 파일을 만들 수 있습니다.

그러나 많은 Dbms에서 프로그래밍 방식으로 데이터 소스를 만들 수 있습니다. 일부 데이터 원본은 데이터베이스의 디렉터리 사양을 유지 관리 합니다. 즉, 디렉터리는 데이터 원본이 고 데이터 원본 내의 각 테이블은 별도의 파일에 저장 됩니다 (dBASE의 경우 각 테이블은 .dbf 파일). Microsoft Access 및 SQL Server 같은 다른 ODBC 데이터베이스의 드라이버를 사용 하려면 데이터 원본을 설정 하기 전에 특정 조건을 충족 해야 합니다. 예를 들어 SQL Server ODBC 드라이버를 사용 하는 경우 SQL Server 컴퓨터를 설정 해야 합니다.

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource 예제

다음 예에서는 ODBC API 함수를 사용 하 여 `::SQLConfigDataSource` 새 excel 데이터 원본 이라는 새 excel 데이터 원본을 만듭니다.

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

데이터 원본은 실제로 디렉터리 (C:\EXCELDIR)입니다. 이 디렉터리가 있어야 합니다. Excel 드라이버는 디렉터리를 데이터 원본으로 사용 하 고 파일을 개별 테이블 (.xls 파일 당 하나의 테이블)로 사용 합니다.

테이블을 만드는 방법에 대 한 자세한 내용은 [데이터 소스: ODBC 데이터 원본에서 프로그래밍 방식으로 테이블 만들기](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)를 참조 하세요.

다음 정보는 ODBC API 함수에 전달 해야 하는 매개 변수에 대해 설명 합니다 `::SQLConfigDataSource` . 을 사용 하려면 `::SQLConfigDataSource` odbcinst.ini 헤더 파일을 포함 하 고 odbcinst.ini 가져오기 라이브러리를 사용 해야 합니다. 또한 Odbccp32.dll는 런타임에 경로에 있어야 합니다 (또는 16 비트의 Odbcinst.dll).

Odbc 관리자 또는 유사한 유틸리티를 사용 하 여 ODBC 데이터 원본 이름을 만들 수 있습니다. 그러나 경우에 따라 사용자가 별도의 유틸리티를 실행할 필요 없이 액세스 권한을 얻으려면 응용 프로그램에서 직접 데이터 원본 이름을 만드는 것이 좋습니다.

ODBC 관리자 (일반적으로 제어판에 설치 됨)는 Windows 레지스트리에 항목을 배치 하 여 새 데이터 소스를 만듭니다 (16 비트의 경우 Odbc.ini 파일). ODBC 드라이버 관리자는이 파일을 쿼리하여 데이터 원본에 대 한 필요한 정보를 가져옵니다. 에 대 한 호출을 제공 해야 하므로 레지스트리에 배치 해야 하는 정보를 알고 있어야 `::SQLConfigDataSource` 합니다.

이 정보는를 사용 하지 않고 레지스트리에 직접 쓸 수도 있지만이를 `::SQLConfigDataSource` 수행 하는 모든 응용 프로그램은 드라이버 관리자가 데이터를 유지 관리 하는 데 사용 하는 현재 기술에 의존 합니다. ODBC 드라이버 관리자의 이후 수정이 데이터 원본에 대 한 레코드 유지를 다른 방식으로 구현 하는 경우이 기술을 사용 하는 모든 응용 프로그램은 중단 됩니다. 일반적으로 API 함수를 제공 하는 경우이 함수를 사용 하는 것이 좋습니다. 예를 들어 함수를 사용 하는 경우 함수는 `::SQLConfigDataSource` Odbc.ini 파일 또는 레지스트리에 올바르게 기록 되기 때문에 코드를 16 비트에서 32 비트로 이식할 수 있습니다.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource 매개 변수

다음은 함수의 매개 변수에 대 한 설명 `::SQLConfigDataSource` 입니다. 대부분의 정보는 Visual C++ 버전 1.5 이상에서 제공 되는 ODBC API *프로그래머 참조* 에서 가져옵니다.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a> 함수 프로토타입

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>설명

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a> 매개 변수 및 사용법

*hwndParent*<br/>
ODBC 드라이버 관리자나 특정 ODBC 드라이버에서 새 데이터 원본에 대 한 추가 정보를 얻기 위해 만드는 모든 대화 상자의 소유자로 지정 된 창입니다. *LpszAttributes* 매개 변수가 충분 한 정보를 제공 하지 않으면 대화 상자가 나타납니다. *HwndParent* 매개 변수는 NULL 일 수 있습니다.

*lpszDriver*<br/>
드라이버 설명입니다. 실제 드라이버 이름 (DLL)이 아닌 사용자에 게 표시 되는 이름입니다.

*lpszAttributes*<br/>
"Keyname = value" 형식의 특성 목록입니다. 이러한 문자열은 목록의 끝에 두 개의 연속 된 null 종결자를 사용 하 여 null 종결자로 구분 됩니다. 이러한 특성은 기본적으로 새 데이터 원본에 대 한 레지스트리로 이동 하는 드라이버 관련 항목입니다. 이 함수에 대 한 ODBC API 참조에 설명 되지 않은 중요 한 키는 새 데이터 원본의 이름을 지정 하는 "DSN" ("데이터 원본 이름")입니다. 나머지 항목은 새 데이터 원본에 대 한 드라이버와 관련이 있습니다. 드라이버가 사용자에 게 새 값에 대 한 대화 상자를 표시할 수 있으므로 모든 항목을 제공할 필요는 없습니다. 이를 발생 시키려면 *hwndParent* 를 NULL로 설정 합니다. 사용자에 게 메시지가 표시 되지 않도록 기본값을 명시적으로 제공할 수도 있습니다.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>ODBC 관리자를 사용 하 여 lpszDriver 매개 변수에 대 한 드라이버 설명을 확인 하려면

1. ODBC 관리자를 실행 합니다.

1. **추가** 를 클릭합니다.

그러면 설치 된 드라이버와 해당 설명의 목록이 제공 됩니다. 이 설명을 *lpszDriver* 매개 변수로 사용 합니다. 설명에 있는 경우 파일 이름 확장명 및 괄호를 포함 하 여 전체 설명 (예: "Excel 파일 (* .xls)")을 사용 합니다.

또는 레지스트리 키 "ODBC 드라이버" (또는 Odbcinst.ini의 ODBC 드라이버] 섹션에서 모든 드라이버 항목 및 설명의 목록을 포함 하는 레지스트리 또는 16 비트의 파일 Odbcinst.ini)를 검사할 수 있습니다.

*LpszAttributes* 매개 변수에 대 한 키 이름 및 값을 확인 하는 한 가지 방법은 이미 구성 된 데이터 원본에 대 한 Odbc.ini 파일을 검사 하는 것입니다 (ODBC 관리자가 구성한 것으로).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>LpszAttributes 매개 변수에 대 한 키 이름 및 값을 찾으려면

1. Windows 레지스트리 편집기를 실행 합니다. 16 비트의 경우 Odbc.ini 파일을 엽니다.

1. 다음 중 하나를 사용 하 여 ODBC 데이터 원본 정보를 찾습니다.

   - 32 비트의 경우 왼쪽 창에서 **HKEY_CURRENT_USER\Software\ODBC\ODBC.INI \ODBC 데이터 원본** 에 대 한 키를 찾습니다.

      오른쪽 창에는 "pub: REG_SZ:" 형식의 항목이 나열 *\<data source name>* 됩니다. 여기서 *\<data source name>* 는 사용 하려는 드라이버에 대해 원하는 설정을 사용 하 여 이미 구성 된 데이터 원본입니다. 원하는 데이터 원본을 선택 합니다 (예: SQL Server). 문자열 "pub:" 다음에 나오는 항목은 순서 대로 *lpszAttributes* 매개 변수에서 사용할 keyname 및 값입니다.

   - 16 비트의 경우 []로 표시 된 Odbc.ini 파일에서 섹션을 찾습니다 *\<data source name>* .

      이 줄 다음의 줄은 "keyname = value" 형식입니다. 이러한 항목은 *lpszAttributes* 매개 변수에 사용할 항목입니다.

또한 사용 하려는 특정 드라이버에 대 한 설명서를 검토 하는 것이 좋습니다. 드라이버에 대 한 온라인 도움말에서 유용한 정보를 찾을 수 있습니다 .이 정보는 ODBC 관리자를 실행 하 여 액세스할 수 있습니다. 이러한 도움말 파일은 일반적으로 Windows NT, Windows 3.1 또는 Windows 95의 WINDOWS\SYSTEM 디렉터리에 배치 됩니다.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>ODBC 드라이버에 대 한 온라인 도움말을 가져오려면

1. ODBC 관리자를 실행 합니다.

1. **추가** 를 클릭합니다.

1. 드라이버 이름을 선택 합니다.

1. **확인** 을 클릭합니다.

ODBC 관리자가 특정 드라이버에 대 한 새 데이터 원본을 만들기 위한 정보를 표시 하는 경우 **도움말** 을 클릭 합니다. 이렇게 하면 일반적으로 드라이버 사용과 관련 된 중요 한 정보가 포함 된 특정 드라이버에 대 한 도움말 파일이 열립니다.

## <a name="see-also"></a>참고 항목

[데이터 원본 (ODBC)](../../data/odbc/data-source-odbc.md)
