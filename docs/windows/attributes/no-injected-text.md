---
description: '다음에 대 한 자세한 정보: no_injected_text'
title: no_injected_text (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.no_injected_text
helpviewer_keywords:
- no_injected_text attribute
ms.assetid: 5256f808-e41e-4f4a-9ea5-e447919f5696
ms.openlocfilehash: 3d6b4b77055b6706256b25b0b722034e0275ec19
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327471"
---
# <a name="no_injected_text"></a>no_injected_text

컴파일러가 특성 사용의 결과로 코드를 삽입 하지 않도록 합니다.

## <a name="syntax"></a>구문

```cpp
[ no_injected_text(boolean) ];
```

### <a name="parameters"></a>매개 변수

*boolean*<br/>
(선택 사항) **`true`** 코드를 삽입 하지 않으려는 경우 코드를 삽입할 **`false`** 수 있습니다. **`true`** 가 기본값입니다.

## <a name="remarks"></a>설명

**No_injected_text** c + + 특성의 가장 일반적인 용도는 **no_injected_text** 특성을 .mrg 파일에 삽입 하는 [/fx](../../build/reference/fx-merge-injected-code.md) 컴파일러 옵션을 사용 하는 것입니다.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)
