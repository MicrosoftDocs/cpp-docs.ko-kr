---
description: '자세히 알아보기: 입력/출력 스트림'
title: Input-Output 스트림
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: fd261bfdac5b9ce95b04430e9d77c6bd1df56c7d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231643"
---
# <a name="inputoutput-streams"></a>입력/출력 스트림

`basic_iostream`헤더 파일에 정의 된는 \<istream> 입력 및 출력 문자 기반 i/o 스트림을 모두 처리 하는 개체에 대 한 클래스 템플릿입니다.

의 문자 관련 특수화를 정의 하는 두 가지 형식 정의를 사용 하 여 `basic_iostream` 코드를 보다 쉽게 읽을 수 있습니다. `iostream` (헤더 파일과 혼동 하지 않음)는을 기반으로 하는 i/o 스트림입니다 .는을 기반으로 하는 i/o \<iostream> `basic_iostream<char>` `wiostream` 스트림입니다 `basic_iostream<wchar_t>` .

자세한 내용은 [basic_iostream 클래스](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md) 및 [wiostream](../standard-library/basic-iostream-class.md)을 참조하세요.

`basic_iostream`에서 파생은 클래스 템플릿 `basic_fstream`이며, 파일 간에 문자 데이터를 스트림하는 데 사용됩니다.

`basic_fstream`의 문자 관련 특수화를 제공하는 형식 정의도 있습니다. 이는을 기반으로 하는 파일 i/o 스트림 이며을 기반으로 하는 파일 i/o 스트림입니다 `fstream` **`char`** `wfstream` **`wchar_t`** . 자세한 내용은 [basic_fstream 클래스](../standard-library/basic-fstream-class.md), [fstream](../standard-library/basic-fstream-class.md) 및 [wfstream](../standard-library/basic-fstream-class.md)을 참조하세요. 이러한 형식 정의를 사용 하려면 헤더 파일을 포함 해야 합니다 \<fstream> .

> [!NOTE]
> `basic_fstream` 개체를 사용하여 파일 I/O를 수행하는 경우 기본 버퍼에 읽기 및 쓰기를 위해 별도로 지정된 위치가 포함되어 있어도 현재 입력 및 현재 출력 위치가 함께 연결되어 있으므로 일부 데이터를 읽으면 출력 위치가 이동합니다.

클래스 템플릿 `basic_stringstream` 및 해당 공용 특수화 `stringstream`은 I/O 스트림 개체를 사용하여 문자 데이터를 삽입하고 추출하는 데 자주 사용됩니다. 자세한 내용은 [basic_stringstream 클래스](../standard-library/basic-stringstream-class.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[stringstream](../standard-library/basic-stringstream-class.md)\
[basic_stringstream 클래스](../standard-library/basic-stringstream-class.md)\
[\<sstream>](../standard-library/sstream.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)
