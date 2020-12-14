---
description: Type_info 클래스에 대해 자세히 알아보세요.
title: type_info 클래스
ms.date: 11/04/2016
f1_keywords:
- type_info
helpviewer_keywords:
- class type_info
- type_info class
ms.assetid: 894ddda2-7de4-4da3-9404-d2c74e356c16
ms.openlocfilehash: 6be4d6774842ad015b34e771455026ca27e6539b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295317"
---
# <a name="type_info-class"></a>type_info 클래스

**Type_info** 클래스는 컴파일러에 의해 프로그램 내에서 생성 되는 형식 정보를 설명 합니다. 이 클래스의 개체는 형식의 이름에 대한 포인터를 효과적으로 저장합니다. 또한 **type_info** 클래스는 두 형식에 대해 같음 또는 정렬 순서를 비교 하는 데 적합 한 인코딩된 값을 저장 합니다. 형식의 인코딩 규칙 및 정렬 시퀀스는 지정되지 않으며 프로그램 간에 다를 수 있습니다.

`<typeinfo>` **Type_info** 클래스를 사용 하려면 헤더 파일이 포함 되어 있어야 합니다. **Type_info** 클래스에 대 한 인터페이스는 다음과 같습니다.

```cpp
class type_info {
public:
    type_info(const type_info& rhs) = delete; // cannot be copied
    virtual ~type_info();
    size_t hash_code() const;
    _CRTIMP_PURE bool operator==(const type_info& rhs) const;
    type_info& operator=(const type_info& rhs) = delete; // cannot be copied
    _CRTIMP_PURE bool operator!=(const type_info& rhs) const;
    _CRTIMP_PURE int before(const type_info& rhs) const;
    size_t hash_code() const noexcept;
    _CRTIMP_PURE const char* name() const;
    _CRTIMP_PURE const char* raw_name() const;
};
```

클래스에 전용 복사 생성자만 있기 때문에 **type_info** 클래스의 개체를 직접 인스턴스화할 수 없습니다. (임시) **type_info** 개체를 생성 하는 유일한 방법은 [typeid](../cpp/typeid-operator.md) 연산자를 사용 하는 것입니다. 할당 연산자도 private 이므로 **type_info** 클래스의 개체를 복사 하거나 할당할 수 없습니다.

`type_info::hash_code`**typeinfo** 형식의 값을 인덱스 값의 분포에 매핑하는 데 적합 한 해시 함수를 정의 합니다.

연산자 `==` 와를 `!=` 사용 하 여 다른 **type_info** 개체와 같음 및 같지 않음을 비교할 수 있습니다.

형식의 정렬 순서와 상속 관계 간에 링크가 없습니다. `type_info::before`멤버 함수를 사용 하 여 형식의 정렬 순서를 확인 합니다. `type_info::before`다른 프로그램 또는 동일한 프로그램의 여러 실행에서 동일한 결과를 얻을 수 있는 것은 아닙니다. 이러한 방식으로 `type_info::before` 는 주소 연산자와 유사 `(&)` 합니다.

`type_info::name`멤버 함수는 `const char*` 사용자가 읽을 수 있는 형식의 이름을 나타내는 null로 끝나는 문자열에 대 한를 반환 합니다. 가리키는 메모리는 캐시되며 직접 할당 해지되면 안 됩니다.

`type_info::raw_name`멤버 함수는 `const char*` 개체 형식의 데코레이팅된 이름을 나타내는 null로 끝나는 문자열에 대 한를 반환 합니다. 공간을 절약하기 위해 이름은 실제로 데코레이팅된 형식으로 저장됩니다. 따라서이 함수는 `type_info::name` 이름을 데코레이팅 필요가 없기 때문에 보다 빠릅니다. 함수에서 반환 되는 문자열은 `type_info::raw_name` 비교 작업에 유용 하지만 읽을 수는 없습니다. 사람이 읽을 수 있는 문자열이 필요한 경우 함수를 대신 사용 `type_info::name` 합니다.

형식 정보는 [/gr (Run-Time 형식 정보 사용)](../build/reference/gr-enable-run-time-type-information.md) 컴파일러 옵션이 지정 된 경우에만 다형 클래스에 대해 생성 됩니다.

## <a name="see-also"></a>참고 항목

[런타임 형식 정보](../cpp/run-time-type-information.md)
