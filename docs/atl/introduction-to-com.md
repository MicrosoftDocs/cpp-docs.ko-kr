---
title: COM 소개 | Microsoft Docs
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 938d0c45cae5ec9a2988f77f539af1a3d5513b83
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-com"></a>COM 소개
COM은 ActiveX 컨트롤과 OLE의 기반이 되는 "개체 모델"입니다.  COM을 이용하면 개체의 기능을 다른 구성요소나 응용 프로그램 호스팅으로 노출이 가능합니다. 이는 객체 자신을 노출시키는 것과 프로세스 및 네트워크를 통한 노출 작동 방식 모두를 정의 합니다. 또한 COM은 개체의 수명 주기를 정의합니다.  
  
 COM의 기본 개념:  
  
-   [인터페이스](../atl/interfaces-atl.md) — 개체가 자신의 기능을 제공하는 메커니즘입니다.  
  
-   [IUnknown](../atl/iunknown.md) — 다른 모든 것의 기반이 되는 기본 인터페이스로, COM을 통해 실행하는 참조 횟수 및 쿼리 메커니즘을 구현합니다.  
  
-   [참조 횟수](../atl/reference-counting.md) — 개체(엄격한 의미로 인터페이스)가 더이상 사용되지 않아 자신을 소멸시키고자 할 때 판단하는 기술입니다.를 제거 하는 방법입니다.  
  
-   [QueryInterface](../atl/queryinterface.md) — 지정된 인터페이스에 대한 개체를 쿼리하는 데 사용하는 메서드.  
  
-   [마샬링](../atl/marshaling.md) — 스레드, 프로세스 및 네트워크 경계에서 개체를 사용할 수 있도록 하는 메커니즘으로 위치 독립성을 구현합니다.  
  
-   [집계](../atl/aggregation.md) — 개체가 다른 개체를 사용할 수 있도록 하는 방법을 사용합니다.  
  
## <a name="see-also"></a>참고 항목  
 [COM 및 ATL 소개](../atl/introduction-to-com-and-atl.md)   
 [구성 요소 개체 모델](http://msdn.microsoft.com/library/windows/desktop/ms694363)

