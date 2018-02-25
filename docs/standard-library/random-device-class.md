---
title: "random_device 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
dev_langs:
- C++
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d5cb39aa4158f69b1c6e168742e6c7a2b3dcdc97
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/23/2018
---
# <a name="randomdevice-class"></a>random_device 클래스
외부 장치에서 임의 시퀀스를 생성합니다.  
  
## <a name="syntax"></a>구문  
  
```
class random_device {  
public:  
   typedef unsigned int result_type;  
   
   // constructor 
   explicit random_device(const std::string& token = "");
   
   // properties 
   static result_type min();
   static result_type max();
   double entropy() const;
   
   // generate 
   result_type operator()();

   // no-copy functions 
   random_device(const random_device&) = delete;  
   void operator=(const random_device&) = delete;  
   };  
```  

## <a name="members"></a>멤버  
  
|||  
|-|-|  
|[random_device](#random_device)|[entropy](#entropy)|  
|[random_device::operator()](#op_call)||  
  
## <a name="remarks"></a>설명  
이 클래스는 난수의 소스를 설명하고 ISO C++ 표준에 따라 명확하지 않거나 안전을 위해 암호화하는 것이 허용되지만 그럴 필요는 없습니다. Visual Studio 구현 시 생성된 값은 명확하지 않거나 암호화되지만 엔진 및 엔진 어댑터(예: 대부분의 응용 프로그램에 선택되는 빠른 고품질 엔진인 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md))에서 생성된 생성기보다 훨씬 느리게 실행됩니다.  
  
`random_device` 결과는 닫힌 범위 [ `0, 2`<sup>32</sup>) 내에서 균일하게 분포됩니다.  
  
`random_device`는 비블로킹 호출이 수행되지 않을 수도 있습니다.  
  
일반적으로 `random_device`는 엔진 또는 엔진 어댑터를 통해 생성된 다른 생성기를 시드하는 데 사용됩니다. 자세한 내용은 [\<random>](../standard-library/random.md)을 참조하세요.  
  
## <a name="example"></a>예  
다음 코드는 이 클래스의 기본 기능과 예제 결과를 보여줍니다. `random_device`의 명확하지 않은 특성 때문에 **출력** 섹션에 표시된 난수 값은 사용자의 결과와 일치하지 않습니다. 이는 정상적이며 예상된 결과입니다.  
  
```cpp  
// random_device_engine.cpp   
// cl.exe /W4 /nologo /EHsc /MTd   
#include <random>   
#include <iostream>   
using namespace std;  
  
int main()   
{   
    random_device gen;   
  
    cout << "entropy == " << gen.entropy() << endl;   
    cout << "min == " << gen.min() << endl;   
    cout << "max == " << gen.max() << endl;   
  
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
    cout << "a random value == " << gen() << endl;   
}  
```  
  
```Output  
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```  
  
이 예제는 간단한 예제로 이러한 생성기의 일반적인 사용 사례를 대표적으로 보여주지는 않습니다. 보다 대표적인 코드 예제는 [\<random>](../standard-library/random.md)을 참조하세요.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** \<random>  
  
 **네임스페이스:** std  
  
##  <a name="random_device"></a>  random_device::random_device  
생성기를 생성합니다.  
  
```  
random_device(const std::string& = "");
```  
  
### <a name="remarks"></a>설명  
이 생성자는 필요에 따라 생성기를 초기화하여 문자열 매개 변수를 무시합니다. `random_device`를 초기화할 수 없는 경우 [exception](../standard-library/exception-class.md)에서 파생된 구현 정의 형식의 값을 throw합니다.  
  
##  <a name="entropy"></a>  random_device::entropy  
소스의 임의성을 예측합니다.  
  
```  
double entropy() const noexcept;  
```  
  
### <a name="remarks"></a>설명  
이 멤버 함수는 비트 단위로 측정된 소스의 임의성에 대한 예상 값을 반환합니다.  
  
##  <a name="op_call"></a>  random_device::operator()  
난수 값을 반환합니다.  
  
```  
result_type operator()();
```  
  
### <a name="remarks"></a>설명  
구성원 함수 `min()` 및 `max()`에서 결정한 대로 닫힌 간격 [ `min, max`]에 균일하게 분포된 값을 반환합니다. 난수 값을 얻을 수 없는 경우 [exception](../standard-library/exception-class.md)에서 파생된 구현 정의 형식의 값을 throw합니다.  
  
## <a name="see-also"></a>참고 항목  
[\<random>](../standard-library/random.md)

