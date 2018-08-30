---
title: 격리 된 응용 프로그램을 C/c + + 빌드 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26a21eb12d9da1caaae3dbd12fe2f3ffd1194bac
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43219095"
---
# <a name="building-cc-isolated-applications"></a>C/C++ 격리된 응용 프로그램 빌드
격리 된 응용 프로그램 side-by-side-어셈블리에만 의존 하 고 매니페스트를 사용 하 여 해당 종속성을 바인딩합니다. Windows;에서 제대로 실행 하기 위해 완전히 격리 된 응용 프로그램에 필요 하지 않습니다. 그러나 완전히 격리 된 응용 프로그램을 만드는에 투자를 하 여 나중에 응용 프로그램을 서비스 하는 경우 시간을 절약할 수 있습니다. 완전히 격리 된 응용 프로그램의 이점에 자세한 내용은 참조 [격리 된 응용 프로그램](/windows/desktop/SbsCs/isolated-applications)합니다.  
  
 Visual c + +를 사용 하 여 네이티브 C/c + + 응용 프로그램을 빌드하면 기본적으로 Visual Studio 프로젝트 시스템에서 Visual c + + 라이브러리 응용 프로그램의 종속성을 설명 하는 매니페스트 파일을 생성 합니다. 경우에 종속성에 응용 프로그램을 Visual Studio를 사용 하 여 다시 빌드하는 즉시는 격리 된 응용 프로그램이 됩니다. 응용 프로그램은 런타임 시 다른 라이브러리를 사용 하는 경우에 설명 된 단계를 수행 하는 side-by-side-어셈블리와 해당 라이브러리를 다시 작성 해야 할 수 있습니다 [C/c + +-side-by-side 어셈블리 빌드](../build/building-c-cpp-side-by-side-assemblies.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [격리 된 응용 프로그램 및 side-by-side-어셈블리의 개념](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [C/C++ 격리된 응용 프로그램 및 side-by-side 어셈블리 빌드](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)