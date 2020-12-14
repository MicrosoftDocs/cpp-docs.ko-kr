---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4503'
title: 컴파일러 경고(수준 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 4ff438c3ae9e698bdaaf476d022b8914add4169e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294901"
---
# <a name="compiler-warning-level-1-c4503"></a>컴파일러 경고(수준 1) C4503

> '*identifier*': 데코레이팅된 이름 길이를 초과 했으므로 이름이 잘렸습니다.

## <a name="remarks"></a>설명

이 컴파일러 경고는 사용 되지 않으며 Visual Studio 2017 이상 컴파일러에서 생성 되지 않습니다.

데코레이팅된 이름이 컴파일러 한계 (4096) 보다 길어 잘렸습니다. 이 경고 및 잘림을 방지 하려면 사용 되는 인수의 수 또는 식별자의 길이를 줄입니다. 컴파일러 제한 보다 긴 데코레이팅된 이름에는 해시가 적용 되며 이름 충돌의 위험이 없습니다.

이전 버전의 Visual Studio를 사용 하는 경우 코드에 템플릿에서 특수화 된 템플릿이 반복 해 서 포함 되어 있는 경우이 경고가 발생 합니다. 예를 들어 map map (c + + 표준 라이브러리)입니다. 이 경우 형식 정의를 **`struct`** 맵을 포함 하는 형식 (예:)으로 만들 수 있습니다.

그러나 코드를 재구성 하지 않도록 결정할 수 있습니다.  C4503를 생성 하는 응용 프로그램을 제공할 수 있지만 잘린 기호에서 링크 시간 오류가 발생 하면 오류에서 기호 유형을 확인 하기가 더 어려울 수 있습니다. 디버깅이 더 어려울 수도 있습니다. 디버거에서 기호 이름을 형식 이름에 문제 등급이 높을수록 매핑 했을 수 있습니다. 그러나 프로그램의 정확성은 잘린 이름의 영향을 받지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 Visual Studio 2017 이전에 컴파일러에 C4503를 생성 합니다.

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

이 샘플에서는 C4503를 확인 하기 위해 코드를 다시 작성 하는 한 가지 방법을 보여 줍니다.

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```
