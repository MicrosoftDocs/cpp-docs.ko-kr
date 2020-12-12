---
description: '자세한 정보: MFC 클래스 개체의 형식 캐스팅'
title: MFC 클래스 개체의 형식 캐스팅
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: bec49afc0050aa32c6e5436e5efca9b0dab30709
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218673"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC 클래스 개체의 형식 캐스팅

형식 캐스팅 매크로는 특정 클래스의 개체를 가리키는 포인터에 대 한 포인터를 캐스트 하는 방법을 제공 합니다.

다음 표에서는 MFC 형식 캐스팅 매크로를 보여 줍니다.

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>MFC 클래스 개체에 대 한 포인터를 캐스트 하는 매크로

|Name|설명|
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|캐스트가 유효한 지 여부를 확인 하는 동안 클래스 개체에 대 한 포인터로 포인터를 캐스팅 합니다.|
|[STATIC_DOWNCAST](#static_downcast)|특정 클래스의 개체에 대 한 포인터를 관련 형식의 포인터로 캐스팅 합니다. 디버그 빌드에서 개체가 대상 형식의 "종류"가 아니면 어설션이 발생 합니다.|

## <a name="dynamic_downcast"></a><a name="dynamic_downcast"></a> DYNAMIC_DOWNCAST

캐스팅이 유효한 지 여부를 확인 하는 동안 클래스 개체에 대 한 포인터를 포인터로 캐스팅 하는 편리한 방법을 제공 합니다.

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>매개 변수

*class*<br/>
클래스의 이름입니다.

*놓고*<br/>
*클래스* 형식의 개체에 대 한 포인터로 캐스팅 될 포인터입니다.

### <a name="remarks"></a>설명

이 매크로는 *포인터* 매개 변수를 *클래스* 매개 변수 형식의 개체에 대 한 포인터로 캐스팅 합니다.

포인터가 참조 하는 개체가 식별 된 클래스의 "종류" 이면 매크로는 적절 한 포인터를 반환 합니다. 올바른 캐스트가 아니면 매크로가 NULL을 반환 합니다.

## <a name="static_downcast"></a><a name="static_downcast"></a> STATIC_DOWNCAST

*Pobject* 를 *class_name* 개체에 대 한 포인터로 캐스팅 합니다.

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>매개 변수

*class_name*<br/>
캐스팅 되는 클래스의 이름입니다.

*pobject*<br/>
*Class_name* 개체에 대 한 포인터로 캐스팅 될 포인터입니다.

### <a name="remarks"></a>설명

*pobject* 은 NULL 이거나, *class_name* 에서 직접 파생 되거나 간접적으로 파생 되는 클래스의 개체를 가리켜야 합니다. _DEBUG 전처리기 기호가 정의 된 응용 프로그램의 빌드에서는 *pobject* 가 NULL이 아니거나 *class_name* 매개 변수에 지정 된 클래스의 "종류"가 아닌 개체를 가리키는 경우 ( [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)참조)를 어설션 합니다. **_DEBUG** 되지 않은 빌드에서는 매크로는 형식 검사 없이 캐스트를 수행 합니다.

*Class_name* 매개 변수에 지정 된 클래스는에서 파생 되어야 `CObject` 하며, CObject [클래스: cobject에서 클래스 파생](../../mfc/deriving-a-class-from-cobject.md)문서에 설명 된 대로 DECLARE_DYNAMIC 및 IMPLEMENT_DYNAMIC, DECLARE_DYNCREATE 및 IMPLEMENT_DYNCREATE, DECLARE_SERIAL 및 IMPLEMENT_SERIAL 매크로를 사용 해야 합니다.

예를 들어, 라고 하는 포인터를 `CMyDoc` `pMyDoc` 이 식을 사용 하는 포인터로 캐스팅할 수 있습니다 `CDocument` .

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

`pMyDoc`가에서 직접 또는 간접적으로 파생 된 개체를 가리키지 않는 경우 `CDocument` 매크로는을 어설션 합니다.

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)
