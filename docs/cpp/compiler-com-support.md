---
title: 컴파일러 COM 지원
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 421930088dcbf9762d50b5af37d994b9008890eb
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606382"
---
# <a name="compiler-com-support"></a>컴파일러 COM 지원

## <a name="microsoft-specific"></a>Microsoft 전용

Microsoft C++ 컴파일러는 COM (구성 요소 개체 모델) 형식 라이브러리를 직접 읽고 해당 콘텐츠를 컴파일에 C++ 포함할 수 있는 소스 코드로 변환할 수 있습니다. 데스크톱 응용 프로그램의 경우 클라이언트 쪽에서 COM 프로그래밍을 용이 하 게 하기 위해 언어 확장을 사용할 수 있습니다.

[#Import 전처리기 지시문](../preprocessor/hash-import-directive-cpp.md)을 사용 하면 컴파일러는 형식 라이브러리를 읽고 COM 인터페이스를 클래스로 설명 하 C++ 는 헤더 파일로 변환할 수 있습니다. `#import` 특성 집합은 결과 형식 라이브러리 헤더 파일에 대한 콘텐츠를 사용자가 제어하는 데 사용할 수 있습니다.

[__Declspec](../cpp/declspec.md) 확장 특성 [uuid](../cpp/uuid-cpp.md) 를 사용 하 여 COM 개체에 guid (globally unique identifier)를 할당할 수 있습니다. [__Uuidof](../cpp/uuidof-operator.md) 키워드는 COM 개체와 연결 된 GUID를 추출 하는 데 사용할 수 있습니다. 또 다른 **__declspec** 특성 [속성](../cpp/property-cpp.md)은 `get` COM 개체의 데이터 멤버에 대 한 및 `set` 메서드를 지정 하는 데 사용할 수 있습니다.

COM 집합은 `VARIANT` 및 `BSTR` 형식을 지원 하 고, 스마트 포인터를 구현 하 고,에서 `_com_raise_error`throw 되는 오류 개체를 캡슐화 하기 위해 전역 함수 및 클래스를 지원 합니다.

- [컴파일러 COM 전역 함수](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[컴파일러 COM 지원 클래스](../cpp/compiler-com-support-classes.md)<br/>
[컴파일러 COM 전역 함수](../cpp/compiler-com-global-functions.md)
