---
description: '자세한 정보: iostreams 규칙'
title: iostreams 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 3676c6aa14a5ebac1d39ed50821449caa7313e40
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231396"
---
# <a name="iostreams-conventions"></a>iostreams 규칙

iostreams 헤더는 텍스트와 인코드된 형식 간 변환 및 외부 파일에 대한 입력과 출력을 지원합니다.

[\<fstream>](../standard-library/fstream.md)\
[\<iomanip>](../standard-library/iomanip.md)\
[\<ios>](../standard-library/ios.md)\
[\<iosfwd>](../standard-library/iosfwd.md)\
[\<iostream>](../standard-library/iostream.md)\
[\<istream>](../standard-library/istream.md)\
[\<ostream>](../standard-library/ostream.md)\
[\<sstream>](../standard-library/sstream.md)\
[\<streambuf>](../standard-library/streambuf.md)\
[\<strstream>](../standard-library/strstream.md)

Iostreams을 가장 간단 하 게 사용 하려면 헤더를 포함 해야 합니다 [\<iostream>](../standard-library/iostream.md) . 그런 다음 [cin](../standard-library/iostream.md#cin) 또는 [wcin](../standard-library/iostream.md#wcin)에서 값을 추출하여 표준 입력을 읽을 수 있습니다. 이 작업을 수행하는 규칙은 [basic_istream 클래스](../standard-library/basic-istream-class.md)에 대한 설명에 간략하게 나와 있습니다. [cout](../standard-library/iostream.md#cout) 또는 [wcout](../standard-library/iostream.md#wcout)에 값을 삽입하여 표준 출력을 쓸 수도 있습니다. 이 작업을 수행하는 규칙은 [basic_ostream 클래스](../standard-library/basic-ostream-class.md)에 대한 설명에 간략하게 나와 있습니다. 추출기와 삽입기에 공통된 형식 제어는 [basic_ios 클래스](../standard-library/basic-ios-class.md)에 의해 관리됩니다. 개체 추출 및 삽입을 가장하여 이 형식 정보를 조작하는 것이 여러 조작자의 영역입니다.

에 선언 된 클래스를 사용 하 여 이름별로 연 파일에 대해 동일한 iostreams 작업을 수행할 수 있습니다 [\<fstream>](../standard-library/fstream.md) . Iostreams 클래스 [basic_string](../standard-library/basic-string-class.md)클래스의 개체 간을 변환 하려면에 선언 된 클래스를 사용 [\<sstream>](../standard-library/sstream.md) 합니다. C 문자열을 사용 하 여 동일한 작업을 수행 하려면에 선언 된 클래스를 사용 [\<strstream>](../standard-library/strstream.md) 합니다.

나머지 헤더는 지원 서비스를 제공하는데, 이 서비스는 일반적으로 iostreams 클래스의 고급 사용자만 직접적인 관심을 보입니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
