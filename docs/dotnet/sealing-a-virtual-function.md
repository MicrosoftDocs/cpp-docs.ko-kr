---
title: 가상 함수 봉인 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
- derived classes, virtual functions
- virtual functions, sealing
- __sealed keyword
ms.assetid: 0e9fae03-6425-4512-9a24-8ccb6dc8a0d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 69ac614d55ade10b94621da2a3eb1c43d25ebaf5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385185"
---
# <a name="sealing-a-virtual-function"></a>가상 함수 봉인

가상 함수 봉인 하는 구문은 Visual c + + Managed Extensions for c + + 변경 되었습니다.

`__sealed` 키워드는 Managed extensions에서 중 하나는 참조 형식에서 파생 되지 않도록 수정 하는 데 사용 됩니다 (참조 [는 관리 되는 클래스 형식 선언](../dotnet/declaration-of-a-managed-class-type.md)), 가상 함수를 수정 하거나 허용 하지 않습니다 후속 메서드의 파생된 클래스에서 재정의 되는 합니다. 예를 들어:

```
__gc class base { public: virtual void f(); };
__gc class derived : public base {
public:
   __sealed void f();
};
```

이 예에서 `derived::f()` 재정의 `base::f()` 함수 프로토타입의 정확히 일치를 기반으로 한 인스턴스. 합니다 `__sealed` 키워드는 파생된 클래스에서 상속 되며, 후속 클래스의 재정의 제공할 수 없습니다 나타냅니다 `derived::f()`합니다.

새 구문에서 `sealed` 아무 위치에 실제 함수 프로토타입 전에 이전에 허용 허용 되는 것이 아니라 서명 뒤에 배치 됩니다. 또한 사용 `sealed` 를 명시적으로 사용할 필요는 `virtual` 키워드에도 합니다. 즉, 올바른 변환 `derived`, 위의 다음과 같습니다.

```
ref class derived: public base {
public:
   virtual void f() override sealed;
};
```

없는 경우는 `virtual` 키워드가 인스턴스에 오류가 발생 합니다. 새 구문에서 상황별 키워드 `abstract` 대신 사용할 수는 `=0` 순수 가상 함수를 나타냅니다. 내 Managed Extensions에서 지원 되지 않았습니다. 예를 들어:

```
__gc class base { public: virtual void f()=0; };
```

다시 작성할 수 있습니다.

```
ref class base { public: virtual void f() abstract; };
```

## <a name="see-also"></a>참고 항목

[클래스 또는 인터페이스 내에서 멤버 선언(C++/CLI)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)<br/>
[sealed](../windows/sealed-cpp-component-extensions.md)