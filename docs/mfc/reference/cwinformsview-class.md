---
title: CWinFormsView 클래스
ms.date: 11/04/2016
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
ms.openlocfilehash: f4a5e6b88527dad8606092ccebd4899bba5181f6
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426290"
---
# <a name="cwinformsview-class"></a>CWinFormsView 클래스

Windows Forms 컨트롤을 MFC 뷰로 호스팅하기 위한 일반 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CWinFormsView : public CView;
```

## <a name="members"></a>구성원

### <a name="public-constructors"></a>Public 생성자

|속성|Description|
|----------|-----------------|
|[CWinFormsView:: CWinFormsView](#cwinformsview)|`CWinFormsView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|속성|Description|
|----------|-----------------|
|[CWinFormsView:: GetControl](#getcontrol)|Windows Forms 컨트롤에 대 한 포인터를 검색 합니다.|

### <a name="public-operators"></a>Public 연산자

|속성||
|----------|-|
|[CWinFormsView:: operator 컨트롤 ^](#operator_control)|Windows Forms 컨트롤에 대 한 포인터로 형식을 캐스팅 합니다.|

## <a name="remarks"></a>설명

MFC는 `CWinFormsView` 클래스를 사용 하 여 MFC 뷰 내에서 .NET Framework Windows Forms 컨트롤을 호스팅합니다. 컨트롤은 네이티브 뷰의 자식 이며 MFC 뷰의 전체 클라이언트 영역을 차지 합니다. 결과는 `CFormView` 뷰와 비슷하며 Windows Forms 디자이너와 런타임을 활용 하 여 풍부한 폼 기반 보기를 만들 수 있습니다.

Windows Forms 사용에 대 한 자세한 내용은 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

> [!NOTE]
>  MFC Windows Forms 통합은 MFC (AFXDLL가 정의 된 프로젝트)와 동적으로 연결 되는 프로젝트 에서만 작동 합니다.

> [!NOTE]
>  CWinFormsView는 MFC 분할자 창 ( [CSplitterWnd 클래스](../../mfc/reference/csplitterwnd-class.md))을 지원 하지 않습니다. 현재는 Windows Forms Splitter 컨트롤만 지원 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** afxwinforms

##  <a name="cwinformsview"></a>CWinFormsView:: CWinFormsView

`CWinFormsView` 개체를 생성합니다.

```
CWinFormsView(System::Type^ pManagedViewType);
```

### <a name="parameters"></a>매개 변수

*pManagedViewType*<br/>
Windows Forms 사용자 정의 컨트롤의 데이터 형식에 대 한 포인터입니다.

### <a name="example"></a>예제

다음 예제에서는 `CUserView` 클래스가 `CWinFormsView`에서 상속 하 고 `UserControl1` 형식을 `CWinFormsView` 생성자에 전달 합니다. `UserControl1`는 ControlLibrary1에서 사용자가 빌드한 컨트롤입니다.

[!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]

[!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]

##  <a name="getcontrol"></a>CWinFormsView:: GetControl

Windows Forms 컨트롤에 대 한 포인터를 검색 합니다.

```
System::Windows::Forms::Control^ GetControl() const;
```

### <a name="return-value"></a>Return Value

`System.Windows.Forms.Control` 개체에 대한 포인터입니다.

### <a name="remarks"></a>설명

Windows Forms를 사용 하는 방법에 대 한 예제는 [MFC에서 Windows Form 사용자 정의 컨트롤 사용](../../dotnet/using-a-windows-form-user-control-in-mfc.md)을 참조 하세요.

##  <a name="operator_control"></a>CWinFormsView:: operator 컨트롤 ^

Windows Forms 컨트롤에 대 한 포인터로 형식을 캐스팅 합니다.

```
operator System::Windows::Forms::Control^() const;
```

### <a name="remarks"></a>설명

이 연산자를 사용 하면 <xref:System.Windows.Forms.Control>형식의 Windows Forms 컨트롤에 대 한 포인터를 허용 하는 함수에 `CWinFormsView` 뷰를 전달할 수 있습니다.

### <a name="example"></a>예제

  [CWinFormsView:: GetControl](#getcontrol)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CWinFormsControl 클래스](../../mfc/reference/cwinformscontrol-class.md)<br/>
[CWinFormsDialog 클래스](../../mfc/reference/cwinformsdialog-class.md)<br/>
[CFormView 클래스](../../mfc/reference/cformview-class.md)
