---
title: "이전 버전과의 호환성 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility, C run-time libraries
- compatibility, C run-time libraries
- backward compatibility
ms.assetid: cc3175cf-97fd-492f-b329-5791aea63090
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a8ffcc5ab1f50c474ed0ecf4d014419111682b85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="backward-compatibility"></a>이전 버전과의 호환성
제품 버전 간의 호환성을 위해 OLDNAMES.LIB 라이브러리는 이전 이름을 새 이름에 매핑합니다. 예를 들어 `open`은 `_open`에 매핑됩니다. 다음 명령줄 옵션 조합을 사용하여 컴파일할 때만 OLDNAMES.LIB와 명시적으로 연결해야 합니다.  
  
-   `/Zl`(개체 파일에서 기본 라이브러리 이름 생략)과 `/Ze`(기본값, Microsoft 확장 사용)  
  
-   `/link`(링커 컨트롤), `/NOD`(기본 라이브러리 검색 없음) 및 `/Ze`  
  
 컴파일러 명령줄 옵션에 대한 자세한 내용은 [컴파일러 참조](../build/reference/compiler-options.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [호환성](../c-runtime-library/compatibility.md)