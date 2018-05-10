---
title: 선언 개요 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cd8670815b908f66a6e2ed400bc87ca07c369ee4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="overview-of-declarations"></a>선언자 개요
"선언"은 식별자 집합에 대한 해석 및 특성을 지정합니다. 식별자에 의해 이름이 지정된 개체나 함수용으로 저장소를 예약하는 선언은 "정의"라고도 합니다. 변수, 함수 및 형식에 대한 C 선언에는 다음과 같은 구문이 사용됩니다.  
  
## <a name="syntax"></a>구문  
 `declaration`:  
 *declaration-specifiers* *attribute-seq*opt*init-declarator-list*opt **;**  
  
 /\* *attribute-seq*opt는 Microsoft 전용임 */  
  
 *declaration-specifiers*:  
 *storage-class-specifier declaration-specifiers*opt  
  
 *type-specifier declaration-specifiers*opt  
  
 *type-qualifier declaration-specifiers*opt  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init-declarator-list* , *init-declarator*  
  
 *init-declarator*:  
 *declarator*  
  
 *declarator*  **=**  *initializer*  
  
> [!NOTE]
>  이 `declaration` 구문은 후속 섹션에서 반복되지 않습니다. 일반적으로 후속 섹션의 구문은 `declarator` 비단말로 시작됩니다.  
  
 *init-declarator-list*의 선언에는 명명 중인 식별자가 포함됩니다. *init*는 이니셜라이저의 약어입니다. *init-declarator-list*는 쉼표로 구분된 일련의 선언자로서 각 선언자에는 추가 형식 정보나 이니셜라이저 또는 이 두 가지가 모두 있을 수 있습니다. `declarator`에는 선언 중인 식별자(있는 경우)가 포함됩니다. *declaration-specifiers* 비터미널은 일련의 형식 및 저장소 클래스 지정자로 구성됩니다. 이러한 지정자는 선언자가 나타내는 엔터티의 링크, 저장 기간 및 최소한의 형식 부분을 나타냅니다. 따라서 선언은 저장소 클래스 지정자, 형식 지정자, 형식 한정자, 선언자 및 이니셜라이저의 조합으로 구성됩니다.  
  
 선언에는 *attribute-seq*에 나열된 선택적 특성이 하나 이상 포함될 수 있습니다. *seq*는 시퀀스의 약어입니다. 이러한 Microsoft 전용 특성은 이 설명서 전반에 설명되어 있는 다양한 기능을 수행합니다.  
  
 변수 선언에 대한 일반적인 양식에서 *type-specifier*는 변수의 데이터 형식을 제공합니다. *type-specifier*는 형식이 **const** 또는 `volatile`에 의해 수정될 때처럼 복합형이 될 수 있습니다. `declarator`는 변수 이름을 제공합니다. 이러한 변수 이름은 배열이나 포인터 형식을 선언하기 위해 수정할 수 있습니다. 예를 들어 개체에 적용된  
  
```  
int const *fp;  
```  
  
 이 예제는 `fp`라는 이름의 변수를 수정할 수 없는 (**const**) `int` 값에 대한 포인터로 선언합니다. 쉼표로 구분된 여러 선언자를 사용하여 한 선언에서 둘 이상의 변수를 정의할 수 있습니다.  
  
 선언에 선언자가 하나 이상 있거나 형식 지정자가 구조체 태그, 공용 구조체 태그 또는 열거형의 멤버를 선언해야 합니다. 선언자는 식별자에 대한 나머지 정보를 제공합니다. 선언자는 대괄호(**[ ]**), 별표(**\***) 또는 괄호( **( )** )로 수정하여 배열, 포인터 또는 함수 형식을 각각 선언할 수 있는 식별자입니다. 단순 변수(문자, 정수 및 부동 소수점 항목) 또는 단순 변수의 구조체 및 공용 구조체를 선언할 때 `declarator`는 식별자로만 사용됩니다. 선언자에 대한 자세한 내용은 [선언자 및 변수 선언](../c-language/declarators-and-variable-declarations.md)을 참조하세요.  
  
 모든 정의는 암시적으로 선언이지만 모든 선언이 정의인 것은 아닙니다. 예를 들어 `extern` 저장소 클래스 지정자로 시작되는 변수 선언은 "정의" 선언이라기 보다는 "참조" 선언입니다. 외부 변수가 정의 전에 참조되거나 사용된 소스 파일과 다른 소스 파일에 정의된 경우 `extern` 선언이 필요합니다. 저장소는 "참조" 선언에 의해 할당되지 않으며 선언에서 변수를 초기화할 수도 없습니다.  
  
 저장소 클래스 또는 형식(또는 둘 다)은 변수 선언에 필요합니다. `__declspec`을 제외하고, 선언에는 하나의 저장소 클래스 지정자만 허용되며 각 컨텍스트에서는 일부 저장소 클래스 지정자만 허용됩니다. `__declspec` 저장소 클래스는 다른 저장소 클래스 지정자에 사용할 수 있으며 두 번 이상 허용됩니다. 선언의 저장소 클래스 지정자는 선언된 항목이 저장 및 초기화되는 방법과 프로그램에서 해당 항목을 참조할 수 있는 부분에 영향을 줍니다.  
  
 C로 정의된 *storage-class-specifier* 터미널에는 **auto**, `extern`, **register**, **static** 및 `typedef`가 포함됩니다. 또한 Microsoft C에는 *storage-class-specifier* 터미널 `__declspec`이 포함됩니다. `typedef`와 `__declspec`을 제외한 모든 *storage-class-specifier* 터미널에 대해서는 [저장소 클래스](../c-language/c-storage-classes.md)에 설명되어 있습니다. `typedef`에 대한 내용은 [Typedef 선언](../c-language/typedef-declarations.md)을 참조하세요. `__declspec`에 대한 내용은 [확장된 저장소 클래스 특성](../c-language/c-extended-storage-class-attributes.md)을 참조하세요.  
  
 소스 프로그램 내 선언의 위치 및 기타 변수 선언의 유무는 변수 수명을 결정하는 중요한 요소입니다. 재선언은 여러 개 있을 수 있지만 정의는 하나만 있어야 합니다. 하지만 정의는 둘 이상의 변환 단위에 있을 수 있습니다. 내부 링크가 있는 개체의 경우에는 내부적으로 연결된 개체가 변환 단위별로 고유하므로 이 규칙이 각 변환 단위에 따로 적용됩니다. 외부 링크가 있는 개체의 경우 이 규칙은 전체 프로그램에 적용됩니다. 표시 유형에 대한 자세한 내용은 [수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)를 참조하세요.  
  
 형식 지정자는 식별자의 데이터 형식에 대한 일부 정보를 제공합니다. 기본 형식 지정자는 `int`입니다. 자세한 내용은 [형식 지정자](../c-language/c-type-specifiers.md)를 참조하세요. 형식 지정자는 형식 태그, 구조체 및 공용 구조체 구성 요소 이름 및 열거형 상수도 정의합니다. 자세한 내용은 [열거형 선언](../c-language/c-enumeration-declarations.md), [구조체 선언](../c-language/structure-declarations.md) 및 [공용 구조체 선언](../c-language/union-declarations.md)을 참조하세요.  
  
 *type-qualifier* 터미널에는 **const**와 `volatile`이라는 두 가지가 있습니다. 이러한 한정자는 l-value를 통해 해당 형식의 개체에 액세스하는 경우에만 관련된 형식의 추가 속성을 지정합니다. **const** 및 `volatile`에 대한 자세한 내용은 [형식 한정자](../c-language/type-qualifiers.md)를 참조하세요. l-value 정의에 대한 내용은 [L-Value 및 R-Value 식](../c-language/l-value-and-r-value-expressions.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [C 언어 구문 요약](../c-language/c-language-syntax-summary.md)   
 [선언 및 형식](../c-language/declarations-and-types.md)   
 [선언 요약](../c-language/summary-of-declarations.md)