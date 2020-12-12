---
description: '자세한 정보: 링커 도구 경고 LNK4286'
title: 링커 도구 경고 LNK4286
ms.date: 04/15/2019
f1_keywords:
- LNK4286
helpviewer_keywords:
- LNK4286
ms.openlocfilehash: 6a1e397967857ae3f982bf8f5e55f4bf74c9abe4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244448"
---
# <a name="linker-tools-warning-lnk4286"></a>링커 도구 경고 LNK4286

> '*filename_1 .obj*'에 정의 된 '*symbol*' 기호는 '*filename_2 .obj*'에 의해 가져옴

기호가 동일한 이미지의 개체 파일 *filename_1* 에 정의 되어 있어도 (dllimport) *기호* 에 대해 [__declspec (dllimport)](../../cpp/dllexport-dllimport.md) 가 지정 되었습니다. `__declspec(dllimport)`이 경고를 해결 하려면 한정자를 제거 합니다.

## <a name="remarks"></a>설명

경고 LNK4286는 [링커 도구 경고 LNK4217](linker-tools-warning-lnk4217.md)보다 일반적인 버전입니다. 링커에서는 어떤 개체 파일이 어떤 함수를 참조 하는지 알 수 LNK4286 경고를 생성 합니다.

LNK4286를 해결 하려면 `__declspec(dllimport)` *filename_2 .obj* 에서 참조 하는 *기호의* 전방 선언에서 선언 한정자를 제거 합니다.

최종 생성 된 코드는 올바르게 동작 하지만 가져온 함수를 호출 하기 위해 생성 되는 코드는 함수를 직접 호출 하는 것 보다 효율성이 떨어집니다. 이 경고는 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 옵션을 사용 하 여 컴파일할 때 표시 되지 않습니다.

데이터 가져오기 및 내보내기에 대 한 자세한 내용은 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[링커 도구 경고 LNK4049](linker-tools-warning-lnk4049.md) \
[링커 도구 경고 LNK4217](linker-tools-warning-lnk4217.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
