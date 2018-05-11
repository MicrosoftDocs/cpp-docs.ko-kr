---
title: C++ 프로그램 시작 및 종료 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- C++ Standard Library, program startup and termination
- terminating execution
- Function Main procedures
- control text streams
- startup code, and C++ program termination
- main function, program startup
ms.assetid: f72c8f76-f507-4ddd-a270-7b60f4fed625
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f781df914384b553c53e5c42fe16d4c74c9ef99d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="c-program-startup-and-termination"></a>C++ Program Startup 및 Termination

C++ 프로그램은 여기에 설명된 몇 가지 추가 작업 외에도 C 프로그램이 프로그램 시작 시와 프로그램 종료 시에 수행하는 것과 동일한 작업을 수행합니다.

대상 환경에서 `main` 함수를 호출하기 전과 정적 기간이 있는 모든 개체에서 지정한 모든 상수 초기 값을 저장한 후에 프로그램은 이러한 정적 개체에 대해 나머지 생성자를 실행합니다. 실행 순서가 변환 단위 간에 지정되지 않지만, 그럼에도 불구하고 이러한 정적 생성자에서 사용하기 위해 일부 [iostreams](../standard-library/iostreams-conventions.md) 개체가 제대로 초기화된다고 추정할 수 있습니다. 이러한 텍스트 스트림 제어는 다음과 같습니다.

- [cin](../standard-library/iostream.md#cin) - 표준 입력의 경우

- [cout](../standard-library/iostream.md#cout) - 표준 출력의 경우

- [cerr](../standard-library/iostream.md#cerr) - 버퍼링되지 않은 표준 오류 출력의 경우

- [clog](../standard-library/iostream.md#clog) - 버퍼링된 표준 오류 출력의 경우

또한 프로그램 종료 중 정적 개체에 대해 호출된 소멸자 내에서도 이러한 개체를 사용할 수 있습니다.

C에서와 마찬가지로 `main`에서 반환하거나 `exit`를 호출하면 `atexit`를 통해 등록된 모든 함수가 레지스트리의 역순으로 호출됩니다. 이렇게 등록된 함수에서 throw된 예외는 `terminate`를 호출합니다.

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
