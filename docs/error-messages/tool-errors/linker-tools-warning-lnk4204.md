---
title: 링커 도구 경고 LNK4204 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4204
dev_langs:
- C++
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f000fa42357a299c943eda0cd5f8697aee138f4a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4204"></a>링커 도구 경고 LNK4204
'filename' 디버깅 모듈 참조에 대 한 정보가 없습니다. 디버그 정보가 없는 것 처럼 개체를 링크 합니다.  
  
 .Pdb 파일에 잘못 된 서명이 있습니다. 디버그 정보 없이 개체를 연결 하는 링커 계속 됩니다. 사용 하 여 개체 파일을 다시 컴파일할 수도 있습니다는 [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 옵션입니다.  
  
 LNK4204는 라이브러리의 개체 중 일부를 더 이상 존재 하는 파일을 참조 하는 경우에 발생할 수 없습니다. 이러한 상황은 솔루션을 구축할 때 예를 들어 개체 파일 삭제 하 고 컴파일 오류 때문에 다시 작성 하지 수도 있습니다. 로 컴파일하여이 경우 **/Z7**, 또는 **/Fd**단일 파일 당-라이브러리 (하지 않은 기본.pdb 파일 이름)을 참조 하도록 개체를 업데이트 합니다.  자세한 내용은 [/Fd(프로그램 데이터베이스 파일 이름)](../../build/reference/fd-program-database-file-name.md)를 참조하세요.  소스 제어 시스템에서 업데이트 될 때마다.pdb 라이브러리와 함께 저장 되도록 합니다.