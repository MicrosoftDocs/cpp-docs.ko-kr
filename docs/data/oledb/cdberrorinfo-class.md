---
description: '자세한 정보: CDBErrorInfo 클래스'
title: CDBErrorInfo 클래스
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: fe57963e5964403c6b17b6b41dc7ae5f77063f50
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170856"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo 클래스

OLE DB [Ierrorrecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) 인터페이스를 사용 하 여 OLE DB 오류 처리를 지원 합니다.

## <a name="syntax"></a>Syntax

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|오류 레코드에 포함 된 모든 오류 정보를 반환 합니다.|
|[GetBasicErrorInfo](#getbasicerrorinfo)|[Ierrorrecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 를 호출 하 여 지정 된 오류에 대 한 기본 정보를 반환 합니다.|
|[GetCustomErrorObject](#getcustomerrorobject)|는 [Ierrorrecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 를 호출 하 여 사용자 지정 오류 개체의 인터페이스에 대 한 포인터를 반환 합니다.|
|[GetErrorInfo](#geterrorinfo)|[Ierrorrecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 를 호출 하 여 `IErrorInfo` 지정 된 레코드에 대 한 인터페이스 포인터를 반환 합니다.|
|[GetErrorParameters](#geterrorparameters)|는 [Ierrorrecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 를 호출 하 여 오류 매개 변수를 반환 합니다.|
|[GetErrorRecords](#geterrorrecords)|지정 된 개체에 대 한 오류 레코드를 가져옵니다.|

## <a name="remarks"></a>설명

이 인터페이스는 사용자에 게 하나 이상의 오류 레코드를 반환 합니다. [Cdberrorinfo:: GetErrorRecords](#geterrorrecords) 를 먼저 호출 하 여 오류 레코드 수를 가져옵니다. 그런 다음 [Cdberrorinfo:: GetAllErrorInfo](#getallerrorinfo)와 같은 액세스 함수 중 하나를 호출 하 여 각 레코드에 대 한 오류 정보를 검색 합니다.

## <a name="cdberrorinfogetallerrorinfo"></a><a name="getallerrorinfo"></a> CDBErrorInfo:: GetAllErrorInfo

오류 레코드에 포함 된 모든 오류 정보 유형을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>매개 변수

*ulRecordNum*<br/>
진행 오류 정보를 반환할 레코드의 0부터 시작 하는 번호입니다.

*lcid*<br/>
진행 반환 될 오류 정보에 대 한 로캘 ID입니다.

*pbstrDescription*<br/>
제한이 오류의 텍스트 설명에 대 한 포인터 이거나, 로캘이 지원 되지 않는 경우 NULL입니다. 설명 부분을 참조하세요.

*pbstrSource*<br/>
제한이 오류를 생성 한 구성 요소의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*pguid*<br/>
제한이 오류를 정의한 인터페이스의 GUID에 대 한 포인터입니다.

*pdwHelpContext*<br/>
제한이 오류에 대 한 도움말 컨텍스트 ID에 대 한 포인터입니다.

*pbstrHelpFile*<br/>
제한이 오류를 설명 하는 도움말 파일의 경로를 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 다른 반환 값에 대 한 *OLE DB 프로그래머 참조* 에서 [Ierrorrecords:: geterrorinfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 를 참조 하세요.

### <a name="remarks"></a>설명

*Pbstrdescription* 의 출력 값은를 호출 하 여 내부적으로 가져오며 `IErrorInfo::GetDescription` , 로캘이 지원 되지 않는 경우에는 값을 NULL로 설정 하 고, 다음 두 조건에 모두 해당 하는 경우에는 NULL로 설정 합니다.

1. *lcid* 의 값은 미국 영어 및

1. *lcid* 의 값이 GetUserDefaultLCID에서 반환한 값과 같지 않습니다.

## <a name="cdberrorinfogetbasicerrorinfo"></a><a name="getbasicerrorinfo"></a> CDBErrorInfo:: GetBasicErrorInfo

는 [Ierrorrecords:: GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 를 호출 하 여 반환 코드 및 공급자별 오류 번호와 같은 오류에 대 한 기본 정보를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [Ierrorrecords:: getbasicerrorinfo](/previous-versions/windows/desktop/ms723907(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cdberrorinfogetcustomerrorobject"></a><a name="getcustomerrorobject"></a> CDBErrorInfo:: GetCustomErrorObject

는 [Ierrorrecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 를 호출 하 여 사용자 지정 오류 개체의 인터페이스에 대 한 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [Ierrorrecords:: GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cdberrorinfogeterrorinfo"></a><a name="geterrorinfo"></a> CDBErrorInfo:: GetErrorInfo

[Ierrorrecords:: GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 를 호출 하 여 지정 된 레코드에 대 한 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85)) 인터페이스 포인터를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 에서 [Ierrorrecords:: geterrorinfo](/previous-versions/windows/desktop/ms711230(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cdberrorinfogeterrorparameters"></a><a name="geterrorparameters"></a> CDBErrorInfo:: GetErrorParameters

는 [Ierrorrecords:: GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 를 호출 하 여 오류 매개 변수를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>매개 변수

*OLE DB 프로그래머 참조* 의 [Ierrorrecords:: geterrorparameters](/previous-versions/windows/desktop/ms715793(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cdberrorinfogeterrorrecords"></a><a name="geterrorrecords"></a> CDBErrorInfo:: GetErrorRecords

지정 된 개체에 대 한 오류 레코드를 가져옵니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 오류 레코드를 가져올 개체에 대 한 인터페이스입니다.

*iid*<br/>
진행 오류와 연결 된 인터페이스의 IID입니다.

*pcRecords*<br/>
제한이 (1부터만) 오류 레코드 수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

오류 정보를 가져올 인터페이스를 확인 하려는 경우 함수의 첫 번째 형태를 사용 합니다. 그렇지 않으면 두 번째 형태를 사용 합니다.

## <a name="see-also"></a>참고 항목

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
