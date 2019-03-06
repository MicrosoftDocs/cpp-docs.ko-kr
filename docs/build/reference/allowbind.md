---
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 8f59cc83c06bbaaccba911c44835247253cb264b
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416893"
---
# <a name="allowbind"></a>/ALLOWBIND

DLL을 바인딩할 수 있는지 여부를 지정합니다.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>설명

합니다 **여 /ALLOWBIND** 옵션 비트 이미지를 바인딩할 수 있음을 나타냅니다 bind.exe 하는 DLL의 헤더를 설정 합니다. 바인딩 이미지 로더가 기준 주소 다시 지정 및 참조 된 각 DLL에 대 한 주소 픽스업 수행 없을 때 더 빠르게 로드를 허용할 수 있습니다. 디지털 서명 된 경우 DLL 않을-바인딩 서명이 무효화 합니다. 주소 공간 레이아웃 불규칙화 (ASLR)를 사용 하 여 이미지에 사용 되 면 바인딩에 영향을 주지 않습니다 **/DYNAMICBASE** ASLR을 지 원하는 Windows 버전에서 합니다.

사용 하 여 **/allowbind: no** Bind.exe에서 DLL 바인딩 방지 하기 위해.

자세한 내용은 참조는 [여 /ALLOWBIND](../../build/reference/allowbind-prevent-dll-binding.md) 링커 옵션입니다.

## <a name="see-also"></a>참고자료

[EDITBIN 옵션](../../build/reference/editbin-options.md)
