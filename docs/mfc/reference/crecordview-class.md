---
description: '자세히 알아보기: CRecordView 클래스'
title: CRecordView 클래스
ms.date: 11/04/2016
f1_keywords:
- CRecordView
- AFXDB/CRecordView
- AFXDB/CRecordView::CRecordView
- AFXDB/CRecordView::IsOnFirstRecord
- AFXDB/CRecordView::IsOnLastRecord
- AFXDB/CRecordView::OnGetRecordset
- AFXDB/CRecordView::OnMove
helpviewer_keywords:
- CRecordView [MFC], CRecordView
- CRecordView [MFC], IsOnFirstRecord
- CRecordView [MFC], IsOnLastRecord
- CRecordView [MFC], OnGetRecordset
- CRecordView [MFC], OnMove
- CRecordView [MFC], OnMove
ms.assetid: 9b4b0897-bd50-4d48-a0b4-f3323f5ccc55
ms.openlocfilehash: ad9ef6ed53ed1f9ad843518701bd6e8d619e6e8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97301154"
---
# <a name="crecordview-class"></a>CRecordView 클래스

컨트롤에 데이터베이스 레코드를 표시하는 뷰입니다.

## <a name="syntax"></a>구문

```
class AFX_NOVTABLE CRecordView : public CFormView
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[CRecordView:: CRecordView](#crecordview)|`CRecordView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRecordView:: IsOnFirstRecord](#isonfirstrecord)|현재 레코드가 연결 된 레코드 집합의 첫 번째 레코드 이면 0이 아닌 값을 반환 합니다.|
|[CRecordView:: IsOnLastRecord](#isonlastrecord)|현재 레코드가 연결 된 레코드 집합의 마지막 레코드 이면 0이 아닌 값을 반환 합니다.|
|[CRecordView:: OnGetRecordset](#ongetrecordset)|에서 파생 된 클래스의 개체에 대 한 포인터를 반환 `CRecordset` 합니다. 클래스 마법사는 사용자를 위해이 함수를 재정의 하 고 필요한 경우 레코드 집합을 만듭니다.|
|[CRecordView:: OnMove](#onmove)||

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CRecordView:: OnMove](#onmove)|현재 레코드가 변경 된 경우 데이터 원본에서 해당 레코드를 업데이트 한 다음 지정 된 레코드 (다음, 이전, 첫 번째 또는 마지막)로 이동 합니다.|

## <a name="remarks"></a>설명

뷰는 개체에 직접 연결 된 폼 뷰입니다 `CRecordset` . 대화 상자 템플릿 리소스에서 뷰를 만들고 `CRecordset` 대화 상자 템플릿의 컨트롤에 개체의 필드를 표시 합니다. `CRecordView`개체는 DDX (대화 상자 데이터 교환) 및 RFX (레코드 필드 교환)를 사용 하 여 폼의 컨트롤과 레코드 집합의 필드 간 데이터 이동을 자동화 합니다. `CRecordView` 는 현재 보기에서 레코드를 업데이트 하기 위한 첫 번째, 다음, 이전, 마지막 레코드 및 인터페이스로 이동 하기 위한 기본 구현도 제공 합니다.

> [!NOTE]
> ODBC (Open Database Connectivity) 클래스 대신 DAO (Data Access Objects) 클래스를 사용 하 여 작업 하는 경우 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 클래스를 대신 사용 합니다. 자세한 내용은 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.

레코드 뷰를 만드는 가장 일반적인 방법은 응용 프로그램 마법사를 사용 하는 것입니다. 응용 프로그램 마법사는 기본 스타터 응용 프로그램의 일부로 레코드 뷰 클래스와 연결 된 레코드 집합 클래스를 모두 만듭니다. 응용 프로그램 마법사를 사용 하 여 레코드 뷰 클래스를 만들지 않는 경우 나중에 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 만들 수 있습니다. 단일 폼만 필요한 경우 응용 프로그램 마법사 방법이 더 쉽습니다. 클래스 마법사를 사용 하면 나중에 개발 프로세스에서 레코드 뷰를 사용 하도록 결정할 수 있습니다. 클래스 마법사를 사용 하 여 레코드 뷰 및 레코드 집합을 별도로 만든 다음 연결 하 여 가장 유연한 방법으로 레코드 집합 클래스의 이름을 지정 하는 데 더 많은 제어 기능을 제공 합니다. H/. CPP 파일. 이 방법을 사용 하면 동일한 레코드 집합 클래스에 여러 레코드 뷰를 사용할 수도 있습니다.

최종 사용자가 레코드 뷰에서 레코드를 쉽게 이동할 수 있도록 하기 위해 응용 프로그램 마법사는 첫 번째, 다음, 이전 또는 마지막 레코드로 이동 하기 위한 메뉴 (및 필요에 따라 도구 모음) 리소스를 만듭니다. 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 만드는 경우 메뉴 및 비트맵 편집기를 사용 하 여 이러한 리소스를 직접 만들어야 합니다.

레코드에서 레코드로 이동 하는 기본 구현에 대 한 자세한 내용은 `IsOnFirstRecord` 및 `IsOnLastRecord` 및 [레코드 뷰 사용](../../data/using-a-record-view-mfc-data-access.md)문서를 참조 하세요.

`CRecordView` 레코드 뷰에서 사용자 인터페이스를 업데이트할 수 있도록 레코드 집합에서 사용자의 위치를 추적 합니다. 사용자가 레코드 집합의 끝으로 이동할 때 레코드 뷰는 메뉴 항목 또는 도구 모음 단추와 같은 사용자 인터페이스 개체를 사용 하지 않도록 설정 하 여 동일한 방향으로 이동 합니다.

레코드 뷰 및 레코드 집합 클래스를 선언 하 고 사용 하는 방법에 대 한 자세한 내용은 문서 [레코드 뷰](../../data/record-views-mfc-data-access.md)의 "레코드 뷰 디자인 및 만들기"를 참조 하세요. 레코드 보기의 작동 방식 및 사용 방법에 대 한 자세한 내용은 [레코드 뷰 사용](../../data/using-a-record-view-mfc-data-access.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`CRecordView`

## <a name="requirements"></a>요구 사항

**헤더:** afxdb

## <a name="crecordviewcrecordview"></a><a name="crecordview"></a> CRecordView:: CRecordView

에서 파생 된 형식의 개체를 만들 때 `CRecordView` 두 가지 형식의 생성자를 호출 하 여 뷰 개체를 초기화 하 고 뷰의 기반이 되는 대화 상자 리소스를 식별 합니다.

```
explicit CRecordView(LPCTSTR lpszTemplateName);
explicit CRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>매개 변수

*lpszTemplateName*<br/>
대화 상자 템플릿 리소스의 이름인 null로 끝나는 문자열을 포함 합니다.

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID 번호를 포함 합니다.

### <a name="remarks"></a>설명

이름으로 리소스를 식별할 수 있습니다 (생성자에 인수로 문자열 전달) 또는 해당 ID (부호 없는 정수를 인수로 전달). 리소스 ID를 사용 하는 것이 좋습니다.

> [!NOTE]
> 파생 클래스는 자체 생성자를 제공 *해야 합니다* . 파생 클래스의 생성자에서 `CRecordView::CRecordView` 아래 예제와 같이 리소스 이름 또는 ID를 인수로 사용 하 여 생성자를 호출 합니다.

`CRecordView::OnInitialUpdate` 를 호출 하 `UpdateData` 는를 호출 `DoDataExchange` 합니다. 이 초기 호출을 `DoDataExchange` `CRecordView` 통해 컨트롤 (간접적)을 `CRecordset` 클래스 마법사에서 만든 필드 데이터 멤버에 연결 합니다. 이러한 데이터 멤버는 기본 클래스 멤버 함수를 호출한 후에만 사용할 수 있습니다 `CFormView::OnInitialUpdate` .

> [!NOTE]
> 클래스 마법사를 사용 하는 경우 마법사는 **`enum`** 값 `CRecordView::IDD` 을 정의 하 고, 클래스 선언에서 지정 하 고, 생성자의 멤버 초기화 목록에이 값을 사용 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#32](../../mfc/codesnippet/cpp/crecordview-class_1.cpp)]

## <a name="crecordviewisonfirstrecord"></a><a name="isonfirstrecord"></a> CRecordView:: IsOnFirstRecord

이 멤버 함수를 호출 하 여 현재 레코드가이 레코드 뷰와 연결 된 레코드 집합 개체의 첫 번째 레코드 인지 여부를 확인 합니다.

```
BOOL IsOnFirstRecord();
```

### <a name="return-value"></a>반환 값

현재 레코드가 레코드 집합의 첫 번째 레코드 이면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 클래스 마법사에서 작성 한 기본 명령 업데이트 처리기의 고유한 구현을 작성 하는 데 유용 합니다.

사용자가 첫 번째 레코드로 이동 하는 경우 프레임 워크는 첫 번째 레코드나 이전 레코드로 이동 하는 데 사용 하는 사용자 인터페이스 개체를 사용 하지 않도록 설정 합니다.

## <a name="crecordviewisonlastrecord"></a><a name="isonlastrecord"></a> CRecordView:: IsOnLastRecord

이 멤버 함수를 호출 하 여 현재 레코드가이 레코드 뷰와 연결 된 레코드 집합 개체의 마지막 레코드 인지 여부를 확인 합니다.

```
BOOL IsOnLastRecord();
```

### <a name="return-value"></a>반환 값

현재 레코드가 레코드 집합의 마지막 레코드 이면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 레코드에서 레코드로 이동 하기 위한 사용자 인터페이스를 지원 하기 위해 클래스 마법사에서 작성 하는 기본 명령 업데이트 처리기의 고유한 구현을 작성 하는 데 유용 합니다.

> [!CAUTION]
> 이 함수의 결과는 뷰가 사용자가 이전에 이동할 때까지 레코드 집합의 끝을 검색할 수 없는 경우를 제외 하 고 신뢰할 수 있습니다. 사용자는 레코드 뷰가 사용자 인터페이스 개체를 사용 하지 않도록 설정 하 여 다음 또는 마지막 레코드로 이동 해야 함을 알리기 전에 마지막 레코드를 넘어 이동 해야 합니다. 사용자가 마지막 레코드를 지난 후 마지막 레코드로 다시 이동 하는 경우 (또는 이전) 레코드 뷰는 레코드 집합에서 사용자의 위치를 추적 하 고 사용자 인터페이스 개체를 올바르게 비활성화할 수 있습니다. `IsOnLastRecord` 는 `OnRecordLast` ID_RECORD_LAST 명령 또는를 처리 하는 구현 함수를 호출한 후에도 신뢰할 수 없습니다 `CRecordset::MoveLast` .

## <a name="crecordviewongetrecordset"></a><a name="ongetrecordset"></a> CRecordView:: OnGetRecordset

레코드 뷰와 연결 된 파생 개체에 대 한 포인터를 반환 `CRecordset` 합니다.

```
virtual CRecordset* OnGetRecordset() = 0;
```

### <a name="return-value"></a>반환 값

`CRecordset`개체가 성공적으로 만들어졌으면 파생 개체에 대 한 포인터이 고, 그렇지 않으면 NULL 포인터입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 재정의 하 여 레코드 집합 개체를 생성 하거나 가져오고 해당 개체에 대 한 포인터를 반환 해야 합니다. 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 선언 하면 마법사에서 기본 재정의를 작성 합니다. 클래스 마법사의 기본 구현에서는 레코드 뷰에 저장 된 레코드 집합 포인터가 있는 경우이를 반환 합니다. 그렇지 않으면 클래스 마법사를 사용 하 여 지정한 형식의 레코드 집합 개체를 생성 하 고 해당 `Open` 멤버 함수를 호출 하 여 테이블을 열거나 쿼리를 실행 한 다음 개체에 대 한 포인터를 반환 합니다.

자세한 내용 및 예제는 레코드 뷰 [: 레코드 뷰 사용](../../data/using-a-record-view-mfc-data-access.md)문서를 참조 하세요.

## <a name="crecordviewonmove"></a><a name="onmove"></a> CRecordView:: OnMove

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

기본 구현에서는 `Move` 레코드 뷰와 연결 된 개체의 적절 한 멤버 함수를 호출 합니다 `CRecordset` .

기본적으로는 `OnMove` 사용자가 레코드 뷰에서 데이터 원본의 현재 레코드를 변경한 경우 해당 레코드를 업데이트 합니다.

응용 프로그램 마법사는 첫 번째 레코드, 마지막 레코드, 다음 레코드 및 이전 레코드 메뉴 항목을 사용 하 여 메뉴 리소스를 만듭니다. 도킹 가능한 도구 모음 옵션을 선택 하는 경우 응용 프로그램 마법사는 이러한 명령에 해당 하는 단추가 있는 도구 모음도 만듭니다.

레코드 집합에서 마지막 레코드를 지 나 이동 하면 레코드 뷰는 마지막 레코드를 계속 표시 합니다. 첫 번째 레코드를 벗어나 뒤로 이동 하는 경우 레코드 뷰는 첫 번째 레코드를 계속 표시 합니다.

> [!CAUTION]
> 레코드 `OnMove` 집합에 레코드가 없는 경우를 호출 하면 예외가 throw 됩니다. 해당 이동 작업 전에 적절 한 사용자 인터페이스 업데이트 처리기 함수,, 또는를 호출 하 여 레코드 `OnUpdateRecordFirst` `OnUpdateRecordLast` `OnUpdateRecordNext` `OnUpdateRecordPrev` 집합에 레코드가 있는지 여부를 확인 합니다.

## <a name="see-also"></a>참고 항목

[CFormView 클래스](../../mfc/reference/cformview-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CRecordset 클래스](../../mfc/reference/crecordset-class.md)<br/>
[CFormView 클래스](../../mfc/reference/cformview-class.md)
