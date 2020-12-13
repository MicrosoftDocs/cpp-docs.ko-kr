---
description: '자세한 정보: 출력 스트림'
title: Output Streams
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: ec09a6bee1bcd2f329522b61950f3d051fb57889
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340868"
---
# <a name="output-streams"></a>Output Streams

출력 스트림 개체는 바이트에 대한 대상입니다. 가장 중요한 3개 출력 스트림 클래스는 `ostream`, `ofstream`, `ostringstream`입니다.

`ostream` 클래스는 파생 클래스 `basic_ostream`을 통해 미리 정의된 스트림 개체를 지원합니다.

- `cout` 표준 출력

- `cerr` 표준 오류(버퍼링 제한)

- `clog`(`cerr`과 비슷하지만 전체 버퍼링 가능)

개체는 `ostream`에서 구성되는 경우가 거의 없으며 일반적으로는 미리 정의된 개체가 사용됩니다. 경우에 따라 프로그램 시작 후 미리 정의된 개체를 다시 할당할 수 있습니다. 버퍼링되거나 버퍼링되지 않는 작업용으로 구성할 수 있는 `ostream` 클래스는 순차적 텍스트 모드 출력에 가장 적합합니다. 기본 클래스 `ios`의 모든 기능이 `ostream`에 포함됩니다. `ostream` 클래스의 개체를 생성하는 경우에는 생성자에 대한 `streambuf` 개체를 지정해야 합니다.

`ofstream` 클래스는 디스크 파일 출력을 지원합니다. 출력 전용 디스크가 필요한 경우에는 클래스가 `ofstream`인 개체를 생성합니다. `ofstream` 개체를 생성할 때나 개체의 `open` 구성원 함수를 호출할 때 `ofstream` 개체가 이진 또는 텍스트 모드 데이터를 허용하는지를 지정할 수 있습니다. `ofstream` 개체에는 대부분의 서식 옵션 및 구성원 함수가 적용되며, `ios` 및 `ostream` 기본 클래스의 모든 기능이 포함됩니다.

생성자에서 파일 이름을 지정하면 개체가 생성될 때 파일이 자동으로 열립니다. 그렇지 않으면 기본 생성자를 호출한 후 `open` 구성원 함수를 사용할 수 있습니다.

런타임 함수 `sprintf_s`와 같이 `ostringstream` 클래스는 메모리 내 문자열로의 출력을 지원합니다. I/O 스트림 서식을 사용하여 메모리에서 문자열을 만들려면 클래스 `ostringstream`의 개체를 생성합니다.

## <a name="in-this-section"></a>섹션 내용

[출력 스트림 개체 생성](../standard-library/constructing-output-stream-objects.md)

[삽입 연산자 사용 및 형식 제어](../standard-library/using-insertion-operators-and-controlling-format.md)

[출력 파일 스트림 멤버 함수](../standard-library/output-file-stream-member-functions.md)

[버퍼링 효과](../standard-library/effects-of-buffering.md)

[이진 출력 파일](../standard-library/binary-output-files.md)

[클래스에 대 한 << 연산자 오버 로드](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[인수 없이 고유 조작자 작성](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>참고 항목

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream](../standard-library/basic-ostringstream-class.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)
