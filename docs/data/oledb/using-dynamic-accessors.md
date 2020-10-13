---
title: 동적 접근자 사용
ms.date: 10/18/2018
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
ms.openlocfilehash: 4f42d6f20da819cf325cad06a04878b46e52352a
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008685"
---
# <a name="using-dynamic-accessors"></a>동적 접근자 사용

동적 접근자를 사용 하면 데이터베이스 스키마 (기본 구조)에 대 한 지식이 없을 때 데이터 원본에 액세스할 수 있습니다. OLE DB 템플릿 라이브러리는 도움이 되는 몇 가지 클래스를 제공 합니다.

[Dynamicconsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) 샘플은 동적 접근자 클래스를 사용 하 여 열 정보를 가져오고 접근자를 동적으로 만드는 방법을 보여 줍니다.

## <a name="using-cdynamicaccessor"></a>CDynamicAccessor 사용

[Cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md) 를 사용 하면 데이터베이스 스키마 (데이터베이스의 기본 구조)에 대 한 지식이 없을 때 데이터 원본에 액세스할 수 있습니다. `CDynamicAccessor` 메서드는 열 이름, 개수, 데이터 형식 등의 열 정보를 가져옵니다. 이 열 정보를 사용 하 여 런타임에 동적으로 접근자를 만들 수 있습니다. 열 정보는이 클래스로 만들고 관리 하는 버퍼에 저장 됩니다. [GetValue](./cdynamicaccessor-class.md#getvalue) 메서드를 사용 하 여 버퍼에서 데이터를 가져옵니다.

## <a name="example-cdynamic-accessors"></a>예: CDynamic 접근자

```cpp
// Using_Dynamic_Accessors.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );

    CDataSource ds;
    CSession ss;

    CTable<CDynamicAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            DBTYPE type;
            rs.GetColumnType(i, &type );
            printf_s( "Column %d [%S] is of type %d\n",
                      i, rs.GetColumnName(i ), type );

            switch(type )
            {
                case DBTYPE_WSTR:
                    printf_s( "value is %S\n",
                              (WCHAR*)rs.GetValue(i ) );
                break;
                case DBTYPE_STR:
                    printf_s( "value is %s\n",
                              (CHAR*)rs.GetValue(i ) );
                default:
                    printf_s( "value is %d\n",
                              *(long*)rs.GetValue(i ) );
            }
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

    return 0;
}
```

## <a name="using-cdynamicstringaccessor"></a>CDynamicStringAccessor 사용

[Cdynamicstringaccessor](../../data/oledb/cdynamicstringaccessor-class.md) 는 한 가지 중요 한 방법을 제외 하 고 [cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md)와 유사 하 게 작동 합니다. 는 `CDynamicAccessor` 공급자가 보고 하는 네이티브 형식으로 데이터를 요청 하 고는 `CDynamicStringAccessor` 공급자가 데이터 저장소에서 액세스 한 모든 데이터를 문자열 데이터로 가져오도록 요청 합니다. 이 프로세스는 데이터 저장소의 내용 표시 또는 인쇄와 같이 데이터 저장소의 값을 계산할 필요가 없는 간단한 작업에 특히 유용 합니다.

`CDynamicStringAccessor`메서드를 사용 하 여 열 정보를 가져옵니다. 이 열 정보를 사용 하 여 런타임에 동적으로 접근자를 만들 수 있습니다. 열 정보는이 클래스에서 만들고 관리 하는 버퍼에 저장 됩니다. [Cdynamicstringaccessor](./cdynamicstringaccessor-class.md#getstring) :: GetString를 사용 하 여 버퍼에서 데이터를 가져오거나 [Cdynamicstringaccessor:: setstring](./cdynamicstringaccessor-class.md#setstring)을 사용 하 여 버퍼에 저장 합니다.

## <a name="example-cdynamicstringaccessor"></a>예: CDynamicStringAccessor

```cpp
// Using_Dynamic_Accessors_b.cpp
// compile with: /c /EHsc
#include <stdio.h>
#include <objbase.h>
#include <atldbcli.h>

int main(int argc, char* argv[] )
{
    HRESULT hr = CoInitialize(NULL );
    if (hr != S_OK)
    {
        exit (-1);
    }

    CDataSource ds;
    CSession ss;

    CTable<CDynamicStringAccessor> rs;

    // The following is an example initialization string:
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"
      L"Integrated Security=SSPI;Persist Security Info=False;"
      L"Initial Catalog=Loginname;Data Source=your_data_source;"
      L"Use Procedure for Prepare=1;Auto Translate=True;"
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"
      L"Use Encryption for Data=False;"
      L"Tag with column collation when possible=False");

    hr = ss.Open(ds );
    hr = rs.Open(ss, "Shippers" );

    hr = rs.MoveFirst();
    while(SUCCEEDED(hr ) && hr != DB_S_ENDOFROWSET )
    {
        for(size_t i = 1; i <= rs.GetColumnCount(); i++ )
        {
            printf_s( "column %d value is %s\n",
                      i, rs.GetString(i ) );
        }
        hr = rs.MoveNext();
    }

    rs.Close();
    ss.Close();
    ds.Close();
    CoUninitialize();

   return 0;
}
```

## <a name="using-cdynamicparameteraccessor"></a>CDynamicParameterAccessor 사용

[Cdynamicparameteraccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 는 ICommandWithParameters 인터페이스를 호출 하 여 설정할 매개 변수 정보를 가져오는 점을 제외 하 고 [cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md)와 유사 `CDynamicParameterAccessor` 합니다. [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) 공급자는 이 클래스를 사용할 소비자에 대해 `ICommandWithParameters` 를 지원해야 합니다.

매개 변수 정보는 이 클래스로 만들고 관리하는 버퍼에 저장됩니다. [Cdynamicparameteraccessor:: GetParam](./cdynamicparameteraccessor-class.md#getparam) 및 [Cdynamicparameteraccessor:: GetParamType](./cdynamicparameteraccessor-class.md#getparamtype)를 사용 하 여 버퍼에서 매개 변수 데이터를 가져옵니다.

이 클래스를 사용 하 여 SQL Server 저장 프로시저를 실행 하 고 출력 매개 변수 값을 가져오는 방법을 보여 주는 예제는 GitHub의 [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) 리포지토리에서 [dynamicconsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) 샘플 코드를 참조 하세요.

## <a name="see-also"></a>참조

[접근자 사용](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 클래스](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)
