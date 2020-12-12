---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4266'
title: 컴파일러 경고(수준 4) C4266
ms.date: 11/04/2016
f1_keywords:
- C4266
helpviewer_keywords:
- C4266
ms.assetid: 90ec5f5b-3451-4c16-bb1b-c30a626bdaa0
ms.openlocfilehash: 173e7da734a1bd94ccee9684bc2400c020dfc76c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285177"
---
# <a name="compiler-warning-level-4-c4266"></a>컴파일러 경고(수준 4) C4266

' function ': 기본 ' type '의 가상 멤버 함수에 대해 재정의를 사용할 수 없습니다. 함수가 숨겨집니다.

파생 클래스가 가상 함수의 모든 오버 로드를 재정의 하지 않았습니다.

기본적으로 이 경고는 해제되어 있습니다.  자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.

다음 샘플에서는 C4266를 생성 합니다.

```cpp
// C4266.cpp
// compile with: /W4 /c
#pragma warning (default : 4266)
class Engine {
public:
   virtual void OnException(int&,int);
   virtual void OnException(int&,int&,int);
};

class LocalBinding : private Engine {
   virtual void OnException(int&,int);
};   // C4266
```

해결 방법:

```cpp
// C4266b.cpp
// compile with: /W4 /c
#pragma warning (default : 4266)
class Engine {
public:
   virtual void OnException(int&,int);
   virtual void OnException(int&,int&,int);
};

class LocalBinding : private Engine {
   virtual void OnException(int&,int);
   virtual void OnException(int&, int&, int);
};
```
