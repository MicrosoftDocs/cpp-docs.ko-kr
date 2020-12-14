---
description: '다음에 대 한 자세한 정보: codecvt_utf8'
title: codecvt_utf8
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf8
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
ms.openlocfilehash: b0da37607d563786285564d17b2c8a49e9e064bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234035"
---
# <a name="codecvt_utf8"></a>codecvt_utf8

U t f-2 또는 u c s-4로 인코드된 와이드 문자와 u t f-8로 인코딩된 바이트 스트림으로 변환 하는 [로캘](../standard-library/locale-class.md) 패싯을 나타냅니다.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>매개 변수

*E*\
와이드 문자 요소 형식입니다.

*Maxcode*\
로캘 패싯에 대한 최대 문자 수입니다.

*모드가*\
로캘 패싯에 대한 구성 정보입니다.

## <a name="remarks"></a>설명

바이트 스트림은 이진 파일 또는 텍스트 파일에 작성할 수 있습니다.

## <a name="requirements"></a>요구 사항

헤더: \<codecvt>

네임스페이스: std
