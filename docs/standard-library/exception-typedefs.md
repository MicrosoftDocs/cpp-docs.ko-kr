---
title: "&lt;exception&gt; 형식 정의 | Microsoft 문서"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- exception/std::exception_ptr
- exception/std::terminate_handler
- exception/std::unexpected_handler
ms.assetid: 2a338480-35e2-46f7-b223-52d4e84a5768
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 24f4fc5d30a95d55b5a4241d9c70eca31255fc18
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="ltexceptiongt-typedefs"></a>&lt;exception&gt; 형식 정의
||||  
|-|-|-|  
|[exception_ptr](#exception_ptr)|[terminate_handler](#terminate_handler)|[unexpected_handler](#unexpected_handler)|  
  
##  <a name="exception_ptr"></a>  exception_ptr  
 예외에 대한 포인터를 설명하는 형식입니다.  
  
```cpp  
typedef unspecified exception_ptr;
```  
  
### <a name="remarks"></a>설명  
 `exception_ptr` 형식을 구현하는 데 사용되는 지정되지 않은 내부 클래스입니다.  
  
 `exception_ptr` 개체를 사용하여 현재 예외 또는 사용자 지정 예외의 인스턴스를 참조합니다. Microsoft 구현에서 예외가 [EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082) 구조체에 의해 표시됩니다. 각 `exception_ptr` 개체에는 예외를 나타내는 `EXCEPTION_RECORD` 구조체의 복사본을 가리키는 예외 참조 필드가 포함됩니다.  
  
 `exception_ptr` 변수를 선언할 때 변수는 예외와 관련되지 않습니다. 즉, 해당 예외 참조 필드는 NULL입니다. 이러한 `exception_ptr` 개체를 *null exception_ptr*라고 합니다.  
  
 `current_exception` 또는 `make_exception_ptr` 함수를 사용하여 `exception_ptr` 개체에 예외를 지정합니다. `exception_ptr` 변수에 예외를 할당하면, 변수 예외 참조 필드는 예외 복사본을 가리킵니다. 메모리가 부족하여 예외를 복사할 수 없는 경우 예외 참조 필드는 [std::bad_alloc](../standard-library/bad-alloc-class.md) 예외의 복사본을 가리킵니다. `current_exception` 또는 `make_exception_ptr` 함수가 다른 이유로 예외를 복사할 수 없는 경우 **terminate** CRT 함수를 호출하여 현재 프로세스를 종료합니다.  
  
 그 이름에도 불구하고 `exception_ptr` 개체 자체는 포인터가 아닙니다. 포인터 의미 체계를 준수하지 않으며 포인터 멤버 액세스(`->`) 또는 간접 참조(*) 연산자와 함께 사용될 수 없습니다. `exception_ptr` 개체에는 공용 데이터 멤버 또는 멤버 함수가 없습니다.  
  
 **비교:**  
  
 등호(`==`) 및 부등호(`!=`) 연산자를 사용하여 두 개의 `exception_ptr` 개체를 비교할 수 있습니다. 연산자는 예외를 나타내는 `EXCEPTION_RECORD` 구조의 이진 값(비트 패턴)을 비교하지 않습니다. 대신, 연산자는 `exception_ptr` 개체의 예외 참조 필드 주소를 비교합니다. 따라서 null `exception_ptr`과 NULL 값이 동일한 것으로 비교됩니다.  
  
##  <a name="terminate_handler"></a>  terminate_handler  
 `terminate_handler`로 사용하는 데 적합한 함수에 대한 포인터를 설명하는 형식입니다.  
  
```
typedef void (*terminate_handler)();
```  
  
### <a name="remarks"></a>설명  
 이 형식은 종료 처리기로 사용하는 데 적합한 함수의 포인터에 대해 설명합니다.  
  
### <a name="example"></a>예  
  `terminate_handler` 사용에 대한 예제는 [set_terminate](../standard-library/exception-functions.md#set_terminate)를 참조하세요.  
  
##  <a name="unexpected_handler"></a>  unexpected_handler  
 이 형식은 `unexpected_handler`로 사용하는 데 적합한 함수에 대한 포인터를 설명합니다.  
  
```
typedef void (*unexpected_handler)();
```  
  
### <a name="example"></a>예  
  `unexpected_handler` 사용에 대한 예제는 [set_unexpected](../standard-library/exception-functions.md#set_unexpected)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [\<exception>](../standard-library/exception.md)



