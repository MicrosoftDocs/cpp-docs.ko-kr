---
description: '자세히 알아보기: CSettingsStoreSP 클래스'
title: CSettingsStoreSP 클래스
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 67e9f881fc43722ab568aa7f149fc7a2b44cc764
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264689"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP 클래스

`CSettingsStoreSP`클래스는 [Csettingsstore 클래스](../../mfc/reference/csettingsstore-class.md)의 인스턴스를 만드는 데 사용할 수 있는 도우미 클래스입니다.

## <a name="syntax"></a>구문

```
class CSettingsStoreSP
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSettingsStoreSP:: CSettingsStoreSP](#csettingsstoresp)|`CSettingsStoreSP` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSettingsStoreSP:: Create](#create)|에서 파생 되는 클래스의 인스턴스를 만듭니다 `CSettingsStore` .|
|[CSettingsStoreSP:: SetRuntimeClass](#setruntimeclass)|런타임 클래스를 설정 합니다. `Create`메서드는 runtime 클래스를 사용 하 여 만들 개체의 클래스를 결정 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|`m_dwUserData`|개체에 저장 된 사용자 지정 사용자 데이터입니다 `CSettingsStoreSP` . 개체의 생성자에이 데이터를 제공 `CSettingsStoreSP` 합니다.|
|`m_pRegistry`|`CSettingsStore`메서드가 만드는 파생 개체입니다 `Create` .|

## <a name="remarks"></a>설명

클래스를 사용 `CSettingsStoreSP` 하 여 모든 MFC 레지스트리 작업을 XML 파일 또는 데이터베이스와 같은 다른 위치로 리디렉션할 수 있습니다. 이렇게 하려면 다음 단계를 수행하세요.

1. 클래스 (예:)를 만들고 `CMyStore` 에서 파생 `CSettingsStore` 합니다.

1. 사용자 지정 클래스를 사용 하 여 [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) 및 [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) 매크로를 사용 `CSettingsStore` 하 여 동적 생성을 사용 하도록 설정 합니다.

1. 가상 함수를 재정의 하 고 `Read` `Write` 사용자 지정 클래스에서 및 함수를 구현 합니다. 원하는 위치에 데이터를 읽고 쓰려면 다른 모든 기능을 구현 합니다.

1. 응용 프로그램에서를 호출 하 `CSettingsStoreSP::SetRuntimeClass` 고 클래스에서 가져온 [CRuntimeClass 구조체](../../mfc/reference/cruntimeclass-structure.md) 에 대 한 포인터를 전달 합니다.

프레임 워크는 일반적으로 레지스트리에 액세스할 때마다 사용자 지정 클래스를 동적으로 인스턴스화하고이를 사용 하 여 데이터를 읽거나 씁니다.

`CSettingsStoreSP::SetRuntimeClass` 전역 정적 변수를 사용 합니다. 따라서 한 번에 하나의 사용자 지정 저장소를 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxsettingsstore

## <a name="csettingsstorespcreate"></a><a name="create"></a> CSettingsStoreSP:: Create

[Csettingsstore 클래스](../../mfc/reference/csettingsstore-class.md)에서 파생 되는 개체의 새 인스턴스를 만듭니다.

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>매개 변수

*bAdmin*<br/>
진행 개체를 관리자 모드로 만들지 여부를 결정 하는 부울 매개 변수입니다 `CSettingsStore` .

*bReadOnly*<br/>
진행 읽기 전용 액세스를 위해 개체를 만들지 여부를 결정 하는 부울 매개 변수입니다 `CSettingsStore` .

### <a name="return-value"></a>반환 값

새로 만든 개체에 대 한 참조 `CSettingsStore` 입니다.

### <a name="remarks"></a>설명

[Csettingsstoresp:: SetRuntimeClass](#setruntimeclass) 메서드를 사용 하 여 만들 개체 형식을 결정할 수 있습니다 `CSettingsStoreSP::Create` . 기본적으로이 메서드는 개체를 만듭니다 `CSettingsStore` .

`CSettingsStore`관리자 모드에서 개체를 만드는 경우 모든 레지스트리 액세스의 기본 위치는 HKEY_LOCAL_MACHINE 됩니다. 그렇지 않으면 모든 레지스트리 액세스의 기본 위치가 HKEY_CURRENT_USER 됩니다.

*Badmin* 이 TRUE 이면 응용 프로그램에 관리 권한이 있어야 합니다. 그렇지 않으면 레지스트리에 액세스 하려고 할 때 실패 합니다.

### <a name="example"></a>예제

다음 예제에서는 클래스의 메서드를 사용 하는 방법을 보여 줍니다 `Create` `CSettingsStoreSP` .

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a> CSettingsStoreSP:: CSettingsStoreSP

[Csettingsstoresp 클래스](../../mfc/reference/csettingsstoresp-class.md) 개체를 생성 합니다.

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>매개 변수

*dwUserData*<br/>
진행 개체가 저장 하는 사용자 정의 데이터입니다 `CSettingsStoreSP` .

### <a name="remarks"></a>설명

`CSettingsStoreSP`개체는 *dwuserdata* 의 데이터를 보호 된 멤버 변수에 저장 합니다 `m_dwUserData` .

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a> CSettingsStoreSP:: SetRuntimeClass

런타임 클래스를 설정 합니다. [Csettingsstoresp:: create](#create) 메서드는 런타임 클래스를 사용 하 여 만들 개체의 형식을 결정 합니다.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>매개 변수

*pRTI*<br/>
진행 [Csettingsstore 클래스](../../mfc/reference/csettingsstore-class.md)에서 파생 된 클래스에 대 한 런타임 클래스 정보에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE입니다. *Prti* 로 식별 되는 클래스가에서 파생 되지 않은 경우 FALSE입니다 `CSettingsStore` .

### <a name="remarks"></a>설명

[Csettingsstoresp 클래스](../../mfc/reference/csettingsstoresp-class.md) 를 사용 하 여에서 클래스를 파생 시킬 수 있습니다 `CSettingsStore` . `SetRuntimeClass`에서 파생 된 사용자 지정 클래스의 개체를 만들려는 경우 메서드를 사용 합니다 `CSettingsStore` .

## <a name="see-also"></a>참고 항목

[클래스](../../mfc/reference/mfc-classes.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore 클래스](../../mfc/reference/csettingsstore-class.md)
