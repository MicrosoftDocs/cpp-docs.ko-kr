---
title: 동적 접근자 사용 | Microsoft Docs
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- accessors [C++], dynamic
- dynamic accessors
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fed93404a6c11addb8068d6140fda48d1c02a253
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056739"
---
# <a name="using-dynamic-accessors"></a>동적 접근자 사용

동적 접근자를 사용 하면 데이터베이스 스키마 (내부 구조)에 대 한 지식이 없는 경우 데이터 소스에 액세스할 수 있습니다. OLE DB 템플릿 라이브러리는이 작업을 수행 하는 데 몇 가지 클래스를 제공 합니다.

합니다 [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) 샘플 동적 접근자 클래스를 사용 하 여 열 정보를 얻을를 동적으로 접근자를 만드는 방법을 보여 줍니다.

## <a name="using-cdynamicaccessor"></a>CDynamicAccessor를 사용 하 여

[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 데이터베이스 스키마 (데이터베이스의 내부 구조)에 대 한 지식이 없는 경우 데이터 소스에 액세스할 수 있습니다. `CDynamicAccessor` 메서드는 열 이름, 수 및 데이터 형식이 같은 열 정보를 가져옵니다. 이 열 정보를 사용 하 여 접근자를 런타임에 동적으로 만듭니다. 열 정보를 만들고이 클래스에서 관리 하는 버퍼에 저장 됩니다. 사용 하 여 버퍼에서 데이터를 가져올는 [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md) 메서드.

## <a name="example"></a>예제

### <a name="code"></a>코드

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

## <a name="using-cdynamicstringaccessor"></a>CDynamicStringAccessor를 사용 하 여

[CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) 처럼 작동 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), 중요 한 한 가지 제외 합니다. 하는 동안 `CDynamicAccessor` 공급자가 보고 한 원시 형식으로 데이터를 요청 `CDynamicStringAccessor` 는 공급자 문자열 데이터로 데이터 저장소에서 액세스 하는 모든 데이터를 인출 하는 요청입니다. 표시 하거나 데이터 저장소의 내용을 인쇄와 같은 데이터 저장소에 대 한 값을 계산할 필요가 없는 간단한 작업에 특히 유용 합니다.

사용 하 여 `CDynamicStringAccessor` 열 정보를 가져오는 방법입니다. 이 열 정보를 사용 하 여 접근자를 런타임에 동적으로 만듭니다. 열 정보를 만들고이 클래스에 의해 관리 되는 버퍼에 저장 됩니다. 사용 하 여 버퍼에서 데이터를 가져올 [cdynamicstringaccessor:: Getstring](../../data/oledb/cdynamicstringaccessor-getstring.md) 아니면 사용 하 여 버퍼에 저장할 [cdynamicstringaccessor:: Setstring](../../data/oledb/cdynamicstringaccessor-setstring.md)합니다.

## <a name="example"></a>예제

### <a name="code"></a>코드

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

## <a name="using-cdynamicparameteraccessor"></a>CDynamicParameterAccessor를 사용 하 여

[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) 비슷합니다 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md)점을 제외 하 고 `CDynamicParameterAccessor` 호출 하 여 설정할 매개 변수 정보를 가져오는 데는 [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) 인터페이스입니다. 공급자는 이 클래스를 사용할 소비자에 대해 `ICommandWithParameters` 를 지원해야 합니다.

매개 변수 정보는 이 클래스로 만들고 관리하는 버퍼에 저장됩니다. 매개 변수 데이터를 사용 하 여 버퍼에서 가져올 [cdynamicparameteraccessor:: Getparam](../../data/oledb/cdynamicparameteraccessor-getparam.md) 하 고 [cdynamicparameteraccessor:: Getparamtype](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)합니다.

SQL Server 저장 프로시저를 실행 하 고 출력 매개 변수 값을 가져옵니다이 클래스를 사용 하는 방법을 보여주는 예제를 참조 하세요. 합니다 [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) 샘플에서 코드를 [Microsoft 사용자를 위해](https://github.com/Microsoft/VCSamples) GitHub의 리포지토리를 제공 합니다.

## <a name="see-also"></a>참고자료

[접근자 사용](../../data/oledb/using-accessors.md)<br/>
[CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor Class](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[DynamicConsumer 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer)  