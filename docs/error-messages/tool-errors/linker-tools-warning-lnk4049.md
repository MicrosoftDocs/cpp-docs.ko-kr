---
description: '자세한 정보: 링커 도구 경고 LNK4049'
title: 링커 도구 경고 LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: 2451c5533b22eacb0b640ed301203f6332b6681d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210324"
---
# <a name="linker-tools-warning-lnk4049"></a>링커 도구 경고 LNK4049

> ' filename '에 정의 된 '*symbol*' 기호를 가져왔습니다 *.*

동일한 이미지의 개체 파일 *파일 이름 .obj* 에서 기호가 정의 된 경우에도 *기호* 에 대해 [__declspec (dllimport)](../../cpp/dllexport-dllimport.md) 가 지정 되었습니다. `__declspec(dllimport)`이 경고를 해결 하려면 한정자를 제거 합니다.

## <a name="remarks"></a>설명

이 경고는 한 개체 파일에서 기호를 정의 하 고 `__declspec(dllimport)` 다른 개체의 선언 한정자를 사용 하 여 참조 하는 경우 링커에서 생성 됩니다.

경고 LNK4049는 [링커 도구 경고 LNK4217](linker-tools-warning-lnk4217.md)보다 일반적인 버전입니다. 링커에서는 가져온 기호를 참조 하는 함수 또는 개체 파일을 확인할 수 없는 경우 경고 LNK4049 생성 합니다.

LNK4217 대신 LNK4049가 생성 되는 일반적인 경우는 다음과 같습니다.

- [/INCREMENTAL](../../build/reference/incremental-link-incrementally.md) 옵션을 사용 하는 경우

- [/Ltcg](../../build/reference/ltcg-link-time-code-generation.md) 옵션을 사용 하는 경우

LNK4049를 해결 하려면 다음 절차 중 하나를 수행 합니다.

- LNK4049를 `__declspec(dllimport)` 트리거한 기호의 전방 선언에서 한정자를 제거 합니다. **DUMPBIN** 유틸리티를 사용 하 여 이진 이미지 내에서 기호를 검색할 수 있습니다. **DUMPBIN/SYMBOLS** 스위치는 이미지의 COFF 기호 테이블을 표시 합니다. **Dumpbin** 유틸리티에 대 한 자세한 내용은 [dumpbin 참조](../../build/reference/dumpbin-reference.md)를 참조 하세요.

- 증분 링크 및 전체 프로그램 최적화를 일시적으로 사용 하지 않습니다. 다시 컴파일하면 응용 프로그램에서 가져온 기호를 참조 하는 함수의 이름을 포함 하는 경고 LNK4217을 생성 합니다. `__declspec(dllimport)`가져온 기호에서 선언 한정자를 제거 하 고 필요에 따라 증분 링크 또는 전체 프로그램 최적화를 다시 사용 하도록 설정 합니다.

최종 생성 된 코드는 올바르게 동작 하지만 가져온 함수를 호출 하기 위해 생성 되는 코드는 함수를 직접 호출 하는 것 보다 효율성이 떨어집니다. 이 경고는 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 옵션을 사용 하 여 컴파일할 때 표시 되지 않습니다.

데이터 가져오기 및 내보내기에 대 한 자세한 내용은 [dllexport, dllimport](../../cpp/dllexport-dllimport.md)를 참조 하세요.

## <a name="example"></a>예제

다음 두 모듈을 연결 하면 LNK4049 생성 됩니다. 첫 번째 모듈은 내보낸 단일 함수를 포함 하는 개체 파일을 생성 합니다.

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

두 번째 모듈은 함수 내에서이 함수를 호출 하는 것과 함께 첫 번째 모듈에서 내보낸 함수에 대 한 전방 선언이 포함 된 개체 파일을 생성 합니다 `main` . 이 모듈을 첫 번째 모듈과 연결 하면 LNK4049 생성 됩니다. 경고를 `__declspec(dllimport)` 해결 하려면 선언에서 한정자를 제거 합니다.

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>참고 항목

[링커 도구 경고 LNK4217](linker-tools-warning-lnk4217.md) \
[링커 도구 경고 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport, dllimport](../../cpp/dllexport-dllimport.md)
