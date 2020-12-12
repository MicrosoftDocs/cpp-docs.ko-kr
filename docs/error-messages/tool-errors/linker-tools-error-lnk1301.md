---
description: '자세한 정보: 링커 도구 오류 LNK1301'
title: 링커 도구 오류 LNK1301
ms.date: 11/04/2016
f1_keywords:
- LNK1301
helpviewer_keywords:
- LNK1301
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
ms.openlocfilehash: ac282aea62836591c6e30abb3030ef2143a78003
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335953"
---
# <a name="linker-tools-error-lnk1301"></a>링커 도구 오류 LNK1301

LTCG clr 모듈이 있습니다./LTCG: parameter와 호환 되지 않습니다.

/Clr 및/GL을 사용 하 여 컴파일된 모듈이/LTCG.의 PGO (프로필 기반 최적화) 매개 변수 중 하 나와 함께 링커에 전달 되었습니다.

/Clr 모듈에 대해 프로필 기반 최적화가 지원 되지 않습니다.

자세한 내용은 다음을 참조하세요.

- [/GL (전체 프로그램 최적화)](../../build/reference/gl-whole-program-optimization.md)

- [/LTCG (링크 타임 코드 생성)](../../build/reference/ltcg-link-time-code-generation.md)

- [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)

- [프로필 기반 최적화](../../build/profile-guided-optimizations.md)

### <a name="to-correct-this-error"></a>이 오류를 해결하려면

1. /Clr을 사용 하 여 컴파일하지 않거나 PGO 매개 변수 중 하나를 사용 하 여/LTCG.에 연결 하지 마세요.

## <a name="example"></a>예제

다음 샘플에서는 LNK1301를 생성 합니다.

```cpp
// LNK1301.cpp
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj
// LNK1301 expected
class MyClass {
public:
   int i;
};
```
