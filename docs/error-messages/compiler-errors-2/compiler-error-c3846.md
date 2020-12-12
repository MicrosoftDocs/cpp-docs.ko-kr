---
description: '자세한 정보: 컴파일러 오류 C3846'
title: 컴파일러 오류 C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 13c9cb7a9dde3710cac31d8ee79fb148f8ff67bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255394"
---
# <a name="compiler-error-c3846"></a>컴파일러 오류 C3846

' symbol ': ' assembly2 '에서 기호를 가져올 수 없습니다. 다른 어셈블리 ' assembly1 '에서 ' 기호 '를 이미 가져왔습니다.

이전에 참조 된 어셈블리에서 가져온 것 이므로 참조 된 어셈블리에서 기호를 가져올 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3846를 생성 합니다.

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

그리고 다음을 컴파일합니다.

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
