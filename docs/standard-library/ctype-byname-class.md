---
description: Ctype_byname 클래스에 대해 자세히 알아보세요.
title: ctype_byname 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype_byname
helpviewer_keywords:
- ctype_byname class
ms.assetid: a5cec021-a1f8-425f-8757-08e6f064b604
ms.openlocfilehash: cc5f44e1c544d2088030621b684c9e070175d695
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233138"
---
# <a name="ctype_byname-class"></a>ctype_byname 클래스

파생 된 클래스 템플릿은 지정 된 로캘의 ctype 패싯으로 사용할 수 있는 개체에 대해 설명 하 고, 대/소문자와 네이티브 및 로캘 지정 문자 집합 간 문자 변환 및 문자 분류를 사용 하도록 설정 합니다.

## <a name="syntax"></a>구문

```cpp
template <class _Elem>
class ctype_byname : public ctype<_Elem>
{
public:
    explicit ctype_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit ctype_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual __CLR_OR_THIS_CALL ~ctype_byname();

};
```

## <a name="remarks"></a>설명

해당 동작은 명명된 로캘 `_Locname`에 따라 결정됩니다. 각 생성자는 [ctype](../standard-library/ctype-class.md) \<CharType> ( `_Refs` ) 또는 기본 클래스에 대해 동일한를 사용 하 여 기본 개체를 초기화 `ctype<char>` 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
