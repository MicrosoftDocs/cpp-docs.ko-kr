---
description: '자세한 정보: 컴파일러 COM 지원 클래스'
title: 컴파일러 COM 지원 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 6d800d9b-b902-4033-9639-740a30b06f88
ms.openlocfilehash: e2f921e9c3ebe759109d741630afe56f6af30bbc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344707"
---
# <a name="compiler-com-support-classes"></a>컴파일러 COM 지원 클래스

**Microsoft 전용**

표준 클래스는 COM 형식 중 일부를 지원하는 데 사용됩니다. 클래스는 \<comdef.h> 및 형식 라이브러리에서 생성 된 헤더 파일에 정의 됩니다.

|클래스|목적|
|-----------|-------------|
|[_bstr_t](../cpp/bstr-t-class.md)|`BSTR` 형식을 래핑하여 유용한 연산자와 메서드를 제공합니다.|
|[_com_error](../cpp/com-error-class.md)|대부분의 오류에서 [_com_raise_error](../cpp/com-raise-error.md) 의해 throw 되는 오류 개체를 정의 합니다.|
|[_com_ptr_t](../cpp/com-ptr-t-class.md)|COM 인터페이스 포인터를 캡슐화 하 고, 및에 대 한 필수 호출을 자동화 합니다 `AddRef` `Release` `QueryInterface` .|
|[_variant_t](../cpp/variant-t-class.md)|`VARIANT` 형식을 래핑하여 유용한 연산자와 메서드를 제공합니다.|

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 COM 지원](../cpp/compiler-com-support.md)<br/>
[컴파일러 COM 전역 함수](../cpp/compiler-com-global-functions.md)<br/>
[C++ 언어 참조](../cpp/cpp-language-reference.md)
