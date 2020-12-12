---
description: '자세히 알아보기: CDaoRecordView 클래스'
title: CDaoRecordView 클래스
ms.date: 11/04/2016
f1_keywords:
- CDaoRecordView
- AFXDAO/CDaoRecordView
- AFXDAO/CDaoRecordView::CDaoRecordView
- AFXDAO/CDaoRecordView::IsOnFirstRecord
- AFXDAO/CDaoRecordView::IsOnLastRecord
- AFXDAO/CDaoRecordView::OnGetRecordset
- AFXDAO/CDaoRecordView::OnMove
helpviewer_keywords:
- CDaoRecordView [MFC], CDaoRecordView
- CDaoRecordView [MFC], IsOnFirstRecord
- CDaoRecordView [MFC], IsOnLastRecord
- CDaoRecordView [MFC], OnGetRecordset
- CDaoRecordView [MFC], OnMove
ms.assetid: 5aa7d0e2-bd05-413e-b216-80c404ce18ac
ms.openlocfilehash: cb91f6d3890806ac357a1f662905845598df1680
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248179"
---
# <a name="cdaorecordview-class"></a>CDaoRecordView 클래스

컨트롤에 데이터베이스 레코드를 표시하는 뷰입니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CDaoRecordView : public CFormView
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CDaoRecordView:: CDaoRecordView](#cdaorecordview)|`CDaoRecordView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoRecordView:: IsOnFirstRecord](#isonfirstrecord)|현재 레코드가 연결 된 레코드 집합의 첫 번째 레코드 이면 0이 아닌 값을 반환 합니다.|
|[CDaoRecordView:: IsOnLastRecord](#isonlastrecord)|현재 레코드가 연결 된 레코드 집합의 마지막 레코드 이면 0이 아닌 값을 반환 합니다.|
|[CDaoRecordView:: OnGetRecordset](#ongetrecordset)|에서 파생 된 클래스의 개체에 대 한 포인터를 반환 `CDaoRecordset` 합니다. 클래스 마법사는 사용자를 위해이 함수를 재정의 하 고 필요한 경우 레코드 집합을 만듭니다.|
|[CDaoRecordView:: OnMove](#onmove)|현재 레코드가 변경 된 경우 데이터 원본에서 해당 레코드를 업데이트 한 다음 지정 된 레코드 (다음, 이전, 첫 번째 또는 마지막)로 이동 합니다.|

## <a name="remarks"></a>설명

뷰는 개체에 직접 연결 된 폼 뷰입니다 `CDaoRecordset` . 대화 상자 템플릿 리소스에서 뷰를 만들고 `CDaoRecordset` 대화 상자 템플릿의 컨트롤에 개체의 필드를 표시 합니다. `CDaoRecordView`개체는 DDX (대화 상자 데이터 교환)와 DFX (DAO 레코드 필드 교환)를 사용 하 여 폼의 컨트롤과 레코드 집합의 필드 간 데이터 이동을 자동화 합니다. `CDaoRecordView` 는 현재 보기에서 레코드를 업데이트 하기 위한 첫 번째, 다음, 이전, 마지막 레코드 및 인터페이스로 이동 하기 위한 기본 구현도 제공 합니다.

> [!NOTE]
> DAO 데이터베이스 클래스는 ODBC (Open Database Connectivity)를 기반으로 하는 MFC 데이터베이스 클래스와는 다릅니다. 모든 DAO 데이터베이스 클래스 이름에는 "CDao" 접두사가 있습니다. 여전히 DAO 클래스를 사용 하 여 ODBC 데이터 원본에 액세스할 수 있습니다. DAO 클래스는 Microsoft Jet 데이터베이스 엔진을 사용 하므로 일반적으로 뛰어난 기능을 제공 합니다.

레코드 뷰를 만드는 가장 일반적인 방법은 응용 프로그램 마법사를 사용 하는 것입니다. 응용 프로그램 마법사는 기본 스타터 응용 프로그램의 일부로 레코드 뷰 클래스와 연결 된 레코드 집합 클래스를 모두 만듭니다.

단일 폼만 필요한 경우 응용 프로그램 마법사 방법이 더 쉽습니다. 클래스 마법사를 사용 하면 나중에 개발 프로세스에서 레코드 뷰를 사용 하도록 결정할 수 있습니다. 응용 프로그램 마법사를 사용 하 여 레코드 뷰 클래스를 만들지 않는 경우 나중에 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 만들 수 있습니다. 클래스 마법사를 사용 하 여 레코드 뷰 및 레코드 집합을 별도로 만든 다음 연결 하 여 가장 유연한 방법으로 레코드 집합 클래스의 이름을 지정 하는 데 더 많은 제어 기능을 제공 합니다. H/. CPP 파일. 이 방법을 사용 하면 동일한 레코드 집합 클래스에 여러 레코드 뷰를 사용할 수도 있습니다.

최종 사용자가 레코드 뷰에서 레코드를 쉽게 이동할 수 있도록 하기 위해 응용 프로그램 마법사는 첫 번째, 다음, 이전 또는 마지막 레코드로 이동 하기 위한 메뉴 (및 필요에 따라 도구 모음) 리소스를 만듭니다. 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 만드는 경우 메뉴 및 비트맵 편집기를 사용 하 여 이러한 리소스를 직접 만들어야 합니다.

레코드에서 레코드로 이동 하는 기본 구현에 대 한 자세한 내용은 및 `IsOnFirstRecord` `IsOnLastRecord` 및에 적용 되는 [레코드 뷰를 사용 하](../../data/using-a-record-view-mfc-data-access.md)는 문서를 참조 하세요 `CRecordView` `CDaoRecordView` .

`CDaoRecordView` 레코드 뷰에서 사용자 인터페이스를 업데이트할 수 있도록 레코드 집합에서 사용자의 위치를 추적 합니다. 사용자가 레코드 집합의 끝으로 이동할 때 레코드 뷰는 메뉴 항목 또는 도구 모음 단추와 같은 사용자 인터페이스 개체를 사용 하지 않도록 설정 하 여 동일한 방향으로 이동 합니다.

레코드 뷰 및 레코드 집합 클래스를 선언 하 고 사용 하는 방법에 대 한 자세한 내용은 문서 [레코드 뷰](../../data/record-views-mfc-data-access.md)의 "레코드 뷰 디자인 및 만들기"를 참조 하세요. 레코드 보기의 작동 방식 및 사용 방법에 대 한 자세한 내용은 [레코드 뷰 사용](../../data/using-a-record-view-mfc-data-access.md)문서를 참조 하세요. 위에서 언급 한 모든 문서는 및에 모두 적용 `CRecordView` `CDaoRecordView` 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CDaoRecordView`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaorecordviewcdaorecordview"></a><a name="cdaorecordview"></a> CDaoRecordView:: CDaoRecordView

에서 파생 된 형식의 개체를 만들 때 `CDaoRecordView` 두 가지 형식의 생성자를 호출 하 여 뷰 개체를 초기화 하 고 뷰의 기반이 되는 대화 상자 리소스를 식별 합니다.

```
explicit CDaoRecordView(LPCTSTR lpszTemplateName);
explicit CDaoRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>매개 변수

*lpszTemplateName*<br/>
대화 상자 템플릿 리소스의 이름인 null로 끝나는 문자열을 포함 합니다.

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID 번호를 포함 합니다.

### <a name="remarks"></a>설명

이름으로 리소스를 식별할 수 있습니다 (생성자에 인수로 문자열 전달) 또는 해당 ID (부호 없는 정수를 인수로 전달). 리소스 ID를 사용 하는 것이 좋습니다.

> [!NOTE]
> 파생 클래스는 자체 생성자를 제공 해야 합니다. 파생 클래스의 생성자에서 `CDaoRecordView::CDaoRecordView` 리소스 이름이 나 ID를 인수로 사용 하 여 생성자를 호출 합니다.

`CDaoRecordView::OnInitialUpdate` 를 호출 하 `CWnd::UpdateData` 는를 호출 `CWnd::DoDataExchange` 합니다. 이 초기 호출을 `DoDataExchange` `CDaoRecordView` 통해 컨트롤 (간접적)을 `CDaoRecordset` 클래스 마법사에서 만든 필드 데이터 멤버에 연결 합니다. 이러한 데이터 멤버는 기본 클래스 멤버 함수를 호출한 후에만 사용할 수 있습니다 `CFormView::OnInitialUpdate` .

> [!NOTE]
> 클래스 마법사를 사용 하는 경우 마법사는 **`enum`** 클래스 선언에 값을 정의 하 `CDaoRecordView::IDD` 고 생성자에 대 한 멤버 초기화 목록에서 값을 사용 합니다.

[!code-cpp[NVC_MFCDatabase#35](../../mfc/codesnippet/cpp/cdaorecordview-class_1.cpp)]

## <a name="cdaorecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a> CDaoRecordView:: IsOnFirstRecord

이 멤버 함수를 호출 하 여 현재 레코드가이 레코드 뷰와 연결 된 레코드 집합 개체의 첫 번째 레코드 인지 여부를 확인 합니다.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>반환 값

현재 레코드가 레코드 집합의 첫 번째 레코드 이면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 클래스 마법사에서 작성 한 기본 명령 업데이트 처리기의 고유한 구현을 작성 하는 데 유용 합니다.

사용자가 첫 번째 레코드로 이동 하는 경우 프레임 워크는 첫 번째 레코드나 이전 레코드로 이동 하는 사용자 인터페이스 개체 (예: 메뉴 항목 또는 도구 모음 단추)를 사용 하지 않도록 설정 합니다.

## <a name="cdaorecordviewisonlastrecord"></a><a name="isonlastrecord"></a> CDaoRecordView:: IsOnLastRecord

이 멤버 함수를 호출 하 여 현재 레코드가이 레코드 뷰와 연결 된 레코드 집합 개체의 마지막 레코드 인지 여부를 확인 합니다.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>반환 값

현재 레코드가 레코드 집합의 마지막 레코드 이면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 레코드에서 레코드로 이동 하기 위한 사용자 인터페이스를 지원 하기 위해 클래스 마법사에서 작성 하는 기본 명령 업데이트 처리기의 고유한 구현을 작성 하는 데 유용 합니다.

> [!CAUTION]
> 이 함수의 결과는 사용자가 이전에 이동할 때까지 뷰가 레코드 집합의 끝을 검색할 수 없는 경우를 제외 하 고 신뢰할 수 있습니다. 레코드 뷰가 사용자 인터페이스 개체를 사용 하지 않도록 설정 하 여 다음 또는 마지막 레코드로 이동 해야 함을 알리기 위해 사용자는 마지막 레코드를 벗어나 이동 해야 할 수 있습니다. 사용자가 마지막 레코드를 지난 후 마지막 레코드로 다시 이동 하는 경우 (또는 이전) 레코드 뷰는 레코드 집합에서 사용자의 위치를 추적 하 고 사용자 인터페이스 개체를 올바르게 비활성화할 수 있습니다.

## <a name="cdaorecordviewongetrecordset"></a><a name="ongetrecordset"></a> CDaoRecordView:: OnGetRecordset

레코드 뷰와 연결 된 파생 개체에 대 한 포인터를 반환 `CDaoRecordset` 합니다.

```
virtual CDaoRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>반환 값

`CDaoRecordset`개체가 성공적으로 만들어졌으면 파생 개체에 대 한 포인터이 고, 그렇지 않으면 NULL 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 재정의 하 여 레코드 집합 개체를 생성 하거나 가져오고 해당 개체에 대 한 포인터를 반환 해야 합니다. 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 선언 하면 마법사에서 기본 재정의를 작성 합니다. 클래스 마법사의 기본 구현에서는 레코드 뷰에 저장 된 레코드 집합 포인터가 있는 경우이를 반환 합니다. 그렇지 않으면 클래스 마법사를 사용 하 여 지정한 형식의 레코드 집합 개체를 생성 하 고 해당 `Open` 멤버 함수를 호출 하 여 테이블을 열거나 쿼리를 실행 한 다음 개체에 대 한 포인터를 반환 합니다.

자세한 내용 및 예제는 레코드 뷰 [: 레코드 뷰 사용](../../data/using-a-record-view-mfc-data-access.md)문서를 참조 하세요.

## <a name="cdaorecordviewonmove"></a><a name="onmove"></a> CDaoRecordView:: OnMove

이 멤버 함수를 호출 하 여 레코드 집합의 다른 레코드로 이동 하 고 레코드 뷰의 컨트롤에 해당 필드를 표시 합니다.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>매개 변수

*nIDMoveCommand*<br/>
다음 표준 명령 ID 값 중 하나입니다.

- ID_RECORD_FIRST 레코드 집합의 첫 번째 레코드로 이동 합니다.

- ID_RECORD_LAST 레코드 집합의 마지막 레코드로 이동 합니다.

- ID_RECORD_NEXT 레코드 집합의 다음 레코드로 이동 합니다.

- ID_RECORD_PREV 레코드 집합의 이전 레코드로 이동 합니다.

### <a name="return-value"></a>반환 값

이동에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다. 이동 요청이 거부 된 경우입니다.

### <a name="remarks"></a>설명

기본 구현에서는 레코드 뷰와 연결 된 개체의 적절 한 이동 멤버 함수를 호출 합니다 `CDaoRecordset` .

기본적으로는 `OnMove` 사용자가 레코드 뷰에서 데이터 원본의 현재 레코드를 변경한 경우 해당 레코드를 업데이트 합니다.

응용 프로그램 마법사는 첫 번째 레코드, 마지막 레코드, 다음 레코드 및 이전 레코드 메뉴 항목을 사용 하 여 메뉴 리소스를 만듭니다. 초기 도구 모음 옵션을 선택 하는 경우 응용 프로그램 마법사는 이러한 명령에 해당 하는 단추가 있는 도구 모음도 만듭니다.

레코드 집합에서 마지막 레코드를 지 나 이동 하면 레코드 뷰는 마지막 레코드를 계속 표시 합니다. 첫 번째 레코드를 벗어나 뒤로 이동 하는 경우 레코드 뷰는 첫 번째 레코드를 계속 표시 합니다.

> [!CAUTION]
> 레코드 `OnMove` 집합에 레코드가 없는 경우를 호출 하면 예외가 throw 됩니다. 해당 이동 작업 전에 적절 한 사용자 인터페이스 업데이트 처리기 함수,, 또는를 호출 하 여 레코드 `OnUpdateRecordFirst` `OnUpdateRecordLast` `OnUpdateRecordNext` `OnUpdateRecordPrev` 집합에 레코드가 있는지 여부를 확인 합니다.

## <a name="see-also"></a>참고 항목

[CFormView 클래스](../../mfc/reference/cformview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset 클래스](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 클래스](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 클래스](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoWorkspace 클래스](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CFormView 클래스](../../mfc/reference/cformview-class.md)
