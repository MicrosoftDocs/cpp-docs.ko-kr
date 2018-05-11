---
title: wbuffer_convert 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36df93b54accbfdc3ff8f486c41a47af72032c3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="wbufferconvert-class"></a>wbuffer_convert 클래스

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
|`Codecvt`|변환 개체를 나타내는 [locale](../standard-library/locale-class.md) 패싯입니다.|
|`Elem`|와이드 문자 요소 형식입니다.|
|`Traits`|*Elem*과 연결된 특성입니다.|

## <a name="remarks"></a>설명

이 템플릿 클래스는 `std::streambuf` 형식의 바이트 스트림 버퍼에서 나가고 들어오는 `_Elem` 형식 요소의 전송을 제어하는 스트림 버퍼에 대해 설명하며, 해당 문자 특성은 `Traits` 클래스로 설명합니다.

`Elem` 값 시퀀스와 멀티바이트 시퀀스 간 변환은 클래스 `Codecvt<Elem, char, std::mbstate_t>`의 개체에 의해 수행되며, 표준 코드 변환 패싯 `std::codecvt<Elem, char, std::mbstate_t>`의 요구 사항을 충족합니다.

이 템플릿 클래스의 개체는 다음을 저장합니다.

- 기본 바이트 스트림 버퍼에 대한 포인터

- 할당된 변환 개체에 대한 포인터([wbuffer_convert](../standard-library/wbuffer-convert-class.md) 개체가 제거될 때 해제됨)
