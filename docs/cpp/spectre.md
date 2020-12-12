---
description: '자세히 알아보기: 스펙터'
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: fc1f56a59dea1eaa3596a6f7a7c0347ab822e302
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113820"
---
# <a name="spectre"></a>spectre

**Microsoft 전용**

는 함수에 대 한 스펙터 variant 1 잘못 된 실행 장벽 명령을 삽입 하지 않도록 컴파일러에 지시 합니다.

## <a name="syntax"></a>Syntax

> **__declspec (스펙터 (nomitigation))**

## <a name="remarks"></a>설명

[/Qspectre](../build/reference/qspectre.md) 컴파일러 옵션을 선택 하면 컴파일러가 잘못 된 실행 장벽 명령을 삽입 합니다. 분석에서 스펙터 variant 1 보안 취약성이 있음을 나타내는 경우 삽입 됩니다. 내보낸 특정 지침은 프로세서에 따라 다릅니다. 이러한 지침은 코드 크기나 성능에 최소한의 영향을 주므로 코드가 취약성의 영향을 받지 않는 경우가 있을 수 있으며,이 경우에는 최대 성능이 필요 합니다.

전문가 분석은 스펙터 변형 1 범위 확인 무시 결함에서 함수가 안전 하다는 것을 확인할 수 있습니다. 이 경우 함수 선언에를 적용 하 여 함수 내의 완화 코드 생성을 억제할 수 있습니다 `__declspec(spectre(nomitigation))` .

> [!CAUTION]
> **/Qspectre** 잘못 된 실행 장벽 지침은 중요 한 보안 보호를 제공 하며 성능에 거의 영향을 주지 않습니다. 함수의 성능이 매우 중요하고 해당 함수의 안전성이 파악되는 드문 경우를 제외하고, 버퍼 보안 검사를 억제하지 않도록 권장합니다.

## <a name="example"></a>예제

다음 코드에서는 `__declspec(spectre(nomitigation))`사용 방법을 보여 줍니다.

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
