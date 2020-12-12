---
description: '자세한 정보: 임시 개체'
title: 임시 개체
ms.date: 11/04/2016
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
ms.openlocfilehash: d827568013b3684c2126887d390ecbf223c46da5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164746"
---
# <a name="temporary-objects"></a>임시 개체

경우에 따라 컴파일러가 임시 개체를 만들어야 합니다. 다음과 같은 이유로 이 임시 개체를 만들 수 있습니다.

- **`const`** 초기화 되는 참조의 기본 형식과 다른 형식의 이니셜라이저를 사용 하 여 참조를 초기화 하려면입니다.

- 사용자 정의 형식을 반환하는 함수의 반환 값을 저장하려는 경우 이러한 임시 개체는 프로그램이 반환 값을 개체에 복사하지 않는 경우에만 만들어집니다. 예를 들어:

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   반환 값이 다른 개체에 복사되지 않기 때문에 임시 개체가 만들어집니다. 임시 개체가 만들어지는 보다 일반적인 경우는 오버로드된 연산자 함수를 호출해야 하는 식을 계산하는 경우입니다. 이러한 오버로드된 연산자 함수는 다른 개체에 자주 복사되지 않는 사용자 정의 형식을 반환합니다.

   `ComplexResult = Complex1 + Complex2 + Complex3` 식을 참조하십시오. `Complex1 + Complex2` 식이 계산되고 결과가 임시 개체에 저장됩니다. 그런 다음 식이 *임시* 식으로 `+ Complex3` 계산 되 고 결과가에 복사 됩니다 `ComplexResult` (대입 연산자가 오버 로드 되지 않는다고 가정).

- 캐스팅 결과를 사용자 정의 형식에 저장하려는 경우. 지정된 형식의 개체를 사용자 정의 형식으로 명시적으로 변환하는 경우 새 개체는 임시 개체로 구성됩니다.

임시 개체는 생성된 시점과 제거되는 시점에 따라 정의되는 수명을 가집니다. 둘 이상의 임시 개체를 만드는 식은 결국 만들어진 순서의 역순으로 제거됩니다. 소멸이 발생하는 시점은 다음 표에 나와 있습니다.

### <a name="destruction-points-for-temporary-objects"></a>임시 개체에 대한 소멸 지점

|임시 생성 원인|소멸 지점|
|------------------------------|-----------------------|
|식 계산 결과|식 계산의 결과로 만들어진 모든 임시 개체는 식 문의 끝 (즉, 세미콜론) 또는 **`for`** ,, **`if`** **`while`** , **`do`** 및 **`switch`** 문에 대 한 제어 식의 끝에서 제거 됩니다.|
|**`const`** 참조 초기화|이니셜라이저가 초기화되고 있는 참조와 동일한 형식의 l-value가 아닌 경우 기본 개체 형식의 임시 개체가 만들어지고 초기화 식을 사용하여 초기화됩니다. 이 임시 개체는 이 개체가 바인딩된 참조 개체가 제거된 후 즉시 제거됩니다.|
