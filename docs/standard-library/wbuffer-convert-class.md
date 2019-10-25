---
title: wbuffer_convert 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 8de0091af93120290105ce7603fae5acff257b76
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688536"
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

|매개 변수|설명|
|---------------|-----------------|
|*Codecvt*|변환 개체를 나타내는 [locale](../standard-library/locale-class.md) 패싯입니다.|
|*Elem*|와이드 문자 요소 형식입니다.|
|*특성*|*Elem*과 연결된 특성입니다.|

## <a name="remarks"></a>주의

이 클래스 템플릿은 형식 `_Elem`의 요소 전송을 제어 하는 스트림 버퍼에 대해 설명 합니다 .이는 문자 특성이 `std::streambuf` 형식의 바이트 스트림 버퍼를 대상으로 하 `Traits` 클래스에서 설명 합니다.

`Elem` 값 시퀀스와 멀티바이트 시퀀스 간 변환은 클래스 `Codecvt<Elem, char, std::mbstate_t>`의 개체에 의해 수행되며, 표준 코드 변환 패싯 `std::codecvt<Elem, char, std::mbstate_t>`의 요구 사항을 충족합니다.

이 클래스 템플릿의 개체는 다음을 저장 합니다.

- 기본 바이트 스트림 버퍼에 대한 포인터

- 할당된 변환 개체에 대한 포인터([wbuffer_convert](../standard-library/wbuffer-convert-class.md) 개체가 제거될 때 해제됨)
