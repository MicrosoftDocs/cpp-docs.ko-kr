---
description: Time_get_byname 클래스에 대해 자세히 알아보세요.
title: time_get_byname 클래스
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_get_byname
helpviewer_keywords:
- time_get_byname class
ms.assetid: 6e54153e-da40-4bb9-a942-1a6ce57b30c9
ms.openlocfilehash: 056681782d0e8edcc3d99ccf2b414b2b93db9986
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180281"
---
# <a name="time_get_byname-class"></a>time_get_byname 클래스

파생 된 클래스 템플릿은 형식의 로캘 패싯으로 사용할 수 있는 개체를 설명 합니다 `time_get` \<CharType, InputIterator> .

## <a name="syntax"></a>구문

```cpp
template <class Elem, class InputIterator =
    istreambuf_iterator<CharType, char_traits<CharType>>>
class time_get_byname : public time_get<CharType, InputIterator>
{
public:
    explicit time_get_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_get_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_get_byname()
};
```

### <a name="parameters"></a>매개 변수

*_Locname*\
명명된 로캘입니다.

*_Refs*\
초기 참조 개수입니다.

## <a name="requirements"></a>요구 사항

해당 동작은 명명 된 로캘 *_Locname* 에 의해 결정 됩니다. 각 생성자는 [time_get](../standard-library/time-get-class.md#time_get)()를 사용 하 여 해당 기준 개체를 초기화 \<CharType, InputIterator> `_Refs` 합니다.

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
