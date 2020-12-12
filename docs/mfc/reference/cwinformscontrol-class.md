---
description: '자세히 알아보기: CWinFormsControl 클래스'
title: CWinFormsControl 클래스
ms.date: 11/04/2016
f1_keywords:
- CWinFormsControl
- AFXWINFORMS/CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CWinFormsControl
- AFXWINFORMS/CWinFormsControl::CreateManagedControl
- AFXWINFORMS/CWinFormsControl::GetControl
- AFXWINFORMS/CWinFormsControl::GetControlHandle
helpviewer_keywords:
- CWinFormsControl [MFC], CWinFormsControl
- CWinFormsControl [MFC], CreateManagedControl
- CWinFormsControl [MFC], GetControl
- CWinFormsControl [MFC], GetControlHandle
ms.assetid: 6406dd7b-fb89-4a18-ac3a-c010d6b6289a
ms.openlocfilehash: 32daf5f1bf9efcd5d5b17d134dc8deaee7e32527
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318444"
---
# <a name="cwinformscontrol-class"></a>CWinFormsControl 클래스

Windows Forms 컨트롤을 호스팅하기 위한 기본 기능을 제공합니다.

## <a name="syntax"></a>구문

```
template<class TManagedControl>
class CWinFormsControl : public CWnd
```

#### <a name="parameters"></a>매개 변수

*TManagedControl*<br/>
MFC 응용 프로그램에 표시 되는 .NET Framework Windows Forms 컨트롤입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CWinFormsControl::CWinFormsControl](#cwinformscontrol)|MFC Windows Forms 컨트롤 래퍼 개체를 생성 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CWinFormsControl::CreateManagedControl](#createmanagedcontrol)|MFC 컨테이너에 Windows Forms 컨트롤을 만듭니다.|
|[CWinFormsControl:: GetControl](#getcontrol)|Windows Forms 컨트롤에 대 한 포인터를 검색 합니다.|
|[CWinFormsControl:: GetControlHandle](#getcontrolhandle)|Windows Forms 컨트롤에 대 한 핸들을 검색 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CWinFormsControl:: operator-&gt;](#operator_-_gt)|식에서 [CWinFormsControl:: GetControl](#getcontrol) 을 바꿉니다.|
|[CWinFormsControl:: operator TManagedControl ^](#operator_tmanagedcontrol)|Windows Forms 컨트롤에 대 한 포인터로 형식을 캐스팅 합니다.|

## <a name="remarks"></a>설명

`CWinFormsControl`클래스는 Windows Forms 컨트롤을 호스팅하기 위한 기본 기능을 제공 합니다.

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

MFC 코드는 창 핸들을 캐시 하지 않아야 합니다 (일반적으로에 저장 `m_hWnd` ). 일부 Windows Forms 컨트롤 속성을 사용 하려면 및를 `Window` 사용 하 여 기본 Win32를 제거 하 고 다시 만들어야 합니다 `DestroyWindow` `CreateWindow` . MFC Windows Forms 구현은 `Destroy` `Create` 컨트롤의 및 이벤트를 처리 하 여 멤버를 업데이트 합니다 `m_hWnd` .

> [!NOTE]
> MFC Windows Forms 통합은 MFC (AFXDLL가 정의 됨)와 동적으로 연결 되는 프로젝트 에서만 작동 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxwinforms

## <a name="cwinformscontrolcreatemanagedcontrol"></a><a name="createmanagedcontrol"></a> CWinFormsControl::CreateManagedControl

MFC 컨테이너에 Windows Forms 컨트롤을 만듭니다.

```
inline BOOL CreateManagedControl(
    System::Type^ pType,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID)
inline BOOL CreateManagedControl(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);

inline BOOL CreateManagedControl(
    DWORD dwStyle,
    int nPlaceHolderID,
    CWnd* pParentWnd);

inline BOOL CreateManagedControl(
    typename TManagedControl^ pControl,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID);
```

### <a name="parameters"></a>매개 변수

*pType*<br/>
만들 컨트롤의 데이터 형식입니다. [형식](/dotnet/api/system.type) 데이터 형식 이어야 합니다.

*dwStyle*<br/>
컨트롤에 적용할 창 스타일입니다. [창 스타일](../../mfc/reference/styles-used-by-mfc.md#window-styles)의 조합을 지정 합니다. 현재는 WS_TABSTOP, WS_VISIBLE, WS_DISABLED 및 WS_GROUP 스타일만 지원 됩니다.

*rect*<br/>
컨트롤의 왼쪽 위 모퉁이와 오른쪽 아래 모퉁이의 좌표를 정의 하는 [RECT 구조체](/windows/win32/api/windef/ns-windef-rect) 입니다 (첫 번째 오버 로드에만 해당).

*nPlaceHolderID*<br/>
리소스 편집기에 배치 된 정적 자리 표시자 컨트롤의 핸들입니다. 새로 만든 Windows Forms 컨트롤은 위치, z 순서 및 스타일을 가정 하 고 정적 컨트롤을 대체 합니다 (두 번째 오버 로드에만 해당).

*pParentWnd*<br/>
부모 창에 대 한 포인터입니다.

*nID*<br/>
새로 만든 컨트롤에 할당 되는 리소스 ID 번호입니다.

*pControl*<br/>
[CWinFormsControl](../../mfc/reference/cwinformscontrol-class.md) 개체와 연결 될 Windows Forms 컨트롤의 인스턴스입니다 (네 번째 오버 로드에만 해당).

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값을 반환 합니다. 실패 하면 0을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 MFC 컨테이너의 .NET Framework Windows Forms 컨트롤을 인스턴스화합니다.

메서드의 첫 번째 오버 로드는 MFC가이 형식의 새 개체를 인스턴스화할 수 있도록 .NET Framework 데이터 형식 *Ptype* 을 허용 합니다. *Ptype* 은 [형식](/dotnet/api/system.type) 데이터 형식 이어야 합니다.

메서드의 두 번째 오버 로드는 `TManagedControl` 클래스의 템플릿 매개 변수를 기반으로 Windows Forms 컨트롤을 만듭니다 `CWinFormsControl` . 컨트롤의 크기와 위치는 메서드에 전달 된 구조체를 기반으로 합니다 `RECT` . 스타일에는 *Dwstyle* 만 중요 합니다.

메서드의 세 번째 오버 로드는 정적 컨트롤을 대체 하 고 해당 위치, z 순서 및 스타일을 가정 하는 Windows Forms 컨트롤을 만듭니다. 정적 컨트롤은 Windows Forms 컨트롤에 대 한 자리 표시자로만 사용 됩니다. 이 오버 로드는 컨트롤을 만들 때 *Dwstyle* 의 스타일을 정적 컨트롤의 리소스 스타일과 결합 합니다.

메서드의 네 번째 오버 로드를 사용 하면 MFC에서 래핑할 *Pcontrol* 을 이미 인스턴스화한 Windows Forms 컨트롤로 전달할 수 있습니다. `TManagedControl`클래스의 템플릿 매개 변수와 동일한 형식 이어야 합니다 `CWinFormsControl` .

Windows Form 컨트롤 사용에 대 한 샘플은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md) 을 참조 하세요.

## <a name="cwinformscontrolcwinformscontrol"></a><a name="cwinformscontrol"></a> CWinFormsControl::CWinFormsControl

MFC Windows Forms 컨트롤 래퍼 개체를 생성 합니다.

```
CWinFormsControl();
```

### <a name="remarks"></a>설명

[CWinFormsControl:: CreateManagedControl](#createmanagedcontrol)를 호출 하면 Windows Forms 컨트롤이 인스턴스화됩니다.

## <a name="cwinformscontrolgetcontrol"></a><a name="getcontrol"></a> CWinFormsControl:: GetControl

Windows Forms 컨트롤에 대 한 포인터를 검색 합니다.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>반환 값

Windows Forms 컨트롤에 대 한 포인터를 반환 합니다.

### <a name="example"></a>예제

  [CWinFormsControl:: CreateManagedControl](#createmanagedcontrol)를 참조 하세요.

## <a name="cwinformscontrolgetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsControl:: GetControlHandle

Windows Forms 컨트롤에 대 한 핸들을 검색 합니다.

```
inline HWND GetControlHandle() const;
```

### <a name="return-value"></a>반환 값

Windows Forms 컨트롤에 대 한 핸들을 반환 합니다.

### <a name="remarks"></a>설명

`GetControlHandle` 는 .NET Framework 컨트롤 속성에 저장 된 창 핸들을 반환 하는 도우미 메서드입니다. 창 핸들 값은 [cwnd:: Attach](../../mfc/reference/cwnd-class.md#attach)를 호출 하는 동안 [cwnd:: m_hWnd](../../mfc/reference/cwnd-class.md#m_hwnd) 에 복사 됩니다.

## <a name="cwinformscontroloperator--gt"></a><a name="operator_-_gt"></a> CWinFormsControl:: operator-&gt;

식에서 [CWinFormsControl:: GetControl](#getcontrol) 을 바꿉니다.

```
inline TManagedControl^  operator->() const;
```

### <a name="remarks"></a>설명

이 연산자는 식에서를 대체 하는 편리한 구문을 제공 합니다 `GetControl` .

Windows Forms에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

## <a name="cwinformscontroloperator-tmanagedcontrol"></a><a name="operator_tmanagedcontrol"></a> CWinFormsControl:: operator TManagedControl ^

Windows Forms 컨트롤에 대 한 포인터로 형식을 캐스팅 합니다.

```
inline operator TManagedControl^() const;
```

### <a name="remarks"></a>설명

이 연산자는 `CWinFormsControl<TManagedControl>` Windows Forms 컨트롤에 대 한 포인터를 허용 하는 함수에 전달 됩니다.

## <a name="see-also"></a>참고 항목

[CWinFormsDialog 클래스](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CWinFormsView 클래스](../../mfc/reference/cwinformsview-class.md)
