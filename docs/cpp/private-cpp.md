---
description: '자세히 알아보기: private (c + +)'
title: private (C++)
ms.date: 11/04/2016
f1_keywords:
- private_cpp
helpviewer_keywords:
- private keyword [C++]
ms.assetid: 94e99983-46a5-4e21-800c-28f8a7c6a8ff
ms.openlocfilehash: f9060dbbe32662a62fcda84b628877b52d87bdfc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198624"
---
# <a name="private-c"></a>private (C++)

## <a name="syntax"></a>구문

```
private:
   [member-list]
private base-class
```

## <a name="remarks"></a>설명

클래스 멤버 목록 앞에 **`private`** 오는 키워드는 클래스의 멤버 함수 및 friend 에서만 이러한 멤버에 액세스할 수 있도록 지정 합니다. 이 설정은 다음 액세스 지정자 또는 클래스 끝까지 선언된 모든 멤버에 적용됩니다.

기본 클래스의 이름 앞에 **`private`** 오는 키워드는 기본 클래스의 공용 및 보호 된 멤버가 파생 클래스의 private 멤버 임을 지정 합니다.

클래스에서 멤버의 기본 액세스는 전용입니다. 구조체나 공용 구조체에서 멤버의 기본 액세스는 공용입니다.

기본 클래스의 기본 액세스는 클래스에 대해 전용이고 구조체에 대해 공용입니다. 공용 구조체에 기본 클래스를 사용할 수 없습니다.

관련 정보는 [클래스 멤버에 대 한 액세스 제어](member-access-control-cpp.md)의 [friend](../cpp/friend-cpp.md), [public](../cpp/public-cpp.md), [protected](../cpp/protected-cpp.md)및 멤버 액세스 테이블을 참조 하세요.

## <a name="clr-specific"></a>/clr 관련

CLR 형식에서 c + + 액세스 지정자 키워드 ( **`public`** , **`private`** 및 **`protected`** )는 어셈블리와 관련 하 여 형식과 메서드를 표시 하는 데 영향을 줄 수 있습니다. 자세한 내용은 [Member Access Control](member-access-control-cpp.md)를 참조 하세요.

> [!NOTE]
> [/LN](../build/reference/ln-create-msil-module.md) 로 컴파일된 파일은이 동작의 영향을 받지 않습니다. 이 경우 관리되는 클래스(공용 또는 전용)가 모두 표시됩니다.

## <a name="end-clr-specific"></a>END /clr 관련

## <a name="example"></a>예제

```cpp
// keyword_private.cpp
class BaseClass {
public:
   // privMem accessible from member function
   int pubFunc() { return privMem; }
private:
   void privMem;
};

class DerivedClass : public BaseClass {
public:
   void usePrivate( int i )
      { privMem = i; }   // C2248: privMem not accessible
                         // from derived class
};

class DerivedClass2 : private BaseClass {
public:
   // pubFunc() accessible from derived class
   int usePublic() { return pubFunc(); }
};

int main() {
   BaseClass aBase;
   DerivedClass aDerived;
   DerivedClass2 aDerived2;
   aBase.privMem = 1;     // C2248: privMem not accessible
   aDerived.privMem = 1;  // C2248: privMem not accessible
                          //    in derived class
   aDerived2.pubFunc();   // C2247: pubFunc() is private in
                          //    derived class
}
```

## <a name="see-also"></a>참고 항목

[클래스 멤버에 대한 액세스 제어](member-access-control-cpp.md)<br/>
[키워드](../cpp/keywords-cpp.md)
