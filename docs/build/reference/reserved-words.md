---
title: 예약어
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 62893d4af1633bc2c89d2d6a0fa71309a0411ad5
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836844"
---
# <a name="reserved-words"></a>예약어

다음 단어는 링커에 예약 되어 있습니다. 이러한 이름은 이름이 큰따옴표 ("")로 묶여 있는 경우에만 [모듈 정의 문에서](module-definition-dot-def-files.md) 인수로 사용할 수 있습니다.

:::row:::
   :::column span="":::
      **`APPLOADER`**<sup>1(sp1)</sup>\
      **`BASE`**\
      **`CODE`**\
      **`CONFORMING`**\
      **`DATA`**\
      **`DESCRIPTION`**\
      **`DEV386`**\
      **`DISCARDABLE`**\
      **`DYNAMIC`**\
      **`EXECUTE-ONLY`**\
      **`EXECUTEONLY`**\
      **`EXECUTEREAD`**\
      **`EXETYPE`**\
      **`EXPORTS`**\
      **`FIXED`** <sup>1</sup>
   :::column-end:::
   :::column span="":::
      **`FUNCTIONS`**<sup>sr-2</sup>\
      **`HEAPSIZE`**\
      **`IMPORTS`**\
      **`IMPURE`**<sup>1(sp1)</sup>\
      **`INCLUDE`**<sup>sr-2</sup>\
      **`INITINSTANCE`**<sup>sr-2</sup>\
      **`IOPL`**\
      **`LIBRARY`**<sup>1(sp1)</sup>\
      **`LOADONCALL`**<sup>1(sp1)</sup>\
      **`LONGNAMES`**<sup>sr-2</sup>\
      **`MOVABLE`**<sup>1(sp1)</sup>\
      **`MOVEABLE`**<sup>1(sp1)</sup>\
      **`MULTIPLE`**\
      **`NAME`**\
      **`NEWFILES`** <sup>2</sup>
   :::column-end:::
   :::column span="":::
      **`NODATA`**<sup>1(sp1)</sup>\
      **`NOIOPL`**<sup>1(sp1)</sup>\
      **`NONAME`**\
      **`NONCONFORMING`**<sup>1(sp1)</sup>\
      **`NONDISCARDABLE`**\
      **`NONE`**\
      **`NONSHARED`**\
      **`NOTWINDOWCOMPAT`**<sup>1(sp1)</sup>\
      **`OBJECTS`**\
      **`OLD`**<sup>1(sp1)</sup>\
      **`PRELOAD`**\
      **`PRIVATE`**\
      **`PROTMODE`**<sup>sr-2</sup>\
      **`PURE`**<sup>1(sp1)</sup>\
      **`READONLY`**
   :::column-end:::
   :::column span="":::
      **`READWRITE`**\
      **`REALMODE`**<sup>1(sp1)</sup>\
      **`RESIDENT`**\
      **`RESIDENTNAME`**<sup>1(sp1)</sup>\
      **`SECTIONS`**\
      **`SEGMENTS`**\
      **`SHARED`**\
      **`SINGLE`**\
      **`STACKSIZE`**\
      **`STUB`**\
      **`VERSION`**\
      **`WINDOWAPI`**\
      **`WINDOWCOMPAT`**\
      **`WINDOWS`**
   :::column-end:::
:::row-end:::

<sup>1</sup> 이 용어를 발견 하면 링커에서 경고 ("무시 됨")를 내보냅니다. 그러나이 단어는 계속 예약 되어 있습니다.

<sup>2</sup> 링커가이 단어를 무시 하지만 경고는 발생 하지 않습니다.

## <a name="see-also"></a>참고 항목

- [MSVC 링커 참조](linking.md)
- [MSVC 링커 옵션](linker-options.md)
