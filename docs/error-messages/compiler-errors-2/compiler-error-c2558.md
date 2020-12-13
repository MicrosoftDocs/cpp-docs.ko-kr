---
description: '자세한 정보: 컴파일러 오류 C2558'
title: 컴파일러 오류 C2558
ms.date: 11/04/2016
f1_keywords:
- C2558
helpviewer_keywords:
- C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
ms.openlocfilehash: 12f75294f02b6586a90515f381b37c8c346f4567
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338722"
---
# <a name="compiler-error-c2558"></a>컴파일러 오류 C2558

'identifier' : 복사 생성자를 사용할 수 없거나 복사 생성자가 'explicit'으로 선언되었습니다.

복사 생성자는 형식이 같은 다른 개체로부터 개체를 초기화하며 (개체의 복사본을 만듭니다.) 생성자를 정의 하지 않으면 컴파일러가 기본 복사 생성자를 생성 합니다.

### <a name="to-fix-this-error"></a>이 오류를 해결하려면

1. 복사 생성자가 인 클래스를 복사 하려고 하면 문제가 발생할 수 있습니다 **`private`** . 대부분의 경우 복사 생성자가 있는 클래스는 **`private`** 복사 하면 안 됩니다. 일반적인 프로그래밍 기술은 **`private`** 복사 생성자를 선언 하 여 클래스를 직접 사용 하지 못하도록 합니다. 이 클래스 자체만으로는 사용될 수 없습니다. 제대로 작동하려면 또 다른 클래스가 필요합니다.

   복사 생성자가 있는 클래스를 사용 하는 것이 안전 하다 고 판단 되는 경우 **`private`** 생성자가 있는 클래스에서 새 클래스를 파생 **`private`** 시키고 **`public`** **`protected`** 새 클래스에서 또는 복사 생성자를 사용할 수 있도록 합니다. 원본 클래스 대신 파생 클래스를 사용하십시오.

1. 복사 생성자가 명시적인 클래스를 복사하려고 하면 문제가 발생할 수 있습니다. 로 복사 생성자를 선언 하면 **`explicit`** 클래스의 개체를 함수에 전달 하거나 함수에서 반환할 수 없습니다. 명시적 생성자에 대 한 자세한 내용은 [사용자 정의 형식 변환](../../cpp/user-defined-type-conversions-cpp.md)을 참조 하세요.

1. **`const`** 참조 매개 변수를 사용 하지 않는 복사 생성자를 사용 하 여 선언 된 클래스 인스턴스를 복사 하려고 하면 문제가 발생할 수 있습니다 **`const`** . **`const`** Const가 아닌 형식 참조 대신 형식 참조를 사용 하 여 복사 생성자를 선언 합니다.
