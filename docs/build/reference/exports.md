---
description: '자세한 정보: 내보내기'
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: b886f626854012c3cc477fcb11ac74a1e7776299
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192346"
---
# <a name="exports"></a>EXPORTS

함수 또는 데이터의 내보낸 이름이나 서수를 지정하는 하나 이상의 내보내기 정의 섹션에 대해 소개합니다. 각 정의는 별도의 줄에 있어야 합니다.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>설명

첫 번째 *정의* 는 키워드와 같은 줄 이나 후속 줄에 있을 수 있습니다 `EXPORTS` . .DEF 파일에는 `EXPORTS` 문이 한 개 이상 있을 수 있습니다.

내보내기 *정의* 의 구문은 다음과 같습니다.

>  \[ entryname __=__ *internal_name* | *other_module.exported_name*] \[ **\@** _서 수_ \[ **NONAME**] \[ ] \[ **개인**] | \[ **데이터**]]

*entryname* 는 내보내고 싶은 함수 또는 변수 이름입니다. 이것은 필수입니다. 내보내는 이름이 DLL의 이름과 다른 경우 *internal_name* 를 사용 하 여 dll에서 내보내기의 이름을 지정 합니다. 예를 들어 DLL이 함수 `func1`을 내보내고 호출자가 이 함수를 `func2`로 사용하도록 하려는 경우 다음과 같이 지정할 수 있습니다.

```DEF
EXPORTS
   func2=func1
```

내보내는 이름이 다른 모듈에서 *other_module. exported_name* 를 사용 하 여 DLL에서 내보내기 이름을 지정 합니다. 예를 들어 DLL이 함수 `other_module.func1`을 내보내고 호출자가 이 함수를 `func2`로 사용하도록 하려는 경우 다음과 같이 지정할 수 있습니다.

```DEF
EXPORTS
   func2=other_module.func1
```

내보내는 이름이 서 수로 내보내는 다른 모듈에서 가져온 경우 *other_module* 를 사용 하 여 DLL에서 내보내기의 서 수를 지정 합니다. __#__ *서 수*. 예를 들어, DLL이 서 수 42 인 다른 모듈에서 함수를 내보내고 호출자에 게이 함수를 사용 하려면 `func2` 다음을 지정 합니다.

```DEF
EXPORTS
   func2=other_module.#42
```

MSVC 컴파일러는 c + + 함수에 이름 데코레이션을 사용 하기 때문에 데코레이팅된 *internal_name* 이름을 사용 하거나 소스 코드에서를 사용 하 여 내보낸 함수를 정의 해야 합니다 `extern "C"` . 또한 컴파일러는 밑줄 () 접두사를 사용 하 여 [__stdcall](../../cpp/stdcall.md) 호출 규칙을 사용 하 \_ 고 \@ 인수 목록의 바이트 수 (10 진수)로 구성 된 접미사를 사용 하는 C 함수를 데코 레이트 합니다.

컴파일러에서 생성 한 데코레이팅된 이름을 찾으려면 [DUMPBIN](dumpbin-reference.md) 도구 또는 링커 [/map](map-generate-mapfile.md) 옵션을 사용 합니다. 데코레이팅된 이름은 컴파일러별로 다릅니다. .DEF 파일의 데코레이팅된 이름을 내보내는 경우 DLL에 연결된 실행 파일도 동일한 버전의 컴파일러를 사용하여 빌드해야 합니다. 그래야 호출자의 데코레이팅된 이름이 .DEF 파일의 내보낸 이름과 일치하게 됩니다.

\@ *서* 수를 사용 하 여 함수 이름이 아닌 숫자가 DLL의 내보내기 테이블로 이동 하도록 지정할 수 있습니다. 많은 Windows DLL은 서수를 내보내 레거시 코드를 지원합니다. Windows DLL의 크기를 최소화할 수 있기 때문에 16비트 Windows 코드에서는 서수를 사용하는 것이 일반적입니다. DLL의 클라이언트에서 레거시 지원을 위해 필요로 하지 않는 한 서 수로 함수를 내보내는 것은 권장 되지 않습니다. .LIB 파일에는 서수와 함수 간의 매핑이 포함되므로 DLL을 사용하는 프로젝트에서 일반적으로 하는 것처럼 함수 이름을 사용할 수 있습니다.

선택적 **NONAME** 키워드를 사용 하 여 서 수로만 내보내고 결과 DLL의 내보내기 테이블 크기를 줄일 수 있습니다. 그러나 DLL에서 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) 를 사용 하려는 경우에는 이름이 유효 하지 않기 때문에 서 수를 알아야 합니다.

**PRIVATE 키워드 PRIVATE** 은 LINK에서 생성 된 가져오기 라이브러리에 *entryname* 를 포함 하지 않도록 합니다. 이는 LINK에서도 생성한 이미지에서 내보내기에 영향을 미치지 않습니다.

선택적 키워드 **데이터** 는 내보내기가 코드가 아닌 데이터 임을 지정 합니다. 아래 예제는 `exported_global` 데이터 변수를 내보낼 수 있는 방법을 보여줍니다.

```DEF
EXPORTS
   exported_global DATA
```

다음은 정의를 내보내는 4가지 방법으로 권장 순서대로 나열되었습니다.

1. 소스 코드의 [__declspec (dllexport)](../../cpp/dllexport-dllimport.md) 키워드

1. .DEF 파일의 `EXPORTS` 문

1. LINK 명령의 [/export](export-exports-a-function.md) 사양

1. 폼의 소스 코드에 있는 [주석](../../preprocessor/comment-c-cpp.md) 지시문 `#pragma comment(linker, "/export: definition ")` 입니다. 다음 예제에서는 함수 선언 앞에 #pragma 주석 지시문을 보여 줍니다 `PlainFuncName` . 여기서은 데코레이팅되지 않은 이름이 고 `_PlainFuncName@4` 는 데코레이팅된 함수 이름입니다.

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

#Pragma 지시어는 데코레이팅되지 않은 함수 이름을 내보내야 하 고 빌드 구성에 따라 다른 내보내기를 포함 하는 경우에 유용 합니다 (예: 32 비트 또는 64 비트 빌드).

4가지 메서드 모두 동일한 프로그램에서 사용할 수 있습니다. LINK가 내보내기를 포함하는 프로그램을 빌드하는 경우 빌드에서 .EXP 파일을 사용하지 않는다면 가져오기 라이브러리도 만들게 됩니다.

다음은 EXPORTS 섹션의 예입니다.

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

.DEF 파일을 사용하여 DLL에서 변수를 내보낸 경우 변수에 대해 `__declspec(dllexport)`을 지정할 필요가 없습니다. 그러나 DLL을 사용하는 모든 파일에서는 데이터 선언 시 `__declspec(dllimport)`을 계속해서 사용해야 합니다.

## <a name="see-also"></a>참고 항목

[Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)
