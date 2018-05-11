---
title: 리소스 컴파일러 심각한 오류 RC1015 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1015
dev_langs:
- C++
helpviewer_keywords:
- RC1015
ms.assetid: 23f187e1-5538-40b5-9042-edd2888f55c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7744242e44ecfc72ee57ab979969ad81b209e57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1015"></a>리소스 컴파일러 심각한 오류 RC1015
'filename' 파일 열기를 포함할 수 없습니다  
  
 지정한 포함 파일이 존재 하지 않는 열 수 없습니다, 또는 찾을 수 없습니다.  
  
 환경 설정이 유효하고, 올바른 파일 경로를 지정했는지 확인합니다. 충분 한 파일 핸들은 리소스 컴파일러를 사용할 수 있는지 확인 합니다. 네트워크 드라이브에 파일이 있으면 파일을 열 수 있는 권한이 있는지 확인 합니다.  
  
 RC1015는 일반 속성 페이지 -> 리소스 -> 구성 속성에서 추가 포함 디렉터리로 지정된 디렉터리에 포함 파일이 있는 경우에도 발생할 수 있습니다. 포함 파일의 전체 경로를 지정하십시오.  
  
 자세한 내용은 기술 자료 문서 Q326987 참조: RC1015 오류 때 사용 하 여 리소스 보기 경우 포함 경로 너무 깁니다.