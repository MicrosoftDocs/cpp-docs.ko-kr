---
title: 컴파일러 경고 (수준 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: 9dd4defe18a94f65e265d02f6c26c715667cd696
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052598"
---
# <a name="compiler-warning-level-1-c4621"></a>컴파일러 경고 (수준 1) C4621

' type ' 형식에 대 한 ' operator--' 후 위 형식이 없어 접두사 형식을 사용 합니다.

지정 된 형식에 대해 정의 된 후 위 감소 연산자가 없습니다. 컴파일러가 오버로드된 전위 연산자를 사용했습니다.

이 경고는 후위 `--` 연산자를 정의하여 방지할 수 있습니다. 아래와 같이 `--` 연산자의 두 인수 버전을 만듭니다.

```cpp
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   --a;
   a--;   // C4621
}
```