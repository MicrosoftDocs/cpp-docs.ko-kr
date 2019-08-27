﻿---
title: 명시적 인스턴스화
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- explicit instantiation
- instantiation, explicit
ms.assetid: 8b0d4e32-45a6-49d5-8041-1ebdd674410e
ms.openlocfilehash: 45661653b4b8f1a4f94ece1c53aa86f4a431700b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392208"
---
# <a name="explicit-instantiation"></a>명시적 인스턴스화

명시적 인스턴스화를 통해 코드에서 실제로 사용하지 않고 함수 또는 템플릿 기반 클래스의 인스턴스화를 만들 수 있습니다. 이는 배포를 위해 템플릿을 사용하는 라이브러리(.lib) 파일을 만들 때 유용하기 때문에 인스턴스화되지 않은 템플릿 정의는 개체 파일(.obj)에 저장되지 않습니다.

다음은 **int** 변수 및 6개 항목에 대해 `MyStack`을 명시적으로 인스턴스화합니다.

```cpp
template class MyStack<int, 6>;
```

이 명령문은 개체에 대한 스토리지 없이 `MyStack`의 인스턴스를 만듭니다. 모든 구성원에 대한 코드가 생성됩니다.

다음 라인은 생성자 멤버 함수만을 명시적으로 인스턴스화합니다.

```cpp
template MyStack<int, 6>::MyStack( void );
```

다음 [함수 템플릿 인스턴스화](../cpp/function-template-instantiation.md) 예제에서와 같이 다시 선언하는 특정 형식 인수를 사용하여 함수 템플릿을 명시적으로 인스턴스화할 수 있습니다.

**extern** 키워드를 사용하여 멤버의 자동 인스턴스화를 방지할 수 있습니다. 예를 들면 다음과 같습니다.

```cpp
extern template class MyStack<int, 6>;
```

마찬가지로 특정 멤버를 외부 및 인스턴스화되지 않음으로 표시할 수 있습니다.

```cpp
extern template MyStack<int, 6>::MyStack( void );
```

하나 이상의 개체 모듈에서 같은 인스턴스화 코드를 생성하는 컴파일러를 유지하는 다음 **extern** 키워드를 사용합니다. 만약 함수가 호출되면 하나 이상 연결된 모듈에서 지정된 명시적 템플릿을 사용하여 템플릿 함수를 인스턴스화해야 합니다. 그렇지 않으면 프로그램을 빌드할 때 링커 오류가 발생합니다.

> [!NOTE]
>  특수화의 **extern** 키워드는 클래스 본문 외부에서 정의된 멤버 함수에만 적용됩니다. 클래스 선언 안에 정의된 함수는 인라인 함수로 간주되며 항상 인스턴스화됩니다.

## <a name="see-also"></a>참고 항목

[함수 템플릿](../cpp/function-templates.md)
