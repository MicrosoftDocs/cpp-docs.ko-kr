---
title: _com_ptr_t 추출기 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::operatorInterface&
- _com_ptr_t::operatorbool
- _com_ptr_t::operator->
- _com_ptr_t::operator*
dev_langs:
- C++
helpviewer_keywords:
- operator Interface& [C++]
- '* operator [C++], with specific objects'
- operator& [C++]
- operator* [C++]
- -> operator [C++], with specific objects
- '& operator [C++], with specific objects'
- operator Interface* [C++]
- operator * [C++]
- operator->
- operator bool
- extractors, _com_ptr_t class
- extractors [C++]
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0bfe0cdb5ea9dd524f2e81fcb2719bf40001758
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37944602"
---
# <a name="comptrt-extractors"></a>_com_ptr_t Extractors
**Microsoft 전용**  
  
 캡슐화된 COM 인터페이스 포인터를 추출합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## <a name="remarks"></a>설명  
  
-   **연산자 인터페이스\***  NULL 일 수 있는 캡슐화 된 인터페이스 포인터를 반환 합니다.  
  
-   **연산자 인터페이스 &** 캡슐화 된 인터페이스 포인터에 대 한 참조를 반환 하 고 포인터가 null 인 경우 오류가 발생 합니다.  
  
-   **연산자\***  는 스마트 포인터 개체가 역참조 시 실제로 캡슐화 된 인터페이스인 것 처럼 작동 하도록 허용 합니다.  
  
-   **operator->** 는 스마트 포인터 개체가 역참조 시 실제로 캡슐화 된 인터페이스인 것 처럼 작동 하도록 허용 합니다.  
  
-   **연산자 &** NULL으로 바꿔 모든 캡슐화 된 인터페이스 포인터를 해제 하 고 캡슐화 된 포인터의 주소를 반환 합니다. 이렇게 하면 포함 된 함수를 주소로 전달 되는 스마트 포인터는 *out* 인터페이스 포인터를 반환 하는 매개 변수입니다.  
  
-   **연산자 bool** 스마트 포인터 개체를 조건식에 사용할 수 있습니다. 이 연산자는 포인터가 NULL이 아닌 경우 TRUE를 반환 합니다.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [_com_ptr_t 클래스](../cpp/com-ptr-t-class.md)