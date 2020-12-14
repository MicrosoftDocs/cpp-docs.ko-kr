---
description: Messages_byname 클래스에 대해 자세히 알아보세요.
title: messages_byname 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_byname
helpviewer_keywords:
- messages_byname class
ms.assetid: c6c64841-3e80-43c8-b54c-fed41833ad6b
ms.openlocfilehash: 960db9dd411e4ac42f81a0027e91ae1001b7877d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230525"
---
# <a name="messages_byname-class"></a>messages_byname 클래스

파생 된 클래스 템플릿은 지정 된 로캘의 메시지 패싯으로 사용 하 여 지역화 된 메시지를 검색할 수 있도록 하는 개체를 설명 합니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
class messages_byname : public messages<CharType> {
public:
    explicit messages_byname(
    const char *_Locname,
    size_t _Refs = 0);

    explicit messages_byname(
    const string& _Locname,
    size_t _Refs = 0);

protected:
    virtual ~messages_byname();

};
```

### <a name="parameters"></a>매개 변수

*_Locname*\
명명된 로캘입니다.

*_Refs*\
초기 참조 개수입니다.

## <a name="remarks"></a>설명

해당 동작은 명명 된 로캘 *_Locname* 에 의해 결정 됩니다. 각 생성자는 [메시지](../standard-library/messages-class.md#messages)()를 사용 하 여 해당 기준 개체를 초기화 \<CharType> `_Refs` 합니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
