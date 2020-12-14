---
description: '자세히 알아보기: COleObjectFactory 클래스'
title: COleObjectFactory 클래스
ms.date: 11/04/2016
f1_keywords:
- COleObjectFactory
- AFXDISP/COleObjectFactory
- AFXDISP/COleObjectFactory::COleObjectFactory
- AFXDISP/COleObjectFactory::GetClassID
- AFXDISP/COleObjectFactory::IsLicenseValid
- AFXDISP/COleObjectFactory::IsRegistered
- AFXDISP/COleObjectFactory::Register
- AFXDISP/COleObjectFactory::RegisterAll
- AFXDISP/COleObjectFactory::Revoke
- AFXDISP/COleObjectFactory::RevokeAll
- AFXDISP/COleObjectFactory::UnregisterAll
- AFXDISP/COleObjectFactory::UpdateRegistry
- AFXDISP/COleObjectFactory::UpdateRegistryAll
- AFXDISP/COleObjectFactory::GetLicenseKey
- AFXDISP/COleObjectFactory::OnCreateObject
- AFXDISP/COleObjectFactory::VerifyLicenseKey
- AFXDISP/COleObjectFactory::VerifyUserLicense
helpviewer_keywords:
- COleObjectFactory [MFC], COleObjectFactory
- COleObjectFactory [MFC], GetClassID
- COleObjectFactory [MFC], IsLicenseValid
- COleObjectFactory [MFC], IsRegistered
- COleObjectFactory [MFC], Register
- COleObjectFactory [MFC], RegisterAll
- COleObjectFactory [MFC], Revoke
- COleObjectFactory [MFC], RevokeAll
- COleObjectFactory [MFC], UnregisterAll
- COleObjectFactory [MFC], UpdateRegistry
- COleObjectFactory [MFC], UpdateRegistryAll
- COleObjectFactory [MFC], GetLicenseKey
- COleObjectFactory [MFC], OnCreateObject
- COleObjectFactory [MFC], VerifyLicenseKey
- COleObjectFactory [MFC], VerifyUserLicense
ms.assetid: ab179c1e-4af2-44aa-a576-37c48149b427
ms.openlocfilehash: a47165dc367b132c864364a154dce2450207c434
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226872"
---
# <a name="coleobjectfactory-class"></a>COleObjectFactory 클래스

서버, 자동화 개체, 문서와 같은 OLE 개체를 만드는 OLE 클래스 팩터리를 구현합니다.

## <a name="syntax"></a>구문

```
class COleObjectFactory : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleObjectFactory:: COleObjectFactory](#coleobjectfactory)|`COleObjectFactory` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleObjectFactory:: GetClassID](#getclassid)|이 팩터리가 만드는 개체의 OLE 클래스 ID를 반환 합니다.|
|[COleObjectFactory:: IsLicenseValid](#islicensevalid)|컨트롤의 라이선스가 유효한 지 여부를 확인 합니다.|
|[COleObjectFactory:: IsRegistered](#isregistered)|개체 팩터리가 OLE 시스템 Dll에 등록 되었는지 여부를 나타냅니다.|
|[COleObjectFactory:: Register](#register)|OLE 시스템 Dll을 사용 하 여이 개체 팩터리를 등록 합니다.|
|[COleObjectFactory:: RegisterAll](#registerall)|응용 프로그램의 모든 개체 팩터리를 OLE 시스템 Dll에 등록 합니다.|
|[COleObjectFactory:: Revoke](#revoke)|OLE 시스템 Dll을 사용 하 여이 개체 팩터리의 등록을 취소 합니다.|
|[COleObjectFactory:: RevokeAll](#revokeall)|OLE 시스템 Dll을 사용 하 여 응용 프로그램의 개체 팩터리 등록을 해지 합니다.|
|[COleObjectFactory:: UnregisterAll](#unregisterall)|응용 프로그램의 모든 개체 팩터리를 등록 취소 합니다.|
|[COleObjectFactory:: UpdateRegistry](#updateregistry)|OLE 시스템 레지스트리에이 개체 팩터리를 등록 합니다.|
|[COleObjectFactory:: UpdateRegistryAll](#updateregistryall)|응용 프로그램의 모든 개체 팩터리를 OLE 시스템 레지스트리에 등록 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[COleObjectFactory:: GetLicenseKey](#getlicensekey)|컨트롤의 DLL에서 고유 키를 요청 합니다.|
|[COleObjectFactory:: OnCreateObject](#oncreateobject)|이 팩터리의 형식의 새 개체를 만들기 위해 프레임 워크에서 호출 됩니다.|
|[COleObjectFactory:: VerifyLicenseKey](#verifylicensekey)|컨트롤에 포함 된 키가 컨테이너에 포함 된 키와 일치 하는지 확인 합니다.|
|[COleObjectFactory:: VerifyUserLicense](#verifyuserlicense)|컨트롤에 디자인 타임 사용이 허가 되었는지 확인 합니다.|

## <a name="remarks"></a>설명

클래스에는 `COleObjectFactory` 다음 함수를 수행 하기 위한 멤버 함수가 있습니다.

- 개체 등록 관리

- Ole 시스템 레지스터를 업데이트 하 고 해당 개체가 실행 중이 고 메시지를 수신할 준비가 되었다는 것을 OLE에 알리는 런타임 등록을 업데이트 합니다.

- 디자인 타임에 사용이 허가 된 개발자와 런타임에 사용이 허가 된 응용 프로그램에 대 한 컨트롤의 사용을 제한 하 여 라이선스를 적용 합니다.

- 컨트롤 개체 팩터리를 OLE 시스템 레지스트리에 등록 합니다.

개체 만들기에 대 한 자세한 내용은 [데이터 개체 및 데이터 원본 (OLE)](../../mfc/data-objects-and-data-sources-ole.md) 및 [데이터 개체 및 데이터 원본: 생성 및 소멸](../../mfc/data-objects-and-data-sources-creation-and-destruction.md)문서를 참조 하세요. 등록에 대 한 자세한 내용은 [등록](../../mfc/registration.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleObjectFactory`

## <a name="requirements"></a>요구 사항

**헤더:** afxdisp.h

## <a name="coleobjectfactorycoleobjectfactory"></a><a name="coleobjectfactory"></a> COleObjectFactory:: COleObjectFactory

개체를 생성 하 `COleObjectFactory` 고 등록 되지 않은 개체 팩터리로 초기화 한 다음 팩터리 목록에 추가 합니다.

```
COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    LPCTSTR lpszProgID);

COleObjectFactory(
    REFCLSID clsid,
    CRuntimeClass* pRuntimeClass,
    BOOL bMultiInstance,
    int nFlags,
    LPCTSTR lpszProgID);
```

### <a name="parameters"></a>매개 변수

*가*<br/>
이 개체 팩터리가 나타내는 OLE 클래스 ID에 대 한 참조입니다.

*pRuntimeClass*<br/>
이 팩터리가 만들 수 있는 c + + 개체의 런타임 클래스에 대 한 포인터입니다.

*bMultiInstance*<br/>
응용 프로그램의 단일 인스턴스에서 여러 인스턴스화를 지원할 수 있는지 여부를 나타냅니다. TRUE 이면 각 요청에 대해 개체를 만들기 위해 응용 프로그램의 여러 인스턴스가 시작 됩니다.

*nFlags*<br/>
다음 플래그 중 하나 이상을 포함 합니다.

- `afxRegDefault` 스레딩 모델을 ThreadingModel = 아파트로 설정 합니다.

- `afxRegInsertable` OLE 개체에 대 한 **개체 삽입** 대화 상자에 컨트롤을 표시할 수 있습니다.

- `afxRegApartmentThreading` 레지스트리의 스레딩 모델을 ThreadingModel = 아파트로 설정 합니다.

- `afxRegFreeThreading` 레지스트리의 스레딩 모델을 ThreadingModel = Free로 설정 합니다.

   두 플래그를 결합 하 `afxRegApartmentThreading` 고 `afxRegFreeThreading` ThreadingModel =를 설정할 수 있습니다. 스레딩 모델 등록에 대 한 자세한 내용은 Windows SDK의 [InprocServer32](/windows/win32/com/inprocserver32) 를 참조 하세요.

*lpszProgID*<br/>
"Microsoft Excel"과 같은 구두 프로그램 식별자를 포함 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

그러나 개체를 사용 하려면 해당 개체를 등록 해야 합니다.

자세한 내용은 Windows SDK의 [CLSID 키](/windows/win32/com/clsid-key-hklm) 를 참조 하세요.

## <a name="coleobjectfactorygetclassid"></a><a name="getclassid"></a> COleObjectFactory:: GetClassID

이 팩터리가 나타내는 OLE 클래스 ID에 대 한 참조를 반환 합니다.

```
REFCLSID GetClassID() const;
```

### <a name="return-value"></a>반환 값

이 팩터리가 나타내는 OLE 클래스 ID에 대 한 참조입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK의 [CLSID 키](/windows/win32/com/clsid-key-hklm) 를 참조 하세요.

## <a name="coleobjectfactorygetlicensekey"></a><a name="getlicensekey"></a> COleObjectFactory:: GetLicenseKey

컨트롤의 DLL에서 고유한 라이선스 키를 요청 하 고 *Pbstrkey* 에서 가리키는 BSTR에 저장 합니다.

```
virtual BOOL GetLicenseKey(
    DWORD dwReserved,
    BSTR* pbstrKey);
```

### <a name="parameters"></a>매개 변수

*dwReserved*<br/>
다음에 사용하도록 예약됩니다.

*pbstrKey*<br/>
라이선스 키를 저장 하는 BSTR에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

라이선스 키 문자열이 NULL이 아닌 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현에서는 0을 반환 하 고 BSTR에 아무 것도 저장 하지 않습니다. MFC ActiveX ControlWizard를 사용 하 여 프로젝트를 만드는 경우 ControlWizard는 컨트롤의 라이선스 키를 검색 하는 재정의를 제공 합니다.

## <a name="coleobjectfactoryislicensevalid"></a><a name="islicensevalid"></a> COleObjectFactory:: IsLicenseValid

컨트롤의 라이선스가 유효한 지 여부를 확인 합니다.

```
BOOL IsLicenseValid();
```

### <a name="return-value"></a>반환 값

Successul 인 경우 TRUE입니다. 그렇지 않으면 false입니다.

## <a name="coleobjectfactoryisregistered"></a><a name="isregistered"></a> COleObjectFactory:: IsRegistered

팩터리가 OLE 시스템 Dll에 등록 된 경우 0이 아닌 값을 반환 합니다.

```
virtual BOOL IsRegistered() const;
```

### <a name="return-value"></a>반환 값

팩터리가 등록 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="coleobjectfactoryoncreateobject"></a><a name="oncreateobject"></a> COleObjectFactory:: OnCreateObject

새 개체를 만들기 위해 프레임 워크에서 호출 됩니다.

```
virtual CCmdTarget* OnCreateObject();
```

### <a name="return-value"></a>반환 값

만들어진 개체에 대 한 포인터입니다. 실패 하면 메모리 예외를 throw 할 수 있습니다.

### <a name="remarks"></a>설명

생성자에 전달 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 이외의 항목에서 개체를 만들려면이 함수를 재정의 합니다.

## <a name="coleobjectfactoryregister"></a><a name="register"></a> COleObjectFactory:: Register

OLE 시스템 Dll을 사용 하 여이 개체 팩터리를 등록 합니다.

```
virtual BOOL Register();
```

### <a name="return-value"></a>반환 값

팩터리가 성공적으로 등록 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 응용 프로그램이 시작 될 때 [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 에 의해 호출 됩니다.

## <a name="coleobjectfactoryregisterall"></a><a name="registerall"></a> COleObjectFactory:: RegisterAll

응용 프로그램의 모든 개체 팩터리를 OLE 시스템 Dll에 등록 합니다.

```
static BOOL PASCAL RegisterAll();
```

### <a name="return-value"></a>반환 값

팩터리가 성공적으로 등록 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 응용 프로그램이 시작 될 때 [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 에 의해 호출 됩니다.

## <a name="coleobjectfactoryrevoke"></a><a name="revoke"></a> COleObjectFactory:: Revoke

OLE 시스템 Dll을 사용 하 여이 개체 팩터리의 등록을 취소 합니다.

```cpp
void Revoke();
```

### <a name="remarks"></a>설명

프레임 워크는 응용 프로그램이 종료 되기 전에이 함수를 자동으로 호출 합니다. 필요한 경우 [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)의 재정의에서 호출 합니다.

## <a name="coleobjectfactoryrevokeall"></a><a name="revokeall"></a> COleObjectFactory:: RevokeAll

OLE 시스템 Dll을 사용 하 여 모든 응용 프로그램의 개체 팩터리 등록을 취소 합니다.

```
static void PASCAL RevokeAll();
```

### <a name="remarks"></a>설명

프레임 워크는 응용 프로그램이 종료 되기 전에이 함수를 자동으로 호출 합니다. 필요한 경우 [CWinApp:: ExitInstance](../../mfc/reference/cwinapp-class.md#exitinstance)의 재정의에서 호출 합니다.

## <a name="coleobjectfactoryunregisterall"></a><a name="unregisterall"></a> COleObjectFactory:: UnregisterAll

응용 프로그램의 모든 개체 팩터리를 등록 취소 합니다.

```
static BOOL PASCAL UnregisterAll();
```

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

## <a name="coleobjectfactoryupdateregistry"></a><a name="updateregistry"></a> COleObjectFactory:: UpdateRegistry

응용 프로그램의 모든 개체 팩터리를 OLE 시스템 레지스트리에 등록 합니다.

```cpp
void UpdateRegistry(LPCTSTR lpszProgID = NULL);
virtual BOOL UpdateRegistry(BOOL bRegister);
```

### <a name="parameters"></a>매개 변수

*lpszProgID*<br/>
"Excel.Document"와 같이 사람이 읽을 수 있는 프로그램 식별자를 포함 하는 문자열에 대 한 포인터입니다.

*bRegister*<br/>
컨트롤 클래스의 개체 팩터리가 등록 되는지 여부를 결정 합니다.

### <a name="remarks"></a>설명

이 함수에 대 한 간단한 논의는 다음과 같습니다.

- **UpdateRegistry (** `lpszProgID` **)** 는 OLE 시스템 레지스트리에이 개체 팩터리를 등록 합니다. 이 함수는 일반적으로 응용 프로그램이 시작 될 때 [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 에 의해 호출 됩니다.

- **UpdateRegistry (** `bRegister` **)** 이 형식의 함수는 재정의할 수 있습니다. *BRegister* 가 TRUE 인 경우이 함수는 컨트롤 클래스를 시스템 레지스트리에 등록 합니다. 그렇지 않으면 클래스의 등록을 취소 합니다.

   MFC ActiveX ControlWizard를 사용 하 여 프로젝트를 만드는 경우 ControlWizard는이 순수 가상 함수에 대 한 재정의를 제공 합니다.

## <a name="coleobjectfactoryupdateregistryall"></a><a name="updateregistryall"></a> COleObjectFactory:: UpdateRegistryAll

응용 프로그램의 모든 개체 팩터리를 OLE 시스템 레지스트리에 등록 합니다.

```
static BOOL PASCAL UpdateRegistryAll(BOOL bRegister = TRUE);
```

### <a name="parameters"></a>매개 변수

*bRegister*<br/>
컨트롤 클래스의 개체 팩터리가 등록 되는지 여부를 결정 합니다.

### <a name="return-value"></a>반환 값

팩터리가 성공적으로 업데이트 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 응용 프로그램이 시작 될 때 [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) 에 의해 호출 됩니다.

## <a name="coleobjectfactoryverifylicensekey"></a><a name="verifylicensekey"></a> COleObjectFactory:: VerifyLicenseKey

컨테이너에 OLE 컨트롤을 사용할 수 있는 라이선스가 있는지 확인 합니다.

```
virtual BOOL VerifyLicenseKey(BSTR bstrKey);
```

### <a name="parameters"></a>매개 변수

*bstrKey*<br/>
컨테이너 버전의 라이선스 문자열을 저장 하는 BSTR입니다.

### <a name="return-value"></a>반환 값

런타임 라이선스가 유효한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 버전은 [GetLicenseKey](#getlicensekey) 를 호출 하 여 컨트롤의 라이선스 문자열 복사본을 가져오고이를 *bstrKey* 의 문자열과 비교 합니다. 두 문자열이 일치 하면 함수는 0이 아닌 값을 반환 합니다. 그렇지 않으면 0을 반환 합니다.

이 함수를 재정의 하 여 라이선스에 대 한 사용자 지정 확인을 제공할 수 있습니다.

[Verifyuserlicense](#verifyuserlicense) 함수는 디자인 타임 라이선스를 확인 합니다.

## <a name="coleobjectfactoryverifyuserlicense"></a><a name="verifyuserlicense"></a> COleObjectFactory:: VerifyUserLicense

OLE 컨트롤에 대 한 디자인 타임 라이선스를 확인 합니다.

```
virtual BOOL VerifyUserLicense();
```

### <a name="return-value"></a>반환 값

디자인 타임 라이선스가 유효한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

## <a name="see-also"></a>참고 항목

[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleTemplateServer 클래스](../../mfc/reference/coletemplateserver-class.md)
