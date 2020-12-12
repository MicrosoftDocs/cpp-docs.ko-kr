---
description: '자세한 정보: 컴파일러 경고 C4687'
title: 컴파일러 경고 C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: ffa8e645aa82a8577d0cd39a4963b8008b6cf9a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180723"
---
# <a name="compiler-warning-c4687"></a>컴파일러 경고 C4687

> '*class*': 봉인 된 추상 클래스는 '*interface*' 인터페이스를 구현할 수 없습니다.

## <a name="remarks"></a>설명

봉인 된 추상 형식은 일반적으로 정적 멤버 함수를 보유 하는 데만 유용 합니다.

자세한 내용은 [abstract](../../extensions/abstract-cpp-component-extensions.md) 및 [sealed](../../extensions/sealed-cpp-component-extensions.md)를 참조 하세요.

C4687은 기본적으로 오류로 발급 됩니다. [Warning](../../preprocessor/warning.md) pragma를 사용 하 여 C4687를 억제할 수 있습니다. 봉인 된 추상 형식에서 인터페이스를 구현 하려는 경우 C4687를 표시 하지 않을 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4687를 생성 합니다.

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
