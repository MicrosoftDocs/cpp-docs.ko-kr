---
description: '자세한 정보: ATL 복사 정책 클래스'
title: ATL 복사 정책 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- data [C++], ATL
- classes [C++], copy policy
- copy policy classes [C++]
- _Copy class
- _CopyInterface class
ms.assetid: 06704b68-d318-4c5d-a65b-71457fe9d00d
ms.openlocfilehash: 502befadbd9317602c49d9a5815dee6ebc239d78
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97165760"
---
# <a name="atl-copy-policy-classes"></a>ATL 복사 정책 클래스

복사 정책 클래스는 데이터를 초기화, 복사 및 삭제 하는 데 사용 되는 [유틸리티 클래스](../atl/utility-classes.md) 입니다. 복사 정책 클래스를 사용 하 여 모든 유형의 데이터에 대 한 복사 의미 체계를 정의 하 고 다양 한 데이터 형식 간의 변환을 정의할 수 있습니다.

ATL은 다음 템플릿의 구현에서 복사 정책 클래스를 사용 합니다.

- [CComEnumImpl](../atl/reference/ccomenumimpl-class.md)

- [IEnumOnSTLImpl](../atl/reference/ienumonstlimpl-class.md)

- [ICollectionOnSTLImpl](../atl/reference/icollectiononstlimpl-class.md)

템플릿 인수로 전달 될 수 있는 복사 정책 클래스에서 데이터를 복사 하거나 변환 하는 데 필요한 정보를 캡슐화 하 여 ATL 개발자는 이러한 클래스를 최대한 활용할 수 있도록 제공 했습니다. 예를 들어 임의의 데이터 형식을 사용 하 여 컬렉션을 구현 해야 하는 경우에는 적절 한 복사 정책만 제공 하면 됩니다. 컬렉션을 구현 하는 코드를 터치 하지 않아도 됩니다.

## <a name="definition"></a>정의

정의에 따라 다음과 같은 정적 함수를 제공 하는 클래스는 복사 정책 클래스입니다.

`static void init(` `DestinationType` `* p);`

`static HRESULT copy(` `DestinationType` `* pTo, const`  `SourceType` `* pFrom);`

`static void destroy(` `DestinationType` `* p);`

`DestinationType`각 복사 정책의 형식 및 *SourceType* 을 임의의 데이터 형식으로 바꿀 수 있습니다.

> [!NOTE]
> 임의의 데이터 형식에 대 한 복사 정책 클래스를 정의할 수 있지만 ATL 코드의 클래스를 사용 하는 경우 적합 한 형식을 제한 해야 합니다. 예를 들어, ATL의 컬렉션 또는 열거자 구현에 복사 정책 클래스를 사용 하는 경우은 `DestinationType` COM 인터페이스 메서드에서 매개 변수로 사용할 수 있는 형식 이어야 합니다.

**Init** 를 사용 하 여 데이터를 초기화 하 고, 데이터를 **복사 하 여 복사 하** 고, 데이터를 **해제할 수 있습니다** . 초기화, 복사 및 소멸의 정확한 의미는 복사 정책 클래스의 도메인 이며 관련 된 데이터 형식에 따라 달라 집니다.

Copy policy 클래스의 사용 및 구현에는 다음과 같은 두 가지 요구 사항이 있습니다.

- **복사할** 첫 번째 매개 변수는 **init** 를 사용 하 여 이전에 초기화 한 데이터에 대 한 포인터만 받아야 합니다.

- **제거** 는 **초기화** 를 사용 하 여 이전에 초기화 했거나 **복사** 를 통해 복사 된 데이터에 대 한 포인터만 받아야 합니다.

## <a name="standard-implementations"></a>표준 구현

ATL은 `_Copy` 및 템플릿 클래스의 형식으로 두 개의 복사 정책 클래스를 제공 합니다 `_CopyInterface` .

- `_Copy`클래스는 두 개의 템플릿 매개 변수만 제공 하 고 SourceType를 지정 하기 때문에 유형이 다른 복사 전용 (데이터 형식 간에 변환 안 함)을 허용 `DestinationType` 합니다.  이 템플릿의 제네릭 구현에는 초기화 나 소멸 코드가 포함 되지 않으며 `memcpy` 를 사용 하 여 데이터를 복사 합니다. 또한 ATL은 `_Copy` VARIANT, LPOLESTR, OLEVERB 및 CONNECTDATA 데이터 형식에 대 한 특수화를 제공 합니다.

- `_CopyInterface`클래스는 표준 COM 규칙에 따라 인터페이스 포인터를 복사 하기 위한 구현을 제공 합니다. 이 클래스는 한 번만 복사를 허용 하므로 단순 할당 및에 대 한 호출을 사용 하 여 `AddRef` 복사를 수행 합니다.

## <a name="custom-implementations"></a>사용자 지정 구현

일반적으로 다른 유형의 복사 (즉, 데이터 형식 간 변환)에 대해 고유한 복사본 정책 클래스를 정의 해야 합니다. 사용자 지정 복사 정책 클래스의 몇 가지 [예는 파일](../overview/visual-cpp-samples.md) VCUE_Copy .h 및 VCUE_CopyString를 참조 하세요. 이러한 파일에는 두 개의 템플릿 복사 정책 클래스 `GenericCopy` 와 `MapCopy` , `GenericCopy` 다양 한 데이터 형식에 대 한 다양 한 특수화가 포함 되어 있습니다.

### <a name="genericcopy"></a>GenericCopy

`GenericCopy`*SourceType* 및를 템플릿 인수로 지정할 수 있습니다 `DestinationType` . VCUE_Copy에서 클래스의 가장 일반적인 형태는 `GenericCopy` 다음과 같습니다.

[!code-cpp[NVC_ATL_COM#30](../atl/codesnippet/cpp/atl-copy-policy-classes_1.h)]

VCUE_Copy에는이 클래스의 특수화도 포함 됩니다. `GenericCopy<BSTR>` , `GenericCopy<VARIANT, BSTR>` , `GenericCopy<BSTR, VARIANT>` . VCUE_CopyString에는 **std:: string** s: `GenericCopy<std::string>` , 및에서 복사 하기 위한 특수화가 포함 되어 있습니다. `GenericCopy<VARIANT, std::string>` `GenericCopy<BSTR, std::string>` 사용자 `GenericCopy` 고유의 추가 특수화를 제공 하 여 향상 시킬 수 있습니다.

### <a name="mapcopy"></a>MapCopy

`MapCopy` 복사할 데이터가 c + + 표준 라이브러리 스타일 맵에 저장 되어 있다고 가정 합니다. 그러면 데이터가 저장 되는 맵의 유형과 대상 형식을 지정할 수 있습니다. 클래스의 구현에서는 *maptype* 클래스에서 제공 하는 typedef를 사용 하 여 원본 데이터의 형식을 확인 하 고 적절 한 클래스를 호출 합니다 `GenericCopy` . 이 클래스의 특수화는 필요 하지 않습니다.

[!code-cpp[NVC_ATL_COM#31](../atl/codesnippet/cpp/atl-copy-policy-classes_2.h)]

## <a name="see-also"></a>참고 항목

[C + + 표준 Library-Based 컬렉션 구현](../atl/implementing-an-stl-based-collection.md)<br/>
[이 컬렉션 샘플](../overview/visual-cpp-samples.md)
