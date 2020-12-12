---
description: 다음에 대 한 자세한 정보:/ALLOWBIND
title: /ALLOWBIND
ms.date: 11/04/2016
f1_keywords:
- /allowbind_bind
helpviewer_keywords:
- ALLOWBIND editbin option
- /ALLOWBIND editbin option
- -ALLOWBIND editbin option
ms.assetid: eaadbb8c-4339-4281-9a75-3a1ce2352ff8
ms.openlocfilehash: 54f3056240537d765a9212e774a9a313ded49dab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97179605"
---
# <a name="allowbind"></a>/ALLOWBIND

DLL을 바인딩할 수 있는지 여부를 지정합니다.

```

/ALLOWBIND[:NO]
```

## <a name="remarks"></a>설명

**/Allowbind** 옵션은 이미지를 바인딩할 수 있음을 Bind.exe를 나타내는 DLL 헤더의 비트를 설정 합니다. 바인딩을 사용 하면 로더가 참조 된 각 DLL에 대해 주소를 다시 지정 하 고 주소를 수정 하지 않아도 되는 경우 이미지를 더 빨리 로드할 수 있습니다. 디지털 서명 된 경우에는 DLL이 바인딩되지 않도록 할 수 있습니다. 바인딩에서 서명을 무효화 합니다. ASLR을 지 원하는 Windows 버전에서 **/DYNAMICBASE** 를 사용 하 여 이미지에 대해 aslr (주소 공간 레이아웃 임의 설정)을 사용 하는 경우 바인딩이 적용 되지 않습니다.

**/Allowbind: NO** 를 사용 하 여 Bind.exe DLL을 바인딩하지 않도록 합니다.

자세한 내용은 [/Allowbind](allowbind-prevent-dll-binding.md) 링커 옵션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)
