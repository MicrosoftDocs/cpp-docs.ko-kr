---
description: '자세한 정보: 개체 맵 매크로'
title: 개체 맵 매크로
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: accd1fdaebaab3a5c71730dcfd5db83fc2b320de
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139037"
---
# <a name="object-map-macros"></a>개체 맵 매크로

이러한 매크로는 개체 맵과 항목을 정의 합니다.

|Name|설명|
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|개체 맵에 입력 될 클래스 개체의 텍스트 설명을 지정할 수 있습니다.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|ATL 개체를 개체 맵에 입력 하 고, 레지스트리를 업데이트 하 고, 개체의 인스턴스를 만듭니다.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|개체를 등록하고 초기화해야 하지만 `CoCreateInstance`를 통해 외부적으로 생성할 수 없도록 지정할 수 있습니다.|

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="declare_object_description"></a><a name="declare_object_description"></a> DECLARE_OBJECT_DESCRIPTION

클래스 개체에 대 한 텍스트 설명을 지정할 수 있습니다.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>매개 변수

*x*<br/>
진행 클래스 개체의 설명입니다.

### <a name="remarks"></a>설명

ATL은 [OBJECT_ENTRY_AUTO](#object_entry_auto) 매크로를 통해 개체 맵에이 설명을 입력 합니다.

DECLARE_OBJECT_DESCRIPTION는 `GetObjectDescription` [CComCoClass:: GetObjectDescription](ccomcoclass-class.md#getobjectdescription) 메서드를 재정의 하는 데 사용할 수 있는 함수를 구현 합니다.

`GetObjectDescription`함수는에 의해 호출 됩니다 `IComponentRegistrar::GetComponents` . `IComponentRegistrar` 는 DLL에서 개별 구성 요소를 등록 및 등록 취소할 수 있도록 하는 자동화 인터페이스입니다. ATL 프로젝트 마법사를 사용 하 여 구성 요소 등록자 개체를 만들면 마법사가 자동으로 인터페이스를 구현 합니다 `IComponentRegistrar` . `IComponentRegistrar` 는 일반적으로 Microsoft 트랜잭션 서버에서 사용 됩니다.

ATL 프로젝트 마법사에 대 한 자세한 내용은 [Atl 프로젝트 만들기](../../atl/reference/creating-an-atl-project.md)문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a> OBJECT_ENTRY_AUTO

ATL 개체를 개체 맵에 입력 하 고, 레지스트리를 업데이트 하 고, 개체의 인스턴스를 만듭니다.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>매개 변수

*가*<br/>
진행 *클래스* 라는 c + + 클래스에 의해 구현 되는 COM 클래스의 CLSID입니다.

*class*<br/>
진행 *Clsid* 로 표시 되는 COM 클래스를 구현 하는 c + + 클래스의 이름입니다.

### <a name="remarks"></a>설명

개체 항목 매크로는 클래스 등록, 초기화 및 만들기를 지원하도록 프로젝트의 전역 범위에 배치됩니다.

OBJECT_ENTRY_AUTO는이 개체에 대 한 creator 클래스 및 클래스 팩터리 creator 클래스 함수의 함수 포인터를 `CreateInstance` 자동 생성 된 ATL 개체 맵에 입력 합니다. [Catlcommodule:: RegisterServer](catlcommodule-class.md#registerserver) 가 호출 되 면 개체 맵의 각 개체에 대 한 시스템 레지스트리를 업데이트 합니다.

다음 표에서는 개체 맵에 추가 된 정보를이 매크로에 대 한 두 번째 매개 변수로 제공 된 클래스에서 가져오는 방법을 설명 합니다.

|정보|다음에서 가져옴|
|---------------------|-------------------|
|COM 등록|[레지스트리 매크로](../../atl/reference/registry-macros.md)|
|클래스 팩터리 만들기|[클래스 팩터리 매크로](../../atl/reference/aggregation-and-class-factory-macros.md)|
|인스턴스 만들기|[집계 매크로](../../atl/reference/aggregation-and-class-factory-macros.md)|
|구성 요소 범주 등록|[범주 매크로](../../atl/reference/category-macros.md)|
|클래스 수준 초기화 및 정리|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a> OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

개체를 등록하고 초기화해야 하지만 `CoCreateInstance`를 통해 외부적으로 생성할 수 없도록 지정할 수 있습니다.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>매개 변수

*가*<br/>
진행 *클래스* 라는 c + + 클래스에 의해 구현 되는 COM 클래스의 CLSID입니다.

*class*<br/>
진행 *Clsid* 로 표시 되는 COM 클래스를 구현 하는 c + + 클래스의 이름입니다.

### <a name="remarks"></a>설명

개체 항목 매크로는 클래스 등록, 초기화 및 만들기를 지원하도록 프로젝트의 전역 범위에 배치됩니다.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO를 사용 하 여 개체를 등록 하 고 초기화 해야 함을 지정할 수 있습니다 (자세한 내용은 [OBJECT_ENTRY_AUTO](#object_entry_auto) 참조). 또한를 통해 만들 수는 없습니다 `CoCreateInstance` .

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)
