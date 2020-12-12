---
description: '자세히 알아보기: CSnapInPropertyPageImpl 클래스'
title: CSnapInPropertyPageImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CSnapInPropertyPageImpl
- ATLSNAP/ATL::CSnapInPropertyPageImpl::CancelToClose
- ATLSNAP/ATL::CSnapInPropertyPageImpl::Create
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnApply
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnHelp
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnKillActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnQueryCancel
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnReset
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnSetActive
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardBack
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardFinish
- ATLSNAP/ATL::CSnapInPropertyPageImpl::OnWizardNext
- ATLSNAP/ATL::CSnapInPropertyPageImpl::QuerySiblings
- ATLSNAP/ATL::CSnapInPropertyPageImpl::SetModified
- ATLSNAP/ATL::CSnapInPropertyPageImpl::m_psp
helpviewer_keywords:
- snap-ins, property pages
- snap-ins
- property pages, ATL
- CSnapInPropertyPageImpl class
ms.assetid: 75bdce5a-985e-4166-bd44-493132e023c4
ms.openlocfilehash: c3699dff31291525638f128382ad39369f18deca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140545"
---
# <a name="csnapinpropertypageimpl-class"></a>CSnapInPropertyPageImpl 클래스

이 클래스는 스냅인 속성 페이지 개체를 구현 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
CSnapInPropertyPageImpl : public CDialogImplBase
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSnapInPropertyPageImpl::CSnapInPropertyPageImpl](#csnapinpropertypageimpl)|생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSnapInPropertyPageImpl:: CancelToClose](#canceltoclose)|**확인** 및 **취소** 단추의 상태를 변경 합니다.|
|[CSnapInPropertyPageImpl:: Create](#create)|새로 만든 개체를 초기화 `CSnapInPropertyPageImpl` 합니다.|
|[CSnapInPropertyPageImpl:: OnApply](#onapply)|사용자가 마법사 형식의 속성 시트를 사용 하는 동안 **지금 적용** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnHelp](#onhelp)|마법사 형식의 속성 시트를 사용 하는 동안 사용자가 **도움말** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl::OnKillActive](#onkillactive)|현재 페이지가 더 이상 활성 상태가 아닌 경우 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnQueryCancel](#onquerycancel)|사용자가 취소 단추를 클릭 한 **후 취소가 수행** 되기 전에 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnReset](#onreset)|마법사 형식의 속성 시트를 사용 하는 동안 사용자가 **다시 설정** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnSetActive](#onsetactive)|현재 페이지가 활성화 될 때 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnWizardBack](#onwizardback)|마법사 형식의 속성 시트를 사용 하는 동안 사용자가 **뒤로** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnWizardFinish](#onwizardfinish)|마법사 형식의 속성 시트를 사용 하는 동안 사용자가 **마침** 단추를 클릭 하면 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: OnWizardNext](#onwizardnext)|마법사 형식의 속성 시트를 사용 하는 동안 사용자가 **다음** 단추를 클릭할 때 프레임 워크에서 호출 됩니다.|
|[CSnapInPropertyPageImpl:: QuerySiblings](#querysiblings)|현재 메시지를 속성 시트의 모든 페이지에 전달 합니다.|
|[CSnapInPropertyPageImpl:: SetModified](#setmodified)|을 호출 하 여 **지금 적용** 단추를 활성화 하거나 비활성화 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CSnapInPropertyPageImpl:: m_psp](#m_psp)|`PROPSHEETPAGE`개체에서 사용 하는 Windows 구조체 `CSnapInPropertyPageImpl` 입니다.|

## <a name="remarks"></a>설명

`CSnapInPropertyPageImpl` 스냅인 속성 페이지 개체에 대 한 기본 구현을 제공 합니다. 스냅인 속성 페이지의 기본 기능은 다양 한 인터페이스 및 맵 형식을 사용 하 여 구현 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CDialogImplBase`

`CSnapInPropertyPageImpl`

## <a name="requirements"></a>요구 사항

**헤더:** 고 대/스냅. h

## <a name="csnapinpropertypageimplcanceltoclose"></a><a name="canceltoclose"></a> CSnapInPropertyPageImpl:: CancelToClose

모달 속성 시트의 페이지에 있는 데이터에 대해 복구할 수 없는 변경 내용이 발생 한 후이 함수를 호출 합니다.

```cpp
void CancelToClose();
```

### <a name="remarks"></a>설명

이 함수는 **취소** 단추를 **닫거나** 사용 하지 않도록 설정 하는 **확인** 단추를 변경 합니다. 이 변경으로 인해 사용자에 게 변경 내용이 영구적이 고 수정 내용을 취소할 수 없다는 경고가 발생 합니다.

모덜리스 속성 시트 `CancelToClose` 에는 기본적으로 **취소** 단추가 없기 때문에 멤버 함수는 모덜리스 속성 시트에서 아무 작업도 수행 하지 않습니다.

## <a name="csnapinpropertypageimplcsnapinpropertypageimpl"></a><a name="csnapinpropertypageimpl"></a> CSnapInPropertyPageImpl::CSnapInPropertyPageImpl

`CSnapInPropertyPageImpl` 개체를 생성합니다.

```
CSnapInPropertyPageImpl(LPCTSTR lpszTitle = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszTitle*<br/>
진행 속성 페이지의 제목입니다.

### <a name="remarks"></a>설명

기본 구조를 초기화 하려면 [CSnapInPropertyPageImpl:: Create](#create)를 호출 합니다.

## <a name="csnapinpropertypageimplcreate"></a><a name="create"></a> CSnapInPropertyPageImpl:: Create

이 함수를 호출 하 여 속성 페이지의 기본 구조를 초기화 합니다.

```
HPROPSHEETPAGE Create();
```

### <a name="return-value"></a>반환 값

`PROPSHEETPAGE`새로 만든 속성 시트의 특성을 포함 하는 구조체에 대 한 핸들입니다.

### <a name="remarks"></a>설명

먼저이 함수를 호출 하기 전에 [CSnapInPropertyPageImpl:: CSnapInPropertyPageImpl](#csnapinpropertypageimpl) 를 호출 해야 합니다.

## <a name="csnapinpropertypageimplm_psp"></a><a name="m_psp"></a> CSnapInPropertyPageImpl:: m_psp

`m_psp` 는 멤버가의 특성을 저장 하는 구조체입니다 `PROPSHEETPAGE` .

```
PROPSHEETPAGE m_psp;
```

### <a name="remarks"></a>설명

이 구조체를 사용 하 여 속성 페이지가 생성 된 후 해당 페이지의 모양을 초기화할 수 있습니다.

멤버 목록을 포함 하 여이 구조에 대 한 자세한 내용은 Windows SDK의 [PROPSHEETPAGE](/windows/win32/api/prsht/ns-prsht-propsheetpagea_v3) 를 참조 하세요.

## <a name="csnapinpropertypageimplonapply"></a><a name="onapply"></a> CSnapInPropertyPageImpl:: OnApply

이 멤버 함수는 사용자가 **확인** 또는 **지금 적용** 단추를 클릭할 때 호출 됩니다.

```
BOOL OnApply();
```

### <a name="return-value"></a>반환 값

변경 내용이 수락 되는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

가 `OnApply` 프레임 워크에서 호출 될 수 있도록 하려면를 호출 하 `SetModified` 고 매개 변수를 TRUE로 설정 해야 합니다. 이렇게 하면 사용자가 속성 페이지에서 변경 하는 즉시 **적용** 단추가 활성화 됩니다.

사용자가 **지금 적용** 단추를 클릭할 때 프로그램에서 수행 하는 작업을 지정 하려면이 멤버 함수를 재정의 합니다. 을 재정의 하는 경우 함수는 변경 내용을 적용 하기 위해 TRUE를 반환 하 고 변경 내용을 적용 하지 않도록 하려면 FALSE를 반환 해야 합니다.

의 기본 구현에서는 `OnApply` TRUE를 반환 합니다.

## <a name="csnapinpropertypageimplonhelp"></a><a name="onhelp"></a> CSnapInPropertyPageImpl:: OnHelp

이 멤버 함수는 사용자가 속성 페이지에 대 한 **도움말** 단추를 클릭할 때 호출 됩니다.

```cpp
void OnHelp();
```

### <a name="remarks"></a>설명

속성 페이지에 대 한 도움말을 표시 하려면이 멤버 함수를 재정의 합니다.

## <a name="csnapinpropertypageimplonkillactive"></a><a name="onkillactive"></a> CSnapInPropertyPageImpl::OnKillActive

이 멤버 함수는 페이지가 더 이상 활성 페이지가 아닌 경우 호출 됩니다.

```
BOOL OnKillActive();
```

### <a name="return-value"></a>반환 값

데이터가 성공적으로 업데이트 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

특수 한 데이터 유효성 검사 작업을 수행 하려면이 멤버 함수를 재정의 합니다.

## <a name="csnapinpropertypageimplonquerycancel"></a><a name="onquerycancel"></a> CSnapInPropertyPageImpl:: OnQueryCancel

이 멤버 함수는 사용자가 **취소** 단추를 클릭 한 후 취소 작업이 수행 되기 전에 호출 됩니다.

```
BOOL OnQueryCancel();
```

### <a name="return-value"></a>반환 값

취소 작업을 허용 하지 않는 0입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

사용자가 **취소** 단추를 클릭할 때 프로그램에서 수행 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

의 기본 구현에서는 `OnQueryCancel` TRUE를 반환 합니다.

## <a name="csnapinpropertypageimplonreset"></a><a name="onreset"></a> CSnapInPropertyPageImpl:: OnReset

이 멤버 함수는 사용자가 **[취소** ] 단추를 클릭할 때 호출 됩니다.

```cpp
void OnReset();
```

### <a name="remarks"></a>설명

이 함수가 호출 되 면 사용자가 이전에 **적용** 단추를 클릭 하 여 수행한 모든 속성 페이지의 변경 내용이 삭제 되 고 속성 시트가 포커스를 유지 합니다.

사용자가 **취소** 단추를 클릭할 때 프로그램에서 수행 하는 작업을 지정 하려면이 멤버 함수를 재정의 합니다.

## <a name="csnapinpropertypageimplonsetactive"></a><a name="onsetactive"></a> CSnapInPropertyPageImpl:: OnSetActive

이 멤버 함수는 사용자가 페이지를 선택 하 고 활성 페이지가 되 면 호출 됩니다.

```
BOOL OnSetActive();
```

### <a name="return-value"></a>반환 값

페이지가 활성 상태로 설정 되 면 0이 아닌 값으로 설정 됩니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

페이지가 활성화 될 때 작업을 수행 하려면이 멤버 함수를 재정의 합니다. 이 멤버 함수의 재정의는 다른 처리를 수행 하기 전에 기본 버전을 호출 해야 합니다.

기본 구현에서는 TRUE를 반환 합니다.

## <a name="csnapinpropertypageimplonwizardback"></a><a name="onwizardback"></a> CSnapInPropertyPageImpl:: OnWizardBack

이 멤버 함수는 사용자가 마법사에서 **뒤로** 단추를 클릭할 때 호출 됩니다.

```
BOOL OnWizardBack();
```

### <a name="return-value"></a>반환 값

- 0은 자동으로 이전 페이지로 이동 합니다.

- -1은 페이지가 변경 되지 않도록 합니다.

다음 페이지가 아닌 다른 페이지로 이동 하려면 표시할 대화 상자의 식별자를 반환 합니다.

### <a name="remarks"></a>설명

**뒤로** 단추를 클릭할 때 사용자가 수행 해야 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

## <a name="csnapinpropertypageimplonwizardfinish"></a><a name="onwizardfinish"></a> CSnapInPropertyPageImpl:: OnWizardFinish

이 멤버 함수는 사용자가 마법사에서 **마침** 단추를 클릭할 때 호출 됩니다.

```
BOOL OnWizardFinish();
```

### <a name="return-value"></a>반환 값

마법사가 완료 될 때 속성 시트가 제거 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

**마침** 단추를 클릭할 때 사용자가 수행 해야 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

## <a name="csnapinpropertypageimplonwizardnext"></a><a name="onwizardnext"></a> CSnapInPropertyPageImpl:: OnWizardNext

이 멤버 함수는 사용자가 마법사에서 **다음** 단추를 클릭할 때 호출 됩니다.

```
BOOL OnWizardNext();
```

### <a name="return-value"></a>반환 값

- 0은 자동으로 다음 페이지로 이동 합니다.

- -1은 페이지가 변경 되지 않도록 합니다.

다음 페이지가 아닌 다른 페이지로 이동 하려면 표시할 대화 상자의 식별자를 반환 합니다.

### <a name="remarks"></a>설명

**다음** 단추를 클릭할 때 사용자가 수행 해야 하는 동작을 지정 하려면이 멤버 함수를 재정의 합니다.

## <a name="csnapinpropertypageimplquerysiblings"></a><a name="querysiblings"></a> CSnapInPropertyPageImpl:: QuerySiblings

이 멤버 함수를 호출 하 여 속성 시트의 각 페이지에 메시지를 전달 합니다.

```
LRESULT QuerySiblings(WPARAM wParam, LPARAM lParam);
```

### <a name="parameters"></a>매개 변수

*wParam*<br/>
진행 추가 메시지 종속 정보를 지정 합니다.

*lParam*<br/>
진행 추가 메시지 종속 정보를 지정 합니다.

### <a name="return-value"></a>반환 값

메시지가 다음 속성 페이지로 전달 되지 않아야 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

페이지에서 0이 아닌 값을 반환 하면 속성 시트는 이후 페이지로 메시지를 보내지 않습니다.

## <a name="csnapinpropertypageimplsetmodified"></a><a name="setmodified"></a> CSnapInPropertyPageImpl:: SetModified

속성 페이지의 설정이 적절 한 외부 개체에 적용 되어야 하는지 여부에 따라 [ **지금 적용** ] 단추를 사용 하거나 사용 하지 않도록 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetModified(BOOL bChanged = TRUE);
```

### <a name="parameters"></a>매개 변수

*bChanged 됨*<br/>
진행 마지막으로 적용 된 이후에 속성 페이지 설정이 수정 되었음을 나타내려면 TRUE이 고, 속성 페이지 설정이 적용 되었거나 무시 되어야 함을 나타내려면 FALSE입니다.

### <a name="remarks"></a>설명

속성 시트는 "더티", 즉를 호출한 속성 페이지가 있는 페이지를 추적 합니다 `SetModified( TRUE )` . 페이지 중 하나에 대해를 호출 하면 **지금 적용** 단추가 항상 사용 하도록 설정 됩니다 `SetModified( TRUE )` . 페이지 중 하나에 대해를 호출할 때 [ **지금 적용** ] 단추를 사용할 수 없습니다 `SetModified( FALSE )` . 단, 다른 페이지에는 "더티"가 없는 경우에만 적용 됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
