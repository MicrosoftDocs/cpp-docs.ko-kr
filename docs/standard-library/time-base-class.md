---
title: "time_base 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- locale/std::time_base
dev_langs:
- C++
helpviewer_keywords:
- time_base class
ms.assetid: 9ae37f0b-9a42-496e-9870-3d9b71bab8fb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cc7ed644d7c66ea7e3ca49b6d403b17535fa3eb9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="timebase-class"></a>time_base 클래스
이 클래스는 템플릿 클래스 time_get의 패싯에 대한 기본 클래스로 사용되며 열거형 **dateorder**와 이 형식의 여러 상수만 정의합니다.  
  
## <a name="syntax"></a>구문  
  
```
class time_base : public locale::facet {
public:
    enum dateorder {no_order,
    dmy,
 mdy,
    ymd,
 ydm};
    time_base(
 size_t _Refs = 0)
 ~time_base();

};
```  
  
## <a name="remarks"></a>설명  
 각 상수는 날짜의 구성 요소 순서를 지정하는 다른 방식을 지정합니다. 상수는 다음과 같습니다.  
  
- **no_order**: 특정 순서를 지정하지 않습니다.  
  
- **dmy**: 2/12/1979와 같이 일, 월, 년 순서를 지정합니다.  
  
- **mdy**: 12/2/1979와 같이 월, 일, 년 순서를 지정합니다.  
  
- **ymd**: 1979/12/2와 같이 년, 월, 일 순서를 지정합니다.  
  
- **ydm**: 1979: 2/12와 같이 년, 일, 월 순서를 지정합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<locale>  
  
 **네임스페이스:** std  
  
## <a name="see-also"></a>참고 항목  
 [C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)



