---
description: '자세한 정보: C 비트 필드'
title: C 비트 필드
ms.date: 11/04/2016
helpviewer_keywords:
- bitfields
- bit fields
ms.assetid: 9faf74c4-7fd5-4b44-ad18-04485193d06e
ms.openlocfilehash: e89f74fc68cad11eee63b3dd1101fa71e0b72e27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97186956"
---
# <a name="c-bit-fields"></a>C 비트 필드

구조 선언자는 구조체 또는 공용 구조체의 멤버에 대한 선언자일 뿐만 아니라 “비트 필드"라는 지정된 비트 수로 구성될 수도 있습니다. 해당 길이는 필드 이름에 대한 선언자에서 콜론으로 설정됩니다. 비트 필드는 정수 데이터 형식으로 해석됩니다.

## <a name="syntax"></a>구문

*struct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declarator*<sub>opt</sub> **:** *constant-expression*

*constant-expression* 은 필드의 너비(비트)를 지정합니다. `declarator`에 대한 *type-specifier* 는 **`unsigned int`** , **`signed int`** 또는 **`int`** 여야 하고 *constant-expression* 은 음수가 아닌 정수 값이어야 합니다. 이 값이 0인 경우 선언에는 `declarator`가 없습니다. 비트 필드의 배열, 비트 필드에 대한 포인터 및 비트 필드를 반환하는 함수는 허용되지 않습니다. 선택적 `declarator`는 비트 필드 이름을 지정합니다. 비트 필드는 구조체의 일부로만 선언할 수 있습니다. address-of 연산자( **&** )는 비트 필드 구성 요소에 적용할 수 없습니다.

명명되지 않은 비트 필드는 참조할 수 없으며 런타임에 해당 콘텐츠를 예측할 수 없습니다. 정렬 목적으로 "더미" 필드로 사용할 수 있습니다. 너비가 0으로 지정된 명명되지 않은 비트 필드의 경우 *struct-declaration-list* 에서 해당 필드 다음에 나오는 멤버의 스토리지가 **`int`** 경계에서 시작됩니다.

또한 비트 필드는 비트 패턴을 포함할 만큼 충분히 길어야 합니다. 예를 들어 다음 두 문은 올바르지 않습니다.

```
short a:17;        /* Illegal! */
int long y:33;     /* Illegal! */
```

이 예제에서는 `screen`이라는 구조체의 2차원 배열을 정의합니다.

```
struct
{
    unsigned short icon : 8;
    unsigned short color : 4;
    unsigned short underline : 1;
    unsigned short blink : 1;
} screen[25][80];
```

이 배열에는 2,000개의 요소가 있습니다. 각 요소는 4개의 비트 필드 멤버, 즉 `icon`, `color`, `underline` 및 `blink`를 포함하는 개별 구조체입니다. 각 구조체의 크기는 2바이트입니다.

비트 필드는 정수 형식과 의미 체계가 같습니다. 즉, 비트 필드는 포함된 비트 수에 관계없이, 동일한 기본 형식의 변수가 사용되는 것과 정확히 동일한 방식으로 식에서 사용됩니다.

**Microsoft 전용**

**`int`** 로 정의된 비트 필드는 **`signed`** 로 처리됩니다. ANSI C 표준에 대한 Microsoft 확장은 비트 필드에 대해 **`char`** 및 **`long`** 형식( **`signed`** 및 **`unsigned`** 둘 다)을 허용합니다. 기본 형식 **`long`** , **`short`** 또는 **`char`** ( **`signed`** 또는 **`unsigned`** )을 갖는 명명되지 않은 비트 필드는 기본 형식에 맞게 강제로 경계에 맞춰 정렬됩니다.

비트 필드는 최하위 비트에서 최상위 비트까지 정수 내에 할당됩니다. 다음 코드에서

```
struct mybitfields
{
    unsigned short a : 4;
    unsigned short b : 5;
    unsigned short c : 7;
} test;

int main( void );
{
    test.a = 2;
    test.b = 31;
    test.c = 0;
}
```

비트는 다음과 같이 정렬됩니다.

```
00000001 11110010
cccccccb bbbbaaaa
```

8086 프로세서 제품군은 높은 바이트 앞에 낮은 바이트의 정수 값을 저장하므로 `0x01F2`보다 높은 정수는 `0xF2`와 `0x01`로 실제 메모리에 저장됩니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[구조체 선언](../c-language/structure-declarations.md)
