---
description: '자세히 알아보기: 기본 형식 (c + +/CX)'
title: 기본 형식(C++/CX)
ms.date: 01/22/2017
ms.assetid: c9f82907-25f2-440b-91d6-afb8dbd46ea6
ms.openlocfilehash: 40e0a849d0b838f53ddaea26c8993dcfe625ed5d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321007"
---
# <a name="fundamental-types-ccx"></a>기본 형식(C++/CX)

표준 c + +/CX는 표준 c + + 기본 제공 형식 외에도 표준 c + + 형식에 매핑되는 Windows 런타임 기본 형식에 대 한 형식 정의를 제공 하 여 Windows 런타임 아키텍처에서 정의 된 형식 시스템을 지원 합니다. C + +/CX는 부울, 문자 및 숫자 기본 형식을 구현 합니다. 이러한 형식 정의는 명시적으로 지정할 필요가 없는 `default` 네임스페이스에서 정의됩니다. 또한 c + +/CX는 특정 Windows 런타임 형식 및 인터페이스에 대 한 래퍼 및 구체적인 구현을 제공 합니다.

## <a name="boolean-and-character-types"></a>부울 및 문자 형식

다음 표에는 기본 제공 부울 및 문자 형식과 표준 C++ 해당 항목이 나와 있습니다.

|네임스페이스|C + +/CX 이름|정의|표준 C++ 이름|값의 범위|
|---------------|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|플랫폼|부울|8비트 부울 값입니다.|bool|**`true`** (0이 아님) 및 **`false`** (0)|
|기본값|char16|유니코드(UTF-16) 코드 포인트를 나타내는 숫자가 아닌 16비트 값입니다.|wchar_t<br /><br /> 또는<br /><br /> L'c'|(유니코드 표준으로 지정됨)|

## <a name="numeric-types"></a>숫자 유형

다음 표에는 기본 제공 숫자 형식이 나와 있습니다. 숫자 형식은 `default` 네임스페이스에서 선언되고 해당 C++ 기본 제공 형식의 형식 정의입니다. 일부 c + + 기본 제공 형식 (예: long)은 Windows 런타임에서 지원 되지 않습니다. 일관성과 명확성을 위해 c + +/CX 이름을 사용 하는 것이 좋습니다.

|C + +/CX 이름|정의|표준 C++ 이름|값의 범위|
|-----------------------------------------------------------------------|----------------|-------------------------|---------------------|
|int8|8비트 부호 있는 숫자 값입니다.|signed char|-128 ~ 127|
|uint8|8비트 부호 없는 숫자 값입니다.|unsigned char|0 ~ 255|
|int16|16비트 부호 있는 정수입니다.|short|-32768 ~ 32767|
|uint16|16비트 부호 없는 정수입니다.|unsigned short|0 ~ 65,535|
|int32|32비트 부호 있는 정수입니다.|int|-2147483648 ~ 2147483647|
|uint32|32비트 부호 없는 정수입니다.|부호 없는 정수|0 ~ 4,294,967,295|
|int64|64비트 부호 있는 정수입니다.|long long 또는-__int64|-9223372036854, 775808 ~ 9223372036854775807|
|uint64|64비트 부호 없는 정수입니다.|부호 없는 long long 또는-unsigned __int64|0 ~ 18,446,744,073,709,551,615|
|float32|32비트 IEEE 754 부동 소수점 숫자입니다.|float|3.4E+/-38(7개의 자릿수)|
|float64|64비트 IEEE 754 부동 소수점 숫자입니다.|double|1.7E+/-308(15개의 자릿수)|

## <a name="windows-runtime-types"></a>Windows 런타임 형식

다음 표에는 Windows 런타임 아키텍처에서 정의 되 고 c + +/CX에 기본 제공 되는 몇 가지 추가 형식이 나와 있습니다. 개체 및 문자열은 참조 형식입니다. 기타 항목은 값 형식입니다. 이러한 형식은 모두 `Platform` 네임스페이스에서 선언됩니다. 전체 목록은 [Platform namespace](../cppcx/platform-namespace-c-cx.md)를 참조하세요.

|Name|정의|
|----------|----------------|
|개체|모든 Windows 런타임 형식을 나타냅니다.|
|String|텍스트를 나타내는 일련의 문자입니다.|
|Rect|사각형의 위치와 크기를 나타내는 네 부동 소수점 숫자 집합입니다.|
|SizeT|높이와 너비를 지정하는 부동 소수점 숫자의 순서가 지정된 쌍입니다.|
|Point|2차원 평면에서 점을 정의하는 부동 소수점 X 좌표 및 Y 좌표의 순서가 지정된 쌍입니다.|
|Guid|고유 식별자로 사용되는 128비트 숫자가 아닌 값입니다.|
|UIntPtr|내부용 으로만 사용 됩니다. 포인터로 사용 되는 부호 없는 64 비트 값입니다.|
|IntPtr|내부용 으로만 사용 됩니다.  포인터로 사용 되는 부호 있는 64 비트 값입니다.|

## <a name="see-also"></a>참고 항목

[유형 시스템](../cppcx/type-system-c-cx.md)
