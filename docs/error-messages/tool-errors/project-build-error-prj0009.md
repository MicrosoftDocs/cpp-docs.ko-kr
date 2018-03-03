---
title: "프로젝트 빌드 오류 PRJ0009 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- PRJ0009
dev_langs:
- C++
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0ee183c24cf330b54a335efbd0bbe2b00e18d209
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="project-build-error-prj0009"></a>프로젝트 빌드 오류 PRJ0009
빌드 로그 쓰기 위해 열 수 없습니다.  
  
 **파일이 다른 프로세스에서 열려 있지 않으면 및 쓰기 금지 되어 있는지 확인 합니다.**  
  
 설정한 후의 **빌드 로깅** 속성을 **예** 작성 또는 다시 작성을 수행할 Visual c + + 없습니다 배타 모드에 빌드 로그를 열 수 있습니다.  
  
 검사는 **빌드 로깅** 열어 설정는 **옵션** 대화 상자 (에 **도구** 메뉴를 클릭 **옵션** 명령) 한 다음 선택 하면 **VC + + 빌드** 에 **프로젝트** 폴더입니다. 빌드 파일 BuildLog.htm 라고 하 고 중간 디렉터리 $(IntDir)에 기록 됩니다.  
  
 이 오류의 원인은 다음과 같습니다.  
  
-   Visual c + +의 두 프로세스를 실행 하 고 동시에 둘 다에서 동일한 프로젝트의 구성이 동일을 빌드하려고 합니다.  
  
-   빌드 로그 파일의 파일을 잠그는 프로세스에서 열립니다.  
  
-   사용자에가 파일을 만들 수 있는 권한이 없습니다.  
  
-   현재 사용자 BuildLog.htm 파일에 대 한 쓰기 권한이 없습니다.