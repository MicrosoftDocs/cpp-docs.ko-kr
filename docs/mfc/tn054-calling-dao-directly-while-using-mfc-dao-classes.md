---
description: '자세히 알아보기: TN054: MFC DAO 클래스를 사용 하는 동안 직접 DAO 호출'
title: 'TN054: MFC DAO 클래스를 사용하면서 직접 DAO 호출'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
ms.openlocfilehash: e374f283639fde095d63f2626246c97d5606466e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214964"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>TN054: MFC DAO 클래스를 사용하면서 직접 DAO 호출

> [!NOTE]
> DAO는 Access 데이터베이스에 사용 되며 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다. Visual C++ 환경과 마법사는 dao를 지원 하지 않습니다 (DAO 클래스가 포함 되어 있지만 계속 사용할 수 있음). 새 프로젝트에 [OLE DB 템플릿](../data/oledb/ole-db-templates.md) 또는 [ODBC 및 MFC](../data/odbc/odbc-and-mfc.md) 를 사용 하는 것이 좋습니다. DAO는 기존 응용 프로그램을 유지 관리 하는 데만 사용 해야 합니다.

MFC DAO 데이터베이스 클래스를 사용 하는 경우 DAO를 직접 사용 해야 하는 경우가 있을 수 있습니다. 일반적으로이는 그렇지 않지만 mfc 클래스 사용과 직접 DAO 호출을 결합 하는 경우 직접 DAO 호출을 용이 하 게 하는 도우미 메커니즘을 제공 합니다. MFC 관리 DAO 개체의 메서드에 대 한 직접 DAO 호출을 수행 하려면 몇 줄의 코드만 필요 합니다. MFC를 통해 관리 *되지* 않는 DAO 개체를 만들고 사용 해야 하는 경우 실제로 개체에 대해를 호출 하 여 좀 더 많은 작업을 수행 해야 합니다 `Release` . 이 기술 정보는 DAO를 직접 호출할 수 있는 경우, MFC 도우미가 도움을 주는 기능 및 DAO OLE 인터페이스를 사용 하는 방법을 설명 합니다. 마지막으로,이 참고는 DAO 보안 기능에 대해 DAO를 직접 호출 하는 방법을 보여 주는 몇 가지 샘플 함수를 제공 합니다.

## <a name="when-to-make-direct-dao-calls"></a>직접 DAO 호출을 수행 해야 하는 경우

직접 DAO 호출을 수행 하는 가장 일반적인 상황은 컬렉션을 새로 고쳐야 할 때 또는 MFC에서 래핑된 기능을 구현 하는 경우에 발생 합니다. MFC에서 노출 하지 않는 가장 중요 한 기능은 보안입니다. 보안 기능을 구현 하려는 경우에는 DAO 사용자 및 그룹 개체를 직접 사용 해야 합니다. 보안 외에도 몇 가지 다른 DAO 기능이 MFC에서 지원 되지 않습니다. 여기에는 몇 가지 런타임에 DAO를 추가 하는 레코드 집합 복제 및 데이터베이스 복제 기능이 포함 됩니다.

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>DAO 및 MFC 구현에 대 한 간략 한 개요

MFC의 DAO를 래핑하는 경우에는 몇 가지 세부 정보를 처리 하 여 DAO를 더 쉽게 사용할 수 있으므로 걱정할 필요가 없습니다. 여기에는 OLE 초기화, DAO 개체의 생성 및 관리 (특히 컬렉션 개체), 오류 검사, 강력한 형식의 간단한 인터페이스 제공 ( **변형** 또는 인수 없음)이 포함 됩니다 `BSTR` . 직접 DAO 호출을 수행할 수 있으며 이러한 기능을 계속 사용할 수 있습니다. 모든 코드는 `Release` 직접 DAO 호출로 생성 된 개체에 대해 호출 해야 하며 MFC에서 내부적으로 사용할 수 있는 인터페이스 포인터를 수정 *하지* 않아야 합니다. 예를 들어 모든 내부 결과를 이해 하지 않는 한 열려 있는 개체의 *m_pDAORecordset* 멤버를 수정 하지 마십시오 `CDaoRecordset` .  그러나 *m_pDAORecordset* 인터페이스를 사용 하 여 DAO를 직접 호출 하 여 필드 컬렉션을 가져올 수 있습니다. 이 경우 *m_pDAORecordset* 멤버가 수정 되지 않습니다. 개체를 완료 한 경우에는 `Release` Fields 컬렉션 개체에 대해를 호출 하기만 하면 됩니다.

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>DAO 호출을 용이 하 게 하는 도우미 설명

DAO를 쉽게 호출할 수 있도록 제공 되는 도우미는 MFC DAO 데이터베이스 클래스에서 내부적으로 사용 되는 것과 동일한 도우미입니다. 이러한 도우미는 직접 DAO 호출을 수행 하 고, 디버그 출력을 로깅하고, 예상 되는 오류를 확인 하 고, 필요한 경우 적절 한 예외를 throw 할 때 반환 코드를 확인 하는 데 사용 됩니다. 이러한 두 도우미 중 하나에 매핑되는 두 개의 기본 도우미 함수와 4 개의 매크로가 있습니다. 가장 좋은 설명은 간단히 코드를 읽기만 하는 것입니다. AFXDAO의 **DAO_CHECK**, **DAO_CHECK_ERROR**, **DAO_CHECK_MEM** 및 **DAO_TRACE** 을 참조 하세요. H를 참조 하 여 매크로를 확인 하 고 **AfxDaoCheck** 및 **AfxDaoTrace** in daocore .CPP.

## <a name="using-the-dao-ole-interfaces"></a>DAO OLE 인터페이스 사용

DAO 개체 계층의 각 개체에 대 한 OLE 인터페이스는 헤더 파일 DBDAOINT에 정의 되어 있습니다. H는 FileFiles\Microsoft Visual Studio .NET 2003 \ VC7\include 디렉터리에 있습니다. 이러한 인터페이스는 전체 DAO 계층 구조를 조작할 수 있는 메서드를 제공 합니다.

DAO 인터페이스의 여러 메서드에 대해 `BSTR` 개체 (OLE 자동화에서 사용 되는 길이 접두사가 있는 문자열)를 조작 해야 합니다. `BSTR`일반적으로 개체는 **VARIANT** 데이터 형식 내에 캡슐화 됩니다. MFC 클래스 `COleVariant` 자체는 **VARIANT** 데이터 형식에서 상속 됩니다. ANSI 또는 유니코드를 위해 프로젝트를 빌드 하는지에 따라 DAO 인터페이스는 ANSI 또는 유니코드 s를 반환 `BSTR` 합니다. V_BSTR 및 V_BSTRT 두 매크로는 DAO 인터페이스가 필요한 형식의를 가져오는 데 유용 합니다 `BSTR` .

V_BSTR은의 *bstrVal* 멤버를 추출 합니다 `COleVariant` . 이 매크로는의 내용을 `COleVariant` DAO 인터페이스의 메서드에 전달 해야 하는 경우에 일반적으로 사용 됩니다. 다음 코드 조각에서는 V_BSTR 매크로를 활용 하는 DAO DAOUser 인터페이스의 두 메서드에 대 한 선언과 실제 사용을 모두 보여 줍니다.

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

`VT_BSTRT`위의 생성자에 지정 된 인수는 응용 프로그램 `COleVariant` `BSTR` `COleVariant` 의 ansi 버전 및 유니코드 `BSTR` 버전의 응용 프로그램에 대 한 유니코드를 빌드하는 경우에 ansi가 있는지 확인 합니다. 이는 DAO가 필요로 하는 것입니다.

다른 매크로 V_BSTRT은  `COleVariant` 빌드 유형 (ansi 또는 유니코드)에 따라의 Ansi 또는 유니코드 bstrVal 멤버를 추출 합니다. 다음 코드에서는에서로 값을 추출 하는 방법을 보여 줍니다 `BSTR` `COleVariant` `CString` .

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

V_BSTRT 매크로는에 저장 된 다른 형식을 여는 다른 기술과 함께 `COleVariant` DAOVIEW 샘플에 나와 있습니다. 특히이 변환은 메서드에서 수행 됩니다 `CCrack::strVARIANT` . 가능 하면이 메서드는의 값을 `COleVariant` 의 인스턴스로 변환 `CString` 합니다.

## <a name="simple-example-of-a-direct-call-to-dao"></a>DAO에 대 한 직접 호출의 간단한 예

기본 DAO 컬렉션 개체를 새로 고쳐야 하는 경우에 발생할 수 있습니다. 일반적으로이 작업은 필요 하지 않지만 필요한 경우 간단한 절차입니다. 컬렉션을 새로 고쳐야 하는 경우의 예는 새 테이블을 만드는 여러 사용자가 있는 다중 사용자 환경에서 작동 하는 경우입니다. 이 경우에는 테이블의 컬렉션이 부실 해질 수 있습니다. 컬렉션을 새로 고치려면 `Refresh` 특정 컬렉션 개체의 메서드를 호출 하 고 오류를 확인 하기만 하면 됩니다.

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

현재 모든 DAO 컬렉션 개체 인터페이스는 MFC DAO 데이터베이스 클래스에 대 한 문서화 되지 않은 구현 세부 정보입니다.

## <a name="using-dao-directly-for-dao-security-features"></a>Dao 보안 기능에 직접 DAO 사용

MFC DAO 데이터베이스 클래스는 DAO 보안 기능을 래핑 하지 않습니다. Dao 보안 기능을 사용 하려면 DAO 인터페이스의 메서드를 호출 해야 합니다. 다음 함수는 시스템 데이터베이스를 설정 하 고 사용자의 암호를 변경 합니다. 이 함수는 나중에 정의 되는 세 가지 함수를 호출 합니다.

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

    // Set system database before MFC initilizes DAO
    // NOTE: An MFC module uses only one instance
    // of a DAO database engine object. If you have
    // called a DAO object in your application prior
    // to calling the function below, you must call
    // AfxDaoTerm to destroy the existing database
    // engine object. Otherwise, the database engine
    // object already in use will be reused, and setting
    // a system datbase will have no effect.
    //
    // If you have used a DAO object prior to calling
    // this function it is important that DAO be
    // terminated with AfxDaoTerm since an MFC
    // module only gets one copy of the database engine
    // and that engine will be reused if it hasn't been
    // terminated. In other words, if you do not call
    // AfxDaoTerm and there is currently a database
    // initialized, setting the system database will
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

다음 네 가지 예제에서는 다음을 수행 하는 방법을 보여 줍니다.

- 시스템 DAO 데이터베이스를 설정 합니다. MDW 파일).

- 기본 사용자 및 암호를 설정 합니다.

- 사용자의 암호를 변경 합니다.

- 의 암호를 변경 합니다. MDB 파일.

### <a name="setting-the-system-database"></a>시스템 데이터베이스 설정

다음은 응용 프로그램에서 사용 되는 시스템 데이터베이스를 설정 하는 샘플 함수입니다. 이 함수는 다른 DAO 호출을 수행 하기 전에 호출 해야 합니다.

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>기본 사용자 및 암호 설정

시스템 데이터베이스에 대 한 기본 사용자 및 암호를 설정 하려면 다음 함수를 사용 합니다.

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>사용자 암호 변경

사용자의 암호를 변경 하려면 다음 함수를 사용 합니다.

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>의 암호 변경 MDB 파일

의 암호를 변경 합니다. MDB 파일, 다음 함수를 사용 합니다.

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
