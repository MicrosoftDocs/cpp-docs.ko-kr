---
title: 링커 도구 오류 LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 407f5eaf94a0e2da43425c3bbdd1955a88c95f14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991183"
---
# <a name="linker-tools-error-lnk2033"></a>링커 도구 오류 LNK2033

' type '에 대 한 확인 되지 않은 typeref 토큰 (토큰)

형식에 MSIL 메타 데이터에 대 한 정의가 없습니다.

LNK2033는 **/clr: safe** 를 사용 하 여 컴파일하는 경우 및 msil 모듈의 형식에 대해 전방 선언만 있는 경우에 발생할 수 있습니다. 여기서 형식은 msil 모듈에서 참조 됩니다.

형식은 **/clr: safe**에서 정의 해야 합니다.

자세한 내용은 [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)을 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 LNK2033를 생성 합니다.

```cpp
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```
