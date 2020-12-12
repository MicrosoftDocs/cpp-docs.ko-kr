---
description: '자세히 알아보기: 범주 매크로'
title: 범주 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 31cbef36ca02fb990ba8935915837074d7dd4116
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165084"
---
# <a name="category-macros"></a>범주 매크로

이러한 매크로는 범주 맵을 정의 합니다.

|매크로|설명|
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|범주 맵의 시작을 표시 합니다.|
|[END_CATEGORY_MAP](#end_category_map)|범주 맵의 끝을 표시 합니다.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|COM 개체에서 구현 하는 범주를 나타냅니다.|
|[REQUIRED_CATEGORY](#required_category)|COM 개체에 의해 컨테이너에 필요한 범주를 나타냅니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="begin_category_map"></a><a name="begin_category_map"></a> BEGIN_CATEGORY_MAP

범주 맵의 시작을 표시 합니다.

```cpp
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>매개 변수

*theClass*<br/>
진행 범주 맵을 포함 하는 클래스의 이름입니다.

### <a name="remarks"></a>설명

범주 맵은 COM 클래스에서 구현 하는 구성 요소 범주와 해당 컨테이너에서 필요한 범주를 지정 하는 데 사용 됩니다.

COM 클래스에서 구현 하는 각 범주에 대 한 [IMPLEMENTED_CATEGORY](#implemented_category) 항목을 맵에 추가 합니다. 클래스에서 클라이언트를 구현 해야 하는 각 범주에 대 한 [REQUIRED_CATEGORY](#required_category) 항목을 맵에 추가 합니다. 맵의 끝을 [END_CATEGORY_MAP](#end_category_map) 매크로로 표시 합니다.

클래스에 연결 된 [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 또는 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)있는 경우 맵에 표시 되는 구성 요소 범주는 모듈이 등록 될 때 자동으로 등록 됩니다.

> [!NOTE]
> ATL은 표준 구성 요소 범주 관리자를 사용 하 여 구성 요소 범주를 등록 합니다. 모듈이 등록 될 때 시스템에 관리자가 없으면 등록에 성공 하지만 해당 클래스에 대해 구성 요소 범주가 등록 되지 않습니다.

구성 요소 범주에 대 한 자세한 내용은 [구성 요소 범주 정의 및 Windows SDK에서 작동 하는 방법](/windows/win32/com/component-categories-and-how-they-work) 을 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a> END_CATEGORY_MAP

범주 맵의 끝을 표시 합니다.

```cpp
END_CATEGORY_MAP()
```

### <a name="example"></a>예제

[BEGIN_CATEGORY_MAP](#begin_category_map)의 예제를 참조 하세요.

## <a name="implemented_category"></a><a name="implemented_category"></a> IMPLEMENTED_CATEGORY

구성 요소의 [범주 맵에](#begin_category_map) IMPLEMENTED_CATEGORY 매크로를 추가 하 여 *catID* 매개 변수로 식별 된 범주를 구현 하도록 등록 해야 함을 지정 합니다.

```cpp
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>매개 변수

*catID*<br/>
진행 구현 된 범주에 대 한 GUID (globally unique identifier)가 포함 된 CATID 상수 또는 변수입니다. *CatID* 주소가 사용 되 고 맵에 추가 됩니다. 선택한 주식 범주에 대해서는 아래 표를 참조 하세요.

### <a name="remarks"></a>설명

클래스에 연결 된 [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 또는 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) 매크로가 있는 경우 맵에 나열 된 구성 요소 범주는 모듈이 등록 될 때 자동으로 등록 됩니다.

클라이언트는 클래스에 대해 등록 된 범주 정보를 사용 하 여 인스턴스를 만들지 않고도 기능 및 요구 사항을 확인할 수 있습니다.

구성 요소 범주에 대 한 자세한 내용은 [구성 요소 범주 정의 및 Windows SDK에서 작동 하는 방법](/windows/win32/com/component-categories-and-how-they-work) 을 참조 하세요.

### <a name="a-selection-of-stock-categories"></a>선택 된 스톡 범주

|설명|기호|레지스트리 GUID|
|-----------------|------------|-------------------|
|스크립팅에 안전|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|초기화 안전|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|단순한 프레임 사이트 포함|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|단순 데이터 바인딩|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|고급 데이터 바인딩|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|창 없는 컨트롤|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|개체 Internet-Aware|샘플 목록은 Windows SDK의 [인터넷 인식 개체](/windows/win32/com/internet-aware-objects) 를 참조 하세요.||

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a> REQUIRED_CATEGORY

구성 요소 [범주 맵에](#begin_category_map) REQUIRED_CATEGORY 매크로를 추가 하 여 *catID* 매개 변수로 식별 된 범주가 필요한 것으로 등록 되도록 지정 합니다.

```cpp
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>매개 변수

*catID*<br/>
진행 필수 범주의 GUID (globally unique identifier)를 포함 하는 CATID 상수 또는 변수입니다. *CatID* 주소가 사용 되 고 맵에 추가 됩니다. 선택한 주식 범주에 대해서는 아래 표를 참조 하세요.

### <a name="remarks"></a>설명

클래스에 연결 된 [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) 또는 [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) 매크로가 있는 경우 맵에 나열 된 구성 요소 범주는 모듈이 등록 될 때 자동으로 등록 됩니다.

클라이언트는 클래스에 대해 등록 된 범주 정보를 사용 하 여 인스턴스를 만들지 않고도 기능 및 요구 사항을 확인할 수 있습니다. 예를 들어, 컨트롤에서 컨테이너가 데이터 바인딩을 지원 하도록 요구할 수 있습니다. 컨테이너는 해당 컨트롤에 필요한 범주에 대 한 범주 관리자를 쿼리하여 컨트롤을 호스트 하는 데 필요한 기능이 있는지 확인할 수 있습니다. 컨테이너가 필요한 기능을 지원 하지 않는 경우 COM 개체의 호스트를 거부할 수 있습니다.

샘플 목록을 비롯 한 구성 요소 범주에 대 한 자세한 내용은 [구성 요소 범주 정의 및 Windows SDK에서 작동 하는 방법](/windows/win32/com/component-categories-and-how-they-work) 을 참조 하세요.

### <a name="a-selection-of-stock-categories"></a>선택 된 스톡 범주

|설명|기호|레지스트리 GUID|
|-----------------|------------|-------------------|
|스크립팅에 안전|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|초기화 안전|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|단순한 프레임 사이트 포함|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|단순 데이터 바인딩|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|고급 데이터 바인딩|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|창 없는 컨트롤|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|개체 Internet-Aware|샘플 목록은 Windows SDK의 [인터넷 인식 개체](/windows/win32/com/internet-aware-objects) 를 참조 하세요.||

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
