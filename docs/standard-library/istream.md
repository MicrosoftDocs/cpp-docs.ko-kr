---
description: '자세히 알아보기: &lt; istream&gt;'
title: '&lt;istream&gt;'
ms.date: 11/04/2016
f1_keywords:
- istream/std::<istream>
- <istream>
- std::<istream>
helpviewer_keywords:
- istream header
ms.assetid: efcf24e4-05d1-4719-ab0b-9e7ebe845d89
ms.openlocfilehash: c897441eef935cd6ef5a8b4e9f4676d06a57e1af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97277819"
---
# <a name="ltistreamgt"></a>&lt;istream&gt;

Iostreams의 추출 중재 클래스 템플릿 및 삽입과 추출를 모두 중재 하는 클래스 템플릿 basic_iostream을 정의 basic_istream 합니다. 헤더에서 관련 조작자도 정의합니다. 이 헤더 파일은 일반적으로 다른 iostreams 헤더에 의해 포함되며, 직접 포함해야 하는 경우는 거의 없습니다.

## <a name="syntax"></a>Syntax

```cpp
#include <istream>
```

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[iostream](../standard-library/istream-typedefs.md#iostream)|`basic_iostream`에서 특수화 된 형식 **`char`** 입니다.|
|[istream](../standard-library/istream-typedefs.md#istream)|`basic_istream`에서 특수화 된 형식 **`char`** 입니다.|
|[wiostream](../standard-library/istream-typedefs.md#wiostream)|**wchar** 에서 특수화된 `basic_iostream` 형식입니다.|
|[wistream](../standard-library/istream-typedefs.md#wistream)|**wchar** 에서 특수화된 `basic_istream` 형식입니다.|

### <a name="manipulators"></a>조작자

|Name|설명|
|-|-|
|[ws](../standard-library/istream-functions.md#ws)|스트림의 공백을 건너뜁니다.|
|[스왑을](../standard-library/istream-functions.md#istream_swap)|두 스트림 개체를 교환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자>>](../standard-library/istream-operators.md#op_gt_gt)|스트림에서 문자 및 문자열을 추출합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_iostream](../standard-library/basic-iostream-class.md)|입력과 출력을 둘 다 수행할 수 있는 스트림 클래스입니다.|
|[basic_istream](../standard-library/basic-istream-class.md)|클래스 템플릿은 char_type 형식 요소가 포함 된 스트림 버퍼에서 요소 및 인코드된 개체의 추출을 제어 하는 개체를 설명 합니다 `Elem` . 해당 문자 [](../standard-library/basic-ios-class.md#char_type)특성은 클래스 (traits_type 라고도 함)에 의해 결정 됩니다 `Tr` . [](../standard-library/basic-ios-class.md#traits_type)|

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
