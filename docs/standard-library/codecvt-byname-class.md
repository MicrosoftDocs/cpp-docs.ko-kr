---
title: codecvt_byname 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt_byname
dev_langs:
- C++
helpviewer_keywords:
- codecvt_byname class
ms.assetid: b63b6c04-f60c-47b9-8e30-a933f24a8ffb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a785c7868f3a1f3262283cf131bbd3cc3ae88e4c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102158"
---
# <a name="codecvtbyname-class"></a>codecvt_byname 클래스

지정된 로캘의 데이터 정렬 패싯으로 사용할 수 있는 개체를 설명하는 파생된 템플릿 클래스입니다. 이 클래스를 사용하여 변환과 관련된 문화 영역별 정보를 검색할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType, class Byte, class StateType>
class codecvt_byname: public codecvt<CharType, Byte, StateType> {
public:
    explicit codecvt_byname(
    const char* _Locname,
    size_t _Refs = 0);
```

```cpp
explicit codecvt_byname(
    const string& _Locname,
    size_t _Refs = 0);
```

```cpp
protected:
    virtual ~codecvt_byname();

};
```

### <a name="parameters"></a>매개 변수

*_Locname*<br/>
명명된 로캘입니다.

*_Refs*<br/>
초기 참조 개수입니다.

## <a name="remarks"></a>설명

명명된 로캘이 생성되는 경우 byname 패싯이 자동으로 생성됩니다.

해당 동작은 명명 된 로캘에 따라 결정 됩니다 *_Locname*합니다. 각 생성자는 [codecvt](../standard-library/codecvt-class.md)\<CharType, Byte, StateType>( `_Refs`)를 통해 해당 기본 개체를 초기화합니다.

## <a name="requirements"></a>요구 사항

**헤더:** \<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
