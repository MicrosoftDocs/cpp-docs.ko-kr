---
description: 다음에 대해 자세히 알아보세요. `__asm`
title: __asm
ms.date: 10/09/2018
f1_keywords:
- __asm
- _asm
- __asm_cpp
helpviewer_keywords:
- __asm keyword [C++], vs. asm blocks
- __asm keyword [C++]
ms.assetid: 77ff3bc9-a492-4b5e-85e1-fa4e414e79cd
ms.openlocfilehash: 5fa4e64bdb9ae4fc01e6e379de3e8a6771959e80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118058"
---
# `__asm`

**Microsoft 전용**

**`__asm`** 키워드는 인라인 어셈블러를 호출 하 고 c 또는 c + + 문이 유효한 모든 위치에 나타날 수 있습니다. 이 키워드는 자체적으로 표시할 수 없습니다. 이 키워드 다음에는 어셈블리 명령, 중괄호로 묶은 명령 그룹 또는 최소한 빈 괄호의 쌍이 와야 합니다. 여기서 " **`__asm`** 블록" 항은 중괄호에 상관없이 명령 또는 명령 그룹을 참조합니다.

> [!NOTE]
> 표준 c + + 키워드에 대 한 Visual C++ 지원은 **`asm`** 컴파일러가 키워드에서 오류를 생성 하지 않도록 제한 됩니다. 그러나 블록은 **`asm`** 의미 있는 코드를 생성 하지 않습니다. **`__asm`** 대신를 사용 **`asm`** 합니다.

## <a name="grammar"></a>문법

*asm-블록*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm`***어셈블리 명령* **`;`** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`__asm {`***어셈블리 명령 목록* **`}`** **`;`** <sub>opt</sub>

*어셈블리-명령 목록*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*어셈블리 명령* **`;`** <sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*어셈블리 명령* **`;`** *어셈블리 명령 목록* **`;`** <sub>opt</sub>

## <a name="remarks"></a>설명

괄호 없이 사용 하는 경우 **`__asm`** 키워드는 줄의 나머지가 어셈블리 언어 문 임을 의미 합니다. 이 키워드가 중괄호와 함께 사용되는 경우 중괄호 사이의 각 줄이 어셈블리 언어 문임을 의미합니다. 이전 버전과의 호환성을 위해 **`_asm`** 은의 동의어입니다 **`__asm`** .

키워드는 **`__asm`** 문 구분 기호 이므로 같은 줄에 어셈블리 명령을 넣을 수 있습니다.

Visual Studio 2005 이전에는 명령

```cpp
__asm int 3
```

**/clr** 을 사용 하 여 컴파일할 때 네이티브 코드가 생성 되지 않았습니다. 컴파일러가 명령을 CLR break 명령으로 변환 했습니다.

이제 `__asm int 3`을 사용하면 함수의 네이티브 코드가 생성됩니다. 함수를 사용 하 여 코드에서 중단점을 발생 시 키 려 고 하는 함수를 MSIL로 컴파일하려면 [__debugbreak](../../intrinsics/debugbreak.md)를 사용 합니다.

이전 버전과의 호환성을 위해 **`_asm`** 는 **`__asm`** 컴파일러 옵션 [/Za \( 사용 안 함 언어 확장](../../build/reference/za-ze-disable-language-extensions.md) 을 지정 하지 않는 경우의 동의어입니다.

## <a name="example"></a>예제

다음 코드 조각은 **`__asm`** 중괄호로 묶인 간단한 블록입니다.

```cpp
__asm {
   mov al, 2
   mov dx, 0xD007
   out dx, al
}
```

또는 **`__asm`** 을 각 어셈블리 명령 앞에 배치할 수 있습니다.

```cpp
__asm mov al, 2
__asm mov dx, 0xD007
__asm out dx, al
```

키워드는 **`__asm`** 문 구분 기호 이므로 동일한 줄에 어셈블리 명령을 넣을 수도 있습니다.

```cpp
__asm mov al, 2   __asm mov dx, 0xD007   __asm out dx, al
```

세 가지 예제 모두 동일한 코드를 생성 하지만 첫 번째 스타일 ( **`__asm`** 중괄호 안에 블록 포함)에는 몇 가지 장점이 있습니다. 중괄호는 C 또는 c + + 코드에서 어셈블리 코드를 명확 하 게 구분 하 고 키워드의 불필요 한 반복을 방지 합니다 **`__asm`** . 중괄호는 모호성을 방지할 수도 있습니다. C 또는 c + + 문을 블록과 같은 줄에 배치 하려면 **`__asm`** 해당 블록을 중괄호로 묶어야 합니다. 중괄호가 없으면 컴파일러는 어셈블리 코드가 중지되고 C 또는 C++ 문이 시작되는 위치를 파악할 수 없습니다. 마지막으로, 중괄호 안의 텍스트는 일반 MASM 텍스트와 형식이 동일하므로 기존 MASM 소스 파일의 텍스트를 쉽게 잘라내고 붙여 넣을 수 있습니다.

C 및 c + +의 중괄호와 달리 블록을 묶는 중괄호는 **`__asm`** 변수 범위에 영향을 주지 않습니다. 블록을 중첩할 수도 있습니다. **`__asm`** 중첩은 변수 범위에 영향을 주지 않습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[키워드](../../cpp/keywords-cpp.md)<br/>
[인라인 어셈블러](../../assembler/inline/inline-assembler.md)<br/>
