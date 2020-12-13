---
description: '자세한 정보: 링커 도구 경고 LNK4217'
title: 링커 도구 경고 LNK4217
ms.date: 07/23/2019
f1_keywords:
- LNK4217
helpviewer_keywords:
- LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
ms.openlocfilehash: d3ace3586cf11da4dd87f00a58543c6d60fc1a10
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150594"
---
# <a name="linker-tools-warning-lnk4217"></a>링커 도구 경고 LNK4217

> '*filename_1 .obj*'에 정의 된 '*symbol*' 기호는 '*function*' 함수에서 '*filename_2 .obj*'로 가져왔습니다.

기호가 동일한 이미지의 개체 파일에 정의 된 경우에도 기호에 대해 [__declspec (dllimport)](../../cpp/dllexport-dllimport.md) 가 지정 되었습니다. `__declspec(dllimport)`이 경고를 해결 하려면 한정자를 제거 합니다.

## <a name="remarks"></a>설명

*기호* 는 이미지 내에 정의 된 기호 이름입니다. *function* 은 기호를 가져오는 함수입니다.

이 경고는 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 옵션을 사용 하 여 컴파일할 때 표시 되지 않습니다.

LNK4217는 두 모듈을 함께 연결 하려는 경우에도 발생할 수 있습니다. 대신 첫 번째 모듈의 가져오기 라이브러리를 사용 하 여 두 번째 모듈을 컴파일해야 합니다.

```cpp
// main.cpp
__declspec(dllimport) void func();

int main()
{
    func();
    return 0;
}

```

그리고

```cpp
// tt.cpp
// compile with: /c
void func() {}
```

여기에 표시 된 대로 이러한 두 모듈을 컴파일하면 LNK4217이 발생 합니다.

```cmd
cl.exe /c main.cpp tt.cpp
link.exe main.obj tt.obj
```

오류를 해결 하려면 두 파일을 컴파일한 후에 lib.exe에 .tt를 전달 하 여 .lib 파일을 만든 다음 여기에 표시 된 대로 기본 .obj를 .tt와 연결 합니다.

```cmd
cl.exe /c main.cpp tt.cpp
lib.exe tt.obj /export:func /def
link.exe main.obj tt.lib
```

## <a name="see-also"></a>참고 항목

[링커 도구 경고 LNK4049](linker-tools-warning-lnk4049.md) \
[링커 도구 경고 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
