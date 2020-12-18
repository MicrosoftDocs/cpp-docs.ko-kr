---
description: '자세한 정보: static 스토리지 클래스 지정자'
title: 정적 스토리지 클래스 지정자
ms.date: 11/04/2016
helpviewer_keywords:
- static variables, specifier
- storage classes, static
- static storage class specifiers
ms.assetid: 9bce361e-919b-46b9-8148-40d7ab0eb024
ms.openlocfilehash: da7ca4ea71b3e450da986ec175adcaf08852d81b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168750"
---
# <a name="static-storage-class-specifier"></a>정적 스토리지 클래스 지정자

**`static`** 스토리지 클래스 지정자를 사용하여 내부 수준에서 선언된 변수는 global 수명을 갖지만 선언된 블록 안에만 표시됩니다. 상수 문자열의 경우 **`static`** 을 사용하면 자주 호출된 함수에서 빈번한 초기화 부담이 줄어들어 도움이 됩니다.

## <a name="remarks"></a>설명

**`static`** 변수를 명시적으로 초기화하지 않으면 기본적으로 0으로 초기화됩니다. 함수 내부에서 **`static`** 은 스토리지를 할당되게 하며 정의로 사용됩니다. 내부 정적 변수는 단일 함수에만 표시되는 전용 영구 스토리지를 제공합니다.

## <a name="see-also"></a>참조

[C 스토리지 클래스](c-storage-classes.md)<br/>
[스토리지 클래스(C++)](../cpp/storage-classes-cpp.md)
