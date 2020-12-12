---
description: '자세한 정보: 필요한 값 계산'
title: 필요한 값 계산
ms.date: 11/04/2016
helpviewer_keywords:
- helper functions, calculating necessary values
ms.assetid: 4f037d0f-881a-4a48-a9d2-9f8872dfccb7
ms.openlocfilehash: 92d8462be2db55dbc10375629b133d9286560878
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179345"
---
# <a name="calculating-necessary-values"></a>필요한 값 계산

지연 도우미 루틴은 두 가지 중요 한 정보를 계산 해야 합니다. 이를 위해이 정보를 계산 하기 위한 두 개의 인라인 함수를 delayhlp에 있습니다.

- 첫 번째는 세 개의 다른 테이블에 대 한 현재 가져오기의 인덱스를 계산 합니다 (가져오기 주소 테이블 (IAT), 바운드 가져오기 주소 테이블 (BIAT) 및 바인딩되지 않은 가져오기 주소 테이블 (UIAT)).

- 두 번째는 유효한 IAT의 가져오기 수를 셉니다.

```cpp
// utility function for calculating the index of the current import
// for all the tables (INT, BIAT, UIAT, and IAT).
__inline unsigned
IndexFromPImgThunkData(PCImgThunkData pitdCur, PCImgThunkData pitdBase) {
    return pitdCur - pitdBase;
    }

// utility function for calculating the count of imports given the base
// of the IAT. NB: this only works on a valid IAT!
__inline unsigned
CountOfImports(PCImgThunkData pitdBase) {
    unsigned        cRet = 0;
    PCImgThunkData  pitd = pitdBase;
    while (pitd->u1.Function) {
        pitd++;
        cRet++;
        }
    return cRet;
    }
```

## <a name="see-also"></a>참고 항목

[도우미 함수 이해](understanding-the-helper-function.md)
