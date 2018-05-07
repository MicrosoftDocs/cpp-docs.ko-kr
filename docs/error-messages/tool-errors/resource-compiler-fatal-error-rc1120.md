---
title: 리소스 컴파일러 심각한 오류 RC1120 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d117f7b106e14cde2def5477fab5ad0fc92a6411
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="resource-compiler-fatal-error-rc1120"></a>리소스 컴파일러 심각한 오류 RC1120
메모리 부족, 필요한 바이트 수입니다.  
  
 리소스 컴파일러는 힙에 저장 하는 항목에 대 한 저장소 부족 합니다. 일반적으로 이것이 하지 않거나 너무 많은 기호입니다.  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.  
  
1.  Windows 스왑 파일 공간을 늘리십시오. 스왑 파일 공간 증가 하는 방법에 대 한 자세한 내용은 Windows 도움말에서 가상 메모리를 참조 하십시오.  
  
2.  불필요 한 제거 포함 파일, 특히 `#define`지시문과 함수 프로토타입을 합니다.  
  
3.  현재 파일을 두 개 이상의 파일로 분할 하 고 별도로 컴파일하십시오.  
  
4.  다른 프로그램이 나 상당량의 메모리 소비 되는 시스템에서 실행 중인 드라이버를 제거 합니다.