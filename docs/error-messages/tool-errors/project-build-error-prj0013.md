---
title: 프로젝트 빌드 오류 PRJ0013 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0013
dev_langs:
- C++
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aeb0ac9011697c440667a538bd1805780810fb4a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43221561"
---
# <a name="project-build-error-prj0013"></a>프로젝트 빌드 오류 PRJ0013
시스템 리소스가 심각하게 부족할 수 있습니다. 빌드를 시작하는 데 필요한 파이프를 만들 수 없습니다.  
  
 이 오류는 시스템 리소스가 부족함을 나타냅니다. 이 오류를 해결하려면 다른 프로세스/응용 프로그램의 시스템 리소스 사용을 줄입니다.  
  
 보안 수준이 파이프를 만드는 충분 하지 않은 경우에이 오류가 발생할 수 있습니다 (참조 [CreatePipe](https://msdn.microsoft.com/library/windows/desktop/aa365152.aspx)).