---
description: '자세한 정보: 함수 템플릿 인스턴스화'
title: 함수 템플릿 인스턴스화
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
ms.openlocfilehash: 1278190c9f86034374ee295a308fe0b8396b8716
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341375"
---
# <a name="function-template-instantiation"></a>함수 템플릿 인스턴스화

함수 템플릿이 각 형식에 대해 처음 호출될 때 컴파일러는 인스턴스를 만듭니다(인스턴스화). 각 인스턴스는 형식에 대해 특수화된 템플릿 함수의 버전입니다. 이 인스턴스는 함수가 형식에 사용될 때마다 호출됩니다. 동일한 인스턴스가 여러 개 있는 경우 서로 다른 모듈에 있더라도 인스턴스의 복사본이 하나만 실행 파일에 존재하게 됩니다.

함수 인수의 변환은 매개 변수가 템플릿 인수에 종속되지 않은 인수 및 매개 변수 쌍에 대해 함수 템플릿에서 허용됩니다.

함수 템플릿은 특정 형식을 인수로 사용하는 템플릿을 선언하여 명시적으로 인스턴스화할 수 있습니다. 예를 들어 다음 코드는 허용됩니다.

```cpp
// function_template_instantiation.cpp
template<class T> void f(T) { }

// Instantiate f with the explicitly specified template.
// argument 'int'
//
template void f<int> (int);

// Instantiate f with the deduced template argument 'char'.
template void f(char);
int main()
{
}
```

## <a name="see-also"></a>참고 항목

[함수 템플릿](../cpp/function-templates.md)
