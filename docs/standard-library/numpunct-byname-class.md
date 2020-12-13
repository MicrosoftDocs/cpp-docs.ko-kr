---
description: Numpunct_byname 클래스에 대해 자세히 알아보세요.
title: numpunct_byname 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::numpunct_byname
helpviewer_keywords:
- numpunct_byname class
ms.assetid: 18412924-e085-4771-b5e9-7a200cbdd7c0
ms.openlocfilehash: e4e6352f9f65b2a726acf3f8f5f8ede9bffe54f9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338032"
---
# <a name="numpunct_byname-class"></a>numpunct_byname 클래스

파생 된 클래스 템플릿은 `numpunct` 숫자 및 부울 식의 서식 지정 및 문장 부호를 사용할 수 있도록 지정 된 로캘의 패싯으로 사용할 수 있는 개체를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
class numpunct_byname : public numpunct<Elem> {
public:
    explicit numpunct_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit numpunct_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~numpunct_byname();

};
```

## <a name="remarks"></a>설명

해당 동작은 [명명](../standard-library/locale-class.md#name) 된 로캘에 의해 결정 됩니다 `_Locname` . 생성자는 [numpunct](../standard-library/numpunct-class.md#numpunct)()를 사용 하 여 해당 기본 개체를 초기화 \<CharType> `_Refs` 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
