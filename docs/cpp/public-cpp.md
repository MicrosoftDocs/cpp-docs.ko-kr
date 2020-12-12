---
description: '자세한 정보: 공용 (c + +)'
title: public (C++)
ms.date: 11/04/2016
f1_keywords:
- public_cpp
helpviewer_keywords:
- public keyword [C++]
ms.assetid: f3e10a59-39f6-4bcd-827e-3e99f8f89497
ms.openlocfilehash: 1fd9377647568a9f4e2079d93097ca49bd6ed9be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319445"
---
# <a name="public-c"></a>public (C++)

## <a name="syntax"></a>구문

```
public:
   [member-list]
public base-class
```

## <a name="remarks"></a>설명

클래스 멤버 목록 앞에 **`public`** 오는 키워드는 모든 함수에서 해당 멤버에 액세스할 수 있도록 지정 합니다. 이 설정은 다음 액세스 지정자 또는 클래스 끝까지 선언된 모든 멤버에 적용됩니다.

기본 클래스의 이름 앞에 **`public`** 오는 키워드는 기본 클래스의 공용 및 보호 된 멤버가 각각 파생 클래스의 공용 및 보호 된 멤버 임을 지정 합니다.

클래스에서 멤버의 기본 액세스는 전용입니다. 구조체나 공용 구조체에서 멤버의 기본 액세스는 공용입니다.

기본 클래스의 기본 액세스는 클래스에 대해 전용이고 구조체에 대해 공용입니다. 공용 구조체에 기본 클래스를 사용할 수 없습니다.

자세한 내용은 [private](../cpp/private-cpp.md), [protected](../cpp/protected-cpp.md), [friend](../cpp/friend-cpp.md)및 [클래스 멤버에 대 한 액세스 제어](member-access-control-cpp.md)의 멤버 액세스 테이블을 참조 하세요.

## <a name="clr-specific"></a>/clr 관련

CLR 형식에서 c + + 액세스 지정자 키워드 ( **`public`** , **`private`** 및 **`protected`** )는 어셈블리와 관련 하 여 형식과 메서드를 표시 하는 데 영향을 줄 수 있습니다. 자세한 내용은 [Member Access Control](member-access-control-cpp.md)를 참조 하세요.

> [!NOTE]
> [/LN](../build/reference/ln-create-msil-module.md) 로 컴파일된 파일은이 동작의 영향을 받지 않습니다. 이 경우 관리되는 클래스(공용 또는 전용)가 모두 표시됩니다.

## <a name="end-clr-specific"></a>END /clr 관련

## <a name="example"></a>예제

```cpp
// keyword_public.cpp
class BaseClass {
public:
   int pubFunc() { return 0; }
};

class DerivedClass : public BaseClass {};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   aBase.pubFunc();       // pubFunc() is accessible
                          //    from any function
   aDerived.pubFunc();    // pubFunc() is still public in
                          //    derived class
}
```

## <a name="see-also"></a>참고 항목

[클래스 멤버에 대한 액세스 제어](member-access-control-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
