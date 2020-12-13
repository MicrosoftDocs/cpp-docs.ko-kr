---
description: Bad_optional_access 클래스에 대해 자세히 알아보세요.
title: bad_optional_access 클래스
ms.date: 08/06/2019
f1_keywords:
- optional/std::bad_optional_access
ms.openlocfilehash: e3439c53766a1890592bde8ed449f5ff2779f347
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97132758"
---
# <a name="bad_optional_access-class"></a>bad_optional_access 클래스

`optional`값을 포함 하지 않는 개체의 값에 대 한 액세스를 시도 하는 상황을 보고 하는 예외로 throw 되는 개체의 형식을 정의 합니다.

## <a name="syntax"></a>구문

```cpp
class bad_optional_access : public exception
{
public:
    bad_optional_access() noexcept;
    bad_optional_access(const bad_optional_access&) noexcept;
    bad_optional_access& operator=(const bad_optional_access&) noexcept;
    const char* what() const noexcept override;
};
```

## <a name="see-also"></a>참고 항목

[\<optional>](optional.md)\
[선택적 클래스](optional-class.md)
