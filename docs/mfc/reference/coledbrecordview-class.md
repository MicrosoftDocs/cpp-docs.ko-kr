---
description: '자세히 알아보기: COleDBRecordView 클래스'
title: COleDBRecordView 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDBRecordView
- AFXOLEDB/COleDBRecordView
- AFXOLEDB/COleDBRecordView::COleDBRecordView
- AFXOLEDB/COleDBRecordView::OnGetRowset
- AFXOLEDB/COleDBRecordView::OnMove
helpviewer_keywords:
- COleDBRecordView [MFC], COleDBRecordView
- COleDBRecordView [MFC], OnGetRowset
- COleDBRecordView [MFC], OnMove
ms.assetid: 98612427-c4c9-4760-b7e1-85b17448add9
ms.openlocfilehash: bce03a482aff558ed6d22c7720ff74f304a9214f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227314"
---
# <a name="coledbrecordview-class"></a>COleDBRecordView 클래스

컨트롤에 데이터베이스 레코드를 표시하는 뷰입니다.

## <a name="syntax"></a>구문

```
class COleDBRecordView : public CFormView
```

## <a name="members"></a>멤버

### <a name="protected-constructors"></a>Protected 생성자

|Name|설명|
|----------|-----------------|
|[COleDBRecordView:: COleDBRecordView](#coledbrecordview)|`COleDBRecordView` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDBRecordView:: OnGetRowset](#ongetrowset)|표준 HRESULT 값을 반환 합니다.|
|[COleDBRecordView:: OnMove](#onmove)|데이터 원본에서 현재 레코드 (더티 인 경우)를 업데이트 한 다음 지정 된 레코드 (다음, 이전, 첫 번째 또는 마지막)로 이동 합니다.|

## <a name="remarks"></a>설명

뷰는 개체에 직접 연결 된 폼 뷰입니다 `CRowset` . 대화 상자 템플릿 리소스에서 뷰를 만들고 `CRowset` 대화 상자 템플릿의 컨트롤에 개체의 필드를 표시 합니다. `COleDBRecordView`개체는 DDX (대화 상자 데이터 교환) 및에 기본 제공 되는 탐색 기능을 사용 `CRowset` 하 여 양식의 컨트롤과 행 집합의 필드 간 데이터 이동을 자동화 합니다. `COleDBRecordView` 는 현재 보기에서 레코드를 업데이트 하기 위한 첫 번째, 다음, 이전, 마지막 레코드 및 인터페이스로 이동 하기 위한 기본 구현도 제공 합니다.

에서 DDX 함수 `COleDbRecordView` 를 사용 하 여 데이터베이스 레코드 집합에서 직접 데이터를 가져오고 대화 상자 컨트롤에 표시할 수 있습니다. 과 같은 메서드 (예:)를 사용 해야 `DDX_*` `DDX_Text` `DDX_Field*` `DDX_FieldText` `COleDbRecordView` 합니다. `DDX_FieldText` 는 `COleDbRecordView` `DDX_FieldText` `CRecordset*` (의 경우 `CRecordView` ) 또는 `CDaoRecordset*` (의 경우) 형식의 추가 인수를 사용 하므로에서 사용할 수 없습니다 `CDaoRecordView` .

> [!NOTE]
> OLE DB 소비자 템플릿 클래스 대신 DAO (Data Access Objects) 클래스를 사용 하 여 작업 하는 경우 [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md) 클래스를 대신 사용 합니다. 자세한 내용은 [개요: 데이터베이스 프로그래밍](../../data/data-access-programming-mfc-atl.md)문서를 참조 하세요.

`COleDBRecordView` 레코드 뷰에서 사용자 인터페이스를 업데이트할 수 있도록 행 집합에서 사용자의 위치를 추적 합니다. 사용자가 행 집합의 한쪽 끝으로 이동할 때 레코드 뷰는 메뉴 항목 또는 도구 모음 단추와 같은 사용자 인터페이스 개체를 사용 하지 않도록 설정 하 여 동일한 방향으로 이동 합니다.

행 집합 클래스에 대 한 자세한 내용은 [OLE DB 소비자 템플릿 사용](../../data/oledb/ole-db-consumer-templates-cpp.md) 문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

`COleDBRecordView`

## <a name="requirements"></a>요구 사항

**헤더:** afxoledb

## <a name="coledbrecordviewcoledbrecordview"></a><a name="coledbrecordview"></a> COleDBRecordView:: COleDBRecordView

`COleDBRecordView` 개체를 생성합니다.

```
COleDBRecordView(LPCTSTR lpszTemplateName);
COleDBRecordView(UINT nIDTemplate);
```

### <a name="parameters"></a>매개 변수

*lpszTemplateName*<br/>
대화 상자 템플릿 리소스의 이름인 null로 끝나는 문자열을 포함 합니다.

*nIDTemplate*<br/>
대화 상자 템플릿 리소스의 ID 번호를 포함 합니다.

### <a name="remarks"></a>설명

에서 파생 된 형식의 개체를 만드는 경우 생성자 중 `COleDBRecordView` 하나를 호출 하 여 뷰 개체를 만들고 뷰의 기반이 되는 대화 상자 리소스를 식별 합니다. 이름을 기준으로 (문자열을 생성자에 인수로 전달 하거나 부호 없는 정수를 인수로 전달) 리소스를 식별할 수 있습니다.

> [!NOTE]
> 파생 클래스는 자체 생성자를 제공 *해야 합니다* . 생성자에서 `COleDBRecordView::COleDBRecordView` 리소스 이름이 나 ID를 인수로 사용 하 여 생성자를 호출 합니다.

## <a name="coledbrecordviewongetrowset"></a><a name="ongetrowset"></a> COleDBRecordView:: OnGetRowset

레코드 뷰와 연결 된 **CRowset<>** 개체에 대 한 핸들을 반환 합니다.

```
virtual CRowset<>* OnGetRowset() = 0;
```

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 멤버 함수를 재정의 하 여 행 집합 개체를 생성 하거나 가져와 핸들을 반환 해야 합니다. 클래스 마법사를 사용 하 여 레코드 뷰 클래스를 선언 하면 마법사에서 기본 재정의를 작성 합니다. 클래스 마법사의 기본 구현에서는 레코드 뷰에 저장 된 행 집합 핸들이 있는 경우이를 반환 합니다. 그렇지 않으면 클래스 마법사를 사용 하 여 지정한 형식의 행 집합 개체를 생성 하 고 해당 `Open` 멤버 함수를 호출 하 여 테이블을 열거나 쿼리를 실행 한 다음 개체에 대 한 핸들을 반환 합니다.

> [!NOTE]
> MFC 7.0 이전에는 `OnGetRowset` 에 대 한 포인터를 반환 했습니다 `CRowset` . 을 호출 하는 코드가 있는 경우 `OnGetRowset` 반환 형식을 템플릿 화 클래스 **CRowset<>** 로 변경 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDatabase#38](../../mfc/codesnippet/cpp/coledbrecordview-class_1.cpp)]

자세한 내용 및 예제는 레코드 뷰 [: 레코드 뷰 사용](../../data/using-a-record-view-mfc-data-access.md)문서를 참조 하세요.

## <a name="coledbrecordviewonmove"></a><a name="onmove"></a> COleDBRecordView:: OnMove

행 집합의 다른 레코드로 이동 하 여 레코드 뷰의 컨트롤에 해당 필드를 표시 합니다.

```
virtual BOOL OnMove(UINT nIDMoveCommand);
```

### <a name="parameters"></a>매개 변수

*nIDMoveCommand*<br/>
다음 표준 명령 ID 값 중 하나입니다.

- ID_RECORD_FIRST-레코드 집합의 첫 번째 레코드로 이동 합니다.

- ID_RECORD_LAST-레코드 집합의 마지막 레코드로 이동 합니다.

- ID_RECORD_NEXT-레코드 집합의 다음 레코드로 이동 합니다.

- ID_RECORD_PREV-레코드 집합의 이전 레코드로 이동 합니다.

### <a name="return-value"></a>반환 값

이동에 성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다. 이동 요청이 거부 된 경우입니다.

### <a name="remarks"></a>설명

기본 구현에서는 `Move` 레코드 뷰와 연결 된 개체의 적절 한 멤버 함수를 호출 합니다 `CRowset` .

기본적으로는 `OnMove` 사용자가 레코드 뷰에서 데이터 원본의 현재 레코드를 변경한 경우 해당 레코드를 업데이트 합니다.

응용 프로그램 마법사는 첫 번째 레코드, 마지막 레코드, 다음 레코드 및 이전 레코드 메뉴 항목을 사용 하 여 메뉴 리소스를 만듭니다. 도킹 가능한 도구 모음 옵션을 선택 하는 경우 응용 프로그램 마법사는 이러한 명령에 해당 하는 단추가 있는 도구 모음도 만듭니다.

레코드 집합에서 마지막 레코드를 지 나 이동 하면 레코드 뷰는 마지막 레코드를 계속 표시 합니다. 첫 번째 레코드를 벗어나 뒤로 이동 하는 경우 레코드 뷰는 첫 번째 레코드를 계속 표시 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)
