---
description: '자세한 정보: importlib'
title: importlib (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importlib
helpviewer_keywords:
- importlib attribute
ms.assetid: f129e459-b8d3-4aca-a0bc-ee53e18b62ed
ms.openlocfilehash: f3000be3415ed944d621ebcd36442e33951efc84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114951"
---
# <a name="importlib"></a>importlib

다른 형식 라이브러리에 이미 컴파일된 형식을 만들고 있는 형식 라이브러리에서 사용할 수 있도록 합니다.

## <a name="syntax"></a>구문

```cpp
[ importlib("tlb_file") ];
```

### <a name="parameters"></a>매개 변수

*tlb_file*<br/>
현재 프로젝트의 형식 라이브러리로 가져오려는 .tlb 파일의 이름으로, 따옴표로 묶습니다.

## <a name="remarks"></a>설명

**Importlib** c + + 특성은 `importlib` 생성 된 .idl 파일의 라이브러리 블록에 문을 배치 합니다. **Importlib** 특성은 [importlib](/windows/win32/Midl/importlib) MIDL 특성과 동일한 기능을 포함 합니다.

## <a name="example"></a>예제

다음 코드에서는 **importlib** 를 사용 하는 방법의 예를 보여 줍니다.

```cpp
// cpp_attr_ref_importlib.cpp
// compile with: /LD
[module(name="MyLib")];
[importlib("importlib.tlb")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[되어야](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
