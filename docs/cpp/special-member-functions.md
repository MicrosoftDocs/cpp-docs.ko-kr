---
description: '자세한 정보: 특수 멤버 함수'
title: 특수 멤버 함수
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: ab3b5be3c7006729e135cc273e9b7856adbd3252
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113833"
---
# <a name="special-member-functions"></a>특수 멤버 함수

*특수 멤버 함수* 는 특정 경우에 컴파일러에서 자동으로 생성 하는 클래스 (또는 구조체) 멤버 함수입니다. 이러한 함수에는 [기본 생성자](constructors-cpp.md#default_constructors), [소멸자](destructors-cpp.md), [복사 생성자 및 복사 할당 연산자](copy-constructors-and-copy-assignment-operators-cpp.md), [이동 생성자 및 이동 할당 연산자](move-constructors-and-move-assignment-operators-cpp.md)가 있습니다. 클래스에서 하나 이상의 특수 멤버 함수를 정의 하지 않는 경우 컴파일러는 사용 되는 함수를 암시적으로 선언 하 고 정의할 수 있습니다. 컴파일러에서 생성 된 구현을 *기본* 특수 멤버 함수 라고 합니다. 필요 하지 않은 경우 컴파일러는 함수를 생성 하지 않습니다.

기본 특수 멤버 함수는 **= default** 키워드를 사용 하 여 명시적으로 선언할 수 있습니다. 이렇게 하면 컴파일러가 함수를 전혀 선언 하지 않은 경우와 동일한 방법으로 필요한 경우에만 함수를 정의 합니다.

경우에 따라 컴파일러는 정의 되지 않았으므로 호출할 수 없는 *삭제* 된 특수 멤버 함수를 생성할 수 있습니다. 클래스의 다른 속성이 지정 된 경우 클래스에 대 한 특정 특수 멤버 함수를 호출 하는 것이 적합 하지 않은 경우이 문제가 발생할 수 있습니다. 특수 멤버 함수의 자동 생성을 명시적으로 방지 하려면 **= delete** 키워드를 사용 하 여 삭제 된 것으로 선언할 수 있습니다.

컴파일러는 다른 생성자를 선언 하지 않은 경우에만 인수를 사용 하지 않는 생성자 인 *기본 생성자* 를 생성 합니다. 매개 변수를 사용 하는 생성자만 선언 하면 기본 생성자를 호출 하려고 시도 하는 코드에서 컴파일러가 오류 메시지를 생성 합니다. 컴파일러에서 생성 된 기본 생성자는 개체의 간단한 멤버 단위 [기본 초기화](initializers.md#default_initialization) 를 수행 합니다. 기본 초기화는 모든 멤버 변수를 결정 되지 않은 상태로 둡니다.

기본 소멸자는 개체의 멤버 단위 소멸을 수행 합니다. 기본 클래스 소멸자가 virtual 인 경우에만 가상입니다.

기본 복사 및 이동 생성 및 할당 작업은 멤버 단위 비트 패턴 복사 또는 비정적 데이터 멤버의 이동 작업을 수행 합니다. 이동 작업은 소멸자 또는 이동 또는 복사 작업이 선언 되지 않은 경우에만 생성 됩니다. 기본 복사 생성자는 복사 생성자가 선언 되지 않은 경우에만 생성 됩니다. 이동 작업이 선언 되 면 암시적으로 삭제 됩니다. 기본 복사 할당 연산자는 명시적으로 선언 된 복사 할당 연산자가 없는 경우에만 생성 됩니다. 이동 작업이 선언 되 면 암시적으로 삭제 됩니다.

## <a name="see-also"></a>참조

[C++ 언어 참조](cpp-language-reference.md)
