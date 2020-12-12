---
description: '자세한 정보: 변경 가능한 데이터 멤버 (c + +)'
title: 변경할 수 있는 데이터 멤버 (C++)
ms.date: 11/04/2016
f1_keywords:
- mutable_cpp
helpviewer_keywords:
- mutable keyword [C++]
ms.assetid: ebe89746-3d36-43a8-8d69-f426af23f551
ms.openlocfilehash: a288b382b456fa313c49832bd2d13aaceb269be9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313816"
---
# <a name="mutable-data-members-c"></a>변경할 수 있는 데이터 멤버 (C++)

이 키워드는 클래스의 비정적 데이터 멤버 중에서 const가 아닌 멤버에만 적용할 수 있습니다. 데이터 멤버가 선언 된 경우 **`mutable`** 멤버 함수에서이 데이터 멤버에 값을 할당할 수 **`const`** 있습니다.

## <a name="syntax"></a>구문

```
mutable member-variable-declaration;
```

## <a name="remarks"></a>설명

예를 들어 다음 코드는가로 선언 되었으므로가 `m_accessCount` **`mutable`** `GetFlag` const 멤버 함수 이더라도에서 수정할 수 있기 때문에 오류 없이 컴파일됩니다 `GetFlag` .

```cpp
// mutable.cpp
class X
{
public:
   bool GetFlag() const
   {
      m_accessCount++;
      return m_flag;
   }
private:
   bool m_flag;
   mutable int m_accessCount;
};

int main()
{
}
```

## <a name="see-also"></a>참고 항목

[키워드](../cpp/keywords-cpp.md)
