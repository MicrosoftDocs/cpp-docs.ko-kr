---
description: '자세한 정보: &lt; ostream&gt;'
title: '&lt;ostream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ostream>
- ostream/std::<ostream>
- std::<ostream>
helpviewer_keywords:
- ostream header
ms.assetid: 90c3b6fb-57cd-4ae7-99b8-8512f24a67d2
ms.openlocfilehash: 3b17ff221e08b9fc709f1d2c32c5862f6075e451
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193034"
---
# <a name="ltostreamgt"></a>&lt;ostream&gt;

Iostreams에 대 한 삽입을 중재 클래스 템플릿 [basic_ostream](../standard-library/basic-ostream-class.md)를 정의 합니다. 헤더에서 여러 관련 조작자도 정의합니다. 이 헤더는 일반적으로 다른 iostreams 헤더에 의해 포함되며, 직접 포함해야 하는 경우는 거의 없습니다.

## <a name="syntax"></a>Syntax

```cpp
#include <ostream>
```

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[ostream](../standard-library/ostream-typedefs.md#ostream)|에서 `basic_ostream` 특수화 되 고 특수화 된에서 형식을 **`char`** 만듭니다 `char_traits` **`char`** .|
|[wostream](../standard-library/ostream-typedefs.md#wostream)|에서 `basic_ostream` 특수화 되 고 특수화 된에서 형식을 **`wchar_t`** 만듭니다 `char_traits` **`wchar_t`** .|

### <a name="manipulators"></a>조작자

|Name|설명|
|-|-|
|[endl](../standard-library/ostream-functions.md#endl)|줄을 종료하고 버퍼를 플러시합니다.|
|[종료](../standard-library/ostream-functions.md#ends)|문자열을 종료합니다.|
|[플러시가](../standard-library/ostream-functions.md#flush)|버퍼를 플러시합니다.|
|[스왑을](../standard-library/ostream-functions.md#swap)|왼쪽 `basic_ostream` 개체 매개 변수의 값을 오른쪽 `basic_ostream` 개체 매개 변수의 값으로 교환합니다.|

### <a name="operators"></a>연산자

|연산자|설명|
|-|-|
|[연산자<<](../standard-library/ostream-operators.md#op_lt_lt)|스트림에 다양한 형식을 씁니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_ostream](../standard-library/basic-ostream-class.md)|클래스 템플릿은 스트림 버퍼에 요소 및 인코드된 개체 삽입을 제어 하는 개체를 설명 합니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
