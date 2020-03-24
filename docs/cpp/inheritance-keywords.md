---
title: 상속 키워드
ms.date: 11/04/2016
f1_keywords:
- __multiple_inheritance
- __single_inheritance_cpp
- __virtual_inheritance_cpp
- __virtual_inheritance
- __multiple_inheritance_cpp
- __single_inheritance
helpviewer_keywords:
- __single_inheritance keyword [C++]
- declaring derived classes [C++]
- keywords [C++], inheritance keywords
- __multiple_inheritance keyword [C++]
- __virtual_inheritance keyword [C++]
- inheritance, declaring derived classes
- derived classes [C++], declaring
- inheritance, keywords
ms.assetid: bb810f56-7720-4fea-b8b6-9499edd141df
ms.openlocfilehash: 781673582cb2c3086677b05abc6a7eb73eeabdb4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178194"
---
# <a name="inheritance-keywords"></a>상속 키워드

**Microsoft 전용**

```
class [__single_inheritance] class-name;
class [__multiple_inheritance] class-name;
class [__virtual_inheritance] class-name;
```

각 항목이 나타내는 의미는 다음과 같습니다.

*클래스-이름*<br/>
선언되는 클래스의 이름입니다.

C++를 사용하면 클래스의 정의 이전에 클래스 멤버에 대한 포인터를 선언할 수 있습니다. 예를 들면 다음과 같습니다.

```cpp
class S;
int S::*p;
```

위의 코드에서 `p`은 클래스 S의 정수 멤버에 대 한 포인터로 선언 됩니다. 그러나이 코드에는 `class S` 아직 정의 되어 있지 않습니다. 단지 선언 되었습니다. 컴파일러는 이러한 포인터를 발견하면 포인터의 일반화된 표현을 만들어야 합니다. 표현의 크기는 지정된 상속 모델에 따라 달라집니다. 상속 모델을 컴파일러에 지정하는 방법에는 다음 네 가지가 있습니다.

- IDE의 **멤버 포인터 표현** 에서

- [/Vmg](../build/reference/vmb-vmg-representation-method.md) 스위치를 사용 하는 명령줄에서

- [Pointers_to_members](../preprocessor/pointers-to-members.md) pragma 사용

- 상속 키워드 **__single_inheritance**, **__multiple_inheritance**및 **__virtual_inheritance**를 사용 합니다. 이 방법은 클래스별로 상속 모델을 제어합니다.

    > [!NOTE]
    >  항상 클래스를 정의한 후 클래스 멤버에 대한 포인터를 선언하면 이러한 옵션을 사용할 필요가 없습니다.

클래스 정의 이전에 클래스 멤버에 대한 포인터를 선언하면 결과 실행 파일의 크기와 속도가 영향을 받습니다. 클래스에서 사용하는 상속이 복잡할수록 클래스 멤버에 대한 포인터를 표현하는 데 필요한 바이트 수가 증가하고 포인터를 해석하는 데 필요한 코드가 커집니다. 단일 상속이 복잡도가 가장 낮고 가상 상속이 가장 복잡합니다.

위의 예제를 다음과 같이 변경한 경우

```cpp
class __single_inheritance S;
int S::*p;
```

명령줄 옵션이나 pragma에 관계없이 `class S`의 멤버에 대한 포인터는 가장 작은 가능한 표현을 사용합니다.

> [!NOTE]
>  클래스 멤버 포인터 표현의 동일한 정방향 선언이 해당 클래스의 멤버에 대한 포인터를 선언하는 각 변환 단위에서 발생해야 하며, 이 선언은 멤버에 대한 포인터가 선언되기 전에 발생해야 합니다.

이전 버전과의 호환성을 위해 **_single_inheritance**, **_multiple_inheritance**및 **_virtual_inheritance** 는 컴파일러 옵션 [/za __multiple_inheritance 언어 확장 사용 안 함)](../build/reference/za-ze-disable-language-extensions.md) 이 지정 된 경우를 제외 하 고 **__single_inheritance**, **__virtual_inheritance**및 **\(** 의 동의어입니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)
