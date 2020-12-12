---
description: 다음에 대 한 자세한 정보:/RANGE
title: /RANGE
ms.date: 11/04/2016
f1_keywords:
- /RANGE
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
ms.openlocfilehash: 9af54bddde977e92b5256f0835c31afbff1405d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225403"
---
# <a name="range"></a>/RANGE

/RAWDATA 또는/DISASM.와 같은 다른 dumpbin 옵션과 함께 사용 하는 경우 dumpbin의 출력을 수정 합니다.

## <a name="syntax"></a>구문

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>매개 변수

*vaMin*<br/>
Dumpbin 작업을 시작 하려는 가상 주소입니다.

*vaMax*<br/>
필드 Dumpbin 작업을 종료 하려는 가상 주소입니다. 지정 하지 않으면 dumpbin이 파일의 끝으로 이동 합니다.

## <a name="remarks"></a>설명

이미지에 대 한 가상 주소를 확인 하려면 이미지에 대 한 맵 파일 (RVA + Base), dumpbin의 **/DISASM** 또는 **/Oheaders** 옵션 또는 Visual Studio 디버거의 디스어셈블리 창을 사용 합니다.

## <a name="example"></a>예제

이 예제에서는 **/crange** 를 사용 하 여 **/disasm** 옵션의 표시를 수정 합니다. 이 예제에서 시작 값은 10 진수로 표시 되 고 끝 값은 16 진수 숫자로 지정 됩니다.

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>참고 항목

[DUMPBIN 옵션](dumpbin-options.md)
