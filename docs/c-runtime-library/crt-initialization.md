---
title: CRT 초기화
description: CRT가 네이티브 코드에서 전역 상태를 초기화 하는 방법을 설명 합니다.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- CRT initialization [C++]
ms.assetid: e7979813-1856-4848-9639-f29c86b74ad7
ms.openlocfilehash: e33429d63cebb34514918d059649679ed28b924c
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514644"
---
# <a name="crt-initialization"></a>CRT 초기화

이 항목에서는 CRT가 네이티브 코드에서 전역 상태를 초기화 하는 방법에 대해 설명 합니다.

기본적으로 링커는 자체 시작 코드를 제공하는 CRT 라이브러리를 포함합니다. 이 시작 코드는 CRT 라이브러리를 초기화하고 전역 이니셜라이저를 호출한 다음 콘솔 애플리케이션에 대해 사용자 제공 `main` 함수를 호출합니다.

## <a name="initializing-a-global-object"></a>전역 개체 초기화

다음 코드를 살펴보세요.

```
int func(void)
{
    return 3;
}

int gi = func();

int main()
{
    return gi;
}
```

C/C++ 표준에 따라 `func()`을 실행하기 전에 `main()`를 호출해야 합니다. 하지만 누가 호출할까요?

호출자를 확인 하는 한 가지 방법은에서 중단점을 설정 하 `func()` 고, 응용 프로그램을 디버깅 하 고, 스택을 검사 하는 것입니다. 이는 CRT 소스 코드가 Visual Studio에 포함되어 있기 때문에 가능합니다.

스택에서 함수를 검색 하면 CRT가 함수 포인터 목록을 호출 하는 것을 볼 수 있습니다. 이러한 함수는 `func()` 또는 클래스 인스턴스에 대 한 생성자와 유사 합니다.

CRT는 Microsoft c + + 컴파일러에서 함수 포인터 목록을 가져옵니다. 컴파일러는 전역 이니셜라이저를 볼 때 섹션에 동적 이니셜라이저를 생성 합니다 `.CRT$XCU` `CRT` . 여기서는 섹션 이름이 고는 `XCU` 그룹 이름입니다. 동적 이니셜라이저의 목록을 가져오려면 **dumpbin/all main** 명령을 실행 한 다음 섹션을 검색 `.CRT$XCU` 합니다. 이는 기본 .cpp가 C 파일이 아닌 c + + 파일로 컴파일될 때 적용 됩니다. 다음 예제와 유사 합니다.

```
SECTION HEADER #6
.CRT$XCU name
       0 physical address
       0 virtual address
       4 size of raw data
     1F2 file pointer to raw data (000001F2 to 000001F5)
     1F6 file pointer to relocation table
       0 file pointer to line numbers
       1 number of relocations
       0 number of line numbers
40300040 flags
         Initialized Data
         4 byte align
         Read Only

RAW DATA #6
  00000000: 00 00 00 00                                      ....

RELOCATIONS #6
                                               Symbol    Symbol
Offset    Type              Applied To         Index     Name
--------  ----------------  -----------------  --------  -------
00000000  DIR32             00000000           C         ??__Egi@@YAXXZ (void __cdecl `dynamic initializer for 'gi''(void))
```

CRT는 두 포인터를 정의합니다.

- `.CRT$XCA`의 `__xc_a`

- `.CRT$XCZ`의 `__xc_z`

및를 제외한 어떤 그룹에도 다른 기호가 정의 되어 있지 않습니다 `__xc_a` `__xc_z` .

링커는 다양한 `.CRT` 그룹을 읽을 때 해당 그룹을 한 섹션에서 결합하고 사전순으로 정렬합니다. 즉, Microsoft C++ 컴파일러가 `.CRT$XCU`에 넣는 사용자 정의 글로벌 이니셜라이저가 항상 `.CRT$XCA` 뒤와 `.CRT$XCZ` 앞에 옵니다.

이 섹션은 다음 예제와 유사 합니다.

```
.CRT$XCA
            __xc_a
.CRT$XCU
            Pointer to Global Initializer 1
            Pointer to Global Initializer 2
.CRT$XCZ
            __xc_z
```

따라서 CRT 라이브러리는와를 모두 사용 하 여 `__xc_a` `__xc_z` 전역 이니셜라이저 목록의 시작과 끝을 결정 합니다 .이는 이미지가 로드 된 후 메모리에서 배치 되는 방식 때문입니다.

## <a name="see-also"></a>추가 정보

[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
