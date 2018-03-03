---
title: "C 저장소 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2219ac079fecdb0f21215814885ee831d24f8f6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="c-storage-classes"></a>C 저장소 클래스
변수의 "저장소 클래스"는 항목에 "전역" 또는 "로컬" 수명을 사용할지 여부를 결정합니다. C에서는 "정적" 수명과 "자동" 수명을 호출합니다. 프로그램 실행 전체에 전역 수명을 가진 항목이 존재하고 값을 갖습니다. 모든 함수는 전역 수명을 갖습니다.  
  
 정의된 블록에 실행 제어가 전달될 때마다 자동 변수 또는 로컬 수명을 가진 변수에 새 저장소가 할당됩니다. 실행이 반환될 때 변수는 더 이상 의미 있는 값을 갖지 않습니다.  
  
 C에서는 다음과 같은 저장소 클래스 지정자를 제공합니다.  
  
## <a name="syntax"></a>구문  
 *storage-class-specifier*:  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **__declspec** ( *extended-decl-modifier-seq* ) /* Microsoft 전용 \*/  
  
 `__declspec`를 제외하고 선언에서 *declaration-specifier*에 *storage-class-specifier*를 하나만 사용할 수 있습니다. 저장소 클래스 사양을 만들지 않으면 블록 안의 선언이 자동 개체를 만듭니다.  
  
 **auto** 또는 **register** 지정자를 사용하여 선언된 항목은 로컬 수명을 갖습니다. **static** 또는 `extern` 지정자를 사용하여 선언된 항목은 전역 수명을 갖습니다.  
  
 `typedef` 및 `__declspec`는 다른 *storage-class-specifier* 터미널 4개와 의미 체계가 다르므로 따로 설명합니다. `typedef`에 대한 자세한 내용은 [Typedef 선언](../c-language/typedef-declarations.md)을 참조하세요. `__declspec`에 대한 자세한 내용은 [확장된 저장소 클래스 특성](../c-language/c-extended-storage-class-attributes.md)을 참조하세요.  
  
 또한 소스 파일에서 변수 및 함수 선언의 배치가 저장소 클래스와 표시 유형에 영향을 줍니다. 모든 함수 정의 밖의 선언은 "외부 수준"에 나타나며 함수 정의 안의 선언은 "내부 수준"에 나타납니다.  
  
 각 저장소 클래스 지정자의 정확한 의미는 두 가지 요인에 의해 결정됩니다.  
  
-   선언이 외부 또는 내부 수준에서 나타나는지 여부  
  
-   선언할 항목이 변수인지 함수인지 여부  
  
 [외부 수준 선언에 대한 저장소 클래스 지정자](../c-language/storage-class-specifiers-for-external-level-declarations.md) 및 [내부 수준 선언에 대한 저장소 클래스 지정자](../c-language/storage-class-specifiers-for-internal-level-declarations.md)에서는 종류별 선언의 *storage-class-specifier* 터미널을 설명하고 *storage-class-specifier*를 변수에서 생략할 경우 기본 동작을 설명합니다. [함수 선언이 있는 저장소 클래스 지정자](../c-language/storage-class-specifiers-with-function-declarations.md)에서는 함수에 사용되는 저장소 클래스 지정자를 설명합니다.  
  
## <a name="see-also"></a>참고 항목  
 [선언 및 형식](../c-language/declarations-and-types.md)