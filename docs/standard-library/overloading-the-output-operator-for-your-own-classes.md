---
title: "고유 클래스에 대해 &lt;&lt; 오버로드 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- operator<<, overloading for your own classes
- operator <<, overloading for your own classes
ms.assetid: ad1d2c49-d84e-48a8-9c09-121f28b10bf0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: eed1ff7819e93236e6baad192887494e6f956ac2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="overloading-the-ltlt-operator-for-your-own-classes"></a>고유 클래스에 대해 &lt;&lt; 연산자 오버로드
출력 스트림은 표준 형식에 대해 삽입(`<<`) 연산자를 사용합니다. 고유 클래스에 대해 `<<` 연산자를 오버로드할 수도 있습니다.  
  
## <a name="example"></a>예  
 `write` 함수 예제에서는 `Date` 구조체의 사용법을 살펴보았습니다. 이 예제의 C++ 클래스에 사용하기에 적합한 항목은 날짜입니다. 데이터 구성원(월, 일, 년)가 뷰에서 숨겨지기 때문입니다. 출력 스트림은 이러한 구조체를 표시하기 위한 논리적 대상이라 할 수 있습니다. 아래 코드에서는 `cout` 개체를 사용하여 날짜를 표시합니다.  
  
```  
Date dt(1, 2, 92);

cout <<dt;  
```  
  
 삽입 연산자 뒤에 `Date` 개체를 포함할 수 있도록 `cout`를 가져오려면 왼쪽의 `ostream` 개체와 오른쪽의 `Date`를 인식하도록 삽입 연산자를 오버로드합니다. 오버로드된 `<<` 연산자 함수는 `Date` 개체 내의 개인 데이터에 액세스할 수 있도록 `Date` 클래스의 friend로 선언해야 합니다.  
  
```  
// overload_date.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Date  
{  
    int mo, da, yr;  
public:  
    Date(int m, int d, int y)  
    {  
        mo = m; da = d; yr = y;  
    }  
    friend ostream& operator<<(ostream& os, const Date& dt);  
};  
  
ostream& operator<<(ostream& os, const Date& dt)  
{  
    os << dt.mo << '/' << dt.da << '/' << dt.yr;  
    return os;  
}  
  
int main()  
{  
    Date dt(5, 6, 92);  
    cout << dt;  
}  
```  
  
```Output  
5/6/92  
```  
  
## <a name="remarks"></a>설명  
 오버로드된 연산자는 원본 `ostream` 개체에 대한 참조를 반환합니다. 즉, 다음과 같이 삽입을 결합할 수 있습니다.  
  
```  
cout <<"The date is" <<dt <<flush;  
```  
  
## <a name="see-also"></a>참고 항목  
 [출력 스트림](../standard-library/output-streams.md)

