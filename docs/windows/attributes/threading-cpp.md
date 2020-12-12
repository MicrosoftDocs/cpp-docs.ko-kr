---
description: '자세한 정보: 스레딩 (c + +)'
title: 스레딩 (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.threading
helpviewer_keywords:
- threading attribute
ms.assetid: 9b558cd6-fbf0-4602-aed5-31c068550ce3
ms.openlocfilehash: e46a3720280fe7ee7b9debae98e3270825e8db40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327250"
---
# <a name="threading-c"></a>threading(C++)

COM 개체의 스레딩 모델을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ threading(model=enumeration) ]
```

### <a name="parameters"></a>매개 변수

*model*<br/>
필드 다음 스레딩 모델 중 하나입니다.

- `apartment` (아파트 스레딩)

- `neutral` (사용자 인터페이스가 없는 .NET Framework 구성 요소)

- `single` (단순 스레딩)

- `free` (자유 스레딩)

- `both` (아파트 및 자유 스레딩)

기본값은 `apartment`입니다.

## <a name="remarks"></a>설명

**스레딩** c + + 특성은 생성 된 .idl 파일에 표시 되지 않지만 COM 개체의 구현에 사용 됩니다.

ATL 프로젝트에서 [coclass](coclass.md) 특성도 있는 경우 *model* 에 지정 된 스레딩 모델은 특성에 의해 삽입 된 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) 클래스에 템플릿 매개 변수로 전달 됩니다 `coclass` .

또한 **스레딩** 특성은 [event_source](event-source.md)에 대 한 액세스를 보호 합니다.

## <a name="example"></a>예제

**스레딩을** 사용 하는 샘플은 사용 [이 허가](licensed.md) 된 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|**coclass**|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[COM 특성](com-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[이전 코드에 대 한 다중 스레딩 지원 (Visual C++)](../../parallel/multithreading-support-for-older-code-visual-cpp.md)<br/>
[중립 아파트](/windows/win32/cossdk/neutral-apartments)
