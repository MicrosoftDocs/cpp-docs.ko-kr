---
description: '다음에 대 한 자세한 정보: codecvt_utf16'
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 264324d0f827e8999b065205010874ebf62ca501
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325090"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

U t f-2 또는 u s-4로 인코드된 와이드 문자와 u t f-UTF-16LE 또는 UTF-16로 인코딩된 바이트 스트림으로 변환 하는 [로캘](../standard-library/locale-class.md) 패싯을 나타냅니다.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>매개 변수

*E*\
와이드 문자 요소 형식입니다.

*Maxcode*\
로캘 패싯에 대한 최대 문자 수입니다.

*모드가*\
로캘 패싯에 대한 구성 정보입니다.

## <a name="remarks"></a>설명

이 클래스 템플릿은 utf-8 또는 u c s-4로 인코드된 와이드 문자와 u t f-UTF-16LE로 인코딩된 바이트 스트림 (모드 & little_endian 또는 u t f-16이 아닌 경우) 간을 변환 합니다.

바이트 스트림은 이진 파일에 작성해야 하며, 텍스트 파일에 작성하는 경우 손상될 수 있습니다.

## <a name="requirements"></a>요구 사항

헤더: \<codecvt>

네임스페이스: std
