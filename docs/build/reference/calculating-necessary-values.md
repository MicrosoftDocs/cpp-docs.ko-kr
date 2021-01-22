---
description: '자세한 정보: 지연 로드에 필요한 값 계산'
title: 지연 로드에 필요한 값 계산
ms.date: 01/19/2021
helpviewer_keywords:
- helper functions, calculating necessary values
ms.openlocfilehash: ae5e0c15b5b13f12fd90c1378a1e449516b55f43
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667450"
---
# <a name="calculate-necessary-values-for-delay-loading"></a>지연 로드에 필요한 값 계산

지연 로드 도우미 루틴은 두 가지 중요 한 정보를 계산 해야 합니다. 이 정보를 계산 하는 데에는 두 가지 인라인 함수가 있습니다 *`delayhlp.cpp`* .

- 첫 번째는 `IndexFromPImgThunkData` 세 개의 다른 테이블 (가져오기 주소 테이블 (IAT), 바운드 가져오기 주소 테이블 (BIAT) 및 바인딩되지 않은 가져오기 주소 테이블 (UIAT))에 대 한 현재 가져오기의 인덱스를 계산 합니다.

- 두 번째는 `CountOfImports` 유효한 IAT의 가져오기 수를 계산 합니다.

```C
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
