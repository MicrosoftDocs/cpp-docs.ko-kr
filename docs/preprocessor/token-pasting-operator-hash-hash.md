---
title: 토큰 붙여넣기 연산자 (#) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- '##'
dev_langs:
- C++
helpviewer_keywords:
- preprocessor, operators
- '## preprocessor operator'
ms.assetid: 4f173503-990f-4bff-aef3-ec4d1f1458ef
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6e224c0327a7ba50c3e13ca78d749f41ad4641f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2018
---
# <a name="token-pasting-operator-"></a>토큰 붙여넣기 연산자 (##)
이중 숫자 기호 또는 "토큰 붙여넣기" 연산자 (**##**)을 모두 개체 형식 및 함수 형식 매크로에 사용 되는 "병합" 연산자 라고도 합니다. 이 연산자는 별도의 토큰이 단일 토큰으로 조인되도록 허용하므로 매크로 정의의 첫 번째 토큰 또는 마지막 토큰이 될 수 없습니다.  
  
 매크로 정의의 정식 매개 변수 앞이나 뒤에 토큰 붙여넣기 연산자가 오는 경우 정식 매개 변수가 즉시 확장되지 않은 실제 인수로 바뀝니다. 이러한 교체 이전에 해당 인수에서 매크로 확장이 수행되지 않습니다.  
  
 그런 다음 각 항목에 토큰 붙여넣기 연산자의 *토큰 문자열* 제거 되 고 이전 값과 그 다음 토큰 연결 됩니다. 결과 토큰은 올바른 토큰이어야 합니다. 올바른 토큰인 경우 해당 토큰은 매크로 이름을 나타낼 때 가능한 교체에 대해 검색됩니다. 식별자는 교체하기 전에 연결된 토큰이 프로그램에서 인식될 이름을 나타냅니다. 각 토큰은 프로그램 내 또는 컴파일러 명령줄 등 다른 곳에서 정의된 토큰을 나타냅니다. 연산자 앞이나 뒤의 공백은 선택 사항입니다.  
  
 이 예제에서는 문자열화 연산자와 토큰 붙여넣기 연산자를 모두 사용하여 프로그램 출력을 지정하는 방법을 보여 줍니다.  
  
```  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
```  
  
 매크로가 다음과 같은 숫자 인수로 호출되는 경우  
  
```  
paster( 9 );  
```  
  
 매크로에서 다음을 생성하고  
  
```  
printf_s( "token" "9" " = %d", token9 );  
```  
  
 위는 다음이 됩니다.  
  
```  
printf_s( "token9 = %d", token9 );  
```  
  
## <a name="example"></a>예제  
  
```  
// preprocessor_token_pasting.cpp  
#include <stdio.h>  
#define paster( n ) printf_s( "token" #n " = %d", token##n )  
int token9 = 9;  
  
int main()  
{  
   paster(9);  
}  
```  
  
```Output  
token9 = 9  
```  
  
## <a name="see-also"></a>참고 항목  
 [전처리기 연산자](../preprocessor/preprocessor-operators.md)