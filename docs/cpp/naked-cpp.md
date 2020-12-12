---
description: '자세한 정보: naked (c + +)'
title: naked(C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: 1f416f116d7d2a3179dc43545f1302fcd9c7d101
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313829"
---
# <a name="naked-c"></a>naked(C++)

**Microsoft 전용**

특성을 사용 하 여 선언 된 함수의 경우 **`naked`** 컴파일러는 프롤로그 및 에필로그 코드 없이 코드를 생성 합니다. 이 기능을 이용하여 인라인 어셈블러 코드로 사용자 정의 프롤로그/에필로그 코드 시퀀스를 작성할 수 있습니다. naked 함수는 가상 디바이스 드라이버 작성에 특히 유용합니다.  **`naked`** 특성은 x86 및 ARM 에서만 유효 하며 x64에서는 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
__declspec(naked) declarator
```

## <a name="remarks"></a>설명

특성은 **`naked`** 함수 정의에만 관련 되 고 형식 한정자가 아니기 때문에 naked 함수는 확장 된 특성 구문과 [__declspec](../cpp/declspec.md) 키워드를 사용 해야 합니다.

컴파일러가 [__forceinline](inline-functions-cpp.md) 키워드로 표시 된 경우에도 naked 특성으로 표시 된 함수에 대해 인라인 함수를 생성할 수 없습니다.

**`naked`** 멤버가 멤버가 아닌 메서드의 정의 이외의 값에 적용 되는 경우 컴파일러가 오류를 발생 시킵니다.

## <a name="examples"></a>예제

이 코드는 특성을 사용 하 여 함수를 정의 합니다 **`naked`** .

```
__declspec( naked ) int func( formal_parameters ) {}
```

또는 다음과 같이 합니다.

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**`naked`** 특성은 함수의 프롤로그 및 에필로그 시퀀스에 대 한 컴파일러의 코드 생성 특성에만 영향을 줍니다. 이러한 함수를 호출하기 위해 생성되는 코드에는 영향을 주지 않습니다. 따라서 특성은 **`naked`** 함수 형식의 일부로 간주 되지 않으며, 함수 포인터는 특성을 가질 수 없습니다 **`naked`** . 또한 특성은 **`naked`** 데이터 정의에 적용 될 수 없습니다. 예를 들어 다음 코드 샘플은 오류를 생성 합니다.

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**`naked`** 특성은 함수 정의에만 관련 되며 함수의 프로토타입에는 지정할 수 없습니다. 예를 들어 다음 선언은 컴파일러 오류를 생성 합니다.

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[Naked 함수 호출](../cpp/naked-function-calls.md)
