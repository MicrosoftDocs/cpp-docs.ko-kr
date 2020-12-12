---
description: '자세한 정보: 링커 도구 경고 LNK4224'
title: 링커 도구 경고 LNK4224
ms.date: 11/04/2016
f1_keywords:
- LNK4224
helpviewer_keywords:
- LNK4224
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
ms.openlocfilehash: 35cae5c46b91493a40d4d52650f781010f6d6379
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327908"
---
# <a name="linker-tools-warning-lnk4224"></a>링커 도구 경고 LNK4224

> *옵션* 은 더 이상 지원 되지 않습니다. 무시

## <a name="remarks"></a>설명

사용 되지 않는 잘못 된 링커 옵션이 지정 되 고 무시 되었습니다.

예를 들어/comment 지시문이 .obj에 표시 되는 경우 LNK4224이 발생할 수 있습니다. /Comment 지시문은 사용 되지 않는 exestr 옵션을 사용 하 여 [주석 (c/c + +)](../../preprocessor/comment-c-cpp.md) pragma를 통해 추가 되었습니다. Dumpbin 파일에서 링커 지시문을 보려면 dumpbin [/all](../../build/reference/all.md) 을 사용 합니다.

가능 하면 .obj의 소스를 수정 하 고 pragma를 제거 합니다. 이 경고를 무시 하는 경우 **/clr: pure** 로 컴파일된 실행 파일이 예상 대로 실행 되지 않을 수 있습니다. **/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 LNK4224를 생성 합니다.

```cpp
// LNK4224.cpp
// compile with: /c /Zi
// post-build command: link LNK4224.obj /debug /debugtype:map
int main () {
   return 0;
}
```
