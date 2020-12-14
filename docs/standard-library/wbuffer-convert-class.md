---
description: Wbuffer_convert 클래스에 대해 자세히 알아보세요.
title: wbuffer_convert 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 1aa7258c3cc0a4f78a749f655e9cfb7cd4957378
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187847"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert 클래스

바이트 스트림 버퍼에서 나가고 들어오는 요소의 전송을 제어하는 스트림 버퍼에 대해 설명합니다.

## <a name="syntax"></a>구문

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>매개 변수

*Codecvt*\
변환 개체를 나타내는 [locale](../standard-library/locale-class.md) 패싯입니다.

*E*\
와이드 문자 요소 형식입니다.

*특징이*\
*Elem* 과 연결된 특성입니다.

## <a name="remarks"></a>설명

이 클래스 템플릿은 형식의 요소에 대 한 전송을 제어 하는 스트림 버퍼에 대해 설명 합니다 `_Elem` . 해당 문자 특성은 클래스에서 `Traits` 형식의 바이트 스트림 버퍼에 대 한 형식으로 표현 됩니다 `std::streambuf` .

`Elem` 값 시퀀스와 멀티바이트 시퀀스 간 변환은 클래스 `Codecvt<Elem, char, std::mbstate_t>`의 개체에 의해 수행되며, 표준 코드 변환 패싯 `std::codecvt<Elem, char, std::mbstate_t>`의 요구 사항을 충족합니다.

이 클래스 템플릿의 개체는 다음을 저장 합니다.

- 기본 바이트 스트림 버퍼에 대한 포인터

- 할당된 변환 개체에 대한 포인터([wbuffer_convert](../standard-library/wbuffer-convert-class.md) 개체가 제거될 때 해제됨)
