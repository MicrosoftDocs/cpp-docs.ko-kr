---
description: '자세한 정보: 디버깅 및 예외 클래스'
title: 디버깅 및 예외 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 2c14ea8d51fd1b63427ad1495e711a906e013ea4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291118"
---
# <a name="debugging-and-exception-classes"></a>디버깅 및 예외 클래스

이러한 클래스는 동적 메모리 할당을 디버깅하고 예외가 throw된 함수에서 예외가 catch된 함수로 예외 정보를 전달하기 위한 지원을 제공합니다.

[MFC 응용 프로그램 디버깅](/visualstudio/debugger/mfc-debugging-techniques)에 설명 된 대로 개발 중에 [CDumpContext](reference/cdumpcontext-class.md) 및 [cmemorystate](reference/cmemorystate-structure.md) 클래스를 사용 하 여 디버깅을 지원할 수 있습니다. [CRuntimeClass](reference/cruntimeclass-structure.md) 를 사용 하 여 [Run-Time 클래스 정보 액세스](accessing-run-time-class-information.md)문서에 설명 된 대로 런타임에 개체의 클래스를 확인 합니다. 프레임워크는 `CRuntimeClass`를 사용해서 특정 클래스의 개체를 동적으로 만듭니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
