---
description: Time_put_byname 클래스에 대해 자세히 알아보세요.
title: time_put_byname 클래스
ms.date: 11/04/2016
f1_keywords:
- xloctime/std::time_put_byname
helpviewer_keywords:
- time_put_byname class
ms.assetid: e08c2348-64d2-4ace-98b1-1496e14c7b1a
ms.openlocfilehash: b519b28b7af8f5b54f9150d1d84f68cd6695bc49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97167255"
---
# <a name="time_put_byname-class"></a>time_put_byname 클래스

파생 된 클래스 템플릿은 형식의 로캘 패싯으로 사용할 수 있는 개체를 설명 합니다 `time_put` \< CharType, OutputIterator > .

## <a name="syntax"></a>구문

```cpp
template <class CharType, class OutIt = ostreambuf_iterator<CharType, char_traits<CharType>>>
class time_put_byname : public time_put<CharType, OutputIterator>
{
public:
    explicit time_put_byname(
    const char* _Locname,
    size_t _Refs = 0);

    explicit time_put_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~time_put_byname();

};
```

### <a name="parameters"></a>매개 변수

*_Locname*\
로캘 이름

*_Refs*\
초기 참조 개수입니다.

## <a name="remarks"></a>설명

해당 동작은 [명명](../standard-library/locale-class.md#name) 된 로캘 *_Locname* 에 의해 결정 됩니다. 각 생성자는 [time_put](../standard-library/time-put-class.md#time_put)()를 사용 하 여 해당 기준 개체를 초기화 \<CharType, OutputIterator> `_Refs` 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
