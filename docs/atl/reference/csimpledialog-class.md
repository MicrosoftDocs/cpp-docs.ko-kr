---
description: '자세히 알아보기: CSimpleDialog 클래스'
title: CSimpleDialog 클래스
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 50889c4387515c85cd3c6e53bf12e7c0494504ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140649"
---
# <a name="csimpledialog-class"></a>CSimpleDialog 클래스

이 클래스는 기본 모달 대화 상자를 구현 합니다.

## <a name="syntax"></a>구문

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>매개 변수

*t_wDlgTemplateID*

대화 상자 템플릿 리소스의 리소스 ID입니다.

*t_bCenter*<br/>
대화 상자 개체가 소유자 창 가운데에 배치 되 면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSimpleDialog::D oModal](#domodal)|모달 대화 상자를 만듭니다.|

## <a name="remarks"></a>설명

기본 기능을 사용 하 여 모달 대화 상자를 구현 합니다. `CSimpleDialog` Windows 공용 컨트롤에 대 한 지원도 제공 합니다. 모달 대화 상자를 만들고 표시 하려면이 클래스의 인스턴스를 만들어 대화 상자에 대 한 기존 리소스 템플릿의 이름을 제공 합니다. 사용자가 미리 정의 된 값 (예: IDOK 또는 IDCANCEL)의 컨트롤을 클릭 하면 대화 상자 개체가 닫힙니다.

`CSimpleDialog` 모달 대화 상자를 만들 수 있습니다. `CSimpleDialog` 기본 메시지 맵을 사용 하 여 메시지를 적절 한 처리기에 전달 하는 대화 상자 프로시저를 제공 합니다.

자세한 내용은 [대화 상자 구현](../../atl/implementing-a-dialog-box.md) 을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>요구 사항

**헤더:.**

## <a name="csimpledialogdomodal"></a><a name="domodal"></a> CSimpleDialog::D oModal

모달 대화 상자를 호출 하 고 완료 되 면 대화 상자 결과를 반환 합니다.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>매개 변수

*hWndParent*<br/>
대화 상자의 부모에 대 한 핸들입니다. 값을 제공 하지 않으면 부모는 현재 활성 창으로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 반환 값은 대화 상자를 해제 한 컨트롤의 리소스 ID입니다.

함수가 실패 하면 반환 값은-1입니다. 확장 오류 정보를 가져오려면 `GetLastError`를 호출합니다.

### <a name="remarks"></a>설명

이 메서드는 대화 상자가 활성화 되어 있는 동안 사용자와의 모든 상호 작용을 처리 합니다. 이를 통해 대화 상자를 모달로 만듭니다. 즉, 사용자가 대화 상자를 닫을 때까지 다른 창과 상호 작용할 수 없습니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
