---
description: '자세한 정보: dllexport 및 dllimport를 사용 하 여 인라인 c + + 함수 정의'
title: dllexport 및 dllimport로 인라인 C++ 함수 정의
ms.date: 11/04/2016
helpviewer_keywords:
- inline functions [C++], defining
- functions [C++], defining inline
- dllimport attribute [C++], inline functions
- dllexport attribute [C++], inline functions
ms.assetid: 3b48678b-e7b8-4eda-bb46-b5d34dcf7817
ms.openlocfilehash: 158fc5a8fa3805763b1a5abc731abc8905310a27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339477"
---
# <a name="defining-inline-c-functions-with-dllexport-and-dllimport"></a>dllexport 및 dllimport로 인라인 C++ 함수 정의

**Microsoft 전용**

특성을 사용 하 여 함수를 인라인으로 정의할 수 있습니다 **`dllexport`** . 이 경우 프로그램의 임의의 모듈이 함수를 참조하는지 여부와 상관없이 함수가 항상 인스턴스화되어 내보내집니다. 함수는 다른 프로그램에서 가져올 수 있는 것으로 간주됩니다.

**`dllimport`** 특성으로 선언된 함수를 인라인으로 정의할 수도 있습니다. 이 경우 함수는 /Ob 지정에 따라 확장될 수 있으나 인스턴스화되지는 않습니다. 특히 인라인으로 가져온 함수의 주소가 사용된 경우 DLL에 상주하는 함수의 주소가 반환됩니다. 이 동작은 인라인으로 가져온 함수가 아닌 함수의 주소를 사용할 때와 동일합니다.

이러한 규칙은 정의가 클래스 정의 내에서 나타나는 인라인 함수에 적용됩니다. 또한, 인라인 함수의 정적 로컬 데이터 및 문자열은 단일 프로그램(즉, DLL 인터페이스가 없는 실행 파일)과 마찬가지로 DLL과 클라이언트 사이에 같은 ID를 유지합니다.

가져온 인라인 함수를 제공할 때 특별히 주의해야 합니다. 예를 들어 DLL을 업데이트하는 경우 클라이언트에서 DLL의 변경된 버전을 사용하는 것으로 단정하지 마십시오. 적합한 버전의 DLL을 로드하려면 DLL의 클라이언트를 다시 빌드하십시오.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
