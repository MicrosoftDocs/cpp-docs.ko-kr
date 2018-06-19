---
title: 구조체 선언 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure declarations
- anonymous structures
- types [C], declarations
- structure members
- embedded structures
ms.assetid: 5be3be77-a236-4153-b574-7aa77675df7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7d305b2bc74455abd6fdbcfb29ed7ef4103bf19
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391902"
---
# <a name="structure-declarations"></a>구조체 선언
"구조체 선언"은 형식의 이름을 지정하고 다른 형식이 포함될 수 있는 변수 값의 시퀀스(구조체의 "멤버" 또는 "필드")를 지정합니다. "태그"라는 선택적 식별자는 구조체 형식의 이름을 제공하며 구조체 형식에 대한 향후 참조에 사용될 수 있습니다. 해당 구조체 형식의 변수는 해당 형식으로 정의된 전체 시퀀스를 보유합니다. C의 구조체는 다른 언어에서 "레코드"로 알려진 형식과 비슷합니다.  
  
## <a name="syntax"></a>구문  
 *struct-or-union-specifier*:  
 *struct-or-union identifier* opt **{** *struct-declaration-list* **}**  
  
 *struct-or-union identifier*  
  
 *struct-or-union*:  
 **struct**  
  
 **union**  
  
 *struct-declaration-list*:  
 *struct-declaration*  
  
 *struct-declaration-list struct-declaration*  
  
 구조체 콘텐츠는 다음과 같이 정의됩니다.  
  
 *struct-declaration*:  
 *specifier-qualifier-list struct-declarator-list*  **;**  
  
 *specifier-qualifier-list*:  
 *type-specifier specifier-qualifier-list* opt  
  
 *type-qualifier specifier-qualifier-list* opt  
  
 *struct-declarator-list*:  
 *struct-declarator*  
  
 *struct-declarator-list*  **,**  *struct-declarator*  
  
 *struct-declarator*:  
 `declarator`  
  
 구조체 형식의 선언에서는 구조체를 위한 공간이 따로 마련되지 않습니다. 이 선언은 구조체 변수의 향후 선언을 위한 템플릿일 뿐입니다.  
  
 이전에 정의된 *identifier*(태그)를 사용하여 다른 곳에 정의된 구조체 형식을 참조할 수 있습니다. 이 경우 정의가 표시되는 한 *struct-declaration-list*를 반복할 수 없습니다. 구조체에 대한 포인터의 선언과 구조체 형식의 typedef는 구조체 형식이 정의되기 전에 구조체 태그를 사용할 수 있습니다. 그러나 필드 크기를 실제로 사용하기 전에 구조체 정의가 발생해야 합니다. 이는 불완전한 형식 및 형식 태그 정의입니다. 이 정의가 완전해지려면 형식 정의가 동일한 범위에서 나중에 나타나야 합니다.  
  
 *struct-declaration-list*는 구조체 구성원의 형식 및 이름을 지정합니다. *struct-declaration-list* 인수에는 하나 이상의 변수 또는 비트 필드 선언이 포함됩니다.  
  
 *struct-declaration-list*에 선언된 각 변수는 구조체 형식의 구성원으로 정의됩니다. *struct-declaration-list* 내 변수 선언의 형태는 선언에 저장소 클래스 지정자 또는 이니셜라이저를 포함할 수 없다는 점을 제외하고 이 섹션에 설명된 다른 변수 선언과 동일합니다. 구조체 멤버에는 `void` 형식, 불완전한 형식 또는 함수 형식을 제외한 모든 변수 형식을 포함할 수 있습니다.  
  
 자신이 나타나는 구조체의 형식을 가지도록 멤버를 선언할 수 없습니다. 그러나 구조체 형식에 태그가 있는 한 자신이 나타나는 구조체 형식에 대한 포인터로 멤버를 선언할 수 있습니다. 이렇게 하면 연결된 구조체 목록을 만들 수 있습니다.  
  
 구조체는 다른 식별자와 동일한 범위 지정을 따릅니다. 구조체 식별자는 표시 유형이 동일한 다른 구조체, 공용 구조체 및 열거형 태그와 달라야 합니다.  
  
 *struct-declaration-list*의 각 *struct-declaration*은 목록 내에서 고유해야 합니다. 그러나 *struct-declaration-list*에 있는 식별자 이름은 일반 변수 이름이나 다른 구조체 선언 목록의 식별자와 다르지 않아도 됩니다.  
  
 중첩된 구조체는 파일 범위 수준에서 선언된 것처럼 액세스할 수도 있습니다. 예를 들어, 다음과 같은 선언이 있을 경우  
  
```  
struct a  
{  
    int x;  
    struct b  
    {  
      int y;  
    } var2;  
} var1;  
```  
  
 다음 선언은 모두 올바릅니다.  
  
```  
struct a var3;  
struct b var4;  
```  
  
## <a name="examples"></a>예제  
 다음 예제에서는 구조체 선언을 보여 줍니다.  
  
```  
struct employee   /* Defines a structure variable named temp */  
{  
    char name[20];  
    int id;  
    long class;  
} temp;  
```  
  
 `employee` 구조체에는 `name`, `id` 및 `class`라는 세 개의 멤버가 있습니다. `name` 구성원은 20개의 요소를 가진 배열이며, `id` 및 `class`는 각각 `int` 및 **long** 형식이 지정된 단순 구성원입니다. `employee` 식별자는 구조체 식별자입니다.  
  
```  
struct employee student, faculty, staff;  
```  
  
 다음 예제에서는 `student`, `faculty` 및 `staff`라는 세 가지 구조체 변수를 정의합니다. 각 구조체에는 세 가지 멤버로 구성된 동일한 목록이 있습니다. 멤버는 이전 예제에 정의된 구조체 형식인 `employee`를 갖도록 선언됩니다.  
  
```  
struct           /* Defines an anonymous struct and a */  
{                /* structure variable named complex  */  
    float x, y;  
} complex;  
```  
  
 `complex` 구조체에는 **float** 형식이 지정된 `x` 및 `y`라는 두 가지 구성원이 있습니다. 구조체 형식에 태그가 없으므로 해당 형식은 명명되지 않은 형식 또는 익명 형식입니다.  
  
```  
struct sample   /* Defines a structure named x */  
{  
    char c;  
    float *pf;  
    struct sample *next;  
} x;  
```  
  
 구조체의 처음 두 구성원은 `char` 변수와 **float** 값에 대한 포인터입니다. 세 번째 멤버인 `next`는 정의되는 구조체 형식에 대한 포인터로 선언됩니다(`sample`).  
  
 익명 구조체는 명명된 태그가 필요하지 않은 경우 유용할 수 있습니다. 하나의 선언이 모든 구조체 인스턴스를 정의하는 경우가 그렇습니다. 예:  
  
```  
struct  
{  
    int x;  
    int y;  
} mystruct;  
```  
  
 포함 구조체는 종종 익명입니다.  
  
```  
struct somestruct  
{  
    struct    /* Anonymous structure */  
    {  
        int x, y;  
    } point;  
    int type;  
} w;  
```  
  
 **Microsoft 전용**  
  
 컴파일러는 크기가 지정되지 않았거나 크기가 0인 배열을 구조체의 마지막 멤버로 허용합니다. 이는 다양한 상황에서 사용할 때 상수 배열의 크기가 다를 경우 유용할 수 있습니다. 이러한 구조체의 선언은 다음과 같습니다.  
  
 `struct` *identifier***{** *set-of-declarations* *type array-name***[ ];};**  
  
 크기가 지정되지 않은 배열은 구조체의 마지막 멤버로만 나타날 수 있습니다. 크기가 지정되지 않은 배열 선언을 포함하는 구조체는 바깥쪽 구조체에 멤버를 더 이상 선언하지 않는 한 다른 구조체 내에 중첩될 수 있습니다. 구조체에 멤버를 더 선언하는 경우 해당 배열은 허용되지 않습니다. `sizeof` 연산자는 이 형식의 배열이나 배열 자체에 적용될 경우 배열 크기가 0이라고 가정합니다.  
  
 다른 구조체 또는 공용 구조체의 멤버일 경우 선언자 없이 구조체 선언을 지정할 수도 있습니다. 필드 이름은 바깥쪽 구조체로 승격됩니다. 예를 들어, 이름이 없는 구조체는 다음과 같습니다.  
  
```  
struct s  
{  
    float y;  
    struct  
    {  
        int a, b, c;  
    };  
    char str[10];  
} *p_s;  
.  
.  
.  
p_s->b = 100;  /* A reference to a field in the s structure */  
```  
  
 구조체 참조에 대한 자세한 내용은 [구조체 및 공용 구조체 구성원](../c-language/structure-and-union-members.md)을 참조하세요.  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고 항목  
 [선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)