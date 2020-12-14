---
description: '자세히 알아보기: C추가 정보'
title: CMenuTearOffManager 클래스
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: b80f2e935f8d1dd47bf19a11522e4556b35490b4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336644"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager 클래스

분리 메뉴를 관리합니다. 분리 메뉴는 메뉴 모음의 메뉴입니다. 사용자는 메뉴 모음에서 분리 메뉴를 제거하여 이동 가능한 상태로 만들 수 있습니다.

   자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

## <a name="syntax"></a>구문

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMenuTearOffManager:: CMenuTearOffManager](#cmenutearoffmanager)|`CMenuTearOffManager` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMenuTearOffManager:: Build](#build)||
|[CMenuTearOffManager:: GetRegPath](#getregpath)||
|[CMenuTearOffManager:: Initialize](#initialize)|`CMenuTearOffManager` 개체를 초기화합니다.|
|[CMenuTearOffManager:: IsDynamicID](#isdynamicid)||
|[Arse 관리자::P](#parse)||
|[CMenuTearOffManager:: Reset](#reset)||
|[CMenuTearOffManager:: SetInUse](#setinuse)||
|[CMenuTearOffManager:: SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>설명

응용 프로그램에서 분리 메뉴를 사용 하려면 개체가 있어야 합니다 `CMenuTearOffManager` . 대부분의 경우 개체를 직접 만들거나 초기화 하지 않습니다 `CMenuTearOffManager` . [CWinAppEx:: EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) 함수를 호출할 때이를 처리 합니다.

## <a name="example"></a>예제

다음 예제에서는 `CMenuTearOffManager` 메서드를 호출 하 여 개체를 생성 하 고 초기화 하는 방법을 보여 줍니다 `CWinAppEX::EnableTearOffMenus` . 이 코드 조각은 [워드 패드 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>요구 사항

**헤더:** afxmenutearoffmanager

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a> CMenuTearOffManager:: Build

```cpp
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>매개 변수

진행 *Uiteoff바코드 id*<br/>

진행 *Strtext*<br/>

### <a name="remarks"></a>설명

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a> CMenuTearOffManager:: CMenuTearOffManager

[Cmenutearoffmanager](../../mfc/reference/cmenutearoffmanager-class.md) 개체를 생성 합니다.

```
CMenuTearOffManager();
```

### <a name="remarks"></a>설명

대부분의 경우를 수동으로 만들지 마십시오 `CMenuTearOffManager` . 응용 프로그램의 프레임 워크는 `CMenuTearOffManager` [CWinAppEx:: EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)를 호출할 때 개체를 만듭니다.

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a> CMenuTearOffManager:: GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a> CMenuTearOffManager:: Initialize

[Cmenutearoffmanager](../../mfc/reference/cmenutearoffmanager-class.md) 개체를 초기화 합니다.

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>매개 변수

*lpszRegEntry*<br/>
진행 레지스트리 항목의 경로를 포함 하는 문자열입니다. 응용 프로그램은이 레지스트리 항목에 분리 된 모음에 대 한 설정을 저장 합니다.

*uiTearOffMenuFirst*<br/>
진행 분리 메뉴의 첫 번째 메뉴 ID입니다.

*Uiteoffa*<br/>
진행 분리 메뉴의 마지막 메뉴 ID입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*Uitearoffmenufirst* 에서 *Uiteoffmenuulast* 까지의 메뉴 id 범위는 연속 간격 이어야 합니다. 간격은 응용 프로그램에서 동시에 표시 될 수 있는 분리 메뉴 수를 정의 합니다.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a> CMenuTearOffManager:: IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>매개 변수

진행 *Uiid*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a> Arse 관리자::P

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>매개 변수

진행 *str*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a> CMenuTearOffManager:: Reset

```cpp
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>매개 변수

진행 *hmenu*<br/>

### <a name="remarks"></a>설명

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a> CMenuTearOffManager:: SetInUse

```cpp
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>매개 변수

진행 *Uicmdid*<br/>

진행 *bUse*<br/>

### <a name="remarks"></a>설명

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a> CMenuTearOffManager:: SetupTearOffMenus

```cpp
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>매개 변수

진행 *hMenu*<br/>

### <a name="remarks"></a>설명

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)
