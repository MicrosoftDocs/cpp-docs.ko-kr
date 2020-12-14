---
description: '자세한 정보: 링커 도구 오류 LNK1107'
title: 링커 도구 오류 LNK1107
ms.date: 11/04/2016
f1_keywords:
- LNK1107
helpviewer_keywords:
- LNK1107
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
ms.openlocfilehash: 2a5ed9ba0bc4789a324d143b6287a08712299cdd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281394"
---
# <a name="linker-tools-error-lnk1107"></a>링커 도구 오류 LNK1107

파일이 잘못 되었거나 손상 되었습니다. 위치에서 읽을 수 없습니다.

도구에서 파일을 읽을 수 없습니다. 파일을 다시 만듭니다.

LNK1107 ( [/clr: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) 또는  [/noassembly](../../build/reference/noassembly-create-a-msil-module.md)를 사용 하 여 만든) 모듈 (.dll 또는 .netmodule 확장명)을 링커에 전달 하려고 시도 하는 경우에도 발생할 수 있습니다. 대신 .obj 파일을 전달 합니다.

다음 샘플을 컴파일하는 경우:

```cpp
// LNK1107.cpp
// compile with: /clr /LD
public ref class MyClass {
public:
   void Test(){}
};
```

그런 다음 명령줄에서 **링크 LNK1107.dll** 지정 하면 LNK1107이 발생 합니다.  오류를 해결 하려면 **링크 LNK1107** 를 대신 지정 합니다.
