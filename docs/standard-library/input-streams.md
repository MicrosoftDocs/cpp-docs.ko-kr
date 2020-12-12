---
description: '자세히 알아보기: 입력 스트림'
title: Input Streams
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: f7e6d41b904b2d28893637681e3c751d24aef441
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323964"
---
# <a name="input-streams"></a>Input Streams

입력 스트림 개체는 바이트의 소스입니다. 세 가지 가장 중요한 입력 스트림 클래스는 [istream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md) 및 [istringstream](../standard-library/basic-istringstream-class.md)입니다.

`istream` 클래스는 순차적 텍스트 모드 입력에 가장 적합합니다. 버퍼링되거나 버퍼링되지 않은 작업을 위해 `istream` 클래스의 개체를 구성할 수 있습니다. 기본 클래스 `ios`의 모든 기능이 `istream`에 포함됩니다. `istream` 클래스에서는 개체를 거의 생성하지 않습니다. 대신 미리 정의된 `cin` 개체를 일반적으로 사용하는데, 이 개체는 실제로 [ostream](../standard-library/basic-ostream-class.md) 클래스의 개체입니다. 경우에 따라 프로그램 시작 후 다른 스트림 개체에 `cin`을 할당할 수 있습니다.

`ifstream` 클래스는 디스크 파일 입력을 지원합니다. 입력 전용 디스크 파일이 필요한 경우 `ifstream` 클래스의 개체를 생성하세요. 이진 또는 텍스트 모드 데이터를 지정할 수 있습니다. 생성자에서 파일 이름을 지정하면 개체가 생성될 때 파일이 자동으로 열립니다. 그렇지 않으면 기본 생성자를 호출한 후 `open` 함수를 사용할 수 있습니다. 많은 서식 옵션 및 멤버 함수가 `ifstream` 개체에 적용됩니다. 기본 클래스 `ios` 및 `istream`의 모든 기능이 `ifstream`에 포함됩니다.

라이브러리 함수 `sscanf_s`와 같이 `istringstream` 클래스는 메모리 내 문자열에서 입력을 지원합니다. null 종결자가 있는 문자 배열에서 데이터를 추출하려면 문자열을 할당하고 초기화한 다음 `istringstream` 클래스의 개체를 생성합니다.

## <a name="in-this-section"></a>섹션 내용

[입력 스트림 개체 생성](../standard-library/constructing-input-stream-objects.md)

[추출 연산자 사용](../standard-library/using-extraction-operators.md)

[추출 오류 테스트](../standard-library/testing-for-extraction-errors.md)

[입력 스트림 조작자](../standard-library/input-stream-manipulators.md)

[입력 스트림 멤버 함수](../standard-library/input-stream-member-functions.md)

[고유 클래스에 대해 >> 연산자 오버로드](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>참고 항목

[iostream 프로그래밍](../standard-library/iostream-programming.md)
