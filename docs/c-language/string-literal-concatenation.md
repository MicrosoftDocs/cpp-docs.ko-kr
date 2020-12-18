---
description: '자세한 정보: 문자열 리터럴 연결'
title: 문자열 리터럴 연결
ms.date: 11/04/2016
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
ms.openlocfilehash: 3486857cb0d218ea80c00252de02d9f29d58f2c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137295"
---
# <a name="string-literal-concatenation"></a>문자열 리터럴 연결

두 줄 이상이 필요한 문자열 리터럴을 형성하려면 두 문자열을 연결합니다. 이렇게 하려면 백슬래시를 입력한 다음 리턴 키를 누릅니다. 백슬래시를 사용하면 컴파일러가 다음 줄 바꿈 문자를 무시합니다. 예를 들어, 다음 문자열 리터럴은

```
"Long strings can be bro\
ken into two or more pieces."
```

다음 문자열과 동일합니다.

```
"Long strings can be broken into two or more pieces."
```

문자열 연결은 이전에 백슬래시를 사용한 모든 위치에 사용할 수 있습니다. 두 줄 이상의 문자열을 입력하려면 뒤에 줄 바꿈 문자를 추가하면 됩니다.

문자열 리터럴 내에서 줄을 강제로 추가하려면 다음과 같이 줄을 나눌 문자열 지점에 줄 바꿈 이스케이프 시퀀스( **\n**)를 입력합니다.

```
"Enter a number between 1 and 100\nOr press Return"
```

문자열은 소스 코드의 모든 열에서 시작할 수 있으며 긴 문자열은 다음 줄의 임의 열에서 계속될 수 있으므로 소스 코드를 읽기 쉽도록 문자열을 배치할 수 있습니다. 어떤 경우든 출력 시의 화면 표현에는 영향이 없습니다. 예를 들어:

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

문자열의 각 부분이 큰따옴표로 묶여 있는 한 해당 부분은 연결되고 단일 문자열로 출력됩니다. 이 연결은 [변환 단계](../preprocessor/phases-of-translation.md)에 따라 지정된 컴파일이 진행되는 동안 이벤트 시퀀스에 따라 발생합니다.

```
"This is the first half of the string, this is the second half"
```

공백으로만 구분된 두 개의 개별 문자열 리터럴로 초기화되는 문자열 포인터는 단일 문자열로 저장됩니다(포인터는 [포인터 선언](../c-language/pointer-declarations.md)에서 설명). 다음 예제와 같이 올바르게 참조하는 경우 결과는 앞의 예제와 동일합니다.

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

변환 6단계에서는 인접 문자열 리터럴 또는 인접 와이드 문자열 리터럴의 임의 시퀀스로 지정된 멀티바이트 문자 시퀀스가 단일 멀티바이트 문자 시퀀스로 연결됩니다. 따라서 실행 중에 문자열 리터럴을 수정할 수 있도록 프로그램을 설계하지 마십시오. ANSI C 표준은 문자열의 수정 결과가 정의되지 않도록 지정합니다.

## <a name="see-also"></a>참조

[C 문자열 리터럴](../c-language/c-string-literals.md)
