---
description: '자세한 정보: &lt; a m&gt;'
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 98fe18306d50a9d6f1f8a360d4d29b6e865f6328
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324267"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

외부 파일에 저장된 시퀀스에 대한 Iostreams 작업을 지원하는 여러 클래스를 정의합니다.

## <a name="syntax"></a>Syntax

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|`basic_filebuf`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.|
|[a m](../standard-library/fstream-typedefs.md#fstream)|`basic_fstream`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|`basic_ifstream`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|`basic_ofstream`템플릿 매개 변수에서 특수화 된 형식 **`char`** 입니다.|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|`basic_fstream`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|`basic_ifstream`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|`basic_ofstream`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|`basic_filebuf`템플릿 매개 변수에서 특수화 된 형식 **`wchar_t`** 입니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|클래스 템플릿에서는 형식 요소의 전송을 제어 하는 스트림 버퍼에 대해 설명 합니다 `Elem` . 해당 문자 특성은 `Tr` 외부 파일에 저장 된 요소의 시퀀스로 결정 됩니다.|
|[basic_fstream](../standard-library/basic-fstream-class.md)|클래스 템플릿은 [](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> `Elem` 문자 특성이 클래스에 의해 결정 되는 형식의 요소가 포함 된 basic_filebuf 클래스의 스트림 버퍼를 사용 하 여 요소 및 인코드된 개체의 삽입 및 추출을 제어 하는 개체를 설명 합니다 `Tr` .|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|클래스 템플릿은 [](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> `Elem` 문자 특성이 클래스에 의해 결정 되는 형식의 요소를 사용 하 여 basic_filebuf 클래스의 스트림 버퍼에서 요소 및 인코드된 개체의 추출을 제어 하는 개체를 설명 합니다 `Tr` .|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|클래스 템플릿은 [](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> `Elem` 문자 특성이 클래스에 의해 결정 되는 형식의 요소가 포함 된 basic_filebuf 클래스의 스트림 버퍼에 요소 및 인코드된 개체 삽입을 제어 하는 개체를 설명 합니다 `Tr` .|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
